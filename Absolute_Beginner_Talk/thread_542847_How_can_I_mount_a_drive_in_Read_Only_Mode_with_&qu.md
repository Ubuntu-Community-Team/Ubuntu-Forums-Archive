---
title: "How can I mount a drive in Read Only Mode with &quot;mount&quot;?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by felipebarroeta on 2007-09-04
Hello everyone.

How can I mount a drive in Read Only Mode with "mount"?

---

### Post by mendingo84 on 2007-09-04
```
mount -r path_to_device mount_directory
```

---

### Post by GMachine_24 on 2007-09-04
I think it might be more complicated than that.

At the least, he/she must use "sudo" to mount a drive. And, he/she must create a mount point first, right?

So

<code>

user@computer~$sudo mkdir /nameofdirectorywhereyouwanttomountyourharddrive
password:xxx

user@computer~$sudo mount -r ext3 /locationofharddrive /harddrivemountdirectorythatyoucreated

</code>

Practically speaking this looks more like:

<code>

user@computer~$sudo mkdir /felipedrive
password:[your password]

user@computer~$sudo mount -r ext3 /dev/hde1 /felipedrive

</code>

I'm not sure if the 'ext3' is needed - it is one of the Linux file systems.

You must find your hard drive in order to mount it. Here I'm assuming it's listed in the /dev file as hde1. This is just for an example. It could be sda1, hde2, hdf1, etc.

As always, providing more information about your drive and system will get you a better answer.

--gm

---

### Post by felipebarroeta on 2007-09-04
Hi! 
sda2, Windows Vista (currently completely collapsed). NTFS System. I could read the information about two days ago, but after i unmounted and try to remount in order to read/write Ubuntu stopped reading it, I assume it has something to do with the Windows Vista working no more.

I'm trying to access there because I want to back-up some information I have there, as I think to reinstall XP...

I did this and this is what I get (The text in Spanish is not important, is some kind of help file):

felipe@felipe-desktop:~$ sudo mount -r ntfs /dev/sda2 /felipedrive
Uso: mount -V                 : muestra la versión
     mount -h                 : muestra esta ayuda
     mount                    : muestra los sistemas de ficheros  montados
     mount -l                 : ídem, incluyendo etiquetas de volumen
Hasta aquí la parte informativa. Vayamos al montaje.
La orden es `mount [-t tiposf] cosa sitio.
Los detalles que se encuentran en /etc/fstab se pueden omitir.
     mount -a [-t|-O] ...     : monta todo lo que hay en /etc/fstab
     mount dispositivo        : monta el dispositivo en el sitio conocido
     mount directorio         : monta el dispositivo conocido aquí
     mount -t tipo disp dir   : orden mount ordinaria
Tenga en cuenta que uno no monta realmente un dispositivo, uno monta un
sistema de ficheros (del tipo dado) que se encuentra en el dispositivo.
También se puede montar un árbol de directorios ya visible en otro sitio:
     mount --bind dirantiguo dirnuevo
o mover un subárbol:
     mount --move dirantiguo dirnuevo
Se puede dar un dispositivo mediante el nombre, digamos /dev/hda1 o /dev/cdrom,
o mediante la etiqueta, utilizando -L etiqueta, o mediante uuid, mediante -U uuid.
Otras opciones: [-nfFrsvw] [-o opciones] [-p passwdfd].
Escriba man 8 mount para saber mucho más.
felipe@felipe-desktop:~$ 



By the way... do I need to uninstall Ubuntu for installing XP? Hopefully not!!!

Thanx for the Information!!!

---

### Post by schorsch on 2007-09-04
```
sudo mount -r -t ntfs /dev/sda2 /felipedrive
```

---

### Post by GMachine_24 on 2007-09-04
Haha... yeah... see... that information about it being a Window$ drive was dead set necessary.

--gm

---

### Post by schorsch on 2007-09-04
> **GMachine_24 said:**
> Haha... yeah... see... that information about it being a Window$ drive was dead set necessary.

--gm
 .... not really ... without "-t" your suggested command would have failed, too ....

---

### Post by felipebarroeta on 2007-09-04
well of course is necessary... but what i meant of being not so important is because every time i get that screen my problem is still there...

anyway... thanx for helping me out!

---

### Post by GMachine_24 on 2007-09-04
> **schorsch said:**
> .... not really ... without "-t" your suggested command would have failed, too ....

Yes, I understand. But the ntfs part was also needed. That's what I meant.

--gm

---

