---
title: "GRUB on MBR of primary slave?"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by Jucato on 2006-02-13
I have two hard disks. hda contains WinXP, and hdb contains Kubuntu. I'm about to do a reinstall of both OS'es (XP got drowned with spyware and I need to repartition my hdb). So my simple question is this. 

Is it possible to put GRUB on the MBR of hdb and set BIOS to boot hdb rather than hda? My reason was that I don't want to mess up GRUB and the MBR of hda everytime I need to reinstall Windows (which might be often thanks to my sister's surfing habits).

Another question, is there a sort of Linux startup disk or bootdisk that can be used for recovery? Or is the Live CD a better alternative?

Thanks for any insight! :D

---

### Post by cotcot on 2006-02-13
Answer on your first question is yes.
Second question. LiveCD is OK. You could have also a look to the ultimate boot CD : [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by Jucato on 2006-02-13
Ok, thanks! I'll take a look at that ultimate boot cd. :D

---

### Post by xmastree on 2006-02-13
[QUOTE=Fenyx]Is it possible to put GRUB on the MBR of hdb and set BIOS to boot hdb rather than hda?[/QUOTE]Yes, that's what I'm doing. **But...** I can't get grub to offer Windows from /dev/hda as an alternative. Well, I can but windows won't start since once the computer's booted windows thinks that hdb is the first (c:) disk.

So, if I want windows I have to hit Tab - escape at the right time so that the BIOS will ask me which disk to boot from.

That's with an asus A7V8X. Yours might not have that option...

---

### Post by xyferx on 2006-02-13
hi i've just downloaded ubuntu and im planning to install it with winXP
can you guys give me tips how can successfuly install it
I currently have 1 HD but planning to buy another... I mean can I install it by just partitioning the HD...
coz I had problems with fedora when I tried to intall it with winXP...
thanks in advance

xmasstree pinoy den ako...

---

### Post by Jucato on 2006-02-13
[QUOTE=xmastree]Yes, that's what I'm doing. **But...** I can't get grub to offer Windows from /dev/hda as an alternative. Well, I can but windows won't start since once the computer's booted windows thinks that hdb is the first (c:) disk.

So, if I want windows I have to hit Tab - escape at the right time so that the BIOS will ask me which disk to boot from.

That's with an asus A7V8X. Yours might not have that option...[/QUOTE]

hey, yo *kababayan*!! (fellow countryman)

So you mean, if I installed GRUB on hdb, I won't be able to boot WinXP through it? Ok, then that practically makes GRUB a bit useless. I was hoping it would still work normally even if I didn't install it on hda. Guess I have to do it the hard way and install it on the proper MBR.  changing the BIOS setup everytime I need to use another OS will be too tiresome...

---

### Post by damianubuntu on 2006-02-13
I have XP on hd0 and ubuntu on hd1. Set bios boot to hd1 and up comes grub with the option to go to XP if needed, but default ubuntu.
Works for me...
Having said that, HD1 is secondary master, not primary slave - but I dont know enough to know whether that makes any difference:-)

---

### Post by dannyliu on 2006-02-13
Fenyx,

I have ubuntu on hd0 (primary) and xp on hd1(slave). My bios only supports boot from primary so I installed grub loader on ubuntu. To allow grub loader to
pick xp, an entry needsto be added to /boot/grub/menu.lst.

sudo gedit /boot/grub/menu.lst

add an entry like this
title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
makeactive
chainloader +1

then comment out hiddenmenu

That fixes the problem.

---

### Post by Jucato on 2006-02-13
Thanks to everyone for their insight. I'll try those out when I reinstall everything tomorrow.

---

