---
title: "Intel Mac Mini and non working widescreen"
date: 2007-06-05
forum: Apple Intel Users
---

### Post by weezel on 2007-06-05
Hi!

I bought Intel Mac Mini (Intel core duo 1.83GHz, superdrive, 512M -version).
This uses Intel Chipset 945GM for graphics.
After installing Kubuntu Feisty 7.04 it works like a charm but widescreen resolution didn't seem to identify correctly. I had a working Kubuntu system with my old Radeon 9500 Pro and ViewSonic(VX2025wm). Radeon seemed to work without any bios hack, thank god.

So far I've done these kind of combinations:
> 
aptitude install 915-resolution (didn't work, xorg.conf drivers tested: intel, i810, vesa)
aptitude install xserver-xorg-intel (doesn't seem to get memory loaded correctly, or get's out of range)
 

and just to mention: 915resolution -l  doesn't detect any 1680x1050 resolution, nor any other widescreen modes.

Here's my configs: 
[ATTACH]34421[/ATTACH]
[ATTACH]34422[/ATTACH]
[ATTACH]34426[/ATTACH]

---

### Post by ronocdh on 2007-06-06
> **weezel said:**
> Hi!

I bought Intel Mac Mini (Intel core duo 1.83GHz, superdrive, 512M -version).
This uses Intel Chipset 945GM for graphics.
After installing Kubuntu Feisty 7.04 it works like a charm but widescreen resolution didn't seem to identify correctly. I had a working Kubuntu system with my old Radeon 9500 Pro and ViewSonic(VX2025wm). Radeon seemed to work without any bios hack, thank god.

So far I've done these kind of combinations:
 

and just to mention: 915resolution -l  doesn't detect any 1680x1050 resolution, nor any other widescreen modes.

Here's my configs: 
[ATTACH]34421[/ATTACH]
[ATTACH]34422[/ATTACH]
[ATTACH]34426[/ATTACH]
Have you seen [this post]("http://ubuntuforums.org/showthread.php?t=415070")? It seems to address the problem you're having, and you didn't mention this post specifically. The author mentions the same steps as you, but seems to have worked through it. Good luck!

---

### Post by weezel on 2007-06-09
> **ronocdh said:**
> Have you seen [this post]("http://ubuntuforums.org/showthread.php?t=415070")? It seems to address the problem you're having, and you didn't mention this post specifically. The author mentions the same steps as you, but seems to have worked through it. Good luck!

Actually that your mentioned tip resolved something: I can have 1680x1050 resolution on kdm-login screen, but after login it get's out of range. Quite weird..

Here's the new xorg.log:
[ATTACH]34827[/ATTACH]

---

### Post by ronocdh on 2007-06-09
> **weezel said:**
> Actually that your mentioned tip resolved something: I can have 1680x1050 resolution on kdm-login screen, but after login it get's out of range. Quite weird..

Here's the new xorg.log:
[ATTACH]34827[/ATTACH]
Perhaps if you run the following command, you'll be able to add the resolution you want manually, after which point it should show up in your Screen Resolution panel:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by weezel on 2007-06-10
> **ronocdh said:**
> Perhaps if you run the following command, you'll be able to add the resolution you want manually, after which point it should show up in your Screen Resolution panel:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I already had only 1680 x 1050 resolution in my xorg.conf. What I did compared on last situation were: 1) remove VideoRam option from xorg.conf 2) remove Option ignoreEDID 3) remove refresh rate -lines 4) remove Modeline "1680x1050@60.00 and Option Preferred mode -lines 5) tried without defaultDepth option

After this I got the right resolution, but still it get's out of range after login.

---

### Post by weezel on 2007-06-10
Uuh, I got it work finally! I removed .kde* directories from my home because I thought it might be KDE related automation problem. It seemed to do the trick. Thanks for the help ronocdh.

Now I can get rid of OS X finally.

---

### Post by LieToPurify3 on 2007-06-10
I don't really know what you did to get it to work.  weezel, can you just tell me the steps you did that worked for you?

---

### Post by weezel on 2007-06-10
> **LieToPurify3 said:**
> I don't really know what you did to get it to work.  weezel, can you just tell me the steps you did that worked for you?

At the very first I stabbed my xorg.conf to look like this: 
[ATTACH]34908[/ATTACH]

Then, I installed 915resolution with this command: aptitude install 915resolution
After that I did the following: sudo 915resolution -l    which didn't seem to find out widescreen modes correctly. Here's the thing I didn't know: you may set your own resolution for example this way: sudo 915resolution 5c 1680 1050
After that I went back to kdm-login screen and pressed ALT + CTRL + BACKSPACE. It's same than pkill -HUP kdm  , or choosing option 'Restart Xserver' from drop down box shown on the kdm-login screen. Then it worked, but it went out of sync after I had typed my password and pressed return. Back to the console and: rm -rf ~/.kde*  . (This removes your KDE configurations).
Since those tricks I'm able to use 1680x1050 and 3D accelerated Kubuntu.

---

### Post by LieToPurify3 on 2007-06-12
What do you mean by "stabbed my xorg.conf"?  What exactly do I have to do there?

---

### Post by weezel on 2007-06-12
> **LieToPurify3 said:**
> What do you mean by "stabbed my xorg.conf"?  What exactly do I have to do there?

Change the Resolution, Hsync and Vsync lines pointing to your screen specifications.

---

### Post by LieToPurify3 on 2007-06-12
it wont let me edit my xorg.conf.  When I go to overwrite it or delete it and replace it with my edited version, it won't let me.

---

### Post by weezel on 2007-06-12
> **LieToPurify3 said:**
> it wont let me edit my xorg.conf.  When I go to overwrite it or delete it and replace it with my edited version, it won't let me.

sudo nano /etc/X11/xorg.conf

---

### Post by LieToPurify3 on 2007-06-12
when I type that into the console, it just shows me a blank screen.  Do i have to type in the entire document?  Cant I just view what is already there and then edit and change what I want?

---

### Post by weezel on 2007-06-12
> **LieToPurify3 said:**
> when I type that into the console, it just shows me a blank screen.  Do i have to type in the entire document?  Cant I just view what is already there and then edit and change what I want?

Yep, that's correct. You may edit already existing file. Just change needed lines.
Paste your /var/log/Xorg.0.log if you cannot get it work.

---

### Post by LieToPurify3 on 2007-06-12
I just edited it in the terminal by copying and pasting my xorg.conf file.  How do I save it?  I tried exiting and when it asks me if I want to save, I hit yes and tell it /etc/x11/xorg.conf, but when I hit enter, it tells me there is no such location!

---

### Post by chandru.in on 2007-09-28
Removing the .kde directory solved the problem because, Kubuntu enables session restoration in KDE by default.  This stores the previous resolution also.  Hence, all you need to do is disable sessions in System Settings or execute this command,
```
rm -rf ~/.kde/share/config/session
```

But the lack of automatic recognition of wide screen monitors is a big drawback.  Which new user would have the patience to try these things??

:)

---

### Post by zavizionov on 2007-10-06
For a long time searching I have found a solution. I have described in the my HOWTO [http://zavizionov.blogspot.com/2007/09/howto-ubuntu-intel-945-widescreen.html](http://zavizionov.blogspot.com/2007/09/howto-ubuntu-intel-945-widescreen.html)

---

### Post by cyberdork33 on 2007-10-08
> **LieToPurify3 said:**
> I just edited it in the terminal by copying and pasting my xorg.conf file.  How do I save it?  I tried exiting and when it asks me if I want to save, I hit yes and tell it /etc/x11/xorg.conf, but when I hit enter, it tells me there is no such location!
It is /etc/X11/xorg.conf not /etc/x11/xorg.conf Welcome to case-sensitive.

---

### Post by shawnansasio on 2008-04-03
I had the same problem. You just need to type sudo dexconf or sudo system-config-display. 
that alyways works for me   :lolflag:  :D

---

