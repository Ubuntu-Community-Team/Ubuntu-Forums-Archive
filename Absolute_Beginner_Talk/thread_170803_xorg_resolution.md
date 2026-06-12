---
title: "xorg resolution"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by bt224 on 2006-05-05
Do I need to save or anything after I change this:

edit your xorg.conf file and add the resolution you need

sudo gedit /etc/X11/xorg.conf

in a terminal

it will pop up with the xorg.conf file.. scroll down to the section where you see the resolutions displayed.. and add the one you need in front of the others in the same format

heres what mine looks like.. find this section

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x800"
EndSubSection

then add in say 1024x768 if thats what you want in those spaces near the other resolutions in the same format
so after modes "1024x768" "1280x800"

reboot and select your resolution in the screen resolution under system

---

### Post by bt224 on 2006-05-05
just got the gedit window open, all I got was a blinking cursor, none of the above text.

---

### Post by henriquemaia on 2006-05-05
Yes, you have to save the changes so they will become efective next time you restart your graphical environment.

As for your second question, close gedit and open it again writing this on a terminal:

```
sudo gedit
```

Then, once gedit is open, press **File** --> **Open** (or ctrl+o) and find your way to the file xorg.conf . You'll find it under **etc**, then **X11**. Maybe you'll get it open like this. 

After that, make the changes you want and save them.

---

### Post by bt224 on 2006-05-05
That worked beautifully to get me there.

But the correct resolution is there 1024x768. However when I try to change the resolution from Preferences, the highest it goes is something like 860x480 and 600x480.

---

### Post by hellmet on 2006-05-05
**sudo dpkg-reconfigure xserver-xorg**
u'll be asked for all the res's u want.
select the one u want.
then onwards..u'd be able to select
you res's from the preferences.

Happy Ubuntuing

---

### Post by bt224 on 2006-05-05
Nope, tried that several times.

[http://ubuntuforums.org/showthread.php?t=170535](http://ubuntuforums.org/showthread.php?t=170535)

No worky, except that it did put the correct resolution in gedit, it's just not in the drop down to select. I basically have a 2 inch frame around a small window. This is a laptop and there are no buttons to change the monitor sizing. There are some function buttons that did this is MS, but not in Linux.

Edit: For what I'm going to use this for, the actual resolution isn't so important, I just want to use the whole screen (not to be confused with fullscreeen)

---

### Post by hellmet on 2006-05-05
oh k..
i got that working in my PC.
Sry cud not help.

---

### Post by bt224 on 2006-05-05
Nope, thanks for the suggestion!

---

### Post by georgetoon on 2006-05-06
[QUOTE=hellemt]**sudo dpkg-reconfigure xserver-xorg**
u'll be asked for all the res's u want.
select the one u want.
then onwards..u'd be able to select
you res's from the preferences.

Happy Ubuntuing[/QUOTE]

Thanks for this.:) 

I went through most of this and all it did was ask me for keyboard layouts and configurations. so, I dumped out of it.  if the screen rez routine was in there someplace, it takes an awful long time to get to it.

My screen rez problem is still unreolved.

---

### Post by richbarna on 2006-05-06
bt224 hi,
what graphics card have you got on your laptop?
With an ATI graphics card you can do 1 of 2 things

1. sudo gedit /etc/X11/xorg.conf and instead of using the driver "ati" you can delete it and type "vesa". (This solved a laptop problem for me)
2. or download a newer ati driver from here :-
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

I'm no expert at this, but I actually prefer different suggestions if they work or not.

---

### Post by georgetoon on 2006-05-06
[QUOTE=richbarna]bt224 hi,
what graphics card have you got on your laptop?
Is it ATI ?[/QUOTE]

I'm using a desktop.  I have the Nvidia FX5500-TD256 card.  256 megs.

---

### Post by georgetoon on 2006-05-06
Success!:)

I ran sudo dpkg-reconfigure xserver-xorg and went through the entire thing.  I then selected the resolutions I needed.:)  (a quick tip:  I got this from the Linspire forum folks...use the space bar to select and deselect the monitor resolutions you want to add).  I also made sure of the proper horizontal and and vertical synchronization rates for my monitor. 

My monitor info is at:
[http://www.kdsusa.com/ProductDetails.asp?prod=10](http://www.kdsusa.com/ProductDetails.asp?prod=10)

anyone else running a KDS can find similar info for thier monitor up there, as well.:)

So, that did it! Many thanks to all!

I'm now getting the same rez and refresh rates as when I'm in Linspire. Nice!:)

---

