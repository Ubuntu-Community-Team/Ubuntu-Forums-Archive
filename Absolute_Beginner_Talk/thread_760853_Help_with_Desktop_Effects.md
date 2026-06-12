---
title: "Help with Desktop Effects"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by anarchy88 on 2008-04-20
Hey.  I am looking for help trying to figure out the desktop cube settings.  I ran
sudo apt-get install compizconfig-settings-manager
after that i followed the instructions and everything installed.  However when i go into the appearance window and select visual effects I try to click on the custom tab that is available and it says the composite extension is unavailable.  I am not sure what i am missing any help will be appreciated.  My graphics card is ATI Radeon Xpress Graphics Card.  I am also new to linux so details in the steps would be much appreciated.
Thanks
Geoff

---

### Post by aktiwers on 2008-04-20
Type:
```
ccsm
```And disselect "desktop wall" and enable "desktop cube" and "rotating cube".

Then enjoy your Cube.

:)

---

### Post by anarchy88 on 2008-04-20
I was able to get into the properties and have applied those settings.  The problem though is that when i try to select between the effects of 
None
Normal
Extra
Custom
It does not let me select one of those options it says composite extension is not available and then does not save the selection i made and my desktop remains the same and goes goes back to the none selection.  In the restricted drivers I also have my ATI accelerated graphics drivers in use.

---

### Post by aktiwers on 2008-04-20
That sounds like your video drivers are not installed correctly.
Have you tried download and installing the driver manually?

---

### Post by anarchy88 on 2008-04-20
I have not tried that how would I go about that? Also thanks for your time.

---

### Post by aktiwers on 2008-04-20
I think this guide will do :)
[http://linuxpoison.blogspot.com/2008/03/installing-ati-drivers-on-ubuntu.html](http://linuxpoison.blogspot.com/2008/03/installing-ati-drivers-on-ubuntu.html)

Though it does not explain how to install the .run file that well imo.
Here is how I would go:

Download the file to Desktop and open Terminal (applications=>accessories=> Terminal)

And type:
```
cd Desktop
``````
sudo chmod +x ati<hit tab key on your keyboard>
```Then:
```
sudo ./ati<hit tab key on your keyboard>
```If it says something about an error because xserver is running, let me know. I don't remember if X can be running on ATI driver install. It's 2 years since I had an ATI card.
EDIT: Oh yeah if it does not give an error, follow the from the "sudo dpkg...." part in the guide. 

Don't be scared ;)

---

### Post by anarchy88 on 2008-04-20
Thanks I will let you know how everything goes.

---

### Post by anarchy88 on 2008-04-20
Ok I have the driver downloaded.  When i tried to open it and run it it said could not open and gave me options of character coding.  I tried a few of those different options and that did not open the file.  I entered the code in the terminal even though i could not open that installer package and after entering

sudo dpkg-reconfigure xserver-xorg

I gota window about auto configuring xserver i selected yes and that took me to a screen saying I had the ATI Radeon Xpress 200 M 5955 (PCIE) Then I hit a dead end and it would not let me select anything else to continue.

Attached is the screenshot of what happens when i try to open the installer.

---

### Post by aktiwers on 2008-04-20
The commands I wrote above is the way you need to run the installer

---

### Post by Sef on 2008-04-20
Read [Forlong's blog]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#").

---

### Post by anarchy88 on 2008-04-20
> **aktiwers said:**
> The commands I wrote above is the way you need to run the installer

I wasnt entirely sure that is why i entered them anyway and was still unable to get it to work and got stuck when the xserver window came up

---

### Post by anarchy88 on 2008-04-21
Thanks i figured i finally got it to work.

---

