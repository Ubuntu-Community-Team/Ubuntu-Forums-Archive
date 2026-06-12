---
title: "reinstalar ubuntu edgy"
date: 2007-03-13
forum: Argentina Team
---

### Post by zspikes on 2007-03-13
perdonen q sea tan molesto, pero este amigo q les dije q no podia hacer andar la placa de wifi no se q pedo se mando y necesitamos reinstalar.

El problema es q no se por que, cuando booteamos el live cd no anda el x server, nisiquiera en modo seguro.

No saben como podemos reinstalar desde el mismo ubuntu, o consola, o como sea? gracias!!!

---

### Post by Mafber on 2007-03-13
Hola zspikes!! 
Te funciona el modo grafico de tu instalación de Ubuntu? sino probá esto:
sudo dpkg-reconfigure xserver-xorg
Si no funca avisá y probamos otra cosas (me resulta raro que no te arranque desde el CD el modo grafico :confused: )
Suerte!!!

PD: tus preguntas no molestan :)

---

### Post by gakna on 2007-08-22
Mafber, pregunto acá porque estoy desesperado!!! instalé ubuntu feisti en mi AMD sempron 3000, ATI radeon 9250 (que creo es complicada para todos los ubunteros y no tengo idea despues de 2 semanas seguidas de leer tutoriales de como configurarla para que ande la aceleracion 3D), y compiz andaba bien. Luego un amigo intentó instalar compiz fusion y todo se *****. No he podido lograr que reconozca mi ati (está funcionando como VESA generico), ni tengo aceleracion 3D, ya ni siquiera andan los efectos de escritorio que al principio andaban. Estoy pensando en reinstalar Ubuntu. Se te ocurre alguna otra cosa?? 
Muchas gracias desde ya!

---

### Post by Hei Ku on 2007-08-22
Es raro. Esa placa anda joya con Ubuntu, asi que debe ser otra cosa. Podes postear to xorg.conf? Yo uso los drivers free y no tengo problemas para correr Compiz Fusion. Que drivers estabas usando en el momento de instalarlo?

---

