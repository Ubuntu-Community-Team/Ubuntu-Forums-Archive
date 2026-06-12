---
title: "Boot from live CD using Vista, how?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by metalaxesucks on 2007-06-02
How do I boot my live Ubuntu CD? I have Vista. When I used to have XP I just put the CD in and restarted my PC and it automaticaly booted from the CD. I have an Acer computer. I heard that phoenix only works with Vista, is that true? I know the CD is good because I already tried it on a XP  computer.
Thanks in advance

---

### Post by drowner on 2007-06-02
Just stick it in, and reboot the computer.

It should work, provided your BIOS is set to boot from CD before harddrive

---

### Post by supersonicdarky on 2007-06-02
are you sure you burned the .iso correctly? for it to boot, you need to burn as image, and not a regular file.

---

### Post by rillip on 2007-06-02
Your OS shouldn't ahve any impact on your ability to boot from a CD or not.  You need to go into your bios (usually by pressing delete, tab or escape at some point during the boot) and set it to use your CD Rom as a boot device before your hard drive.

> **drowner said:**
> Just stick it in, and reboot the computer.

It should work, provided your BIOS is set to boot from CD before harddrive

He already tried it on another computer and it worked, the disk is fine. It sounds like he just isn't getting the choice, it's booting straight to Vista, as noted, most likely due to bios.

---

### Post by supersonicdarky on 2007-06-02
offtopic:

you can delete your own posts?

---

### Post by Skrynesaver on 2007-06-02
As noted by rillip you can change your BIOS settings from the initial boot by pressing and holding  the appropriate key on boot. If none of the above work, try 'F2' and if that doesn't work watch your boot sequence carefully, it should say "press <magic key> to enter setup" or something like that.  Then change the boot order so that dvd is first boot option.

---

### Post by metalaxesucks on 2007-06-02
Thanks everybody, I figured it out

---

### Post by celticbhoy on 2007-06-02
You need to change the option for first boot device to cd-rom
then then second boot device to hdd0

---

### Post by metalaxesucks on 2007-06-02
Thanks everybody, I figured it out

---

