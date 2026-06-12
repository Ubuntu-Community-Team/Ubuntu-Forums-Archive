---
title: "Resolution issues"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Lee7 on 2007-10-09
Hi all,

I cannot use 1280x1024 resolution with Ubuntu. I have an ATI x1950 PRO graphics card that is capable of running at that resolution. I've read some guides, however I'm not able to edit the xorg.config file using the terminal because it doesn't open up into a text file (it stays in the terminal and I don't know how to save the changes that way).

Also, there are some restricted drivers for ATI - should I use those? When installed, they mess up my desktop a little. Any help would be appreciated. :)

---

### Post by skymera on 2007-10-09
dont edit xorg like that!

you may break it, its sensitive.

sudo dpkg-reconfigure -phigh xserver-xorg

then choose your desired res.

for the driver, use Envy to install the llatest

---

### Post by Tiekyl on 2007-10-09
I don't know much about ATI drivers, but if your trying to edit the xorg.config file, what program are you using to open it? Nano?

...Nvm. I was assuming the backup files and all the neccessary precautions. My apologies.

---

### Post by Lee7 on 2007-10-09
> **skymera said:**
> dont edit xorg like that!

you may break it, its sensitive.

sudo dpkg-reconfigure -phigh xserver-xorg

then choose your desired res.

for the driver, use Envy to install the llatest

Reconfiguring doesn't help, I have to reboot and the GUI can't load - so I have to reinstall Ubuntu. When using Envy to install my ATI drivers, they have load glitches at the bottom of the desktop and are generally sluggish, but don't provide me with a higher resolution. :(

---

### Post by Lee7 on 2007-10-10
I also have dual display, but Ubuntu has detected the lower resolution monitor and that might be why I cannot use a higher resolution? Installing those ATI drivers isn't an option since it messes up my system, but is there a way to get ubuntu/xorg to redetect my higher res monitor?

---

### Post by perixx on 2007-10-10
Hello Lee7!


Dunno if it's any help to you... but I have an Xpertvision X1950gt 512 MB, so basically the same type of graphics card like you. Under Xubuntu 7.02 I made it work by installing the ATI 'restricted' drivers under Applications > System > Restricted Manager... 
I know it's proprietary stuff, but it was the only fast solution for me. I would think that open ATI drivers aren't ready for supporting such a new graphics card by now anyway..?
Maybe also changing the 'Aperture Size' in BIOS from 64MB to 128 MB might help?

perixx

Update:

oops... didn't read the 'sticky' thread overheads.... it might just be what you're looking for (explains also why it worked for me under 7.02): [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by finferflu on 2007-10-10
Could you post your /etc/X11/xorg.conf?
I remember I had to edit that file in order to get the resolution I wanted. Also, if you edit it and then aren't able to start the X server, you can always revert back to a backup file or edit the relevant lines back ;)

---

### Post by perixx on 2007-10-10
Hello again Lee7....


as we're 'brothers in cards' as to say, I'm back again - maybe something of the following's of use to you :^)


I believe I read somewhere that the 'radeon' drivers support the ATI X19xx series, so you might want to try this setting in your xorg.conf - cannot give any guarantee for that, though.

If you want to edit your xorg.conf, just type 'sudo nano /etc/X11/xorg.conf'
you'll be prompted for your password - enter it.
after that, you're in the text-editor; you can navigate with the cursor keys and edit away - that would be "vesa" into "radeon" under your 'device > driver' section in your case. You can also add new resolution options to your 'screen' section; just add sth. like "1280x1024" into the line with your desired color depth.

Another issue (which I need to pay attention to very regularly, for I'm a STILL-BEING-CRT-USER!) is the 'monitor' section, where you can set up your monitor specs for higher refresh rates (that would be, say, HorizSync 30-91 / VertRefresh 50-150 in my case, while the second VertRefresh value resembles the highest possible screen refresh rate... you might have to go a bit higher there for getting appropriate options for higher refresh rates in your 'display settings' manager - to have, e.g. 1024x768@100Hz) - but you hardly will need that, having a LCD panel. Also, keep in mind that editing those values can damage your monitor, if set inappropriate / too high.

There's another possibility via setting specific 'mode lines', but I didn't use them so far - if you'd need info about it, I'd have to dig a bit in my personal 'data base' :]  

Save your work by pressing CTRL+O and exit via CTRL+X.
This should work under console and plain text surface.

Under desktop environment you could also use the 'run program' option > 'sudo mousepad /etc/X11/xorg.conf' for the same purpose.
Please be careful when editing this one, as told before. You can always re-edit it in cmd-line-with nano or e3 (if installed) and insert the old values / drivers.

If I'm mistaken in some cases, please feel free to tell me so.
I hope I could help you with that... good luck and happy editing!

perixx

---

### Post by Lee7 on 2007-10-10
Ok, placing that resolution in the config file has worked. Thanks for the help!

I have two monitors, one that can utilise 1280x1024 and the other can only use 1024x768. Is there anyway to set this?

---

### Post by perixx on 2007-10-10
Beats me ...


maybe if you have a look into your xorg.conf file and there are two separate sections. e.g for 'monitor0' and 'monitor1' or the likes, you can adjust it to your needs accordingly.

I never had a dual-screen setup, so I cannot say. Sorry!

perixx

---

### Post by perixx on 2007-10-15
Hey Lee7!

I've stumbeld upon something that might help you with your dual-screen resolution setup by chance:

[http://ubuntuforums.org/showthread.php?t=532466&highlight=login+screen+localization](http://ubuntuforums.org/showthread.php?t=532466&highlight=login+screen+localization)

have a look a this guy's xorg.config and use it as a template for yours - just change the values to fit your needs...

greetz,


perixx


P.S. provided you use 2 graphic cards, that is - but it still might work if set up correctly.

---

