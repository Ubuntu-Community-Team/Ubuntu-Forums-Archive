---
title: "How to Install Only Ubuntu On iBook G4?"
date: 2010-03-13
forum: Apple Hardware Users
---

### Post by masaharustin on 2010-03-13
I'm trying to install ubuntu on an old iBook G4. I have two cds (9.10 (not PPC specific) and 8.04.1 (the PPC specific version)) along with the G4 install cds. I've tried booting while holding down C, and I've tried to boot holding down option. When the boot menu comes up it does not recognize either one. I've also reset the PRAM.
I've read a lot of guides, and look through [this]("http://ubuntuforums.org/showthread.php?t=427714") very thoroughly. I don't even want to dual boot, just Ubuntu.
So how can I get Ubuntu to install on this old iBook? Thanks!

---

### Post by linuxopjemac on 2010-03-13
You need a PPC version of Ubuntu. You should be able to start the CD by holding c during startup (so holding the key after the system boing). If this fails, I would boot the CD from open firmware:

start your mac with the on/off button
then press:
option+command+o+f (alt+apple+o+f)

you then enter open firmware
then you issue this:
```

boot cd:,\\:tbxi
```

---

### Post by surfmonkee on 2010-03-13
i learnt a great deal about ppc versions today, and encrypted drives. i love ubuntu, its my first ubuntu day ever.

good luck with your install

:popcorn:

---

### Post by linuxopjemac on 2010-03-14
Download a recent version of Ubuntu PPC, I would go for the alternate installer. [http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-alternate-powerpc.iso)

Check its md5sum, cause if you don't have a bad CD, which will not work. Another tip I can give you is that you need to burn at low speed for such old machines. It should work with the two options I gave you. Either booting with the c pressed during boot (hold it until it starts booting from CD), or boot from open firmware. You might also want to try booting with the command (Alt) key pressed. If there is a bootable device, your Apple will show it and you can then select it.

Good luck

---

### Post by unknowndude on 2010-03-14
is there wubi for mac?

---

### Post by linuxopjemac on 2010-03-14
> is there wubi for mac? 
No

---

### Post by masaharustin on 2010-03-14
Thanks, how do I check the md5sum? What is an md5sum? lol.

---

### Post by linuxopjemac on 2010-03-14
an md5sum is some sort of code, produced by some algorithm, to check whether the iso you downloaded is exactly the same as the one which is on the server. I don't know what kind of computer you use to burn disk images, but under OSX it's called md5sum.
[Here]("http://www.versiontracker.com/php/qs.php?mode=basic&action=search&str=md5&srchArea=macosx|macosx-all&submit=Go") you'll find some examples for OSX.

---

