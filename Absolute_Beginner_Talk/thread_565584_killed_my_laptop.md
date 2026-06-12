---
title: "killed my laptop"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by handyguy33 on 2007-10-02
hi all.

well, i've done it. got a laptop yesterday. it had no cd drive and it won't boot from a usb cd drive. so i installed with unetbootin. but it came with no gui. i used apt-get to download a gui but it didn't work entirely; something didn't get found. i checked the forums which said to try a different x server driver. i tried that and now i have lots of colors and gobbledy-gook which doesn't look like a console or a gui. my computer is completely unusable. is there anything i can do or do i now own an expensive paperweight. somebody please reply soon, i won't have this connection all day.

thanks

---

### Post by Daveth on 2007-10-02
is this an Ubuntu only install  your are trying, or as part of a dual boot? Did you partition the hard drive beforehand? A bit more detail would help us out. It sounds like you have got Ubuntu there but with a part wrecked gui.
Are you able to start again?

---

### Post by handyguy33 on 2007-10-02
i formatted the entire drive. kinda wish i hadn't, now. if its any help i have a dell latitude c400. is there some way i can get this to boot from an external cd-rom because i could just re-install with a disc.

---

### Post by tgalati4 on 2007-10-02
In the BIOS (F2 or F12 or Delete) there should be selection of BOOT Order.  Select CDROM to be ahead of the hard disk.  That should do it.

---

### Post by scrooge_74 on 2007-10-02
> **handyguy33 said:**
> hi all.

well, i've done it. got a laptop yesterday. it had no cd drive and it won't boot from a usb cd drive. so i installed with unetbootin. but it came with no gui. i used apt-get to download a gui but it didn't work entirely; something didn't get found. i checked the forums which said to try a different x server driver. i tried that and now i have lots of colors and gobbledy-gook which doesn't look like a console or a gui. my computer is completely unusable. is there anything i can do or do i now own an expensive paperweight. somebody please reply soon, i won't have this connection all day.

thanks

Since you are without a CDROM, my advice to you is to take the drive out of the laptop and hooked up to another one then use a live CD and install the system. Latter take the disk out and put it back on your PC and reconfigure things like the xserver

---

### Post by handyguy33 on 2007-10-02
in the bios i've moved cdrom ahead of hdd (in fact hdd is now at the bottom of the boot list. however there is a one time boot option at startup and it has no listning of a cdrom either internal or external. is there any way to halt grub and get it to boot from the external cdrom?

---

### Post by handyguy33 on 2007-10-02
i've got root console back! ok guys amaze me with your expertise. i need my gui to work.

---

### Post by handyguy33 on 2007-10-02
come on guys, i'm sitting here in front of root@linuxbox:~#  what should i tell it?

---

### Post by handyguy33 on 2007-10-02
ok i'm running out of time. i told it: sudo dpkg-reconfigure -phigh xserver-xorg. now i'm back at the x server drivers list. what now?

---

### Post by benerivo on 2007-10-02
What did you try to install first time around? I would have gone for ```
sudo aptitude install ubuntu-desktop
```

---

### Post by tgalati4 on 2007-10-02
Just pick sensible values in xsetup.  If they don't work, make a note and try again.

Next time you are at a command prompt, amaze us with your hardware specs:

Post the ouput of:

>lspci -vv

and

>lsmod

ps:  For future reference you need a USB-boot floppy or Super GRUB floppy.  This assumes you have a working floppy drive in the laptop.  Older BIOS doesn't recognize boot USB options.  That said, perhaps you can upgrade the BIOS with a download from the manufacturer's site.

---

### Post by scrooge_74 on 2007-10-03
> **handyguy33 said:**
> ok i'm running out of time. i told it: sudo dpkg-reconfigure -phigh xserver-xorg. now i'm back at the x server drivers list. what now?

try the VESA driver or if you know which card you have try its driver, but VESA should at least give you a working GUI

---

