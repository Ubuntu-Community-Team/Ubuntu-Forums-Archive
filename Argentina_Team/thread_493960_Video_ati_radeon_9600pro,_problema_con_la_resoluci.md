---
title: "Video ati radeon 9600pro, problema con la resolucion"
date: 2007-07-06
forum: Argentina Team
---

### Post by Miriknell on 2007-07-06
Buenas, estoy teniendo un problema con la resolucion de pantalla de mi ubuntu.
No me deja poner una resolucion mayor a 1024x768. La placa se banca muhco mas.... no se si habra que instalar algun driver, supuse q lo instalaba el propio ubuntu. Ya probe con el driver original q trae ubuntu y el con el que esta para descargar en la paginad e ati, con ambos no me deja pasar de esa resolucion.
Alguien sabria como hacer?
Gracias!

---

### Post by sdm_cacto on 2007-07-06
Yo tengo la misma placa y es un eror comun. Lo que tenes que hacer es instalar los drivers de Ati, que son los FGLXR.
Sino sabes ocm ohacerlo la manera mas facil (y la que yo uso) es mediante un programita llamado Envy, que lo bajas de [acá]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.5-0ubuntu5_all.deb").

te dejo tambien l apagina del creador de Envy, [Alberto Milone]("http://albertomilone.com/")

---

### Post by Miriknell on 2007-07-06
Ya lo utilice pero me dejo de andar el beryl..... y tuve que instalar otra vez el ubuntu.... :S

---

### Post by sdm_cacto on 2007-07-06
> **Miriknell said:**
> Ya lo utilice pero me dejo de andar el beryl..... y tuve que instalar otra vez el ubuntu.... :S

q error t tiraba? no me digas q reinstalaste solo porq no t andaba beryl

---

### Post by Al_maverick on 2007-07-06
los drivers propietarios de ati no andan con beryl, y por lo que se comenta, no van a andar con beryl/compiz hasta por lo menos fin de año.

---

### Post by sdm_cacto on 2007-07-06
> **Al_maverick said:**
> los drivers propietarios de ati no andan con beryl, y por lo que se comenta, no van a andar con beryl/compiz hasta por lo menos fin de año.

Para para... lso drivers propietarios de ati por si solos no corren beryl, la respuesta completa es q se puede correr beryl con drivers propietarios creando una sesion de XGL, yo tambien tengo una 9600 pro y uso drivers propietarios porq son los mas rapidos y corria Beryl y ahora Compiz Fusion sobre XGL, es mas, postee una guia en este mismo foro q es la q yo use.

---

### Post by Al_maverick on 2007-07-06
Tenes razon, el problema de los drivers era especificamente con Compiz, porque usa AIXGL.
Buscando en la wiki, encontre esta pagina que te puede ser de utilidad.

[https://help.ubuntu.com/community/Beryl/ATI/Feisty](https://help.ubuntu.com/community/Beryl/ATI/Feisty)

---

### Post by Duckzito on 2007-07-08
> **Al_maverick said:**
> Tenes razon, el problema de los drivers era especificamente con Compiz, porque usa AIXGL.
Buscando en la wiki, encontre esta pagina que te puede ser de utilidad.

[https://help.ubuntu.com/community/Beryl/ATI/Feisty](https://help.ubuntu.com/community/Beryl/ATI/Feisty)

Hola yo estoy teniendo este mismo problama, y ya probe con cuanto tutorial encontre en la web, y lo mismo, solo pude levantar el beryl, con los drivers propios de ubuntu, en cuanto pongo los propietarios de ATI, empiezan los problemas! alguien tiene alguna idea mas? se agradece! 

Saludos.

---

