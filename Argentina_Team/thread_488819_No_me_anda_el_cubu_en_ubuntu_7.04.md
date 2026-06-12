---
title: "No me anda el cubu en ubuntu 7.04"
date: 2007-06-30
forum: Argentina Team
---

### Post by aceki on 2007-06-30
Gente buenas tardes, le cuento que no me anda el cubo, cuando recien lo instale andaba barbaro, tengo instalado los drivers de nvidia, los efectos andan, pero no anda el cubo, creo que despues de actualizarce algo...

---

### Post by smo0th on 2007-06-30
che antes ke nada ke cubo usas?

hay 2 sopas: beryl y compiz

para activar compiz simplemente vas a system>preferences>desktop effects y ahi seleccionas Enable Desktop Effects y trae las opciones de wobble de las ventanas y de activar el cubo

si usas beryl entonces prueba reiniciando la sesion o si no jala reinicia la pc, beryl es un software experimental entonces pueden aparecerte algunos bugs, si algo no anda reinicialo o simplemente usa el beryl manager>select window manager para cambiar a compiz o metacity ke es el default de ubuntu.

espero ayude de algo, saludos.

---

### Post by martianz on 2007-06-30
Es un bug que tiene la Feisty, segun dice Launchpad, estará solucionado para la próxima versión.

En Terminal, tipea:

```
sudo apt-get install gnome-compiz-manager
```

Se creará una entrada en el menú ubicada en "Sistema -> Preferencias -> GL Desktop"

Saludos.

---

### Post by Timbis on 2007-07-01
Si no te funca, hace lo siguiente: Sistema > preferencias > efectos de escritorio, y desabilitas los efectos. Despues vas a donde se cambian las areas de trabajo y le das un click derecho y vas a preferencias. en numero de areas de trabajo pones cuatro. Por ultimo habilitas los efectos de escritorio.
Espero que te sirva.

---

### Post by aceki on 2007-07-01
Ya esta gente, para los "descolgados" que le pase lo mismo que yo, estaba bloquado el escritorio, por eso no giraba, muchas gracias a todos.

---

