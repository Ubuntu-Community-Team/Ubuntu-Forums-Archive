---
title: "Complete noob needs custom screen resolution on Hardy Heron"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by vorostatz on 2008-04-21
Ok just to start I am loving Hardy Heron so far, and even though it wasnt to wise for a complete newbie to try the Wubi installation, I couldnt resist it.

On my media center, which is hooked up to my flascreen 32 inch TV (via dvi to hdmi cable) it looks gorgeous, with one slight hitch.  I cant get a resolution which allows me to see the whole screen (the top and bottom and bottom bars are cut off.  The two best resolutions are 1920 x 1080 and 1280 x 720 (everything else cuts off too much).  Is there anyway to tweak the resolution (I am already running the restricted drivers) so that I could try messing around to get a resolution where I could see everything.  I really want to start migrating to linux (my laptop is already about 75% set up how I like it and I would really like my media center to be a linux box as well

Any help would be greatly appreciated, and please speak slowly as I am a **complete** newbie.

thanks

---

### Post by jken146 on 2008-04-21
If you don't have the options you need in Screen Resolution in the System menu, do this:

Press Ctrl+Alt+F1.  You'll get a black terminal screen.  Log in.

Type ```
sudo /etc/init.d/gdm stop
```
then ```
sudo dpkg-reconfigure xserver-xorg
```and go through the wizard.  Screen resolutions are near the end.  Then type ```
sudo /etc/init.d/gdm start
```
You may need to press Ctrl+Alt+F7 to get back to the graphical log in screen.

---

### Post by YawnXen on 2008-04-22
> **jken146 said:**
> If you don't have the options you need in Screen Resolution in the System menu, do this:

Press Ctrl+Alt+F1.  You'll get a black terminal screen.  Log in.

Type ```
sudo /etc/init.d/gdm stop
```
then ```
sudo dpkg-reconfigure xserver-xorg
```and go through the wizard.  Screen resolutions are near the end.  Then type ```
sudo /etc/init.d/gdm start
```
You may need to press Ctrl+Alt+F7 to get back to the graphical log in screen.

thank you thank you thank you
I was trying a new install and the menu bar was taking up the top third of my screen. 
Ctrl+Alt+F1  then  Ctrl+Alt+F7 
fixed the resolution
Yawn Xen

---

### Post by jackflap on 2008-04-22
jken146, I don't think that works in Hardy any more.

I was trying 'sudo dpkg-reconfigure xserver-xorg' out on my laptop the other day, and the resolutions section doesn't come up at the end any more.

I think it has something to do with switching over to randr. Check it out.

---

