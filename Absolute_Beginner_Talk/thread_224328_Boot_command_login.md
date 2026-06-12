---
title: "Boot command login"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by divineleft on 2006-07-27
I installed Ubuntu desktop (460 mb, 1 cd). Everything is in text mode, no graphics or anything, but the installation succeded. So It goes to boot and stops at the login where I enter my user name and password. Once I log in, it just stays in the text mode. How do I get the GUI to run?

Side note - Isn't 400 megs a little small for a os?

**My hardware:**
Intel pentium 4
Ati Radeon 9200
1g ram

---

### Post by LordRaiden on 2006-07-27
Did you install the gui? The official ubuntu CD is almost to max capacity of a CD, 679 MB I last remember.

If the window manager is installed (GNOME or KDE) is installed, the command is ```
sudo /etc/init.d/gdm start
``` for GNOME,and ```
sudo /etc/init.d/kdm start
``` for KDE.

---

### Post by divineleft on 2006-07-27
Ok, I got it to work. The live cd and the installation is all one, right? If it is, I have that one.

When I try to run it a blue window pops up and says X doesn't load, then just stays in text mode. How do I get it to work?

---

### Post by LordRaiden on 2006-07-27
give the exact error if you can. I think it is a video card error but I want to be sure.

---

### Post by divineleft on 2006-07-27
I booted in safe mode and everything works, it installed fine. The only thing is it wont go back into grubs when I restart my system. Also, the resolution wont go any higher than 1024 X 768.

---

### Post by LordRaiden on 2006-07-27
definitely a video card error then. Could you do the following.

UPDATE

If you are connected to the network do this first to upgrade your system.
```
 sudo apt-get update && sudo apt-get dist-upgrade
```  then reboot. If you get the same error do the following.
```
sudo nano /etc/X11/xorg.conf
``` 
locate the "Device" section -  it should have ATI right below it. what is the name of the Driver?

---

### Post by divineleft on 2006-07-27
> **LordRaiden said:**
> definitely a video card error then. Could you do the following.

UPDATE

If you are connected to the network do this first to upgrade your system.
```
 sudo apt-get update && sudo apt-get dist-upgrade
```  then reboot. If you get the same error do the following.
```
sudo nano /etc/X11/xorg.conf
``` 
locate the "Device" section -  it should have ATI right below it. what is the name of the Driver?

Everything is updated.


For some reason it has "dell integrated" as the driver. The ATI card is in the pci slot.

---

