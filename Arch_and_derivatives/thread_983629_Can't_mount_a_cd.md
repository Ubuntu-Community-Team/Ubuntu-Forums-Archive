---
title: "Can't mount a cd"
date: 2008-11-15
forum: Arch and derivatives
---

### Post by TheOrangePeanut on 2008-11-15
I'm trying to install the original Diablo to play in Wine, but I can't mount the CD.  I'm using pcmanfm, which uses HAL, so it should auto-mount (and it is set to do so in fstab).  Unfortunately, when I try to open the directory, it gives me an "unsupported filesystem" error.  I've also tried to mount it manually and this is what I get.

```
[nelson@beta-pc ~]$ sudo mount -t iso9660 /dev/cdrom /media/cdrom
Password: 
mount: unknown filesystem type 'iso9660'
[nelson@beta-pc ~]$ sudo mount /dev/cdrom /media/cdrom
mount: unknown filesystem type 'iso9660'
[nelson@beta-pc ~]$ 

```

Anyone have any ideas?

---

### Post by handy on 2008-11-15
I think when you use HAL you should comment out your CD DVD floppy lines in fstab.

Try that & see how you go?

---

### Post by TheOrangePeanut on 2008-11-15
Thanks, that did it.  I feel like an idiot lol.

---

### Post by handy on 2008-11-16
Yeh, don't worry, we all know that feeling too often. :lolflag:

It's great when we get a simple solution, (like most of them are) though eh!?

---

### Post by chucky chuckaluck on 2008-11-16
> **TheOrangePeanut said:**
> Thanks, that did it.  I feel like an idiot lol.

just think of how many others you've saved from the same fate.

---

### Post by mips on 2008-11-16
> **TheOrangePeanut said:**
> Thanks, that did it.  I feel like an idiot lol.

Don't, I did something far worse the other nite.

After I reinstalled Arch I changed my network settings to static from dhcp and also edited my resolv.conf file for dns servers.

After that DNS would not work. I must have looked at my rc.conf & resolv.conf files about 5 times and occasionally editing things. Still nothing.

Then I compared it to my desktops rc & resolv files, still nothing.

Eventually I figured out I left out the 'nameserver' part in front of the IP address of the dns servers. I could not even see my own error even though I compared it to a 100% working file and have done this setup many times in my life. ](*,) ](*,) ](*,)

---

