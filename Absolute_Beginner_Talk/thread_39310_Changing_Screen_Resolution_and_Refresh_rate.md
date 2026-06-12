---
title: "Changing Screen Resolution and Refresh rate"
date: 2005-06-04
forum: Absolute Beginner Talk
---

### Post by alexmoose on 2005-06-04
This is my first post, so hi. I have been Running Ubuntu for about 4 days. for about a year prior i ran Windows XP home Edition, and about a year prior to *that* i ran Mandrake 9.3, so i am new to the Ubuntu world. Inbetween going from Mandrake to Ubuntu, I upgraded to a 19-inch monitor, CRT, of course. My issue devolopes because i want to run my massive monitor at something higher than 1024 by 768, and at a higher refresh rate than 60hz. The System>>Preferences>>Screen Resolution only lets me run at 1024 by 768 at 60hz, which honestly, is starting to make my head hurt. Being one who know windows all too well, this would lead me to belive that i had poor video drivers, is this the case? and if so, how do i get more? or is this not a driver problem at all? any help would be appreciated.
                                                                                                 Thanks
                                                                                                 Alex Moose

---

### Post by skoal on 2005-06-04
60Hz??  Whoo doggey!  That's like watching your television set through a box fan.

It should be an easy enough fix, and it's more than likely what you suggested -> a video card driver issue (with a touch of frequency monitor loving)...

1. What is the manufacturer name/model of your monitor?
2. What is the manufacturer name/model of your video card?

For example, I have a Sony G400 19" monitor and an Nvidia Ti-4600 video card.  In my '/etc/X11/xorg.conf' file I have these relevant settings:

<snippage>

> Section "Monitor"
        Identifier      "Generic Monitor"
        VendorName      "Sony"
        ModelName       "G400"
        Option          "DPMS"
        HorizSync       30.0 - 107.0
        VertRefresh     48.0 - 120.0
EndSection

and even more <snippage>

> Section "Device"
        Identifier      "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
[...]
EndSection

<snipareffic>

> Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
[...]
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

---

### Post by alexmoose on 2005-06-04
1. Envision En-910e 19" however it is "Generic Monitor in Xorg.config
2.Intel Corporation 82810E DC-133 CGC (on Mainboard)
I also have an ATI Rage 128 PCI in the closet if that would be easier to configure

---

### Post by Error_Msg on 2005-06-04
This worked for me:
sudo dpkg-reconfigure xserver-xorg

E_M

---

### Post by alexmoose on 2005-06-04
Honestly, that scared the crap out of me

---

### Post by skoal on 2005-06-04
[QUOTE=alexmoose]Honestly, that scared the crap out of me[/QUOTE]

hahah. yeah, I'm still learning all these fancy doo-dad terms myself.

You might want to open up a terminal and just copy/paste what he typed in first.  I think I've read before that some guys with Intel i810 chips needed something like that.

Check these threads:
[http://www.ubuntuforums.org/showthread.php?t=27029&highlight=intel+i810](http://www.ubuntuforums.org/showthread.php?t=27029&highlight=intel+i810)
[http://www.ubuntuforums.org/showthread.php?t=30235&highlight=intel+i810](http://www.ubuntuforums.org/showthread.php?t=30235&highlight=intel+i810)
[http://www.ubuntuforums.org/showthread.php?t=35785&highlight=intel+i810](http://www.ubuntuforums.org/showthread.php?t=35785&highlight=intel+i810)

Possible soln's:

1. Copy/paste/type into a terminal what "Error_Msg" gave above.
2. Edit "/etc/X11/xorg.conf" with some editor (vi,gedit,etc.), and add this line under the Section "Monitor":

HorizSync 30.0 - 95.0

those numbers were taken from [http://www.envisiondisplay.com/products.asp?EPage=products&SMenu=en910e](http://www.envisiondisplay.com/products.asp?EPage=products&SMenu=en910e)

3. Use a color depth of 16 (not 24) in that same xorg.conf file.  Make sure under the Section "Screen", the following line is the same as this:

DefaultDepth    16

* Outside of that, you might want to drop that ATI card in there and check out the ATI guide somewhere in these forums.  You can either follow that one (which is for the ATI binary driver) or just use the default Xorg ati driver.

---

### Post by alexmoose on 2005-06-04
I'm typing this thank you on a 19" monitor going at 1280 by 1024, at 85hz, thank you both so much!

---

### Post by skoal on 2005-06-04
[QUOTE=alexmoose]I'm typing this thank you on a 19" monitor going at 1280 by 1024, at 85hz, thank you both so much![/QUOTE]

What was the solution for you?  If you post back with that sol'n it might help others who stumble across this post with a similiar problem.

---

### Post by alexmoose on 2005-06-05
I used the sudo dpkg-reconfigure xserver-xorg answer, it was scary, and at times i thought maybe i would break something. For come reason i couldn't ever find a way to edit Xorg.conf

---

