---
title: "Como blockear en Gaim?"
date: 2006-12-15
forum: Argentina Team
---

### Post by Nemesis Teufel on 2006-12-15
No encuentro la forma de blockear a un usuario con Gaim. Quiero blockear a mi vieja y no puedo :@
Se puede y no se? hay algun plugin? 
a proposito.. alguna pagina de gaim con plugins y agregarles funcionalidades?

---

### Post by Fully216 on 2006-12-15
It has been years since I have studied Spanish, so my translation might be a bit off.  For this reason, I will type it in both English and then Spanish.

You do need gaim's extended preferences to block someone.  I would recommend also installing the guifications package, encryption, and a few others.  You may do it by typing the following in the CLI (assuming you have the correct repos enabled):

Usted necesita realmente las preferencias ampliadas del gaim para bloquear a alguien. Yo recomendaría también por instalar el paquete de guifications, la codificación, y algunos otros. Usted puede hacerlo escribiendo a máquina lo siguiente en el CLI (asunción usted hace permitir repos correcto):

apt-get install gaim-guifications gaim-extendedprefs gaim-hotkeys gaim-encryption

---

### Post by Nemesis Teufel on 2006-12-16
thx fully216, You dont have a perfect Spanish (also i didnt looking for that) but I can understand you very well!! =)

I couldnt open the "fichero"(maybe file?)

thank u and come back later to lernt more Spanish ;)

Edit:
ahh i remember i didnt put the Sudo..
works fine with sudo :D i didnt know if I understand the english very bad or i am a newie.. maybe both :D

but.. :( i cant block my ******* mother!!

---

### Post by DuckMan on 2006-12-16
con el gaim 2 beta hay un boton por lo menos, q te lo bloquea facilmente, es mas, lo mas pajero es desbloquear

---

### Post by beuno on 2006-12-16
> **Nemesis Teufel said:**
> No encuentro la forma de blockear a un usuario con Gaim. Quiero blockear a mi vieja y no puedo :@
Se puede y no se? hay algun plugin? 
a proposito.. alguna pagina de gaim con plugins y agregarles funcionalidades?

Yo lo tengo en Conversation > Block.
Abrite una ventana para chatear con ella y lo tenes en el menu.

Yo tambien la tengo que bloquear frecuentemente    ;)

---

### Post by Nemesis Teufel on 2006-12-16
ah ya encontre.. que pajero que soy..

> Yo tambien la tengo que bloquear frecuentemente 
Son insoportables.. te hablan de boludeces y te persiguen.. ademas no quiero que lea mis nicks puteando o no aptos para ella.. o peor.. cuando la puteo a ella :-P

---

### Post by lavaramano on 2006-12-17
en el gaim 2
vas a herramientas > privacidad > y ahi hay un menu desplegable que dice algo asi como 'bloquear solamente a los siguientes usuarios' 
tb podes hacer que te puedan contactar una lista de "siguientes usuarios" y demas opciones.

bueno, con eso deberia funcionar y sin instalar ningun paquete extra

---

### Post by ubuntu27 on 2006-12-17
> **Fully216 said:**
> It has been years since I have studied Spanish, so my translation might be a bit off.  For this reason, I will type it in both English and then Spanish.

You do need gaim's extended preferences to block someone. I would recommend also installing the guifications package, encryption, and a few others. You may do it by typing the following in the CLI (assuming you have the correct repos enabled):

Usted necesita realmente las preferencias ampliadas del gaim para bloquear a alguien. Yo recomendaría también por instalar el paquete de guifications, la codificación, y algunos otros. Usted puede hacerlo escribiendo a máquina lo siguiente en el CLI (asunción usted hace permitir repos correcto):

apt-get install gaim-guifications gaim-extendedprefs gaim-hotkeys gaim-encryption


@Nemesis Teufel: Hola. Que version de Gaim tienes? 
Si estas usando Ubuntu Edgy Eft (version 6.01), el Gaim te viene  con la version 2.0 beta3.1
No se si es la misma con las versiones anteriores, pero en Gaim 2.0 puedes blokearlo abriendo la ventana de conversacion, y luego anda a menu Conversation o Conversacion, y luego escoje "Block" o Blokear.


Como dice "Fully216" yo tambien te recominedo que installes algunos plug-ins para Gaim talez como:

gaim-encryption (encripcion/cifrado para gaim)
gaim-guifications (notificaciones)
gaim-extendedprefs (provee acceso a opciones/preferencias escondidas) 
gaim-themes (Tema de Iconos) 


```
sudo aptitude install gaim-guifications gaim-extendedprefs gaim-hotkeys gaim-encryption gaim-themes
```

---

