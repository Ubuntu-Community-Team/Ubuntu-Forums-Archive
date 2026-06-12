---
title: "Hola Principiante con problemas"
date: 2007-05-18
forum: Argentina Team
---

### Post by carlos001 on 2007-05-18
Hola mi nombre es carlos 
Soy nuevo en linux y elegi ubuntu para empezar ya que creo que es muy bueno.
tengo este problema tengo una alienware con una nvidia go5700 128mb ,el problema es que cuando monto el driver de nvidia para activar el 3d y los destop effect me da una pantalla negra y nada mas.
ya tratre los drivers nuevos y nada porfavor ayuda es lo unico que me falta de resolver.
Saludos.

---

### Post by zspikes on 2007-05-18
probaste con el ENVY? es un script q te instala solo drivers de nVidia y ATI. Yo lo use en 3 maquinas distintas y en ninguna me trajo problemas.
podes visitar la pagina oficial [acá]("http://www.albertomilone.com/nvidia_scripts1.html"), donde podes bajar el archivo .deb (son como los .exe de win) y tenes las instrucciones para instalarlo

cualquier duda sobre como usarlo avisame :)

---

### Post by carlos001 on 2007-05-22
oka lo pruebo y cuento como me fue gracias!!!!!

---

### Post by carlos001 on 2007-05-22
no sube la interface grafica!
este es el log en attachment ayuda por favor!!

---

### Post by lugonesjoaquin on 2007-05-22
Hola:

Hace un sudo dpkg-reconfigure xserver-xorg

Y contanos!

---

### Post by carlos001 on 2007-05-23
Me recominedas algunos settings en especifico es que soy nuevo en linux.
gracias

---

### Post by jayflower on 2007-05-23
Si comentas que PC tenés podemos ayudarte o guiarte para que elijas bien en las opciones.

---

### Post by el_itur on 2007-05-23
no sé con la go5700 pero yo tuve problemas con los drivers sugeridos por el manejador de controladores propietarios y tiré desde el synaptic la versión más nueva de los drivers de envidia (el paquete es nvidia-glx-new) feisty fawn (asumo que es la versión que vos usás) hace innecesario el script ENVY, ya que tiene varias ventajas como configurarte el xorg al vuelvo (si ENVY también pero el paquete funciona MUCHO mejor). 
Por otro lado. este driver que te hablo (nvidia-glx-new AKA nvidia 9755) según escuché no anda con nada que no sea FX de cualquier manera probaría. tu placa es bastante nueva así que debe andar bien

---

### Post by carlos001 on 2007-05-23
es una laptop alienware 5500 con una NV36 [GeForce FX Go5700] 128mb con SiS AGP Port (virtual PCI-to-PCI bridge.
culaquier otra especificacion que necesiten me lo hacen saber por favor
y use envy pero pantalla negra

---

