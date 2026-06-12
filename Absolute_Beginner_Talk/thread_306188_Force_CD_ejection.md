---
title: "Force CD ejection"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by AirAshby on 2006-11-24
I have the latest version of WinE installed on my ubuntu 5.10. The installation for my windows program runs and works but I'm required to change the disk half-way through ](*,)  the installation but I can't eject the CD because the CD is registered as being used :mad: . Can I force the CD to be ejected or can someone tell me if I can make a Disc image and use a drive emulator.

---

### Post by 900i on 2006-11-24
Can you change to another workspace and right click eject on the cd icon!

---

### Post by deadgobby on 2006-11-24
If you see the CD icon on the ubie desk top, Just right click and scoll down to eject CD.

---

### Post by AirAshby on 2006-11-24
> **deadgobby said:**
> If you see the CD icon on the ubie desk top, Just right click and scoll down to eject CD.

Thats what I was doing it wouldn't eject the disc cause it said it was still in use.

---

### Post by deadgobby on 2006-11-24
If all fails. Find a tooth pick or paper clip. DO NOT USE FORCE and slide the tooth pick or paper clip in the tiny hole on the CD drive. This should pop open up the CD drive. Or you can go Alt-F2 and type in xkill and kill the app tat is using the CD.
Goobby

---

### Post by r4ik on 2006-11-24
Long shot,

As root "eject" in a terminal ?

---

### Post by jagguars on 2006-11-24
ya, or maybe the sudo version ;) 
sudo eject

---

### Post by CatKiller on 2006-11-24
> **AirAshby said:**
> or can someone tell me if I can make a Disc image and use a drive emulator.

You can. The "drive emulator" in this case being the **mount** command :)

```
sudo mkdir /media/fakecd
mount nameofiso.iso  -t iso9660 -o loop /media/fakecd
```

You might need to sudo the mount command as well, I'm not sure.

Then tell **winecfg** to use /media/fakecd as another cd drive and you're away. You can either just mount the second cd there and point the installer to the "second" drive, or use the same mountpoint for both cds, swapping them with the **umount** command.

---

### Post by George Derre on 2006-12-05
> **CatKiller said:**
> You can. The "drive emulator" in this case being the **mount** command :)

```
sudo mkdir /media/fakecd
mount nameofiso.iso  -t iso9660 -o loop /media/fakecd
```

You might need to sudo the mount command as well, I'm not sure.

Then tell **winecfg** to use /media/fakecd as another cd drive and you're away. You can either just mount the second cd there and point the installer to the "second" drive, or use the same mountpoint for both cds, swapping them with the **umount** command.

Or you could do this: 

```
sudo umount -l /media/cdrom0
eject
```

After you put your cd in type 

```
mount /media/cdrom0
```

Problem solved.

---

