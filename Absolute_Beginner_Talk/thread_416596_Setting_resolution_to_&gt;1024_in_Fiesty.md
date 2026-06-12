---
title: "Setting resolution to &gt;1024 in Fiesty?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by BrewsterPilot on 2007-04-21
Hi again, 
here's another n00b question...
I'm wondering if it's possible to set the resolution to larger than 1024x768px, preferably 1280x1024px?
It was possible in XP.:-\" 

As you can see, the maximum from the drop-down menu is 1024x768px.
[IMG]http://img99.imageshack.us/img99/5732/screenshotscreenresolutkd9.jpg[/IMG]

Thanks!
-BrewsterPilot

---

### Post by sad_iq on 2007-04-21
Type in a terminal **sudo nano /etc/X11/xorg.conf** and replace every instance of 1024x768 with 1280x1024 save...restart gnome...should work!!!
 Also install the graphical drivers for your card!!!
 ....well install the driver first and if it doesn't work try the comand I gave you!!! :)

---

### Post by altaaa on 2007-04-21
Open a terminal, type this in:

```
sudo gedit /etc/X11/xorg.conf
```

Find the section labeled "Screen";

Here you can find the resolutions per bit depth. For every bit depth, a resolution is specified in separate "subsections". IIt looks like this:

```
SubSection "Display"
Depth		24
Modes		"1024x768"
EndSubSection
```

Just add a subsection there with your resolution specifications. Like this (assuming you want 24-bit color):

```
SubSection "Display"
Depth		24
Modes		"1280x1024"
EndSubSection
```

Save and exit the file; restart X by hitting CTRL-ALT-BACKSPACE and you should be able to select the resolution in System > Preferences > Screen Resolution.

---

### Post by dnns on 2007-04-21
Do you have an NVIDIA video card? You could then try the restricted drivers and in the terminal type "nvidia-settings". A GUI will popup which options to write out a new xorg.conf file when you have configured among other things resolution and refresh rate.

---

### Post by jtraub on 2007-04-21
Before editing xorg.conf don't forget to make backup of this file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by BrewsterPilot on 2007-04-21
I've managed to screw this up... :-\" 
I tried all your tips (one at a time though), and since none worked I edited the depth setting from 24 to 32. Now when I try to start Ubuntu I get a row of gfx-related error messages after it boots into code mode. How can I revert the setting back again? I've got the original file saved on my desktop as "xorg.conf".

Thanks!

-BrewsterPilot

---

### Post by mdknaebel on 2007-04-21
I have the same error, is there also a way to increase the Refresh Rate?

Thanks

---

### Post by BrewsterPilot on 2007-04-21
Btw I'm currently úsing an old Win 98 laptop. :lolflag:

---

### Post by fire_storm on 2007-04-21
i got the same error yesterday because i tried those xserv commands , i formated the partition which linux was on from windows and reinstalled it , don't do what i did , i am a noob and i was too lazy to read..

however now my screen resultion is fine i used "nvidia-settings" thanks man , however my refresh rate is 57 it should be 60   =/

anyways thank you

---

### Post by mdknaebel on 2007-04-21
Those codes did nothing for me, changing the values and all, i have an ATI X850XT

Any Ideas?
Thanks

---

### Post by BrewsterPilot on 2007-04-21
> **mdknaebel said:**
> Those codes did nothing for me, changing the values and all, i have an ATI X850XT

Any Ideas?
Thanks


I have the X700 SE, did nothing for me either but screwing up my Ubuntu when changing the depth from 24 to 32...

---

### Post by Beliar on 2007-04-21
DONT change the color depth to 32 bit.
Its not like in Windows, 24 is the highest, thats because they are counting it differently.
If I remember correct, its that Windows also counts the Alpha Channel: 24 Bit Color + 8 Bit Alpha.

24 Bit is the highest, and its as good as Windows 32 Bit, it sounds just different, its the same.

---

### Post by BrewsterPilot on 2007-04-21
> **Beliar said:**
> DONT change the color depth to 32 bit.
Its not like in Windows, 24 is the highest, thats because they are counting it differently.
If I remember correct, its that Windows also counts the Alpha Channel: 24 Bit Color + 8 Bit Alpha.

24 Bit is the highest, and its as good as Windows 32 Bit, it sounds just different, its the same.

Yup, I've learned that now...:mrgreen: 
Any way to set it back through code/safe mode?
I just had spent ~5 1/2 hours setting up Ubuntu, I wouldn't want to do it again!:cry:

---

### Post by fire_storm on 2007-04-21
now that i checked my color depth is 24 also...
how can i increase it, i use nvidia 7600 GS

---

### Post by BrewsterPilot on 2007-04-21
> **fire_storm said:**
> now that i checked my color depth is 24 also...
how can i increase it, i use nvidia 7600 GS

You can't. 24 is maximum for Ubuntu; but according to other members (&Google) it's just as good as Windows' 32-bit.
Don't ever try it... ;-)

---

### Post by lagartoflojo on 2007-04-21
> **BrewsterPilot said:**
> Yup, I've learned that now...:mrgreen: 
Any way to set it back through code/safe mode?
I just had spent ~5 1/2 hours setting up Ubuntu, I wouldn't want to do it again!:cry:

Ok, so if you have the old xorg.conf saved in
/home/YOURUSERNAME/Desktop/xorg.conf
you can do this on the shell ("code") ```
$ sudo cp /home/YOURUSERNAME/Desktop/xorg.conf /etc/X11/xorg.conf
$ sudo /etc/init.d/gdm stop
$ sudo /etc/init.d/gdm start
```

If that doesn't get you back to X11, the try restarting your computer:
```
$ sudo shutdown -r now
```

Hope this helps!

---

### Post by cheesewhiz on 2007-04-21
> **BrewsterPilot said:**
> I've managed to screw this up... :-\" 
I tried all your tips (one at a time though), and since none worked I edited the depth setting from 24 to 32. Now when I try to start Ubuntu I get a row of gfx-related error messages after it boots into code mode. How can I revert the setting back again? I've got the original file saved on my desktop as "xorg.conf".

Thanks!

-BrewsterPilot

Same here, i've had to reinstall like 4-5 times just trying to fix the resolution.

---

### Post by vanadium on 2007-04-21
I can really help out here (newbe myself) but I guess that other mechanisms that xorg.conf control the available resolutions as well. In my xorg.conf, only the highest possible resolution is listed, yet I can choose a variety of resolutions (laptop with ATI card, proprietary drivers, but also worked after initial install of Edgy).

You could try this thread that discribes how to add custom resolutions to xorg.conf

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by singedwings on 2007-04-21
I am having the same problems, there may be a problem with the nvidia restricted drivers that I have still not worked around, but check out my reply in [http://ubuntuforums.org/showthread.php?t=416725&page=2]("http://ubuntuforums.org/showthread.php?t=416725&page=2") to get you started in the right direction.

The file I am referring to can be edited by typing this in a terminal

> sudo gedit /etc/X11/xorg.conf

Don't forget to backup first

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

To restore the backup if all goes wrong

> sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

### Post by jaja23bd on 2007-04-24
> **dnns said:**
> Do you have an NVIDIA video card? You could then try the restricted drivers and in the terminal type "nvidia-settings". A GUI will popup which options to write out a new xorg.conf file when you have configured among other things resolution and refresh rate.

 Thank you very very much.

---

### Post by Beliar on 2007-04-26
:(  You do not have to reinstal just because of resolution problems! Linux is very configurable and flexible, you can solve nearly every problem without reinstalling. Reinstalling and Rebooting are windows hacks, you can solve the problems easier.

If you have problems, just edit the xorg.conf in /etc/X11, that is where all the resolution and related stuff is located. There are a lot of tutorials for that and i think also tools. I'm totally not sure, but I think that typing "sudo X -configure" creates an xorg.conf with autodetected options. So if everything is broken, that'll maybe help.

---

