---
title: "install flash player in dapper"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Vega on 2006-05-30
not even automatix dapper will help in this one. I've tried using terminal but that fails as well. 

> redsteel@redsteel-d5150:~$ sudo apt-get install flashplugin-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-mozilla
redsteel@redsteel-d5150:~$ sudo apt-get install flash
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flash
redsteel@redsteel-d5150:~$ sudo apt-get install flashplugin-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-mozilla
redsteel@redsteel-d5150:~$ sudo apt-get install flash player
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flash
redsteel@redsteel-d5150:~$


---

### Post by Sef on 2006-05-30
Try [RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats").

Also did you enable Universe and Multiverse?  If not, then click on  [Adding Repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto").

---

### Post by Vega on 2006-05-30
> redsteel@redsteel-d5150:~$   sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
redsteel@redsteel-d5150:~$   sudo update-flashplugin
redsteel@redsteel-d5150:~$


alright this is what I get, what's the next step?

---

### Post by aysiu on 2006-05-30
[QUOTE=Vega]alright this is what I get, what's the next step?[/QUOTE] Go to a website that uses Flash.

---

### Post by Vega on 2006-05-30
[QUOTE=aysiu]Go to a website that uses Flash.[/QUOTE]
I did and it says the same thing, like in youtube. Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Click here to get the latest flash player.

---

### Post by aysiu on 2006-05-30
They don't make Flash 8 for Linux yet.

---

### Post by Vega on 2006-05-30
[QUOTE=aysiu]They don't make Flash 8 for Linux yet.[/QUOTE]
good Lord! the patients I put up with. :rolleyes:

---

### Post by aysiu on 2006-05-30
[QUOTE=Vega]good Lord! the patients I put up with. :rolleyes:[/QUOTE] Yes, I can understand why you might have very little patience for Macromedia, too. [As you can see, they haven't yet produced Flash 8 for Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW). Go complain to them.

That said, you don't need Flash 8 to play videos on YouTube.

---

### Post by Sef on 2006-05-30
Flash 8 will not be ported to GNU/Linux; however, Flash 9 will be.

---

### Post by Vega on 2006-05-30
[QUOTE=aysiu]Yes, I can understand why you might have very little patience for Macromedia, too. [As you can see, they haven't yet produced Flash 8 for Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW). Go complain to them.

That said, you don't need Flash 8 to play videos on YouTube.[/QUOTE]
what will play it then? How do I change options to play with a diff media player?

---

### Post by aysiu on 2006-05-30
[QUOTE=Sef]Flash 8 will not be ported to GNU/Linux; however, Flash 9 will be.[/QUOTE] Thanks for that addendum, Sef. Maybe Vega will develop enough patience to wait for Flash 9.

---

### Post by aysiu on 2006-05-30
[QUOTE=Vega]what will play it then? How do I change options to play with a diff media player?[/QUOTE] Flash 7. That's what I used to get that screenshot.

What web browser are you using? I'm using Firefox, and the Wiki instructions for installing Flash worked for me, just as you did them. Are you using Konqueror maybe? or Opera?

---

### Post by Vega on 2006-05-30
[QUOTE=aysiu]Flash 7. That's what I used to get that screenshot.[/QUOTE]
alright somehow I got flash to install via FF plugin installer. however there is no sound. At least I am making some progress

keep up the good works guys!

---

### Post by aysiu on 2006-05-30
[QUOTE=Vega]alright somehow I got flash to install via FF plugin installer. however there is no sound. At least I am making some progress

keep up the good works guys![/QUOTE] Try this. It may help: ```
sudo aptitude update
sudo aptitude install alsa-oss
``` You'll have to restart Firefox, of course.

---

### Post by Vega on 2006-05-30
[QUOTE=aysiu]Try this. It may help: ```
sudo aptitude update
sudo aptitude install alsa-oss
``` You'll have to restart Firefox, of course.[/QUOTE]
I give you guys a 5 gun salute!

Excellent Work!

---

### Post by aysiu on 2006-05-30
[QUOTE=Vega]I give you guys a 5 gun salute!

Excellent Work![/QUOTE] So, did it work?

---

### Post by Vega on 2006-05-31
[QUOTE=aysiu]So, did it work?[/QUOTE]
absolutely!

---

### Post by aysiu on 2006-05-31
[QUOTE=Vega]absolutely![/QUOTE] Great. Glad to hear it.

---

