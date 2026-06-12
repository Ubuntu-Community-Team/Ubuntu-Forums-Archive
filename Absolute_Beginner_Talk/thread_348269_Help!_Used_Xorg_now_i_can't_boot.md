---
title: "Help! Used Xorg now i can't boot"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Daemion_AF on 2007-01-28
Ok I ran the xorg program to download and update my graphics card driver. Some of the info that i put in was way out of my league so i just went with the defaults. Now when i try to boot ubuntu the screen gets funny and a dialogue box pops up saying it hates me and it is disabling xorg. After this it brings me to a command prompt, at which i have no idea what to do at. I have 3 backups of "the kernel" (i guess?) and each one does the same thing. How do i get back in to my gui, and what is the correct way to use xorg?

---

### Post by taurus on 2007-01-28
Assuming you already logged in, try

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by Daemion_AF on 2007-01-28
Hey thanks alot taurus, that got it. The resolution still isnt right, but im scared to use xorg now lol.

---

### Post by taurus on 2007-01-28
If you want another resolution, just edd it in /etc/X11/xorg.conf.  And of course, always make a backup before you edit it just in case.

And if you tell me which resolution you want and the contend of your /etc/X11/xorg.conf, maybe I will show you how to do it.

```
cat /etc/X11/xorg.conf
```

---

### Post by Daemion_AF on 2007-01-28
I have an ATI x1400 graphics card in my laptop which displays 1920X1240 if my memory serves me correct. Pardon my ignorance for the command line usage as it is absolutely foreign to me. LoL I could barely get the dpkg-reconfigure command to work right as I had no idea that the spaces and hyphens would throw it off.

---

### Post by taurus on 2007-01-28
So you want to add "1920x1240" to /etc/X11/xorg.conf!  Just paste your /etc/X11/xorg.conf if you wish.

Applications -> Accessories -> Terminal
```
cat  /etc/X11/xorg.conf
```
Otherwise. you can edit /etc/X11/xorg.conf with

```
gksudo gedit /etc/X11/xorg.conf
```
Scroll down near the end and you will see a bunch of resolutions.  Add "1920x1240" to the front of all those resolutions in all the lines.

Save it and restart X again with

```
<Ctrl><Alt>Backspace
```

---

### Post by Daemion_AF on 2007-01-28
Im not really sure what im doing wrong here.... 


Applications -> Accessories -> Terminal
```
cat  /etc/X11/xorg.conf
```
Otherwise. you can edit /etc/X11/xorg.conf with
code]gksudo gedit /etc/X11/xorg.conf[/code]
Scroll down near the end and you will see a bunch of resolutions.  Add "1920x1240" to the front of all those resolutions in all the lines.

This is what i get when i type the above
(gedit:7312): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by taurus on 2007-01-28
I guess you have to use the text editor then.

```
sudo nano -Bw /etc/X11/xorg.conf
```
Use the arrow keys to move around.  And when you are done, hold <Ctrl> while pressing x to edit.  Answer the question with Y and Return.

---

### Post by yezzer on 2007-01-28
> **Daemion_AF said:**
> Ok I ran the xorg program to download and update my graphics card driver. Some of the info that i put in was way out of my league so i just went with the defaults. Now when i try to boot ubuntu the screen gets funny and a dialogue box pops up saying it hates me 

LOL :D :D

> **Daemion_AF said:**
> and it is disabling xorg. After this it brings me to a command prompt, at which i have no idea what to do at. I have 3 backups of "the kernel" (i guess?) and each one does the same thing. How do i get back in to my gui, and what is the correct way to use xorg?

Ive been there too! :) Dont worry, it gets easier... :P

---

### Post by Daemion_AF on 2007-01-28
Ok this is what i did when i went in i hope thats what you were talking about!

        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480" "1920X1240"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480" "1920X1240"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480" "1920X1240"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480" "1920X1240"
        EndSubSection

---

### Post by taurus on 2007-01-28
Actually, you want to add your desire resolution to the front.

```

EndSubSection
SubSection "Display"
Depth 8
Modes "1920x1240" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1920x1240" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1920x1240" 1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1920x1240" "1024x768" "800x600" "640x480"
EndSubSection

```

p.s.  Use lower case x...

---

### Post by Daemion_AF on 2007-01-28
Ok changed it to this, now do i need to run xorg or what do i do next?


        SubSection "Display"
                Depth           8
                Modes           "1920x1240" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1240" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1240" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1240" "1024x768" "800x600" "640x480"
        EndSubSection

---

### Post by taurus on 2007-01-28
Save it.  Now, restart X with <Ctrl><Alt>Backspace.  See if it takes the new resolution at all.

---

### Post by Daemion_AF on 2007-01-28
restarted x, it did not take effect immediately and there is no option for it under screen resolution

---

### Post by taurus on 2007-01-28
Are you sure your laptop can run at that high resolution?

---

### Post by Daemion_AF on 2007-01-28
In XP  thats what i was running.....im not really sure if i can run it with ubuntu but i would like to.

---

### Post by taurus on 2007-01-28
Don't forget, you also need to install a driver for your graphic card.  Maybe after installing a driver, you can use that high resolution!

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

