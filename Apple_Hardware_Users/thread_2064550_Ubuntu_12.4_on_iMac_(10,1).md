---
title: "Ubuntu 12.4 on iMac (10,1)"
date: 2012-09-29
forum: Apple Hardware Users
---

### Post by nobodyfamous on 2012-09-29
when I try to boot to live disk, this is what my screen looks like.

I am using rEFIt and a USB drive.  It boots fine with my Macbook, but the iMac screen looks like the attached file.  The same thing happened trying to boot to a MINT distro.

Any Ideas?

---

### Post by Milkshakefiend on 2012-10-31
Hi all, 

This is the exact issue I'm having as well. I've read about booting in a safe graphics mode but can't seem to find that in the menu that's presented. Is this a USB issue? I was hesitant to install via DVD because the super drive in my iMac misbehaves quite frequently.

---

### Post by elctro on 2012-10-31
With Mac devices you should check "nonodeset" box. In the main screen of livecd press F6 then check "nomodeset". After finishing installtion, choose linux in the rEFIt screen after that press key e in the command line screen to edit it and add the word "nomodeset" before two spaces before "quitsplash" word then press F10 to start temporary. Finally edit the file grub.cfg and add the word "nomodeset" before two spaces before "quitsplash" word to make it official^^ then save it.

```
sudo gedit /boot/grub/grub.cfg
```

---

### Post by Milkshakefiend on 2012-11-01
This now gets me to a correctly formatted splash screen, but after the dots cycle a few times, it freezes. Any ideas?

---

### Post by nobodyfamous on 2013-02-01
did you get anywhere with this?

---

### Post by imacg3ppc on 2013-02-20
I love my imac g3.. and i haven't even gotten to use it yet because of a similar issue, i believe i have narrowed it down to xorg starting due to screen resolutions... are you able to get a command prompt or is it just literally freezing?

---

