---
title: "Discos montados pero no los lee"
date: 2007-01-09
forum: Argentina Team
---

### Post by Nemesis Teufel on 2007-01-09
La mala suerte me acompaña, pero por suerte hay un foro con buena onda!

Luego de restaurar mi GDM, mis discos si bien aparecen como montados y si voy a /media figuran ahi, aunque no pueda acceder.

Probé con montarlos y surgió lo obvio.
```

nemesis@nemesis-desktop:~$ sudo mkdir /media/hda1
mkdir: no se puede crear el directorio `/media/hda1': El fichero ya existe
```

Procedí a "remontarlo" bajo otro nombre de esta forma:

```
nemesis@nemesis-desktop:~$ sudo mkdir /media/remontar
mkdir: no se puede crear el directorio `/media/remontar': El fichero ya existe
nemesis@nemesis-desktop:~$ sudo mount /dev/hda1 /media/remontar
mount: /dev/hda1 ya está montado o /media/remontar está ocupado
mount: según mtab, /dev/hda1 está montado en /media/hda1
nemesis@nemesis-desktop:~$ 
```

Antes me pasaba de vez en cuando lo mismo, pero lo solucionaba con reiniciar.

Sugieren que desmonte el disco y lo vuelva a montar?
Cómo se desmonta?

---

### Post by felipelerena on 2007-01-09
sudo umount <la dir del directorio o el device en /dev/"sarasasarasa">

---

### Post by Tinchio on 2007-01-10
justo te iba a sugerir q desmontes y vuelvas a montar, me ha pasado algo similar y al hacer esto volvio todo a la normalidad

---

### Post by Nemesis Teufel on 2007-01-10
Encontré el problema.

```
nemesis@nemesis-desktop:~$ sudo mount /dev/hda1
Failed to mount '/dev/hda1': Operación no soportada
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.

```

Vamos a explorar el infierno.. 
Voy a windows.. si no vuelvo en 1 hora, sigan sin mi (?)

---

### Post by Nemesis Teufel on 2007-01-10
Volví de las tinieblas, accedi al disco como para boludear, escuche musica y apague la computadora como se debe. Ahora que recuerdo, la ultima vez que use win se me tildo feo.

Mis discos estan sanos y salvos como antes..

Es una suerte o desgracia que tenga problemas que aparecen "solos" y se solucionen practicamente "solos"?

Otro caso resuelto.

---

