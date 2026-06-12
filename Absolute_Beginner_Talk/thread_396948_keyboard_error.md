---
title: "keyboard error"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Warpnow on 2007-03-30
Okay, I'm going to explain my situation in detail in hopes that someone knows what's wrong.

My specs:
ECS 661FC-M moterboard
Intel Pentium 4 3ghz processor w/Ht

I've ran windows since I got my computer. At that time it came with a ps/2 mouse and keyboard which worked fine. I have, however, since switched to a microsoft comfort wireless usb keyboard and have also reformatted half a dozen times or so.

Now, I want to install ubuntu. Ubuntu gets to the install page I use my keyboard (WHICH WORKS AT THIS STEP) and select the run or install ubuntu option.

Once ubuntu gets to the main screen (with my usb wireless keyboard) nothing works! No mouse, no keyboard, nothing. The lights on the reciever will light up for half a second if I reset it, but won't stay on.

So, I try it with my ps/2 keyboard and mouse I have. Bios error "No keyboard detected" and it won't even load the install disc. 

I have, however, been able to get my external usb mouse that I use with my laptop to work. However, I don't have a usb nonwireless keyboard to test it with.

Is it possible my bio has defaulted me to a usb keyboard and turned off my ps/2 ports. If so, any idea how I'd turn them back on?

---

### Post by Warpnow on 2007-03-30
I reset my bios settings to "fail safe" and now nothing works. I'll get out tomorrow and buy a nonwireless usb keyboard and see if it works.

---

### Post by tjcannon on 2007-03-30
Try looking in your BIOS for something like "Enable legacy USB keyboard" or something like that is where I would start.

I hate to do this, but I have no idea your level of knowledge so I'll do it and sound mean if I must...

Beware: Changing ANYTHING in your BIOS can lead to your computer not working anymore.  Only change something if you are absolutely sure about it.

When your computer first powers on, press the delete key repeatedly until you see a bios menu (if it gets to a point where it's trying to load an OS, it's gone too far.)  I don't know your motherboard, so if this doesn't work, watch the screen and see if it tells you what to press.  Sometimes it's F2 or F10 instead of delete.

Now see if you can find something about a legacy usb keyboard or type of keyboard set as usb instead of ps2 or anything like that.

Good luck.

---

### Post by tjcannon on 2007-03-30
> **Warpnow said:**
> I reset my bios settings to "fail safe" and now nothing works. I'll get out tomorrow and buy a nonwireless usb keyboard and see if it works.
Well, my intentions were good.  Sorry for dumbing it down (since obviously you knew how to change your BIOS).  Good luck getting everything working!

---

### Post by Warpnow on 2007-03-30
well, i bought a USB keyboard and it didn't work either.

Any advice?

---

### Post by Warpnow on 2007-03-30
well, I removed the motherboard battery for about an hour and now can get usb keyboards and mouses to work, but the ps/2 ports are still nonfunctional.

I guess I better go buy a hub, haha, I only have 2 usb ports that function and they're both in use now.

---

### Post by Warpnow on 2007-03-30
haha, well, I thought briefly that it was fixed. It now detects the usb mouse and keyboard but they won't work once the live version of linux is booted. I enabled usb legacy in the bios...I did everything I can think of. The keyboard works in boot for selecting things, works in bios, but the lights and everything won't even work once ubuntu is booted. Its like its not getting power.

Any idea why?

Gah, I might just have to stick with windows.

---

### Post by Warpnow on 2007-03-30
I've got it working now. Thank you to the people who helped me.

---

### Post by robhick on 2007-04-01
Hi Warpnow - any clues as to how you got it working?  I have pretty much exactly the same problems as you using an ECS RS482-M motherboard.  My (wireless) usb keyboard and mouse won't work once Ubuntu gets to the login screen but they work fine before then.  IS there a setting I need to change (all USB bios settings are already enabled).

Rob

---

### Post by Warpnow on 2007-04-02
I bought a non-wireless keyboard and mouse and mine worked. I couldn't figure anything else out and it seemed to work.

---

