---
title: "22 inch monitor *Out of range*"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Brendan Hart on 2007-06-11
I got a 22 inch monitor and when i took my computer home with my new Ubuntu installed my monitor gave me this message:

Out of range
vFrequency 81(or something like that)
vFrequency 101


I cant view anything in ubuntu except the loading page where the bar fills up then its just a blank screen, i can log into windows so thats all good for me but just ubuntu is screwing up, i can view the recovery mode, but even if i could fix it there i dont know what commands to type.

HELP me before its too late!!

---

### Post by taurus on 2007-06-11
Boot into recovery mode from GRUB menu and reconfigure your X for the new monitor.

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Brendan Hart on 2007-06-11
ok so that code should work?

if it does thanx, ill just write it down now. my home hasnt got the internet :( they do but its slow and i need wireless

---

### Post by taurus on 2007-06-11
That would allow you to reconfigure your monitor section again.

---

### Post by wh0rd on 2007-06-11
Note your monitor's specifications on **horizontal** and **vertical** *refresh rates*, you can obtain this through the monitor manual or do a Google search on the make and model of your monitor. If Ubuntu doesn't automatically recognize them, you'll have to specify the correct settings with the command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Or you can manually edit the** /etc/X11/xorg.conf** under the section **"Monitor"** For example:
[COLOR="Red"]-If you're going to do this make a backup of the xorg.conf first with: **sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup**[/COLOR]
```

Section "Monitor"
        Identifier      "Generic"
        Option          "DPMS"
[B]        HorizSync       28-80
        VertRefresh     48-75[/B]
EndSection

```

---

### Post by Brendan Hart on 2007-06-11
Um where is that section, can i get into that through Ubuntu recovery

---

### Post by wh0rd on 2007-06-11
Write down your **horizontal** and **vertical*** refresh rates* for your monitor.
 
You can edit the file called** xorg.conf** located in **/etc/X11/** with **nano** in safemode.

So just boot up with safe mode. Once you get to the command prompt just follow the steps below:

**[SIZE="3"]1[/SIZE]**. Backup the xorg.conf file so if we do anything wrong we can revert back to the backup:
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

**[SIZE="3"]2.[/SIZE]** Now lets edit the xorg.conf file to put in the correct specs for your monitor. We do this with a command line editor called "**nano**."  So keep these small things in mind, it's command line so no mouse, everything is keyboard even closing and saving files edited in nano:

```
nano /etc/X11/xorg.conf
```

**[SIZE="3"]3.[/SIZE]** Scroll down with the down arrow key until you see the section called **"Monitor"** it should be between the sections *Device* and *Screen*, for example:
> 
Section "Device"
        Identifier      "ATI Technologies Inc RC410 [Radeon Xpress 200]"
        Driver          "ati"
        BusID           "PCI:1:5:0"
EndSection

[B]Section "Monitor"
[INDENT]        Identifie     "Generic"
        Option      "DPMS"
[COLOR="Red"]        HorizSync     28-80
        VertRefresh     48-75[/COLOR][/INDENT]
EndSection[/B]

Section "Screen"
        Identifier      "Default Screen"



**[SIZE="3"]4. [/SIZE]**Edit the variables for [COLOR="Red"]**HorizSync**[/COLOR] (horizontal refresh rate) and [COLOR="Red"]**VertRefresh**[/COLOR] (vertical refresh rate) according to your monitors specs. 

**[SIZE="3"]5. [/SIZE]**Once you have the variables in Save and exit: press **CTRL+X**, 
    -it will ask you to confirm, press **Y** for yes.
   -Then press **Enter** to save with the same filename.

Now reboot, and choose the normal Ubuntu kernel in Grub. It should boot all the way to the login screen.

---

