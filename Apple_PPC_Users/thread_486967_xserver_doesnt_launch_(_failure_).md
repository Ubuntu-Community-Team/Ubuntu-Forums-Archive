---
title: "xserver doesnt launch ( failure )"
date: 2007-06-28
forum: Apple PPC Users
---

### Post by Hinsky on 2007-06-28
hello there :) im absolutely new to linux
when i try to boot ubuntu from the desktop CD i get the error message, that x server has failed.
same when i install it with the alternate disc.
i tried to reconfigure it with "sudo dkpg-reconfigure xserver-xorg"  and tried it through an editor "sudo nano xorg.conf"

i just doenst work ^^

i have a G4 MDD 2x1Ghz and a Radeon 9000 Pro with 64MB v-ram
maybe something with the drivers ? how could i fix that ?

thanks :)  nicolai

---

### Post by tcrroadie on 2007-06-28
I'm at work at the moment, but I try to remember things best I can.  

1.  After you receive the xserver failure message durring boot, open a virtual terminal to bring up the command line by pressing Ctrl+Alt+F2.  You have 7 virtual terminals from F1 thru F7 available to you.   

2.  Log in using the log in information you configured during installation.  

3.  After loging in, open up your xserver configuration file using a terminal application called nano.  Nano is a text editor.  At the command line prompt, enter 

```
sudo nano /etc/X11/xorg.conf
```

4.  Page down using the up and down arrows on your keyboard till you get the the section that says 
    ```
 Section        "Device" 
```

5.  In this section there is a driver line specifying the driver used for your video card.  Make sure it reads this for your Radeon video card.  

```
Driver  "radeon"
```

6.  Save the changes you made to the xorg.conf file by pressing Ctrl+O.  Then close nano by pressing Ctrl+X. 

7.  Restart your xserver by entering this at the terminal command prompt.  
```
sudo /etc/init.d/gdm restart
```

8.  This should bring up the Gnome login manager GDM.  If the radeon driver still doesn't work you can try a driver called "fbdev" in your "Device" section.  The fbdev driver should at least get your xserver up and running so we can problem solve it. 

```
Driver  "fbdev"

```

---

### Post by flyinggeko on 2007-06-28
Yay, I am really lucky to have found this, It was my exact problem. So thanks.:D

On the other hand I only got it to work with the 'fbdev' driver. By the way, I'm using an ati rage 6

The color is a little screwy and trext is slightly garbled, but other than that GNOME runs fine. How do I fix this?

---

### Post by flyinggeko on 2007-06-29
Would I type in 'rage' instead of 'radeon' or 'fbdev'?
Or, do I need to go find a driver?

---

### Post by flyinggeko on 2007-06-29
The card is labeled as a Rage 6 and radeon. Additionally, the device manager in Ubuntu tells me it's a Radeon R100 QD [Radeon 7200]

---

### Post by flyinggeko on 2007-06-29
Yeah me again spamming the posts with 10 minute updates.

I was looking at the xorg.config file and found this under bus id: "PCI:0:16:0"
My card uses an AGP slot. Could this be the problem?

---

### Post by abtabt on 2007-06-29
do a backup of your x.org file

do a sudo dpkg-reconfigure xserver-xorg

then you can use witch driver you want (you get a list of drivers)

the best to try this out is to start in singlemod

then start x 

with 

startx

---

### Post by pxwpxw on 2007-06-29
A good clue to the problem is always in the /var/log/Xorg.0.log file writtten when X failed, it might still be there, you can tell by the date-time, but a new one is written at each restart of the xserver,

---

### Post by tcrroadie on 2007-06-29
Hi flyinggeko,

Could you please post the output you receive from this command?  This will list the display adapter device (video card) installed in your machine. 

```
sudo lshw -C display
```
> 
I was looking at the xorg.config file and found this under bus id: "PCI:0:16:0"
My card uses an AGP slot. Could this be the problem?

AGP video adapters are concidered PCI bus devices on Linux.  

For your information, there are mainly two open source video drivers for ATI graphics chipsets for Linux.  These drivers are "r128" and "radeon".   So for an ATI Rage 128 based video card you would use the "r128" driver in your xorg.conf file.  For ATI Radeon cards you would use the "radeon" driver.  

Please see the man pages for the r128 and radeon drivers for more information 

```
man r128 

```
```
man radeon
```

There is also no need to do a full "dpkg-reconfigure xserver-xorg" when you only need to change your video device driver.  Using a simple text editor such as "nano" to edit one line is much faster.  

PXWPXW also makes a good point about checking your xserver log files.  If you still have problems you may want to post your most recent xserver log file, so that we can take a look at it. 
```

less /var/log/Xorg.0.log > xorglog.txt
```

---

