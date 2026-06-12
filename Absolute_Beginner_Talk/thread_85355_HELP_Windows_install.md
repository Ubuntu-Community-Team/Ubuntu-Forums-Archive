---
title: "HELP Windows install"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by Hesselaar on 2005-11-02
How do i re-install windows cause i installed Ubuntu and now i want to install windows  again how do i do it?
i have a windows cd and i tried with BIOS primary boot cd but it didn't work :???:

---

### Post by Micro Rotors on 2005-11-02
From what I have read and heard, Windows first, then Ubuntu.

---

### Post by jpkotta on 2005-11-02
You'll have to boot from the Windows CD, and it sounds like you're trying to do that.  How did you install Ubuntu if you can't boot from the CD?

Many BIOSs have a "boot menu" option.  On Dells, it's usually hold down F12 when booting.  It will bring up a list of devices that can be booted, one of which is the CD drive (hopefully).

And yes, you should have installed windows first if you wanted dual boot.  Search the forums/wiki for a howto dual boot with Ubuntu then windows.

---

### Post by frodon on 2005-11-02
OK, all you have to do is install windows as usual, if you have problems doing that it's not due to ubuntu since what you need is to boot on your windows CD.

Installing windows after ubuntu will destroy your GRUB, then after the windows install you will boot only on windows.
Therefore after the windows install you will have to restore your GRUB, just follow this HOWTO to perform the grub restore : [http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)

Good luck ;)

---

### Post by Kapre on 2005-11-02
[QUOTE=Hesselaar]How do i re-install windows cause i installed Ubuntu and now i want to install windows  again how do i do it?
i have a windows cd and i tried with BIOS primary boot cd but it didn't work :???:[/QUOTE]

Do you only have 1 hd? If you do, do you want to keep your Ubuntu System and partition your disk so that you can also install it?

If you want to overwrite the whole hd (meaning erase ubuntu), I would suggest to get bootable floppy (win98) and then fdisk and format the hd. reboot and get the option with cd support. Pop in the cd and run set-up from it.

If you still want to use your ubuntu, then you should partition your hd and install M$ on the unused portion.

K

---

### Post by Hesselaar on 2005-11-02
I don't want to use ubuntu anymore and i want to install window again but if i instert the cd during boot it auto loads GRUB and i can't select windows :(

---

### Post by doc_holiday on 2005-11-02
[QUOTE=Hesselaar]I don't want to use ubuntu anymore and i want to install window again but if i instert the cd during boot it auto loads GRUB and i can't select windows :([/QUOTE]

Stay with ubuntu, much better then windows but you have to take the time to learn.

If you want to install windows, make sure cd boot is enabled in your bios. Put in the cd and reboot.

---

### Post by bdash on 2005-11-02
[QUOTE=Hesselaar]I don't want to use ubuntu anymore and i want to install window again but if i instert the cd during boot it auto loads GRUB and i can't select windows :([/QUOTE]

Check the boot sequence in your BIOS. If you computer boots from the CD (the Windows install CD) it will be before grub loads.

Basically, when you install Windows there is no difference between a PC with Ubuntu or a PC with nothing.

---

### Post by nitricacid on 2005-11-02
[QUOTE=Hesselaar]I don't want to use ubuntu anymore and i want to install window again but if i instert the cd during boot it auto loads GRUB and i can't select windows :([/QUOTE]

Dude, 
open the CD tray (while computer is on), Close CD tray.
Restart computer, 
black screen should ask you if you want to boot from CD, press enter.
Computer should now be running from Windows CD.
Follow installation steps.
When the computer restarts and if it asks if you want to boot from the CD DO NOT PRESS ANY KEYS, let the computer load and finish the rest of the install steps.

I spoke slowly so you could understand me.

---

