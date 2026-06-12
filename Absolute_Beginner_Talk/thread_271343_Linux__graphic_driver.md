---
title: "Linux  graphic driver"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2006-10-04
I have replaced an on board graphics card with a 128mb PEAK Nvidia GeForce 5200 AGP8X FX graphics card. The card seems to have been recognised and the graphics appear better to my 60 year old eyes. How can I tell if I've installed this card with the latest driver please.  The present driver is (nv) I have my seventeen inch flat screen monitor set at 1024X768 with a refresh rate of 75Hz at present.

---

### Post by fatsheep on 2006-10-04
If the Nvidia drivers are installed then there should be a "Nvidia Settings" icon in your Applications>System Tools menu.  Open it up and you will see the driver version at the bottom.  The latest linux driver is 1.0-8774 at the moment.  If you do not have the latest drivers then follow this guide to install them:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28drivers%29%7C%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28drivers%29%7C%28nvidia%29)

Hope this helps,

-fatsheep

---

### Post by whizbaby on 2006-10-04
'nv' means that you are not using the nvidia proprietary driver (I suppose you see this in /etc/X11/xorg.conf?).
First backup /etc/X11/xorg.conf
[B]
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup[/B]

Edit /etc/X11/xorg.conf to show *nvidia* instead of *nv* in the section of your/etc/X11/xorg.conf graphics card (after the 'Nvidia GeForce 5200' line).
Then hit ctrl-alt-F1 to change to a console, login and restart the x-server

**sudo /etc/init.d/gdm restart**

if this doesn't take you back to the graphical login logout (ctrl-d) and switch manually (ctrl-alt-F7). If anything goes wrong do

[B]sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart[/B]

EDIT:
Only change to *nvidia* if you have the proprietary drivers installed (nvidia-glx)!

---

### Post by ewl1217 on 2006-10-04
The nv driver is the preset driver, manily because it is open-source. However, it only supports 2D-Acceleration. If you want full 3D acceleration, you'll need the closed source nvidia driver. Just search through the repositories for nvidia and you should find it. After that you'll have to update your xorg.conf. Do that with the following command.
```
sudo nano -B /etc/X11/xorg.conf
```
From there, replace all instances of nv with nvidia. Press CTRL+X, Y, then enter to exit and save it. After that, log out and press CTRL+ALT+Backspace. After that just enjoy the beautiful graphics. If something doesn't work, use the following command to revert to your old xorg.conf.
```
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf && sudo /etc/init.d/gdm restart
```

---

### Post by jaboua on 2006-10-04
Also, the command "sudo nvidia-xconfig" should be able to auto-reconfigure xorg.conf for you (but as mentioned, backup the file before doing anything just in case)

---

### Post by bobpur on 2006-10-04
You might consider [www.getautomatix.com](www.getautomatix.com) or Easy Ubuntu for your nvidia drivers as both would greatly simplify the whole process.
If you've done everything correctly, you should see an nvidia splashscreen during the boot process. 
                                     Good Luck!

---

### Post by a.v.l on 2006-10-06
> **fatsheep said:**
> If the Nvidia drivers are installed then there should be a "Nvidia Settings" icon in your Applications>System Tools menu.  Open it up and you will see the driver version at the bottom.  The latest linux driver is 1.0-8774 at the moment.  If you do not have the latest drivers then follow this guide to install them:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28drivers%29%7C%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28drivers%29%7C%28nvidia%29)

Hope this helps,

-fatsheep

Well, I've followed these instructions and it seems I have installed the nvidea driver because I get a brief glimps of the nvidia splash screen when booting into Gnome.  Trouble is the print size when I go to the sessions window to change to KDE is so small I can barely see it.  All other text within ubuntu appears normalish.  Kubuntu text also appears reasonable.

I am a little unsure if I have the best options selected for my graphics card (nvidia Ge Force 5200 128mbs) as the text edges are a little fuzzy.  Can I make any further alterations to the card and if so where and how should I do this please?

---

