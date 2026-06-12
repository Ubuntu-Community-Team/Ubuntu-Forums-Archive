---
title: "I broke my Ubuntu; where is the big undo button? Geforce 440; X server fails to load."
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by SATTI on 2007-04-04
Hi

After following a guide on 'how to install beryl in Feisty supporting NVIDIA' I broke my Ubuntu system.

I shouldn't have installed it, but after setting up my wireless  and then getting the system to run Realtime in audio apps, i felt quite confident.

The problem is that the X server fails to load, and I am booted out into a terminal. I have no access to my graphical GUI.

I am using a Geforce Nvidia 440 mx, it was not until afterwards i came across a post stating that the new drivers do not support this card. 

So, is there any way i can revert my system to start up in the GUI again? 

I would hate to uninstall Ubuntu, because i have spent so much time trying to get it to work. I have tried following advice in the chat room, about editing the xorg file and replacing 'NVIDIA' with 'NV' 

I used the 'sudo nano /etc/X11/xorg.conf' command to edit that file.

But it is still not working, 

Can any body offer advice?

Thanks,

Satti.

---

### Post by sirhalos on 2007-04-04
I am not familiar with your video card perhaps it is usually the same chipset as a Geforce2 or earlier if it is you need to install the nvidia-legacy-drivers not nvidia-drivers. Please uninstall the regular nvidia driver and try installing the nvidia legacy driver.

---

### Post by Lucifiel on 2007-04-04
Perhaps you could try reading up on what to do, if you booted up into Recovery mode.

---

### Post by Kisil on 2007-04-04
Can you post a little more information about what you did to upgrade?  Specifically, which packages you upgraded and installed, and what line(s) you changed in xorg.conf.

I ran into a similar problem installing beryl, related to nvidia driver and X11 versions.  It sounds to me like you're going to have to downgrade some things, which I don't know how to do from a command line :/.

---

### Post by Obor on 2007-04-04
Try
```
 sudo dpkg-reconfigure xserver-xorg
``` leave default answer in all the questions except for the graphics driver and change that to mesa or nvidia... I think that should help.

Most of the guides tell you to backup your xorg  - are you sure you didn't? If you did you just need to copy the old one back.

---

### Post by fasoulas on 2007-04-04
sudo aptitude install ubuntu-desktop

this is the answer to ur problem

also

sudo dpkg-reconfigure xserver-xorg

Had the same problem before 3 months

---

### Post by rolando2424 on 2007-04-04
I had that problem back when I installed my Nvidia drivers on Edgy (Nvidia GeForce MX 400 (4000 I  can never remember)).

I had to install nvidia-legacy-drivers, but then I had to copy a line from the old log (the one with the nv driver) that had a line of my monitor right. When I replace that line, it started to work. Unfortunantly, I don't know where that file is.

I think it's somewhere in /var/logs or something...

---

### Post by Feba on 2007-04-04
I had a similar problem when I decided to replace my ATi card with my older nVidia because of driver problems.

While I couldn't find any solution to make Xserver boot, I just put the boot CD back in and reinstalled ubuntu. Imo, it saved me a lot of time to just redownload things instead of trying to find a real solution.

Once I reinstalled, however, my MX440 worked fine, the driver installation went right down to the letter of the instructions, and I can happily run games on it...it's not the smoothest...but i'm not expecting much from a card this old.

If you have a lot of things on your PC you can't afford to lose, or if it would be a big pain to redo all your settings, this isn't a very good option, but if you have things backed up or you just started using Ubuntu a few days ago there should be no problem.

---

### Post by lakersforce on 2007-04-04
Every time you upgrade your xorg.conf file a backup is usually made in your /etc/X11/ folder. You just have to find the rigth backup file and replace it. For example:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

EDIT: If you all manually edited the file without taking any backup of it and everything is screwed up and there is nothing you can do, then my friend, you are out of luck. Remember: Real men does not take backup. They cry :)

2nd edit: Always remember to backup your xorg.conf file after a fresh install. It should be the first you do, because then you can always revert your disastrous changes. Of course safe mode might be able to help too.

---

