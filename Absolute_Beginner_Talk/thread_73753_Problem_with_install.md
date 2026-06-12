---
title: "Problem with install"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by nowinvisibly on 2005-10-09
I'm trying to install Breezy Badger on my PC.  Ideally, I'm trying to do a dual boot of Ubuntu and Win2KPro.  I have a 40 GB drive with approximately ~28 GB of free space.  Plenty of room for a partition (all my "main" computing is done on my Mac) to do a dual boot.

My problem:  I cannot get past the initial screen of "type expert (or whatever it says exactly) for advanced setup or press ENTER for regular install"...

...and I cannot type ANYTHING.  I hit enter, and nothing.  I try to type ANYTHING...nothing.  The cursor just blinks at me.

I run with a KVM switch to go from the Mac to the PC (sharing a monitor, keyboard and mouse).  Thinking that may have been the issue, I unplugged the USB keyboard from the KVM switch and plugged it directly into the PC.  I know it works up to a point, because I can hit "DEL" to go to setup and "F8" to go to the regular boot menu (which I do have set up to boot from CD first, then hard drive) upon startup.  I tried this with two separate burned discs (one burned on my Mac, the other on the PC) of two separately downloaded .iso files.  

Still nothing. 

Thinking that perhaps, I had an AMD processor that needed the special install (which I highly doubted, since it's only a 1GHz AMD TNT2 from 2002), I tried the special AMD 64 bit install version.  

Same problem.  When I go to press "enter' to proceed, nothing.  

Any ideas?  Do I need to create a new partition BEFORE I do the install?  If so, how do I do it?  I've been working on this ALL WEEKEND.  :confused: 

I'm not a computer "newbie", just a Linux newbie.  

Any and all help is greatly appreciated!  :)

---

### Post by erikpiper on 2005-10-09
That is really weird...

Do you happen to have a ps2 keyboard anywhere? (Could be the USB)
If that is the case, that is a big bug that needs to be fixed.

Install CD's are very sensitive- something could of burned wrong. Try reburning the cd at a slow speed. I have had to do that before, but I normally get a lot farther.


Good luck dude!

EDIT: Do not use the AMD64- It won't work on anything but 64bit processors.

---

### Post by wylfing on 2005-10-10
Finding a PS/2 keyboard (or using an adapter) is probably a good answer to get you up and running. 

Another option is when you see the prompt, unplug the keyboard and plug it back in again. Something might have polled the bus and switched your keyboard off. Unplugging it and plugging it back in might get it re-detected.

Also, be sure your BIOS is set up for full USB mouse and keyboard support. Many BIOSes have an option specifically for USB keyboard, and yours might be turned off. This is different than USB keyboard support at POST time, so I'd recommend checking it.

---

### Post by nowinvisibly on 2005-10-10
[QUOTE=wylfing]Finding a PS/2 keyboard (or using an adapter) is probably a good answer to get you up and running. 

Another option is when you see the prompt, unplug the keyboard and plug it back in again. Something might have polled the bus and switched your keyboard off. Unplugging it and plugging it back in might get it re-detected.

Also, be sure your BIOS is set up for full USB mouse and keyboard support. Many BIOSes have an option specifically for USB keyboard, and yours might be turned off. This is different than USB keyboard support at POST time, so I'd recommend checking it.[/QUOTE]

I think I have my old PS/2 keyboard lurking in a closet somewhere.  I will most definitely try that when I get home from work.

Question though, how do I change the BIOS for USB support?  Is that in the regular "setup" screen (on my machine, I hit the delete key on boot up for that option)?  

I'll also try the "slow burn" option (although I did both at about 8x on a 52x max burner) too.  

Thanks for the help!

---

### Post by wylfing on 2005-10-10
[QUOTE=nowinvisibly]
Question though, how do I change the BIOS for USB support?  Is that in the regular "setup" screen (on my machine, I hit the delete key on boot up for that option)?[/QUOTE]

Yep, hit DEL when your computer is starting up. I can't tell you where in the BIOS your settings are, because they're different. Many times it's something called "USB Keyboard Legacy Support" or something similar. If you can't find anything like that, there might not be a setting for it in your BIOS. It's just something to look for, that's all.

Good luck.

---

