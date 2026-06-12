---
title: "Borrar varios archivos"
date: 2007-07-08
forum: Argentina Team
---

### Post by Apipote on 2007-07-08
He bajado e instalado catfish y encuentra cualquier cosa. Pero no me da la opcion de borrar nada.
Como lo hago?.
Gracias.

---

### Post by beuno on 2007-07-08
No entiendo bien que es lo que queres hacer...

Borrar archivos de tu pc?
Cuales?

Que algunos no aparezcan en la busqueda?

---

### Post by Apipote on 2007-07-08
Quizas me exprese mal.
Al migrar a linux, pase todas mis fotos que administraba con Picasa. Se crearon, en los directorios,  archivos tales como el picasa.ini y thumbs.db. 
Son como 50, y los quiero borrar de una sola vez.
Ojala me haga entender.
Saludos.

---

### Post by Kantier on 2007-07-08
> **Apipote said:**
> Quizas me exprese mal.
Al migrar a linux, pase todas mis fotos que administraba con Picasa. Se crearon, en los directorios,  archivos tales como el picasa.ini y thumbs.db. 
Son como 50, y los quiero borrar de una sola vez.
Ojala me haga entender.
Saludos.
queres borrar los picasa.ini y thumbs.db?

lo que podes hacer es una búsqueda restringida a el diretorio donde están las fotos, primero con "picasa.ini" y luego con "thumbs.db"


en consola es usando el comando find, pero no recuerdo exactamente cómo tendría que ser. si no sos muy habilidoso con la línea de comandos te diría que hagas el camino gráfico de buscar, borrar resultados, buscar, borrar resultados.

---

### Post by Apipote on 2007-07-08
Solucionado,  pero demasiado poderoso. Ojo, no queda nada luego.

remove file syntax

To remove multiple files such as *.jpg or *.sh with one command find, use

find . -name "FILE-TO-FIND"-exec rm -rf {} \;

OR

find . -type f -name "FILE-TO-FIND" -exec rm -f {} \;

The only difference between above two syntax is that first command can remove directories as well where second command only removes files.

---

