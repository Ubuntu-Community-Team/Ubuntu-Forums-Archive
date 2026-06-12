---
title: "Ubuntu Studio Boot problems"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by sublimesnfu on 2007-12-01
Hello everyone I am completely new linux and am a bit stuck here It will only boot into a command line interface any help would be appreciated greatly, I've just installed ubnutu studio 7.10 from dvd. I went through installation reformatted the hd so that ubuntu would be the only os, everything installed fine, when it came time to install other software  (ubuntu studio desktop, audio editing etc) I installed ubuntu studio desktop as I couldn't figure out how to select all of the available options during the install. The install completed and ejected the and rebooted, but it only rebooted into  what would look command line interface after running through what looked like a bunch of tests which all went good at which point I was prompted for my user name and password which I entered. After that I am still sitting here in the command line part of the os feel lost as what to do. I did try to figure out a few commands and was able to install GIMP after the OS requested I insert the install cd. Things to note, I do not have the computer connected to my network right now as I was planning on installing a wifi card once I had everything up and running. The computer is a Matrix P4 1.8 60gb ide 512 ram and a 32mb nvidea graphics card. Please some one help thanks

---

### Post by jken146 on 2007-12-02
Try ```
startx
```

---

### Post by sublimesnfu on 2007-12-03
entered startx and was told command not found

---

### Post by sonali11 on 2008-04-03
I don't know if you resolved your issue or not. But i had to do "Install Ubuntu Studio Desktop" in the software selection to get it to install the GUI mode, instead of the command prompt thing.

I tried 2d/3d and Video------ but both those options gave me the CUI prompt when i tried to boot the machine after the install.

Hope this helps some one like me (newbee).

I installed this from the ISO DVD image.

---

### Post by thevikingking on 2008-05-12
i have also had the problem stated above, even when i clicked install studio desktop it gave me the command prompt, and if the command isn't found that we were told to do xstart or whatever, then what do we do? 

im running out of options... 

please help!!!

---

### Post by pearjam on 2008-05-12
Try this from the command prompt?

(May have to hit ctrl+alt+f6, then log in as user or su. If already at a command prompt, then type below.)

sudo apt-get update

sudo apt-get -f install

sudo apt-get install ubuntustudio-desktop

(If you used ctrl+alt+f6 above, then use ctrl+alt+f7 to get out.)

Then reboot. It's worked when something like that happened to me (running Ubuntu Studio 8.04 64)

Hope that helps!

---

### Post by thevikingking on 2008-05-12
why is it that when the install was going it wouldnt let me choose ubuntu studio desktop with the other programs such as the music editor, the graphic software and all of that?

---

### Post by pearjam on 2008-05-13
> **thevikingking said:**
> why is it that when the install was going it wouldnt let me choose ubuntu studio desktop with the other programs such as the music editor, the graphic software and all of that?

The desktop installs by default, the optional installs are video, graphics and audio.

I LOVE being able to install just a slim desktop w/ the OS, and having the option to install software bundles that are included. Right on Ubuntu Studio, right on....

I'm keeping the dvds from the alpha releases in case they take away this option in the future!

---

