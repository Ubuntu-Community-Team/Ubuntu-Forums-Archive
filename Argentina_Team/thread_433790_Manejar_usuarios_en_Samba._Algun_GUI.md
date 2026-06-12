---
title: "Manejar usuarios en Samba. Algun GUI?"
date: 2007-05-05
forum: Argentina Team
---

### Post by matog on 2007-05-05
Hola gente. Estoy armando mi red doméstica con 2 maquinas y compartiendo internet mediante un router. Una de las maquinas tiene Ubuntu Feisty y la otra, XP (obvio, de mi novia ;) ).
No hay inconvenientes en compartir archivos, carpetas, impresoras, internet. Todo perfecto.

Pero me **** un poco crear, editar y borrar usuarios de Samba desde la consola ¿Existe alguna aplicación gráfica para hacer esto mas sencillo?

En la página de [Samba](http://ftp.easynet.be/samba/GUI/) vi algunas, pero me gustaría saber cual les parece la mas cómoda y sencilla.

Gracias!

---

### Post by jayflower on 2007-05-05
```
sudo apt-get install gsambad
``` Lo encontré ayer para mí...

---

### Post by gepatino on 2007-05-05
También tenes otro programa que te permite manejar el samba via web, se llama swat. Lo use hace mucho y parecia respetable. Supongo que habrá evolucionado.

La ventaja de un sistema web es que también podes administrar el samba desde algun win, en el caso de ser necesario.

Recien lo busque en el synaptic y está en los repositorios oficiales, asi que no es más que un apt-get install swat (en el servidor, por supuesto)

---

### Post by kalel on 2007-05-07
yo tb estaba buscando algo asi, bien ahi por el post :)

---

