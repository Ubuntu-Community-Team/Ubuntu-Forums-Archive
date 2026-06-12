---
title: "[SOLVED] x-org brokeen"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-09-25
Please help!! I made some changes (screen resolution) using the command sudo gedit /etc/X11/xorg.conf.
I guess I made a mistake on one of the screen sizes because after I saved and did a ctrl,alt,backspace it would not start, and gave me an error 1440x900 not valid (or something to that effect.
I tried to use the sudo command to fix it but got the message gedit command not valid.  Please help me get ubuntu back!!!:(:(:(

---

### Post by reckless2k2 on 2007-09-25
ok....1st of all.....always always always backup before you start "tweaking" an important file like that. hahaha. 2nd....you'll have to edit it from the terminal using nano

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by overdrank on 2007-09-25
> **skyjacker said:**
> Please help!! I made some changes (screen resolution) using the command sudo gedit /etc/X11/xorg.conf.
I guess I made a mistake on one of the screen sizes because after I saved and did a ctrl,alt,backspace it would not start, and gave me an error 1440x900 not valid (or something to that effect.
I tried to use the sudo command to fix it but got the message gedit command not valid.  Please help me get ubuntu back!!!:(:(:(

Hi you can use the command
```
sudo dpkg-reconfigure xserver-xorg
```
Edit to slow

---

### Post by Sarteck on 2007-09-25
Hey, are you by any chance using an nVidia driver?  Recently, there was an update to the linux generic kernel, and when that gets updated, we nVidia users have to re-install the kernel module for our drivers (or at least that's what I read--my kernel update is still downloading, so I haven't confirmed it).

---

### Post by skyjacker on 2007-09-25
> **reckless2k2 said:**
> ok....1st of all.....always always always backup before you start "tweaking" an important file like that. hahaha. 2nd....you'll have to edit it from the terminal using nano

```
sudo nano /etc/X11/xorg.conf
```
I thought about backing up the file but I don't know which file, and I don't know how to recover if something did go wrong --- like now. Thanks for the code, I'll try it.

---

### Post by reckless2k2 on 2007-09-25
how to backup a file prior to tweaking:

from the terminal >

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

that should give you the basic idea.

---

### Post by skyjacker on 2007-09-25
> **reckless2k2 said:**
> how to backup a file prior to tweaking:

from the terminal >

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

that should give you the basic idea.
Thanks, i filed this command for future reference. Now back to my problem... I forgot to put " in front of one of my resolution settings. After using the command [sudo nano /etc/X11/xorg.conf] I was able (after several minutes of guessing) to find the proper lines and edit them. I could not figure out how to save them and exit the program.  Can anyone provide step by step instructions to a noob in trouble???:confused:

---

### Post by Dr Small on 2007-09-25
To save in nano, press CTRL + O.
To exit nano, press CTRL + X.

Dr Small

---

### Post by skyjacker on 2007-09-25
> **Dr Small said:**
> To save in nano, press CTRL + O.
To exit nano, press CTRL + X.

Dr Small  Thanks, going in for another bout with this problem...

---

### Post by skyjacker on 2007-09-25
Thanks to all who helped with this problem. It is corrected and I am once again going full bore in ubuntu. I have documented each piece of code, and will log in my files for reference.  Thanks again!:)

---

