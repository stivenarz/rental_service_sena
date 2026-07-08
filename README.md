# Rental Service Marketplace

Prototipo de interfaz gráfica para una plataforma de intermediación de servicios locativos (plomería, electricidad, mantenimiento del hogar, etc.), que conecta **clientes** que buscan un servicio con **proveedores** que lo ofrecen.

Este repositorio corresponde a la evidencia de diseño de prototipo del programa **Tecnología en Análisis y Desarrollo de Software** (Ficha 3336184, SENA - 2026).

**Autores:**
- Stiven Ariza Rodríguez
- John Fredy Quiroz Gómez
- Juan Esteban Bejarano Hernández
- Daissy Maria Moreno Ramírez
- Félix Alejandro Ballesteros Florez

## Estructura del sitio

El prototipo está compuesto por pantallas HTML estáticas, navegables entre sí mediante el menú superior. El mapa de navegación sigue un modelo de **árbol jerárquico**: una raíz de exploración pública (portada, autenticación y buscador) que se desprende en flujos privados independientes según el rol del usuario (Cliente, Proveedor, Administrador).

| # | Pantalla | Archivo | Rol |
|---|----------|---------|-----|
| 1 | Portada | `index.html` | Público |
| 2 | Autenticación (Login / Registro unificado) | `login.html` | Público |
| 3 | Buscador avanzado de servicios | `buscador.html` | Cliente |
| 4 | Dashboard de control de servicios | `dashboard.html` | Cliente / Proveedor |
| 5 | Perfil público y reputación del proveedor | `perfil.html` | Cliente / Proveedor |
| 6 | Publicación de servicios | `publicar-servicio.html` | Proveedor |
| 7 | Pasarela de pagos y checkout de facturación | `pagos.html` | Cliente |
| 8 | Calificación y feedback del servicio | `calificacion.html` | Cliente |
| 9 | Panel de administración general | `admin.html` | Administrador |


## Estilo del template

El diseño sigue lineamientos de un sistema de componentes tipo *Material Design*, con las siguientes pautas por tipo de pantalla (definidas en la evidencia EV03 - Elaboración de interfaz gráfica y mapa de navegación):

- **Autenticación:** enfoque minimalista, layout de dos columnas (imagen de marca + tarjeta flotante blanca), selector de pestañas (tabs) para alternar entre iniciar sesión y crear cuenta, campos de texto con bordes redondeados y botón principal sólido.
- **Dashboard:** navegación lateral fija (navigation rail), contenido en grilla, tarjetas de estado (KPIs) y tabla de datos, con chips de color para estados (verde = aprobado, amarillo = pendiente).
- **Perfil de proveedor:** columna central ancha, widget de reputación con calificación numérica, estrellas y barra de progreso, chips de habilidades verificadas y lista de comentarios.
- **Buscador de servicios:** mobile-first, barra de búsqueda fija con filtros desplegables, filtros deslizables horizontales y tarjetas de servicio con botón flotante de acción rápida.
- **Pagos / checkout:** flujo guiado por pasos (stepper), campos con validación en tiempo real y tipografía grande por accesibilidad, resumen de factura en panel lateral fijo.
- **Panel de administración:** header distintivo `[ADMIN]`, sidebar de módulos del sistema, KPIs globales y tabla de auditoría.

Todas las pantallas comparten el mismo encabezado (logo + nav), pie de página (derechos reservados, redes sociales, política de privacidad) y componentes base: `text-field`, `btn-filled`, `surface-card`.

## Paleta de colores

Paleta oficial definida en la guía de estilo (EV03 - "Paleta de colores"):

| Token | Hex | Uso |
|-------|-----|-----|
| Primary | `#0F172A` | Color principal de marca, botones e inversos |
| Secondary | `#3B82F6` | Acciones secundarias, enlaces, foco de campos |
| Tertiary | `#10B981` | Acciones de confirmación/éxito (ej. publicar, aprobar) |
| Neutral | `#64748B` | Textos secundarios, bordes, elementos deshabilitados |

**Tipografía:**

| Uso | Fuente |
|-----|--------|
| Headline (títulos) | Manrope |
| Body (texto de cuerpo) | Inter |
| Label (etiquetas, datos técnicos) | JetBrains Mono |

> ⚠️ **Nota de implementación:** las variables CSS actuales en `login.html` e `index.html` usan `--primary-color: #9F172A` y `--secondary-color: #3882F6`, que no coinciden exactamente con la paleta oficial (`#0F172A` / `#3B82F6`) ni incorporan aún los tokens Tertiary/Neutral ni las fuentes Manrope/JetBrains Mono (se usa Inter para todo el texto). Se deja documentado para decidir si se ajusta el CSS a la paleta oficial en una futura iteración.

## Trazabilidad

Cada pantalla está vinculada a un requisito funcional (IEEE 830) del documento de especificación del proyecto, por ejemplo RF-01 (acceso seguro) para Autenticación o RF-04 (búsqueda y filtrado) para el Buscador de servicios.
