# Motor de Envío de Correos — Base Operativa  

## 1. Objetivo

Implementar un mecanismo reutilizable de envío automatizado de correos utilizando:

- Power Automate
- Excel Online como fuente de datos
- Outlook (buzón Comunicaciones)
- Plantilla HTML responsive

El objetivo es habilitar campañas de comunicación administrables por negocio.

---

## 2. Resultado logrado (Estado actual)

El flujo se encuentra operativo y permite:

- Leer contactos desde tabla estructurada en Excel
- Ejecutar envío uno a uno mediante loop (Aplicar a cada uno)
- Personalizar contenido con tokens dinámicos (ej: NOMBRE)
- Usar plantilla HTML real (email-safe)
- Enviar desde buzón de Comunicaciones
- Validar conexiones (Excel / Outlook)
- Detectar errores de autorización
- Confirmar entrega de correos

El mecanismo ya envía correos correctamente.

---

## 3. Arquitectura implementada

### Fuente de datos
Excel Online — Tabla:

tbl_contactos

Campos actuales:

- NOMBRE
- email
- TIPO_CONTACTO
- EMPRESA
- ENVIO_ESTADO
- ENVIO_FECHA
- ENVIO_ERROR

---

### Flujo Power Automate

1. Recurrence (trigger)
2. Enumerar filas de una tabla (Excel)
3. Aplicar a cada uno (loop)
4. Enviar correo electrónico (V2)
   - Destinatario → email
   - Asunto → campaña
   - Cuerpo → HTML template
   - Remitente → Comunicaciones (Send as)

---

## 4. Plantilla HTML base

Se implementó plantilla email-safe basada en tablas.

Características:

- Responsive simple
- Inline CSS
- Logo remoto (URL pública)
- Personalización por token
- Footer corporativo

Esta plantilla será versionada.

---

## 5. Problemas detectados durante implementación

### Técnicos

- Conexiones Outlook expiradas → Unauthorized
- Filas en blanco generan errores de envío
- HTML mostrado como texto → no usar modo texto plano
- Permisos Send As necesarios para buzón Comunicaciones
- Power Automate requiere array válido (value)

---

### Operativos

- Riesgo de reenvío
- No existe control de estado aún
- No hay registro de errores por fila
- No hay batch sending
- No hay gobernanza de campañas

---

## 6. Estado funcional actual

✔ Envío operativo  
✔ Plantilla funcional  
✔ Token dinámico funcionando  
✔ Envío desde buzón correcto  
✔ Base reutilizable creada  

Esto ya constituye un motor de campañas mínimo.

---

## 7. Próxima fase (Pendiente)

### Modelo de control en Excel

Definir uso de:

ENVIO_ESTADO  
Valores sugeridos:
- PENDIENTE
- ENVIADO
- ERROR
- OMITIDO

ENVIO_FECHA  
Fecha real del envío.

ENVIO_ERROR  
Mensaje técnico capturado.

---

### Flujo

Agregar:

- Actualizar fila después del envío
- Try / Catch pattern
- No detener campaña por error individual
- Filtro de pendientes
- Reintentos

---

### Escalabilidad

Diseñar:

- Envío por tandas (batch)
- Throttling
- Control de límites Outlook
- Campañas grandes
- Programación

---

## 8. Alcance habilitado (muy importante)

Este motor permite:

- Aniversarios
- Cumpleaños
- Avisos internos
- Comunicados
- Marketing
- Newsletter
- Campañas masivas
- Automatizaciones futuras

Es base de comunicación organizacional.

---

## 9. Principio de diseño adoptado

Excel = fuente administrable por negocio  
Power Automate = motor de ejecución  
HTML = capa de presentación  
Outlook = canal  

Separación de responsabilidades.

---

## 10. Riesgos conocidos

- Reenvíos sin control de estado
- Bloqueo Outlook si volumen alto
- Permisos Send As incorrectos
- Datos incompletos
- Falta de observabilidad

---

## 11. Siguiente documento sugerido

Motor de campañas — Modelo de estados  
Batch sending strategy  
Plantillas versionadas  
Gobernanza de campañas  
Tracking / métricas  

---

## 12. Estado del arte

Se ha completado la base operativa del motor.

Este es el paso más importante.

A partir de aquí el trabajo es evolución, no construcción.

---
