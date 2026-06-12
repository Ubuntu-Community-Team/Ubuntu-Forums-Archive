---
title: "Should I upgrade to Feisty?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by tm0054 on 2007-03-30
A question to you Feisty users out there....

I have a problem w/Ubuntu 6.10 on my laptop. I can't get any programs to run in full-screen mode. Whether they are set to full-screen or windowed mode all programs show up in a small window. I have an Intel graphics card running 915resolution (in 1200x800).

The question is:

Is there a possibility that upgrading to Feisty will resolve this problem? Does it come with more advanced video drivers? Does Feisty support laptop wide screen resolutions out of the box (Intel Video cards specifically) or will it still require 915Resolution (which I think could be part of my issue)?

I want to decide whether it is worth it before taking the 2 or so hours it will require to download and install (plus configuration and all that stuff). I don't want to wind up with a project that could potentially eat my whole weekend.

---

### Post by aysiu on 2007-03-30
It's possible Feisty could offer better support. I upgraded to Feisty and suspend all of a sudden (without extra tweaking) started working on my Dell Inspiron 500m.

**But** you should keep in mind that it's still beta software, so there's potential that something else could break. You also don't know if Feisty *will* fix your problem, only that it *might* fix your problem.

It's your call.

---

### Post by ubukool on 2007-03-30
I'm not a Feisty user, I use 6.10 which is great.  I plan to ugrade sooner or later but there's a danger of being caught up in Feisty Fever.  It hasn't been released yet (actual release will be 19 April) and it's still beta, so it's risky.

If you want to change your resolution, you could always edit the dreaded xorg.conf file (#-o) and you can find instructions on how to do this on this forum, but beware, the last time I tried to introduce other screen resolutions by editing this file it completely screwed my system so that I couldn't even read the screen anymore and I had to do a complete reinstall.  I'm happily accepting that my Edgy works, regardless of the screen resolution! :) 

In either case, good luck!

---

### Post by ubukool on 2007-03-30
Here's a guide if you're feeling brave:

[http://ubuntuforums.org/archive/index.php/t-83973.html](http://ubuntuforums.org/archive/index.php/t-83973.html)

---

### Post by tm0054 on 2007-03-30
I actually had to download a program out of the repository called '915resolution' to make Ubuntu display in my laptop's native resolution (1200x800) - before that I tried editing the 'xorg.conf' file to no avail. Nothing I did would make 1200x800 an option until I D/Led 915resolution. Initially I couldn't get anything except for 1024x768 even with 1200x800 entries in the xonf.org file.

Now it displays in 1200x800 very nicely, but like I said it doesn't seem to support full screen resolutions. Everything remains in a little Window even when set to full screen. I have a desktop computer with Ubuntu installed on it at 1280x1024 and full screen works perfectly on it so it must have something to do with my Laptop configuration.

---

### Post by aysiu on 2007-03-30
What model is your laptop?

---

### Post by lamalex on 2007-03-30
Thats strange, ubuntu picked up my 1200x800 resolution on install. I'm on an HP laptop. Never had a single problem with 1200x800, except in feisty when I installed the fglrx drivers, but all I had to do was edit xorg.conf.

---

### Post by aysiu on 2007-03-30
It's not really strange at all--hardware detection depends greatly on the laptop model.

More info can be found here:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

---

### Post by tm0054 on 2007-03-30
I have an Acer AS5610-4537. It's a core duo with 'Intel® Graphics Media Accelerator 950' for graphics. I'm dual-booting with Vista.

---

### Post by tm0054 on 2007-03-30
Iamalex, I think it depends on what graphics card your computer comes with. 915resolution I believe is specifically for laptops running Intel graphics cards.

---

