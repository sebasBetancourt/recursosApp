
# 📚 recursosApp

## 📄 Descripción  
Aplicación web para que los usuarios registren su progreso al ver **series**, **películas** y **libros**.  
Permite filtrar por:  
- Estado: ✅ Terminado / 🔄 En progreso / ⏳ Pendiente  
- Formato: 📺 Serie / 🎬 Película / 📖 Libro  
- Plataforma: 🌐 Netflix, Amazon, Disney+, Físico, etc.

---

## 🛠️ Funcionalidades CRUD

### 1️⃣ Mostrar bases de datos  
📌 *Muestra todas las bases de datos existentes en MongoDB.*
```bash
show dbs
```
![Captura desde 2025-06-05 20-45-22](https://github.com/user-attachments/assets/969b34b9-6f6a-4c5f-8002-225b6257a90a)

---

### 2️⃣ Crear base de datos `AppRecursos`  
📌 *Cambia el contexto a la base de datos `AppRecursos` (la crea si no existe).*
```bash
use AppRecursos
```
![Captura desde 2025-06-05 20-47-38](https://github.com/user-attachments/assets/b6a9a621-2d5a-4ef5-a49c-46688971f9c6)

---

### 3️⃣ Crear colección `recursos`  
📌 *Crea una colección donde se guardarán los registros.*
```bash
db.recursos.createCollection("recursos")
```
![Captura desde 2025-06-05 20-50-06](https://github.com/user-attachments/assets/b1d78f8e-ab05-4868-b92d-d5c1ca2c3178)

---

### 4️⃣ Insertar datos en la colección  
📌 *Agrega uno o varios documentos (series, películas, libros) a la colección.*
```bash
db.recursos.insertMany([
  {
    _id: ObjectId('68413445293b6938d43125b9'),
    nombre: 'To Kill a Mockingbird',
    genero: 'drama',
    plataforma: 'Físico',
    estado: {
      progreso: false,
      terminado: true,
      pendiente: false
    },
    formato: {
      serie: false,
      pelicula: false,
      libro: true
    },
    fechaTerminacion: '2017-12-05T14:00:00Z',
    valoracion: 5,
    reseña: 'Clásico de la literatura.'
  }
  // ...Más datos aquí
])
```
![Captura desde 2025-06-05 21-04-20](https://github.com/user-attachments/assets/e8f7f431-8a88-45b2-972f-e8e61350f888)

---

## 🔍 Filtros y Búsquedas

### 🎯 Por Estado

#### ✅ Terminado  
📌 *Muestra todos los recursos que ya han sido completados.*
```bash
db.recursos.find({ "estado.terminado": true })
```

#### 🔄 En Progreso  
📌 *Muestra los recursos que están siendo consumidos actualmente.*
```bash
db.recursos.find({ "estado.progreso": true })
```

#### ⏳ Pendiente  
📌 *Muestra los recursos aún no iniciados.*
```bash
db.recursos.find({ "estado.pendiente": true })
```

---

### 🎞️ Por Formato

#### 🎬 Películas  
📌 *Filtra los recursos cuyo formato es película.*
```bash
db.recursos.find({ "formato.pelicula": true })
```

#### 📺 Series  
📌 *Filtra los recursos cuyo formato es serie.*
```bash
db.recursos.find({ "formato.serie": true })
```

#### 📖 Libros  
📌 *Filtra los recursos cuyo formato es libro.*
```bash
db.recursos.find({ "formato.libro": true })
```

---

### 🌐 Por Plataforma

#### 🟥 Netflix  
📌 *Filtra recursos disponibles en Netflix.*
```bash
db.recursos.find({ plataforma: "Netflix" })
```

#### 📘 Físico  
📌 *Filtra recursos en formato físico (libros).*
```bash
db.recursos.find({ plataforma: "Físico" })
```

#### 🟦 Disney+  
📌 *Filtra recursos disponibles en Disney+.*
```bash
db.recursos.find({ plataforma: "Disney+" })
```
