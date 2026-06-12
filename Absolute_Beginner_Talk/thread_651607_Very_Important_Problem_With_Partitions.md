---
title: "Very Important Problem With Partitions"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Larjk on 2007-12-27
My problem is the following one, my disc was divided in several parts and on having ended I have restarted it, on having returned to enter only it was leaving me to enter the Linux and there was not even track of WIndows's partitions, in addition LInux's partition instead of having them 20gb of size that had before has the whole space of the hard disk.
There is some way of annulling this formatting of disc? 
Thank you

---

### Post by LaRoza on 2007-12-27
> **Larjk said:**
> My problem is the following one, my disc was divided in several parts and on having ended I have restarted it, on having returned to enter only it was leaving me to enter the Linux and there was not even track of WIndows's partitions, in addition LInux's partition instead of having them 20gb of size that had before has the whole space of the hard disk.
There is some way of annulling this formatting of disc? 
Thank you

I am not sure of what you are saying.

Do you mean you just installed Ubuntu?

If you chose to install to the entire hard disk, the install disk does what you say. There is no cheap way to undo this.

I hope you made backups, which I and others always recommend before doing any sort of partition editing or installing of operating systems.

---

### Post by Larjk on 2007-12-27
No, I don't had backups

---

### Post by sid351 on 2007-12-27
...Unfortunately I don't think so.

You *might* be able to save the data if you take your HDD and slave it in another computer and run some data recovery tools on it.

I stress, MIGHT.

---

### Post by LaRoza on 2007-12-27
> **Larjk said:**
> No, I don't had backups

From now on, I bet you will.

Sorry about your data loss. 

This may help: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd) Live disks with TestDisk

---

### Post by Larjk on 2007-12-27
> **LaRoza said:**
> From now on, I bet you will.

Sorry about your data loss. 

This may help: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd) Live disks with TestDisk

Sorry, I'm spanish and i don't speak very well English.
You might explain to me I explain them detailed?

Thank you

---

### Post by LaRoza on 2007-12-27
> **Larjk said:**
> Sorry, I'm spanish and i don't speak very well English.
You might explain to me I explain them detailed?

Thank you

[http://www.cgsecurity.org/wiki/TestDisk_ES#Dokumentation](http://www.cgsecurity.org/wiki/TestDisk_ES#Dokumentation)

Estoy aprendiendo español y no soy bueno en él

---

### Post by Larjk on 2007-12-27
Oh, you are my god xD
In the spanish forum hav erecomended me the same program, i download this but i I do not know install it. 
Thank you

---

### Post by ADH on 2007-12-27
There is a shareware disk utility called DFSEE ([www.dfsee.com](www.dfsee.com)) with a great support group on Yahoo.  It comes in Linux and Windows versions, if you want to take a look.

---

### Post by LaRoza on 2007-12-27
> **Larjk said:**
> Oh, you are my god xD
In the spanish forum hav erecomended me the same program, i download this but i I do not know install it. 
Thank you

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Do not use the hard disk in question. Anytime you use it, you reduce the chances of anything being recovered.

Use a live cd. I doubt you will be able to get much back, but it is worth a try.

If you don't understand [http://babelfish.altavista.com/](http://babelfish.altavista.com/)

---

### Post by Larjk on 2007-12-28
How that type of ubuntu I have? I talk about Edgy, Dapper...

---

### Post by LaRoza on 2007-12-28
> **Larjk said:**
> How that type of ubuntu I have? I talk about Edgy, Dapper...

What do you mean?

You can tell which one you have under System->About Ubuntu

---

### Post by Larjk on 2007-12-28
Está solucionado.It is solved. Thank you

My principal problem is that ubuntu does not leave me to install k3b

eyendo lista de paquetes... Hecho
Creando árbol de dependencias      
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido     
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
Los siguientes paquetes están ROTOS:
  k3b kcontrol kdebase-bin kdebase-kio-plugins kdelibs4c2a kdesktop kicker
  libk3b2 libkonq4 libqt3-mt
Se instalarán automáticamente los siguientes paquetes NUEVOS:
  kdebase-data kdelibs-data libflac++6 perl-suid
Se instalarán los siguiente paquetes NUEVOS:
  k3b-i18n kdebase-data kdelibs-data libflac++6 perl-suid
0 paquetes actualizados, 15 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 51,1MB de ficheros. Después de desempaquetar se usarán 140MB.
No se satisfacen las dependencias de los siguientes paquetes:
  kdelibs4c2a: Depende: libarts1c2a (>= 1.5.0-1) que es un paquete virtual.
               Depende: libaudio2 que es un paquete virtual.
               Depende: libavahi-qt3-1 (>= 0.6.0) que es un paquete virtual.
               Depende: liblua50 (>= 5.0.3) que es un paquete virtual.
               Depende: liblualib50 (>= 5.0.3) que es un paquete virtual.
               Depende: libopenexr2c2a (>= 1.2.2) que es un paquete virtual.
  libk3b2: Depende: libartsc0 (>= 1.5.0-1) que es un paquete virtual.
           Depende: libaudio2 que es un paquete virtual.
           Depende: libdbus-qt-1-1c2 (>= 0.62.git.20060814) que es un paquete virtual.
           Depende: libmpcdec3 que es un paquete virtual.
  kcontrol: Depende: libaudio2 que es un paquete virtual.
  kicker: Depende: libaudio2 que es un paquete virtual.
  k3b: Depende: libaudio2 que es un paquete virtual.
       Depende: libdbus-qt-1-1c2 (>= 0.62.git.20060814) que es un paquete virtual.
  kdebase-kio-plugins: Depende: libdbus-qt-1-1c2 (>= 0.62.git.20060814) que es un paquete virtual.
                       Depende: libopenexr2c2a (>= 1.2.2) que es un paquete virtual.
  libkonq4: Depende: libarts1c2a (>= 1.5.0-1) que es un paquete virtual.
  kdebase-bin: Depende: libaudio2 que es un paquete virtual.
  kdesktop: Depende: libaudio2 que es un paquete virtual.
  libqt3-mt: Depende: libaudio2 que es un paquete virtual.
Resolving dependencies...
Las acciones siguientes resolverán estas dependencias

Mantener los paquetes siguientes en la versión actual:
k3b [Sin instalar]
k3b-i18n [Sin instalar]
kcontrol [Sin instalar]
kdebase-bin [Sin instalar]
kdebase-kio-plugins [Sin instalar]
kdelibs4c2a [Sin instalar]
kdesktop [Sin instalar]
kicker [Sin instalar]
libk3b2 [Sin instalar]
libkonq4 [Sin instalar]
libqt3-mt [Sin instalar]

La puntuación es -19731

---

### Post by LaRoza on 2007-12-28
Can you go online with this install?

If so, enable all the repositories. In Add/Remove under Applications, it is in the upper right.

I have no idea how to translate that.

---

### Post by Larjk on 2007-12-28
Thank you for your help but I am tired and prefer bearing my father and reinstating WIndows

Really thank you thank you thank you
Thanks

---

### Post by LaRoza on 2007-12-28
> **Larjk said:**
> Thank you for your help but I am tired and prefer bearing my father and reinstating WIndows

Really thank you thank you thank you
Thanks

Whatever works.

De Nada

Visit the forums again!

---

