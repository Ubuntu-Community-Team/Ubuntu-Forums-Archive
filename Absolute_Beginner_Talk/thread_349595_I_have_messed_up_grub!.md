---
title: "I have messed up grub!"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by cellarmation on 2007-01-30
I got an error 18 & 25 the other day with grub and over reacted and installed gag (graphical bootloader) . When i uninstalled gag realizing i was just over reacting, it just re instated my windows xp bootloader. So i cannot currently access my ubuntu install.

How can i reinstall grub dual booting windows xp and ubuntu? i have a live cd to hand.

---

### Post by divague on 2007-01-30
[http://www.ubuntuforums.org/showthre...highlight=grub](http://www.ubuntuforums.org/showthre...highlight=grub)

---

### Post by Mba7eth on 2007-01-30
[try this !! ]("http://www.ubuntuforums.org/showthread.php?t=24113")

---

### Post by shof2k on 2007-01-30
> **cellarmation said:**
> I got an error 18 & 25 the other day with grub and over reacted and installed gag (graphical bootloader) . When i uninstalled gag realizing i was just over reacting, it just re instated my windows xp bootloader. So i cannot currently access my ubuntu install.

How can i reinstall grub dual booting windows xp and ubuntu? i have a live cd to hand.

Try the following...taught to me by ubuntu member "hungsquirrel"

1) Boot up using the ubuntu install CD
2) Wait until your install CD has detected your drives - it will be just about to partition your system
3) Switch to a console by pressing CTRL+ALT+F2
4) Hit enter to activate the console. You should see a root prompt ("#")
5) Type the following commands
```
 mkdir mounted 
```
```
 mount /dev/ide/host0/bus0/target0/lun0/part2 mounted
```
Substitute "target0" to the disk you are using.  This will be 0 for the first disk on your PC etc.
Substitue "part2" for the partition where ubuntu is installed. If you're on a dual boot machine, I'd guess you on partition 2.
```
 chroot mounted /bin/bash 
```
```
 grub-install /dev/hda 
```

This should reinstall grub to it's origninal settings.  Let me know if this helps.

---

### Post by fasoulas on 2007-01-30
Exactly the same problem

[http://www.ubuntuforums.org/showthread.php?p=2083777#post2083777](http://www.ubuntuforums.org/showthread.php?p=2083777#post2083777)

---

### Post by cellarmation on 2007-02-17
Sorry for the slow reply i have only just got round to trying to get it to work.

I couldnt get shof2k's method to work as it wouldnt stop when booting, not sure if its something i was doing wrong.

I also tried the method of going through the install and not formating the drives and just mouting my old ones but the installer would not let me continue if i wasnt going to format.

I tried this method:
> 
Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.


This really looked like it was going to work, i think grub re configured itself or what ever, but when i rebooted the windows xp bootloader still kicked in and there was no sign of grub.

So i think i can narrow the problem down to i need to get grub back in the mbr? any advice would be great :-)

---

