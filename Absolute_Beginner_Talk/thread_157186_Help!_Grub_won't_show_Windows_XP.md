---
title: "Help! Grub won't show Windows XP"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by Ragzy on 2006-04-08
Hello!
I just installed ubuntu and I can't access Windows XP.
I have 2 harddrives, ubuntu is installed on the master drive.
Xp is installed on the first partition on the slave. 
I installed xp first and then ubuntu. But it did not write over Xp's boot with grub. (I didn't get the dialog for that under the installation of ubuntu (this is my brothers computer, worked on mine) Maybe that is because XP is installed on the slave and ubuntu is the first disk to be read at boot...

Anyways, I really need this to work with my current installation and harddrive setup. 
Here is the output from "sudo fdisk -l"

```

Disk /dev/hda: 20,0 GB, 20020396032 byte
255 huvuden, 63 sektorer/spår, 2434 cylindrar
Enheter = cylindrar av 16065 × 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Utökad
/dev/hda5            2331        2434      835348+  82  Linux växling / Solaris

Disk /dev/hdb: 203,9 GB, 203928109056 byte
255 huvuden, 63 sektorer/spår, 24792 cylindrar
Enheter = cylindrar av 16065 × 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hdb1            2551       24792   178658833+   7  HPFS/NTFS
/dev/hdb2   *           1        2550    20482843+   7  HPFS/NTFS

Posterna i partitionstabellen är inte i diskordning

```


And here is what my current grub menu.ls[PHP][/PHP]t looks like. I manually edited it for Windows XP, but ofcourse that did not work out..

```


title                   Windows XP
root                    (hd1,1)
map			(hd0) (hd1)
map			(hd1) (hd0)
savedefault    
makeactive
chainloader +1    

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot


```

With this config, we get an error when attempting to boot WinXP looking something like this:
Filesystem type unknown blablabla 0x7
and it says something about "NTLDR is missing"

Hope u guys can understand this code even if some parts are in Swedish...
Thanx for your time!
/Ragzy

---

### Post by usamahashimi on 2006-04-08
Hi
Try replacing your option;
root (hd1,1)
with
root (hd1,0)
Thanks

---

### Post by sn123 on 2006-04-08
[QUOTE=Ragzy]Hello!
I just installed ubuntu and I can't access Windows XP.
I have 2 harddrives, ubuntu is installed on the master drive.
Xp is installed on the first partition on the slave. 
I installed xp first and then ubuntu. But it did not write over Xp's boot with grub. (I didn't get the dialog for that under the installation of ubuntu (this is my brothers computer, worked on mine) Maybe that is because XP is installed on the slave and ubuntu is the first disk to be read at boot...

Anyways, I really need this to work with my current installation and harddrive setup. 
Here is the output from "sudo fdisk -l"

```

Disk /dev/hda: 20,0 GB, 20020396032 byte
255 huvuden, 63 sektorer/spår, 2434 cylindrar
Enheter = cylindrar av 16065 × 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Utökad
/dev/hda5            2331        2434      835348+  82  Linux växling / Solaris

Disk /dev/hdb: 203,9 GB, 203928109056 byte
255 huvuden, 63 sektorer/spår, 24792 cylindrar
Enheter = cylindrar av 16065 × 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hdb1            2551       24792   178658833+   7  HPFS/NTFS
/dev/hdb2   *           1        2550    20482843+   7  HPFS/NTFS

Posterna i partitionstabellen är inte i diskordning

```


And here is what my current grub menu.ls[PHP][/PHP]t looks like. I manually edited it for Windows XP, but ofcourse that did not work out..
/Ragzy[/QUOTE]

what portions did you edit for Win XP and do you have a backup of the original menu.lst file? If yes, please post it's content over here. Also post the content of your devices.map.
```

$ cat /boot/grub/devices.map

```


S

---

### Post by sn123 on 2006-04-08
also imo mapping the secondary to first harddrive should happen before the root command, see if changing the ordering of them helps you booting into XP.
something like:
<<snippet menu.lst>>
```

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root**noverify** (hd1,0)
savedefault
makeactive
chainloader +1 

```
PS: before trying to edit the menu.lst, make sure that you make a backup of the file.

---

### Post by Sef on 2006-04-08
> Maybe that is because XP is installed on the slave and ubuntu is the first disk to be read at boot...

I know XP needs to be first on a primary partition.  I suspect that it needs to be on the master and not the slave hard drive.

---

### Post by Ragzy on 2006-04-08
thanx for the replys, problem still remains though=/
I tried to edit the menu.lst to:

```

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader +1 

```

Now it just says "NTLDR is missing"

The only thing changed in the menu.lst is the windows xp lines, cuz in the start there was nothing about windows there, just ubuntu. 

> Also post the content of your devices.map."
```

$ cat /boot/grub/devices.map

```

It says I do not have any file with that name...
cat /boot/grub/devices.map
cat: /boot/grub/devices.map: Filen eller katalogen finns inte (does not exist)

---

### Post by catlett on 2006-04-08
Can XP boot without being inside the 1024 mark? Do you think that is the problem? That even if Grub directs to Windows it won't boot ?
Did XP boot normally after you installed it but before you installed Ubuntu? Do you have an F12 (well it's F12 on mine) Where you can choose which device to boot from e.g. boot from secondary drive? Does that do anything if you have that option?
There is one definate but tedious solution. Reinstall both OSs. Putting Windows on the 1st drive. Let it make it's C partition where it wants. Then installing Ubuntu to the 2nd. I only say this because you said you just installed them borh. Hopefuly you haven't loaded them up with important data yet. Wish I had more Grub advice but I can never manage to edit my Grub menu correctly.

---

### Post by sn123 on 2006-04-08
[QUOTE=Ragzy]
The only thing changed in the menu.lst is the windows xp lines, cuz in the start there was nothing about windows there, just ubuntu. 


It says I do not have any file with that name...
cat /boot/grub/devices.map
cat: /boot/grub/devices.map: Filen eller katalogen finns inte (does not exist)[/QUOTE]
sorry my bad, when I'm drunk I generally get the the file names wrong :(
```

cat /boot/grub/device.map

```
 and as others have said generally Xp likes it being on the firstdrive but still post the contents of your device.map file and let's see whether we can tweak something to make xp boot.


S

---

### Post by Ragzy on 2006-04-09
Np=)

here is the output..Thanx for helping!

```

(hd0)   /dev/hda
(hd1)   /dev/hdb

```

Btw, XP lies within in the first cylinders on the slave, Xp is on hdb2 (the 20G). Thought that was the most important for Windows OS's..Would be great to get it to work like it is.

---

### Post by sn123 on 2006-04-09
[QUOTE=Ragzy]Np=)

here is the output..Thanx for helping!

```

(hd0)   /dev/hda
(hd1)   /dev/hdb

```

Btw, XP lies within in the first cylinders on the slave, Xp is on hdb2 (the 20G). Thought that was the most important for Windows OS's..Would be great to get it to work like it is.[/QUOTE]
looks like Grub didn't even detect XP on the second drive during installation otherwise there would have been atleast the entry for Xp in menu.lst, ideally you should have not installed grub in that case. Anyway, once the grub shows the boot menu, press "c" to goto the grub prompt and execute the xp boot commands and see where it exactly fails.
```

grub> map (hd0,1)
grub> map (hd1,0)
grub> rootnoverify (hd0,1)
grub> makeactive
grub> chainloader +1
grub> boot

```
let me know where grub failed in these commands.

S

---

### Post by Ragzy on 2006-04-09
Hi again sn123, Since I had to go home today, and my brother needed XP to work properly, we decided to reinstall both Ubuntu and XP. Yhis time XP is on the master drive and we got asked to place Grub on the master. Everything worked fine this time. We had the important files on the other partiton on hdb so no biggies.. The reason he wanted the previous setup to work, was that that he wanted xp on the new 200GB HD, since its faster than the old one. Would have been easier to make the new one master, but we could only connect a special "smaller" cable to it, so it had to be matser..](*,)  Anywas, thanx alot for your time!

---

