---
title: "mounting 2nd HD"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by JCamus on 2007-02-15
well, i searched for similar posts and found nothing that could help me.

the thing is i had to fresh install ubuntu on my primary hd but in the install i evaded every change done to my slave hd, which fs is ext3. in that hd is all my data (media, docs, etc) and i'd really like to have access to it.

if you're willing to help me, i'm sure you'll need something like this:
```
Disco /dev/hda: 40.0 GB, 40038211584 bytes
255 cabezas, 63 sectores/pista, 4867 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1        4775    38355156   83  Linux
/dev/hda2            4776        4867      738990    5  Extendida
/dev/hda5            4776        4867      738958+  82  Linux swap / Solaris

Disco /dev/hdb: 80.0 GB, 80000000000 bytes
255 cabezas, 63 sectores/pista, 9726 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdb1               1        9726    78124063+  83  Linux
```

the only way to get access to it is mounting it? what about recognizing it as part of the system without mounting it? i thank you in advance.

ps: yes, i use the spanish version. if you need me to translate anything, just tell.

---

### Post by stalker145 on 2007-02-15
> **JCamus said:**
> 
Disco /dev/hdb: 80.0 GB, 80000000000 bytes
255 cabezas, 63 sectores/pista, 9726 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdb1               1        9726    78124063+  83  Linux[/CODE]

the only way to get access to it is mounting it? what about recognizing it as part of the system without mounting it? i thank you in advance.

Assuming that your drive you wish to automount is 1) /dev/hdb and 2) is EXT3, you can simply do the following:
```
sudo mkdir /mount/point/you/want
```

and then add the following to your /etc/fstab file:
```
/dev/hdb	/mount/point/you/want	ext3	defaults	0	0
```

I believe you would then do a 
```
sudo mount -a
```

to verify that it's all correct. You should be all good after a quick reboot.

---

### Post by punx45 on 2007-02-15
> **JCamus said:**
> well, i searched for similar posts and found nothing that could help me.

the thing is i had to fresh install ubuntu on my primary hd but in the install i evaded every change done to my slave hd...

the only way to get access to it is mounting it? what about recognizing it as part of the system without mounting it? i thank you in advance.



i think during the install process there is a section that lets you point out other harddrives and where to mount them.   you probably skipped over it, so you are just manually doing the same thing now.

if i had done the install without a guide plainly telling me this, I probably would have done the same as you! :)

---

### Post by JCamus on 2007-02-15
> **stalker145 said:**
> Assuming that your drive you wish to automount is 1) /dev/hdb and 2) is EXT3, you can simply do the following:
```
sudo mkdir /mount/point/you/want
```
and then add the following to your /etc/fstab file:
```
/dev/hdb	/mount/point/you/want	ext3	defaults	0	0
```
I believe you would then do a 
```
sudo mount -a
```
to verify that it's all correct. You should be all good after a quick reboot.

i did everything and when it came to "sudo mount -a" it said that the fs type is incorrect, option incorrect, superblock incorrect in /dev/hdb, the "code page" is missing.

*original:*
```
mount: tipo de sistema de ficheros incorrecto, opción incorrecta,
       superbloque incorrecto en /dev/hdb, falta la página de códigos,
       o algún otro error
       En algunos casos se encuentra información en syslog, pruebe
   dmesg | tail   o algo parecido
```

well i'm certainly sure it is ext3, the device administrator says so and last time i formatted it it was in ext3.

> **punx45 said:**
> i think during the install process there is a section that lets you point out other harddrives and where to mount them.   you probably skipped over it, so you are just manually doing the same thing now.

i actually did it in automatic... i thought if i included the slave hd, the installation would format it. is that so?

if this mounting doesn't work, i'm gonna reinstall again.

---

### Post by punx45 on 2007-02-16
what does the rest of your /etc/fstab look like?

also, since 'mount -a' mounts everything in the fstab, try mounting just the drive in question to see if you can get that to work and then go from there.

this should do the trick:
```
sudo mount /dev/hdb1 /the/dir/you/made
```

---

