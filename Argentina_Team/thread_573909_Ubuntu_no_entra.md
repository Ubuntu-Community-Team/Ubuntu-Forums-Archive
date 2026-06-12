---
title: "Ubuntu no entra"
date: 2007-10-12
forum: Argentina Team
---

### Post by zerio on 2007-10-12
Bueno, pues acabo de solucionar un problema y ya tengo otro, aunque este es considerablemente más grave.
La cosa es que de repente, sin venir a cuento, cuando empezaba a entrar en ubuntu la barra se quedaba a medio cargar y no entraba.
Iniciando en modo seguro me salía el siguiente mensaje:
BUG: soft lockup detected on cpu#0
Googleando un poco he descubierto que puede ser por algo relacionado con la tarjeta wifi, pero se supone que se arregla con tenerla activada cuando se inicia ubuntu, y yo la tengo activada!. Aparte de eso no he encontrado nada más por más que he buscado.
Pues espero que me podáis ayudar. Muchas gracias de antemano.

---

### Post by nest on 2007-10-12
> **joris1977 said:**
> I have the same problem. Since i upgraded to edgy, my labtop hangs often on bootup. When i do recovery restart i sometimes get the [17179609.344000] Bug: soft lockup detected on cpu#0 

Note that i have my wireless not enabled on bootup. On dapper that was necessary, but on edgy it starts working when i put the button. 

i have intel dual core on Acer aspire 5610. 

This bug is already reported on lunchpad sometimes linked to wireless sometimes to uplash and other issues.

see: [https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=bug%3A+soft+lockup+detected+on+cpu%230&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=bug%3A+soft+lockup+detected+on+cpu%230&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

Will follow this threat, because it seems the most active
but these threats are also about more or less the same issue:

[http://www.ubuntuforums.org/showthread.php?t=286843&highlight=Bug%3A+soft+lockup+detected+on+cpu%230](http://www.ubuntuforums.org/showthread.php?t=286843&highlight=Bug%3A+soft+lockup+detected+on+cpu%230)
[http://www.ubuntuforums.org/showthread.php?t=277922&highlight=Bug%3A+soft+lockup+detected+on+cpu%230](http://www.ubuntuforums.org/showthread.php?t=277922&highlight=Bug%3A+soft+lockup+detected+on+cpu%230)

some people think it is skype related: 
[http://forum.skype.com/lofiversion/index.php/t64990.html](http://forum.skype.com/lofiversion/index.php/t64990.html)

edit: I found out that i could run edgy without problems in the old kernel 2.16.15-27.686. So i thought my problems might be kernel related. Searching on the forums, i found this threat: 
[http://ubuntuforums.org/showthread.php?t=282956](http://ubuntuforums.org/showthread.php?t=282956)

i reinstalled the kernel with the commands i found in the threat:

sudo mkinitramfs -o /boot/initrd.img-2.6.17-10-generic 2.6.17-10-generic
sudo update-initramfs -u -k 2.6.17-10-generic
sudo update-grub
sudo aptitude reinstall linux-restricted-modules-2.6.17-10-generic



not sure what these commands do exactly but it seems that it worked, because i don't have any troubles at starting up anymore. Ofcourse i don't  know if it will work for other people, but you problems could be kernel related as well...

edit2: Well it worked... for a few days: this morning i had the same bug again. Strange... did it again see how long it lasts
edit3: I gave up, just did a fresh install of edgy and everything seems to work fine now. Hope it stays that way.

edit4: It still works... but the troubles come back when  my wireless is enabled when i´m starting up. So i guess in my case it´s related to the 802.11a/b/g wireless LAN. I´ve seen the patch, but not sure exactly how to apply it. I can work around it, so i´&#314;l hope feisty will solve this issue permanent.  

This threat on the kubuntu forums suggests that the problem might be dual-core related:
[http://kubuntuforums.net/forums/index.php?topic=10019](http://kubuntuforums.net/forums/index.php?topic=10019)

podés ver todo el thread [acá]("http://ubuntuforums.org/showthread.php?t=251944&page=1") o el que te postié [acá]("http://ubuntuforums.org/showpost.php?p=1689150&postcount=15").

---

### Post by zerio on 2007-10-12
Muy agradecido por contestar tan rápido.
Por lo que entiendo de lo que pone (mi nivel de inglés no es de lo mejor) tengo que poner una serie de cosas en el terminal. El problema es que cuando entro en el recovery mode me sale el mensaje de error y ya no puedo escribir nada, así que no sé cómo hacerlo.

---

### Post by nest on 2007-10-12
lo que hizo fue reinstalar el kernel con esos comandos.

¿probaste de elegir entrar con el kernel viejo?

---

### Post by zerio on 2007-10-13
Pues sí, intenté entrar con el kernel antiguo y tampoco.
De qué manera (si la hay) podría reinstalar el kernel teniendo en cuenta que no me deja escribir???
A las malas siempre puedo reisntalar ubuntu, que recuerdo que cuando lo instalas te da la opción de conservar en una carpeta los archivos.

---

