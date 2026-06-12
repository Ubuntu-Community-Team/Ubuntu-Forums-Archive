---
title: "Installing clean Kubuntu from Ubuntu"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by cybertron3000 on 2008-02-13
I erased my Windows XP, and have my Ubuntu happily installed.  I love it.  I want to now install my recently received Kubuntu, but it says no application is suitable for automatic installation for "wubi-cdboot.exe" when I try it.

Anyone know how to boot and install Kubuntu from Ubuntu?  I would like to have these as my dual boot.

---

### Post by taurus on 2008-02-13
If you want to check out Kubuntu, KDE, you can install it on your Ubuntu system.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```
And at the GUI login screen, you have an option in the Options, lower left corner, to pick which window manager you want to use.

---

### Post by cybertron3000 on 2008-02-13
I did that once and it was as much a memory hog as my old XP.  Someone said a clean install of the Kubuntu would be best, so I've got one from the mail on disc.

---

### Post by taurus on 2008-02-13
Is your new Kubuntu disc bootable?  What happens if you reboot your machine while the CD is in the drive?

---

### Post by cybertron3000 on 2008-02-13
Good question.  Unfortunately the boot-from off or restart on either Ubuntu or Kubuntu doesn't work.  Actually I think this is a hardware problem as I've not had the function for a while.  I originally booted and installed Ubuntu from my disc in my Windows, but through my own messing with Gparted I eradicated Windows.

I wonder if there is a way to boot it off of DOS somehow?

---

### Post by taurus on 2008-02-13
There is no option in the BIOS to boot from CDROM?

---

### Post by cybertron3000 on 2008-02-13
Oh - sorry - can you tell me how to get to BIOS?  I'm new.

---

### Post by taurus on 2008-02-13
When you first turn on your machine, you usually get a quick logo of the BIOS on the screen and either at the bottom or top right corner, you would see a message saying something like press F2 to get into setup.  So, try pressing F2 to see if it drops you into the BIOS and in the boot device section, make sure you move the CDROM to the top of the list.  I guess you have harddrive first right now.  Then, save it and exit.

---

### Post by cybertron3000 on 2008-02-13
I re-booted and it offers you to enter "c" for command lines, and has heading of "grub" for you to input a command.  No other options for doing stuff.

---

### Post by taurus on 2008-02-13
If you get to GRUB, it's too late then.  Try pressing F2 as soon as your machine reboots.

---

### Post by Northsider on 2008-02-13
Just keep hitting F2 when you reboot, you should get to the BIOS menu.  Then you can select the boot sequence order and check if the cd drive is set to boot.

---

### Post by cybertron3000 on 2008-02-13
ok - I will give that try then.  thanks

---

### Post by macogw on 2008-02-13
It might also be F12 or F10 or Esc.  It's when your computer shows the big Dell or HP or Compaq or whatever splash screen.

---

