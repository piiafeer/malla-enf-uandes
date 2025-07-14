<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Malla Interactiva - Enfermería</title>
  <style>
    body { font-family: sans-serif; background: #f5f5f5; margin: 0; padding: 20px; }
    h1 { text-align: center; }
    .semestre { margin-bottom: 20px; padding: 15px; background: white; border-radius: 10px; box-shadow: 0 2px 4px rgba(0,0,0,0.1); }
    .semestre h2 { margin-top: 0; cursor: pointer; }
    ul { list-style: none; padding: 0; }
    li { margin-bottom: 10px; padding: 10px; border-radius: 8px; background: #eee; display: flex; justify-content: space-between; align-items: center; }
    button { border: none; padding: 6px 12px; border-radius: 6px; cursor: pointer; }
    .pendiente { background-color: #ffd6d6; }
    .curso { background-color: #fff8cc; }
    .aprobado { background-color: #d6ffd6; }
  </style>
</head>
<body>
  <h1>Malla Interactiva - Enfermería</h1>
  <div id="contenedor"></div>
  <script>
    const malla = [
      ["Ciencias Básicas para la Salud", "Anatomía e Histología", "Primeros Auxilios", "Antropología I", "Teología I", "Fundamentos de Enfermería"],
      ["Microbiología y Parasitología", "Integrado Fisiología, Fisiopatología y Farmacología I", "Proceso Enfermero en el Ciclo Vital", "Antropología II", "Programa Optativo Estudios Generales"],
      ["Integrado Fisiología, Fisiopatología y Farmacología II", "Cuidados de Enfermería I", "Bioestadística", "Teología II", "Minor 1", "Educación para la Salud I"],
      ["Desarrollo Personal y Liderazgo", "Sociedad y Cultura", "Cuidados de Enfermería II", "Introducción a la Enfermería Comunitaria", "Inglés Técnico para la Salud", "Epidemiología Salud Pública", "Minor 2", "Relación de Ayuda", "Educación para la Salud II"],
      ["Enfermería y Envejecimiento", "Minor 3", "Enfermería Clínica del Adulto y Persona Mayor", "Enfermería Comunitaria del Adulto y Persona Mayor", "Metodología de la Investigación"],
      ["Enfermería de la Mujer", "Enfermería Comunitaria del Niño y Adolescente", "Práctica Basada en la Evidencia", "Enfermería Clínica del RN, Niño y Adolescente"],
      ["Ética", "Ética Profesional Aplicada", "Cuidados de Enfermería en la Etapa Final de la Vida", "Innovación y Tecnologías en Salud", "Enfermería Gerontogeriátrica en la Comunidad", "Programa Optativo Estudios Generales", "Teología III", "Gestión y Administración en Instituciones de Salud"],
      ["Enfermería en Situaciones de Urgencia", "Enfermería en Salud Mental y Psiquiatría", "Gestión y Liderazgo en Equipos de Salud", "Seminario de Investigación", "Programa Optativo Estudios Generales"],
      ["Internado Profesional de Área Específica", "Internado Profesional Comunitario", "Internado Profesional Intrahospitalario Adulto o Pediatría"],
      ["Examen de Título"]
    ];

    const estados = ["Pendiente", "En curso", "Aprobado"];
    const contenedor = document.getElementById("contenedor");

    malla.forEach((ramos, idx) => {
      const semestreDiv = document.createElement("div");
      semestreDiv.className = "semestre";
      const titulo = document.createElement("h2");
      titulo.textContent = `Semestre ${idx + 1}`;
      const lista = document.createElement("ul");

      ramos.forEach((ramo) => {
        const item = document.createElement("li");
        item.textContent = ramo;
        const boton = document.createElement("button");
        boton.textContent = "Pendiente";
        boton.className = "pendiente";
        boton.onclick = () => {
          const actual = estados.indexOf(boton.textContent);
          const siguiente = (actual + 1) % estados.length;
          boton.textContent = estados[siguiente];
          boton.className = estados[siguiente].toLowerCase();
        };
        item.appendChild(boton);
        lista.appendChild(item);
      });

      semestreDiv.appendChild(titulo);
      semestreDiv.appendChild(lista);
      contenedor.appendChild(semestreDiv);
    });
  </script>
</body>
</html>
# malla-enf-uandes
