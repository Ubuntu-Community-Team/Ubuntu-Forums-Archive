---
title: "Understanding Live Cd's"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by psam3 on 2008-01-20
I have an Ubuntu Live cd that I downloaded and burned from the internet. I don't know very much about Linux and I was trying to run the cd but every time I got halfway through the loading screen it would just stop working. I thought maybe it was a bad cd so I burned a new copy and it did the same thing. So I came across this other Linux called pclinuxos which also has a live cd. I downloaded, burned, and tried this as well but it does the same thing. So I was wondering if their is something I need to do to be able to run these cd's? I also couldn't find the option to just install Ubuntu and that first startup screen. Could it be that my computer isn't compatible with these things? Any help would be appreciated.

Thanks

---

### Post by LaRoza on 2008-01-20
Post your specs.

Specifically, your RAM and Video card. Also, model of computer would help.

Some computers have issues. You can install in a VM if you want to try them out, and you can get a text based installer which almost always works.

---

### Post by psam3 on 2008-01-20
I have a Compaq with an Intel Celeron 2.70 Ghz
2039 MB RAM
128 MB Nvidia Geforce 5200 FX
Windows Vista

The model is Presario SR1010NX

---

### Post by banewman on 2008-01-20
You have to burn the cd's at a slow speed - 4x is the best.
:)

---

### Post by JoshuaRL on 2008-01-20
Your specs should be more than enough to run the Live CD efficiently.  When you load the CD, which option do you choose?

---

### Post by psam3 on 2008-01-20
I think it's the top one the one that says Run Live Cd

---

### Post by frup on 2008-01-20
Have you tried safe graphics?

---

### Post by SunKing2 on 2008-01-20
I had a NVidia card and had to install the NVidia drivers (however my live CD did work though).

To make your LiveCD work, when it first starts, choose the second option on the inital menu "Start Ubuntu in safe graphics mode".  This allow it to complete.  


[INDENT][SIZE="2"](If this still doesn't work, press F6 at that menu and append 

```
vga=771
``` 

to the line that starts with 

```
boot: /boot/vmlinuz-
``` [...]

If this still doesn't work (800X600 graphics mode, 256 colors), try 

```
vga=769 
``` (640X480, 256 colors, I heard all cards support this)[/SIZE][/INDENT]

Once you have it installed, you will most certainly need to install the NVidia driver (that's not included on the Live CD).

---

