---
title: "Right click"
date: 2010-04-26
forum: Apple Hardware Users
---

### Post by limestone on 2010-04-26
Hi all Ubuntu lovers.. I have thought of getting a macbook pro and I know that Ubuntu 10.04 got drivers for all macbook parts with some fixes, but i want to know how to use right-click.. Any ideas/fixes?

---

### Post by HikaKao on 2010-04-26
> **pont.andersson said:**
> Hi all Ubuntu lovers.. I have thought of getting a macbook pro and I know that Ubuntu 10.04 got drivers for all macbook parts with some fixes, but i want to know how to use right-click.. Any ideas/fixes?

As far as I remember, it was just as on OS X, clicking with two fingers = right click. I dunno though, been a while since I've used Ubuntu. :p

---

### Post by sean.d on 2010-04-26
Your F12 key should also function as a right click.

---

### Post by zeroti on 2010-04-26
If you want to right click when you hold down the apple command button, install mouseemu and put this in your /etc/default/mouseemu file:

RIGHT_CLICK="-right 125 272"      # Left Apple Key (LEFTMETA) + click

---

### Post by kosumi68 on 2010-04-26
Beware that mouseemu has a history of creating odd, hard-to-find problems in conjunction with other input devices:
[https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/251830](https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/251830)

---

### Post by xxander on 2010-04-26
Download "poshed" from the software center.. I think that's what it is... I kinda forget though!! I'll remember it and post it later if that's not right.. But yeah, then go to your mouse settings in System.

---

### Post by xxander on 2010-04-26
Oh sorry for the double post... it's called pommed, but it is actually just for backlight and stuff (but still get it)... let's see, for right-clicking, it depends what you want.  If you want two-finger right click, enable that in the System - Mouse thing.  

Sorry.. I know that wasn't much help.

---

### Post by amd-64 on 2010-04-27
Hmmm. Right click? Do you have a wheel mouse. It should work out of the box. All buttons work on these mice. 

Even on the magic mouse, the multitouch device, it would work if you click with two fingers. Now middle click is a different story.

---

### Post by limestone on 2010-04-27
Ok, thanks guys.. It seems that theres some options to chose from. Now I'm ready to get a mac:)

---

### Post by mire on 2010-04-27
In 9.10 and 9.04 the default configuration uses a three finger right click with two fingers meaning middle click. See [https://help.ubuntu.com/community/MacBookPro1-1_1-2/Jaunty](https://help.ubuntu.com/community/MacBookPro1-1_1-2/Jaunty) for instructions on changing this. Also on my machine mouse emu interferes with the caps lock key preventing the led from coming on.

---

### Post by zeroti on 2010-04-28
I just discovered that mouseemu interferes with F11 on my powerbook...

So is there some way to set-up some sort of right click emulation with the command key? I can't use two-finger click since I have an ADB trackpad.

---

### Post by linuxopjemac on 2010-04-28
[http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=67&p=93&hilit=mouseemu#p93](http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=67&p=93&hilit=mouseemu#p93)

---

### Post by Gervs on 2010-05-03
Just click with two fingers on the trackpad. Works for me on MacBook, Ubuntu 10.04.

---

### Post by rabidcentipede on 2010-05-03
is there any way to get it configured where you can click in the bottom-right corner of the touchpad? I particularly like this feature on OS X, as it feels more like a natural mouse to me.
 
Any ideas?

---

