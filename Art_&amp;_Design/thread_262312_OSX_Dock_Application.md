---
title: "OSX Dock Application"
date: 2006-09-21
forum: Art &amp; Design
---

### Post by buzlink on 2006-09-21
Is there an application that will mimic the OSX Dock, such as Object Dock in Windows?

Thanks

---

### Post by wieman01 on 2006-09-21
There is something for KDE, not sure though if you can run it under Gnome (I am using it with KDE):

[http://www.kde-look.org/content/show.php?content=10955]("http://www.kde-look.org/content/show.php?content=10955")

Mine looks like this:

[http://ubuntuforums.org/gallery/showphoto.php?photo=3136&what=allfields&name=wieman01&name=wieman01]("http://ubuntuforums.org/gallery/showphoto.php?photo=3136&what=allfields&name=wieman01&name=wieman01")

---

### Post by HanZo on 2006-09-22
check this out:
[http://www.gnome-dock.org/trac](http://www.gnome-dock.org/trac)

---

### Post by buzlink on 2006-09-22
> **HanZo said:**
> check this out:
[http://www.gnome-dock.org/trac](http://www.gnome-dock.org/trac)

How would I go about installing this program.
Thanks for the link!

---

### Post by enopepsoo on 2006-09-23
re: gnome - dock.

what a weird site, I don't even see a download link.  That is too bad, it looks cool!

---

### Post by Kobalt on 2006-09-24
You can download the archive by clicking on the picture. 
To install it, check [this post]("http://www.ubuntuforums.org/showthread.php?t=200987"). 

Cheerio !

---

### Post by enopepsoo on 2006-09-24
Thanks, Kobalt.  It looks like it might be a bit over my head for the time being, as I can't get XGL/Compiz working yet. :p

---

### Post by janbanan on 2006-09-24
I made an OSX looking dock yesterday.
It's kiba-dock

---

### Post by cmost on 2006-09-28
Your desktop rocks!  I'm using Kiba-dock too, but, I find that my ability to configure it is broken somehow.  (For example, using the Kiba-gset utility fails to apply settings; Gconf doesn't list all options and changes don't stick.)  Maybe I used a flaky cvs snapshot, or something.  I'm stuck with the default configuration and that horrible "barber shop" dock background.  Two questions for you, if you don't mind:  1.)  Can you list the steps you took to install Kiba-dock properly?  Step-by-step so as not to be too confusing.  2.)  Can you tell me how to configured it to look like an OS-X dock?  I especially like your 3D Word icon.  Thanks; much appreciated!!!  :p

---

### Post by janbanan on 2006-09-29
Don't worry I'll try to help you young fella :)
First you probably have it correctly installed. I've those problems too with kiba-gset. I did all the editing in gconf. To get all the options in gconf I played around with kiba-gset(try to change as much as you can) and they will show up in gconf i think.

To make it look like OSX:
There are quite many options so I writing those I think you'll need only.
In geometry:
cap_margin = 0
cap_size = 20
icon_size = 65
margin = 28
radius = 0.1
In style:
animated_background = false
border_alpha = 30
border_color = #ffffff
border_width = 0.6
dock_alpha_1(and 2,3,4,5) = 0.3
dock_background = gradient
dock_color_1(and 2,3,4,5) = #ffffff
dock_style = classic
prelight_alpha = 0.4
prelight_color = #ffffff
show_all_borders = false

I think that's all.

The word icon I got from googeling around. In google search for pictures and firefox.png, amarok.png and so on. You'll probably find what you look for.

---

### Post by reubano on 2006-10-03
> **wieman01 said:**
> There is something for KDE, not sure though if you can run it under Gnome (I am using it with KDE):

[http://www.kde-look.org/content/show.php?content=10955]("http://www.kde-look.org/content/show.php?content=10955")

Mine looks like this:

[http://ubuntuforums.org/gallery/showphoto.php?photo=3136&what=allfields&name=wieman01&name=wieman01]("http://ubuntuforums.org/gallery/showphoto.php?photo=3136&what=allfields&name=wieman01&name=wieman01")

wow... nice icons.. where'd you get them from?

---

### Post by ashrack on 2006-10-10
So, how stable is KIBA DOCK?

---

### Post by ashrack on 2006-10-10
JANBANN
I just compiled it and installed it! And then I set it like U said! But I still only have black background! And when drop an icon on it and then hover it by mouse the icon just dissapears.
Any ideas?

ps. This is the error am getting if its relevant:
```
got desktop file: /usr/share/applications/brasero.desktop
TODO: Font: Sans

(kiba-dock:12349): Gdk-CRITICAL **: gdk_screen_get_monitor_geometry: assertion `monitor_num < GDK_SCREEN_X11 (screen)->num_monitors' failed

```

ps. Just I wild quess, could this be because I dont have XGL nor AIGXL installed?

---

### Post by flargen on 2006-10-13
> **ashrack said:**
> 
ps. Just I wild quess, could this be because I dont have XGL nor AIGXL installed?

Almost certainly

---

### Post by ashrack on 2006-10-14
in that case I wil be trying this proggy next week when I do a clean install of EDGY

---

### Post by falkenheart on 2007-05-08
But it lacks a zoom feature and the true feel of an OSX dock? or did you somehow incorporate that into your dock?

---

### Post by ralvynl on 2007-09-30
Please, hu can help with any dock at all, I just installed Ubuntu Ultimate 1.4 and I still have a plain desktop that I am not happy with, I would like to at least have the dock on ma desktop.
Thanx in advance

---

### Post by santiagoward2000 on 2007-09-30
You could try kiba-dock. It can be found in Treviño's repository, but you need to have compiz or beryl.

---

### Post by jpyanowski on 2007-10-01
Has anyone tried Avant Window Navigator? AWN looks nice and if you search the forum you will find many threads about it.

---

### Post by santiagoward2000 on 2007-10-01
I tried AWN, but couldn't open it (I actually gave up quite soon). Then I tried Kiba, and it worked as soon as I installed it, so I kept it. Besides, it feels so good to throw the icons all around my desktop!! :lolflag:

---

### Post by pavlov24 on 2007-10-02
Please anyone know where i can find this dock style like leopard ? is it a real dock or just flash animation ? 

[http://fr.youtube.com/watch?v=IlRRbWC5fng]("http://fr.youtube.com/watch?v=IlRRbWC5fng")

thanks

---

### Post by gun_p on 2008-01-15
> **pavlov24 said:**
> Please anyone know where i can find this dock style like leopard ? is it a real dock or just flash animation ? 

[http://fr.youtube.com/watch?v=IlRRbWC5fng]("http://fr.youtube.com/watch?v=IlRRbWC5fng")

thanks

I think it is cairo-dock:
[http://doc.ubuntu-fr.org/cairo-dock](http://doc.ubuntu-fr.org/cairo-dock)

---

### Post by nikoPSK on 2008-01-16
Awn kooldock and others.

---

### Post by tnya001 on 2008-02-04
Some body help me please..

I wanna install a xubuntu on my very old computer( 400mHz, 128 Ram, 
8Gig HardDrive, and a stock video card. Is it possible that it can have An Os X style Dock???

---

### Post by nikoPSK on 2008-02-04
> **tnya001 said:**
> Some body help me please..

I wanna install a xubuntu on my very old computer( 400mHz, 128 Ram, 
8Gig HardDrive, and a stock video card. Is it possible that it can have An Os X style Dock???

window composting works on even the oldest computers. Just set the effects to minimal in compiz and you're fine. :)

---

### Post by simplebeep on 2008-07-23
> **jpyanowski said:**
> Has anyone tried Avant Window Navigator? AWN looks nice and if you search the forum you will find many threads about it.

I have just started using AWN.  It is very nice, attractive, and functional.  I would recommend it to everyone!  :)

While you can find more info about it at [https://launchpad.net/awn](https://launchpad.net/awn) ,  I would recommend installing it through System: Administration: Synaptic Package Manager, as that will make sure everything is smooth and automated.  Search for "avant" and select "avant-window-navigator".
After marking that package for installation, and accepting its dependencies, also make sure "dbus-x11" is selected; there have been reports of it not getting selected in Gutsy.

Apply the changes, wait for everything to finish, then go to Applications: Accessories: Avant Window Navigator.  Right-click on a non-icon area of the dock to change settings, etc.  All other questions are probably answered at [http://wiki.awn-project.org/](http://wiki.awn-project.org/) .
The easiest way to add applications is to simply drag them from your Applications menu straight to the dock.  Remove them with a right-click.

I'm not sure about the dock starting up with your computer.  If it doesn't, go to System: Preferences: Sessions: Startup Programs: Add.  In "Command", type "avant-window-navigator" exactly like that.
(Please note that the attached image mistakenly says "manager" instead of "navigator".  Be sure you use "navigator", as it's the correct word!)

---

### Post by graeme3816 on 2008-12-20
Thanks, just followed your instructions, worked perfectly.

Easy to change the icons as well, some of my standard application icons were blurry when used on the dock.

---

