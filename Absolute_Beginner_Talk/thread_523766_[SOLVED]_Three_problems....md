---
title: "[SOLVED] Three problems..."
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by na_silu on 2007-08-12
Ok so I've wanted to use linux for a long time and it wasn't until ubuntu came along that I prompted myself to make the switch. Now that I have ubuntu installed however, I am having some trouble. First problem is that I have no idea how to install drivers. I downloaded a set of drivers for my motherboard and it has the extension .run, which I have never seen before. I tried double clicking it and extracting it but to no avail. I have no idea what to do with it. Secondly I can't seem to find any drivers for the Sound Blaster X-Fi series, is there any that exist for linux? And finally, I've been playing around downloading themes to spice up my distro but I can't seem to get any Window borders. Any help or insight would be greatly appreciated.

---

### Post by zvacet on 2007-08-12
[https://help.ubuntu.com/community/InstallingRunPackage]("https://help.ubuntu.com/community/InstallingRunPackage")

---

### Post by shearn89 on 2007-08-12
hey - welcome!

1. Why do you need to download drivers for your motherboard? surely its already working? Apart from that, make sure they're linux drivers. I've never seen the .run extension either...

2. Have a look [here]("http://ubuntuforums.org/showthread.php?t=239981") and see if that helps?

3. In the theme manager, select your theme, then go to "options" or "details" (something like that), and it should let you choose window borders.

EDIT: just seen post above. Seems like that will solve #1.

---

### Post by por100pre1 on 2007-08-12
Try installing Art Manager, look for it in Add/Remove or copy/paste this in a "terminal" window:

```
sudo apt-get install gnome-art
```

With it you can download window borders and other goodies. Then you can use the Theme Manager to use them:

```
gnome-theme-manager
```

Hope this helps. :)

---

### Post by 1/0 on 2007-08-12
1) [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

[http://www3.telus.net/lordfoul/pics/useful%20ubuntu%20links/useful%20unbuntu%20links.html](http://www3.telus.net/lordfoul/pics/useful%20ubuntu%20links/useful%20unbuntu%20links.html)

Stay away from automatix. It has been reported to have lots of [bugs]("http://mjg59.livejournal.com/77440.html"). Just an advice. I don't understand why you would need external drivers for your main board?? Are the ones in the kernel not sufficient? What board is it?

2) When it comes to the Sound Blaster [Creative labs seems to be actively preventing drivers for Linux]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") as well as [charging $9.99 for Vista drivers!!!]("http://www.dailytech.com/article.aspx?newsid=7926") Talk about suicide!

3) What distro/wm are you using, i.e. Ubuntu, Kubuntu, Xubuntu or Gnome/KDE/XFCE/E17/fluxbox/Ice/wm?

---

### Post by na_silu on 2007-08-12
Ok I probably should have been more specific about my situation, sorry about that. The reason why I am trying to install my motherboard drivers is because I am getting no sound. And I think installing the motherboard driver from Asus that is available for linux will let my on board audio work, until I can get my Sound Blaster card working at least. Unfortunately, and this is going to sound really dumb, but I did check the little box to "run as a program" in the drivers properties, and then it ran. However it requires root access. I tried logging into my root account, but I don't know what the password is :confused: and I don't remember even making one during the setup. I tried leaving it blank, using root as the password, and using the password I use for my user account, none of them worked. As far as the window borders, I installed gnome art but it doesn't seem to have made any difference and I can't find it as an application. But I should have also been more specific about my window problem. It isn't that I can't access the window setting in the theme manager, but the options are very limited and for some reason, when I installed my theme it installed under all other tabs, icons, etc. But theres nothing there for the window border. Maybe I'm just going crazy, I'm sure my problems have simple answers. Thanks for all the help so far, its getting my closer to a solution and more familiar with the linux environment and sorry for all the newbie questions. This is my first time really using linux so everyone knows and I am using the latest official release of Ubuntu. Sorry for the long post as well, hope theres no typos and it makes sense.

---

### Post by 1/0 on 2007-08-12
I think your best solution is to tell us the motherboard model and the model of your sound card. That way it will be easier to point you in the right direction. 

As for root access there is no root account in ubuntu (more secure). Instead type sudo in front of your command it will be the same as doing it as root.

---

### Post by na_silu on 2007-08-12
Ok my motherboard model is a Asus M2N-E SLI and my sound card is a Sound Blaster X-Fi Extreme Music sound card. I can't type sudo when I try to run the driver for my motherboard. It just brings up a terminal that says I don't have the right permissions to install it. And then it only gives me the option to exit, nothing else.

---

### Post by shearn89 on 2007-08-12
ok:
1. For the window borders try downloading Metacity themes. That might work.
2. For the driver, press alt-f2 (maybe alt-f1) and type "gksudo nautilus", then run the driver install. It should work.

---

### Post by na_silu on 2007-08-12
Ok pressing alt+F2 worked, unfortunately my system no longer has internet, and I am writing to you from Windows now :( It said I needed the libc development package and that it couldn't install properly without it. Then my internet connection just went dead. And I don't know how to get it back up now. The drivers I was trying to install were for the ethernet and sound drivers, from Asus.

---

### Post by por100pre1 on 2007-08-12
> **na_silu said:**
>  As far as the window borders, I installed gnome art but it doesn't seem to have made any difference and I can't find it as an application. But I should have also been more specific about my window problem. It isn't that I can't access the window setting in the theme manager, but the options are very limited and for some reason, when I installed my theme it installed under all other tabs, icons, etc. But theres nothing there for the window border.

Art Manager can be found under System> Preferences> Art Manager. Gnome Theme Manager is the same Menu. Be sure to pick select a theme, then select "Customize". There you'll be able to select some settings and even make a custom theme. Give it try, once you find everything, it'll be a snap to use.

---

