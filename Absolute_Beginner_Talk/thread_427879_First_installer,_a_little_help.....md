---
title: "First installer, a little help....?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Recoil42 on 2007-04-29
Okay, just got done installing Feisty about 5 minutes ago.

Actually, it's not my first install... I installed Ubuntu 5.x a while back on one of my PCs, just to play around, but I barely messed with it for 10 minutes before forgetting it altogether.

But I've been reading up on 7.x for a while, and it seems nice, plus yeah, the call of Beryl/Compiz is strong. So I installed it again.




...and promptly, within a few minutes, have run into several problems/questions:


1. *****. I deleted the little wireless indicator icon on the top right of the screen, and have no idea how to get it back.*

See:
[[IMG]http://img259.imageshack.us/img259/9174/screenshotaq4.th.png[/IMG]](http://img259.imageshack.us/my.php?image=screenshotaq4.png)

How do I get it back?

2. ..and how do I get the weather (nifty!) and power/battery indicators, which I *was* able to find, next to it, rather than placed next to the firefox/help/mail icons? And not seperated by a divider?

3. How can I disable the tap-to-click feature on the laptop's synaptics touchpad? I hate the damn thing, and it seems to be even more sensitive in Ubuntu than it is in Windows! I found something listed in the wiki about something called "qsynaptics", but I couldn't figure out, for the life of me, how to use it!

Thanks!

---

### Post by starcraft.man on 2007-04-29
1) I think your referring to the network-manager, if you uninstalled it just type in the terminal :

```
sudo install network-manager
```. Then set it to reboot go to System > Preferences > Sessions. Click add and type, network-manager.

If you just quit it, type network-manager into terminal to start it back up. Or reboot.

2) The power tray icon is added by the menu, System > Preferences > Power Management, go to general tab and click Always Display Icon. :) I don't know the weather icon your referring to... only thing I can think of is its a widget...

3)I'm a desktop guy, I dunno.

---

### Post by Rotaj on 2007-04-29
Rightclick on either the upper or lower panel. 
Sellect  "Add to Panel".
Drag it to where you want it.

---

### Post by Recoil42 on 2007-04-29
Just to be clear, it's the little thing with the little blue connection bars that you can click on, and see a list of all the wireless networks in range... hold on, lemme do a GIS...


here we go:

[http://www.debianadmin.com/images/wpa/2.png](http://www.debianadmin.com/images/wpa/2.png)

that thingie.


edit: The website that GIS found that image on seems to know exactly what I'm talking about... it's too bad I dont speak (spanish?) :

[http://riledhel.blogspot.com/2007/01/configurando-ubuntu-y-wpa.html#links](http://riledhel.blogspot.com/2007/01/configurando-ubuntu-y-wpa.html#links)



Also, I just noticed that my screen seems to be limited to 1024x768... I'm guessing a result of Ubuntu not recognizing the monitor, and just using some genericness. Any help on that?

---

### Post by Recoil42 on 2007-04-29
> **Rotaj said:**
> Rightclick on either the upper or lower panel. 
Sellect  "Add to Panel".
Drag it to where you want it.

It doesn't appear in that list at all.

---

### Post by Rotaj on 2007-04-29
Right-click on an empty area of either the upper or lower panel. "Addto panel" should be the top choice.

---

### Post by shae on 2007-04-29
Right Click on the Panel>Add to Panel>Network Monitor

To move any of those, you can right click on them and click move.  When in the desired location, click.

---

### Post by Recoil42 on 2007-04-30
Again, the network manager doesn't appear in the resulting list. That's the odd part, you would expect it to. but yeah, it doesn't.

And it's definitely not the same thing as the network monitor, shae.

---

### Post by Recoil42 on 2007-04-30
Here's what I see in the add to panel dialog:

[[IMG]http://img441.imageshack.us/img441/5193/screenshotaddtopanelov5.th.png[/IMG]](http://img441.imageshack.us/my.php?image=screenshotaddtopanelov5.png)

See? No option for the network manager.

And yet, apt-get'ing **network-manager **or **network-manager-gnome** seems to result in a message that tells me that both are already installed.

```
recoil@recoil-laptop:~$ sudo apt-get install network-manager-gnome
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-gnome is already the newest version.
The following packages were automatically installed and are no longer required:
  libqt3-mt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
recoil@recoil-laptop:~$ 

```

---

### Post by Recoil42 on 2007-04-30
Okay, after doing alot of tracking down, it looks like I'm looking for something called **nm-applet**.

I need to start it, or something...?

---

