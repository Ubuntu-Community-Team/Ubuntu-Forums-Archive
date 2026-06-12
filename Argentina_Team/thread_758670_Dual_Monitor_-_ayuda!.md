---
title: "Dual Monitor - ayuda!"
date: 2008-04-18
forum: Argentina Team
---

### Post by SLA_leandrin on 2008-04-18
Buenasss

Tengo un par de consultas relacionadas al tema del thread (Dual Monitor).

La placa de video de mi máquina es una nvidia Gforce Go 6100. Es de un notebook  Compaq Presario F565LA. Cuando arranco con el monitor secundario enchufado tengo configurado el xorg.conf para que aparezca como "Separate X Screen". Arranca todo OK, me logueo y aparece bien. El tema es que la pantalla principal, o sea, el monitor de mi notebook anda medio lento. El otro es un LCD LG, anda más rápido pero las ventanas no tienen bordes, a pesar de que en las opciones del compiz está activada la decoración de ventanas.

Alguien tiene alguna pista??

PD: adjunto el xorg.conf

Gracias!!!!

---

### Post by User21 on 2008-04-18
Si instalas el paquete **nvidia-settings**, es mucho mas fácil setear graficamente en xorg.conf las diferentes opciones de manejo de múltiples monitores. Yo lo uso y no tengo ningun problema! 
```
sudo apt-get install nvidia-settings
sudo nvidia-settings
```Ejecutalo como administrador, sino, no puedes guardar los cambios! 

Recuerda mantener una copia de tu actual xorg.conf, por las dudas!
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.copia
```[Aca]("http://www.ismprofessional.net/pascucci/wp-content/uploads/nvidia-settings.png") te dejo una imagen del GUI de nvidia-settings! Si ya lo tenes instalado, pues, **NO SE!** xD

En cuanto a la desaparicion de bordes de ventana, probaste con [esto]("http://www.guia-ubuntu.org/index.php?title=Aceleraci%C3%B3n_gr%C3%A1fica_NVIDIA#Resoluci.C3.B3n_de_problemas") ?

---

### Post by SLA_leandrin on 2008-04-18
Si... efectivamente está configurado con el nvidia-settings.....

Gracias igual...!

---

