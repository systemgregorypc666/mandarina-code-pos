# 🍊 Mandarina Code POS — Documentación Técnica del Proyecto

**Sistema de Punto de Venta y Control de Inventarios**  
Desarrollado por **System Gregory PC** (RIF: V-165419762)  
Programador: **José Gregorio Hernández Calderón**  
Ubicación: San Cristóbal, Estado Táchira - Venezuela  
Soporte: 0416-1177334 / 0276-3468123

---

## 📋 Resumen del Desarrollo

**Mandarina Code POS** es una solución informática de escritorio diseñada en **Visual Basic .NET** que utiliza **SQLite** como motor de base de datos local de alto rendimiento. El sistema está optimizado para la gestión completa de ventas en tiempo real, administración de inventarios, facturación ligera mediante impresoras térmicas y control de accesos mediante licenciamiento alfanumérico.

---

## 🛠️ Estructura del Proyecto y Formularios Creados

* **`FormLogin.vb`**: Ventana de autenticación de usuarios y punto de acceso al control de licencias del sistema.
* **`PanelContenedor.vb`**: Interfaz principal (MDI/Dashboard) que hospeda los módulos operativos, barra de navegación y accesos directos.
* **`FormVentas.vb`**: Módulo de caja y cobro rápido con integración a lectores de código de barras.
* **`FormProductos.vb`**: Gestión del catálogo (Altas, Bajas, Modificaciones y Ajuste de Stock).
* **`FormAnulaciones.vb`**: Módulo de auditoría para la cancelación y reversión de transacciones.
* **`FormAcercaDe.vb`**: Módulo institucional de marca (**System Gregory PC**), datos de contacto y validación de la clave de licencia anual.

---

## ⚙️ Configuración y Comandos de Entorno en Visual Studio

### 1. Requisitos de Compilación
* **Entorno:** Microsoft Visual Studio
* **Lenguaje:** Visual Basic .NET (`.NET Framework 4.7.2` o superior)
* **Librería de Base de Datos:** `System.Data.SQLite.dll`

### 2. Comandos y Atajos Principales en Visual Studio
| Acción | Atajo de Teclado / Comando | Descripción |
| :--- | :--- | :--- |
| **Compilar Solución** | `Ctrl` + `Shift` + `B` | Genera los binarios del programa sin ejecutar. |
| **Ejecutar en Depuración** | `F5` | Arranca la aplicación en modo `Debug`. |
| **Ejecutar sin Depurar** | `Ctrl` + `F5` | Ejecuta la aplicación a velocidad normal. |
| **Limpiar Solución** | Menú *Compilar* > *Limpiar solución* | Elimina archivos temporales de compilación anteriores. |
| **Cambiar Entorno** | Seleccionar **Release** | Prepara la compilación final para entrega al cliente. |

---

## 📦 Estructura de la Base de Datos (SQLite)

El programa gestiona los datos de forma autónoma mediante el archivo de base de datos local (`mandarina.db`):

```sql
-- Tabla de Usuarios
CREATE TABLE IF NOT EXISTS usuarios (
    id_usuario INTEGER PRIMARY KEY AUTOINCREMENT,
    usuario TEXT UNIQUE NOT NULL,
    clave TEXT NOT NULL,
    rol TEXT NOT NULL
);

-- Tabla de Productos
CREATE TABLE IF NOT EXISTS productos (
    id_producto INTEGER PRIMARY KEY AUTOINCREMENT,
    codigo TEXT UNIQUE NOT NULL,
    nombre TEXT NOT NULL,
    precio DECIMAL(10,2) NOT NULL,
    stock INTEGER NOT NULL
);

-- Tabla de Ventas
CREATE TABLE IF NOT EXISTS ventas (
    id_venta INTEGER PRIMARY KEY AUTOINCREMENT,
    fecha DATETIME DEFAULT CURRENT_TIMESTAMP,
    total DECIMAL(10,2) NOT NULL,
    usuario TEXT NOT NULL
);


🔐 Licenciamiento del Software
El sistema utiliza un esquema de clave de activación alfanumérica estructurado de la siguiente forma:

Formato de Clave: SGPC-Y5UY-MANDARINA-365D

Ejemplo de Activación: SGPC-6586-MANDARINA-365D

Validez: Licencia de uso continuo por 1 año gestionada desde FormAcercaDe.vb.

🚀 Despliegue e Instalación en Cliente
Compilar el proyecto en modo Release.

Copiar el contenido de la carpeta bin/Release/ al pendrive.

Copiar la carpeta completa en la PC del cliente en la ruta: C:\SystemGregoryPC\MandarinaPOS\.

Crear acceso directo en el escritorio apuntando a MandarinaCodePOS.exe.

Asignar icono institucional (.ico) de 108 KB.


---

### ¿Cómo agregar este archivo directamente a tu proyecto en Visual Studio?

1. En Visual Studio, ve al explorador a la derecha (**Explorador de soluciones**).
2. Haz clic derecho sobre el nombre de tu proyecto (`MandarinaCodePOS`).
3. Selecciona **Agregar** > **Nuevo elemento...**
4. Selecciona **Archivo de texto** (o *Text File*), nómbralo **`DOCUMENTACION.md`** y haz clic en **Agregar**.
5. Copia y pega el texto de arriba dentro del archivo y presiona `Ctrl + S` para guardar.

De esta forma, tendrás la guía técnica y el resumen completo guardado dentro del mismo código de Visual Studio.


