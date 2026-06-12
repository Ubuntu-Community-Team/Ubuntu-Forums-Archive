---
title: "Dual Booting GRUB issues."
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Bostonian on 2007-06-10
I'm trying to set up an XP pro/ubuntu 7.04 for 64bit on my computer, and am having trouble setting up the dual boot.

I installed both OSs on a 200 gig slave drive. the XP first, on a 100Gb partition, then ~1.5gb swap, then ubuntu on a  ~98Gb partition. Grub didn't come up, so i loaded the boot disk & terminal and did:

```
sudo grub
grub>find /boot/grub/stage1
*(it returned hd1,2)*
grub>root (hd1,2)
grub>setup (hd1)
```

and now get a grub screen with the choices:
```
Ubuntu, kernel 2.6.20-15 generic
Ubuntu, kernel 2.6.20-15 generic (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Microsoft Windows XP professional
```

but all the Ubuntu options return "error 22: No such partition"
and all the Windows return "NTLDR is missing, press Ctrl+alt+del to restart"

i went back and tried grub>setup (hd0),
and tried setting up the boot.ini in windows, but wasn't sure where to point to to start up ubuntu.

how might i go about getting a dual boot working?
Thanks.

---

### Post by tchoklat on 2007-06-10
sometimes with more than one HDD  grub names them incorrectly. In my case with a similar setup I have Ubuntu on hd0,5 but with a kernel upgrade grub is auto amended and points to hd1,5 I then have to amend it myself. If I don't I get a similar error to you. Perhaps that is the issue?

---

### Post by logos34 on 2007-06-10
> i went back and tried grub>setup (hd0),
well, now you've got grub on the Master boot record of master and slave drives.  

Quick test:
Change the Bios boot order so that you boot to the master ide.  Maybe you'll have the correct drive geomtry then and be able to get into ubuntu.
Does it work?  But you'll have to edit menu.lst for windows i think.

---

### Post by Bostonian on 2007-06-10
> **logos34 said:**
> well, now you've got grub on the Master boot record of master and slave drives.  

Quick test:
Change the Bios boot order so that you boot to the master ide.  Maybe you'll have the correct drive geomtry then and be able to get into ubuntu.
Does it work?  But you'll have to edit menu.lst for windows i think.

That fixed it! Thanks a lot!

---

