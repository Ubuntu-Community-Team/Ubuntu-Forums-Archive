---
title: "Crear un mapa de lloc"
date: 2009-05-20
forum: Catalan Team
---

### Post by marteljorge on 2009-05-20
Voldria crear un mapa de lloc del tipus "Google sitemap", alguna idea?

---

### Post by marteljorge on 2009-05-20
No he sabut crear un compatible amb el "sitemap protocol", doncs, el que he fet és molt simple, peró no definitiu:
```
cd ../../var/www/
sudo ls -R > sitemap.txt
sudo emacs sitemap.txt
```
Després, he editat cada línia per fer que es compleixi:
[http://sub.domini/carpeta/arxiu.*](http://sub.domini/carpeta/arxiu.*)

---

### Post by papapep on 2009-05-20
> alguna idea? 

[Unes quantes]("http://www.google.es/search?q=ubuntu+create+sitemap&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:ca:unofficial&client=firefox-a")

---

### Post by totalkiller on 2009-05-21
La teva pregunta es que quin es el format que ha de tenir l'arxiu sitemap.xml?

---

### Post by marteljorge on 2009-05-25
> **totalkiller said:**
> La teva pregunta es que quin es el format que ha de tenir l'arxiu sitemap.xml?

No, sé que el servidor web pot generar mapes, però no sé com.:?

---

### Post by marteljorge on 2009-05-25
> **papapep said:**
> [Unes quantes]("http://www.google.es/search?q=ubuntu+create+sitemap&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:ca:unofficial&client=firefox-a")

El generador de mapes de Google no em funciona, està disponible en C?

---

### Post by marteljorge on 2009-05-28
El problema era la compilació o instal·lació d'un programa en python, però ja ho tinc, a veure si em manca alguna cosa encara.
El que em manca ara és un arxiu config.xml vàlid per al programeta, i l'exemple és massa com per a que jo l'empri com a patró.

---

