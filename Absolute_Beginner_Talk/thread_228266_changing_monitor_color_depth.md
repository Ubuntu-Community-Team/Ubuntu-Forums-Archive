---
title: "changing monitor color depth"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by brian7k on 2006-08-02
Hi I am new to ubuntu and having switched from open suse i cannot figure out how to change my color depth. Can someone plese tell me how to do this in ubuntu Thanks.

---

### Post by Dr. Nick on 2006-08-02
You can change it in your xorg.conf file.


 To edit from within gnome run:
 
 [COLOR=#0000DF]**gksudo gedit /etc/X11/xorg.conf**[/COLOR]
 
 To edit from a command line use:
 
  [COLOR=#0000DF][B]sudo nano /etc/X11/xorg.conf

**[COLOR=Black]look at screen section for default depth and change it, 24 is the highest depth[/COLOR]**

[/B][/COLOR]
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
        Monitor         "Generic Monitor"
        DefaultDepth   [COLOR=MediumTurquoise] [COLOR=RoyalBlue]24[/COLOR][/COLOR]

---

### Post by brian7k on 2006-08-03
Thank you very mutch

---

### Post by Levitation on 2006-11-21
When I entered
/etc/X11/xorg.conf 

I received: No such file or directory

What should I do?

---

### Post by LLRNR on 2006-11-21
[quote="Levitation"]When I entered
/etc/X11/xorg.conf

I received: No such file or directory[/quote]

You have to put "gksudo gedit" in front of your /etc/X11/xorg.conf file, this way you tell it to open with gedit (a text editor) in gksudo mode ("graphical" sudo mode - sudo is used for administrative privileges). Also notice that the X in X11 is an uppercase one, and that there is a slash (/) before etc : this is the way to give a path in UNIX/Linux systems (/ stands for root of filesystem).

---

### Post by DaveBorealis on 2006-11-21
> **Levitation said:**
> When I entered
/etc/X11/xorg.conf 

I received: No such file or directory

What should I do?

Hello,

Did you enter the command exactly as you posted here?  Try copying and pasting the following:
```
sudo gedit /etc/X11/xorg.conf
```

Dave

---

### Post by Levitation on 2006-11-21
Thank you SO much! I did not expect such quick replies. As a relative newcomer I have been banging my head against many walls. My laptop is very happy now.

---

### Post by LLRNR on 2006-11-21
Ok... Try to simply copy & paste the line that DaveBorealis typed in and see what happens. (And it's "gedit", not "gsedit", or maybe you made a typo)

---

### Post by seriousstorm85 on 2006-11-22
Thanks very much dude :-)

I can now visit buccaneers.com / tampabaylightning.com now :-)

---

### Post by jester261 on 2007-07-18
Hi after i entered ** sudo nano /etc/X11/xorg.conf** into the terminal of my Ubuntu 7.04 the only thing that happend is that the terminal changed into a text editor which says GNU nano 2.0.2 but there is nothing except a menu of actions down.:confused:
I want to ask for help and i want to say that i have any kind of Linux  for about a day or two which means that i don't know much about it.

---

### Post by Dr. Nick on 2007-07-18
> **jester261 said:**
> Hi after i entered ** sudo nano /etc/X11/xorg.conf** into the terminal of my Ubuntu 7.04 the only thing that happend is that the terminal changed into a text editor which says GNU nano 2.0.2 but there is nothing except a menu of actions down.:confused:
I want to ask for help and i want to say that i have any kind of Linux  for about a day or two which means that i don't know much about it.

did you use that same case? it is case sensitive.

alternatively you can open a terminal and type** gksudo gedit **then click open and navigate to /etc/X11/xorg.conf then open it.

---

