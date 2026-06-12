---
title: "Sin pelis ni videos con Gutsy Gibbon"
date: 2007-10-22
forum: Argentina Team
---

### Post by hernan blau on 2007-10-22
Como lo dice el título con cds o dvds. O se ven rayas, manchas  o nada. Tampoco TN Noticias por internet. Instalé los códecs que me fue pidiendo y nada. De automatix bajé todo lo que se podía y nada. Comprendan que no soy informático. Todo esto en la portátil con placa Realtek ALC861-VD y una intel Celeron M420. Aclaro que con Feisty se veían bajando los códecs. Por las dudas, me estoy demorando en instalar Gutsy en la pc de escritorio. Aclaro que hice una instalación de cero, eligiendo todo el disco duro. Cordialmente, HB.

---

### Post by scrooge_74 on 2007-10-22
No sé si fue buena idea usar automatix, que tarjeta de video tienes? Acabo de leer un post en inglés sobre alguien que con las películas ve rayas o manchas, me parece que decía que tiene una ATI.

---

### Post by hernan blau on 2007-10-22
Sí, tengo una ATI. Trataré de averiguar el modelo, aunque por unas horas no puedo porque estoy en el trabajo. Gracias.

---

### Post by hernan blau on 2007-10-22
Este es el resultado del comando "lspci"

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

Gracias por vuestra atención.

---

### Post by javier-2714 on 2007-10-22
Hola te comento yo tuve el mismo problema la solución es instalar correctamente el driver de vídeo me baje el Envy lo descargo y lo instalo en forma automática pude ver vídeos lo descargas de [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) fíjate yo puse un thead con lo mismo suerte.

---

### Post by scrooge_74 on 2007-10-22
Sip lo saludable es usar Envy, ATI todavía es problemático pero es lo mejor que se puede hacer hasta que AMD cree mejores drivers

---

### Post by hernan blau on 2007-10-22
Muchas gracias por la información. El proceso de bajada de Envy se corta en un punto. Seguiré insistiendo. Cordialmente, HB

---

### Post by javier-2714 on 2007-10-22
Mira  resien lo baje al toque lo pongo aca :

---

### Post by sajnox on 2007-10-22
Sinceramente no termino de identificar la placa de video, seguramente envy en algun paso la va a identificar.

El tema con envy es que te instala el driver propietario, y sinceramente los drivers actuales de ATI son por lo menos malos, creo que al dia de hoy recien soportan aceleracion 2d (esto significa que si tu placa soporta compiz usando estos drivers compiz no va a funcionar)

Lo mejor, o por lo menos lo fuye en mi caso fue usar los drivers libres que trae ubuntu, generalmente requieren alguna pequeña modificacion al xorg.conf pero nada serio)


PD: ATI/AMD se comprometio a mejorar su soporte para Linux pero al dia de hoy creo que no hay grandes novedades, cuando salgan los nuevos drivers seran motivos de alegria para todos.

---

### Post by sajnox on 2007-10-22
Otra cosa mas,

te dejo [ESTE]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=3600513") link con detalles y modificaciones para hacer a las placas ati respecto a los drivers libres.

Saludos,

---

### Post by Hei Ku on 2007-10-22
para identificar la placa de video podes usar este comando en la consola:

lspci

---

### Post by hernan blau on 2007-10-25
Traté de instalar Envy. Me pide en el proceso de instalación que ponga el disco iso de Gutsy. Lo hago y al rato me sale error, que no pudo cargar algunos archivos. Sólo queda suponer que esos archivos no están en el cd (que bajé por Torrent y grabé a baja velocidad). Por otra parte, en Administración-Controladores restringidos, figura que existe un controlador privatico para tarjeta gráfica ATI que no está en uso y hay una casilla aparentemente para habiolitar. ¿Es aplicable y/o aconsejable su habilitación? Gracias. HB

---

### Post by sajnox on 2007-10-25
> **hernan blau said:**
> Traté de instalar Envy. Me pide en el proceso de instalación que ponga el disco iso de Gutsy. Lo hago y al rato me sale error, que no pudo cargar algunos archivos. Sólo queda suponer que esos archivos no están en el cd (que bajé por Torrent y grabé a baja velocidad). Por otra parte, en Administración-Controladores restringidos, figura que existe un controlador privatico para tarjeta gráfica ATI que no está en uso y hay una casilla aparentemente para habiolitar. ¿Es aplicable y/o aconsejable su habilitación? Gracias. HB

Si queres tener aceleracion 3d no uses envy, por lo menos no todavia, te va a instalar el driver porpietario y ese no tiene soporte 3d, es mas o menos lo mismo que habilitar el driver propietario con Ubuntu

---

### Post by hernan blau on 2007-10-29
Gracias a los compañeros y a Javier. Logré bajar el Envy acmsejado más arriba, luego apareció en Aplicaciones-herramientas del sistema-envy y allí se elige instalar el software necesario. Se rebootea y listo. He logrado ver otra vez dvds, Tn noticias on line y otros videos. Cordialmente, HB

---

