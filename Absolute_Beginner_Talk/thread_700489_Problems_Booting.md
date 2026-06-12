---
title: "Problems Booting"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by beejnnoz04 on 2008-02-18
I downloaded Ubuntu desktop edition 7.10 and burnt it to a blank cd as an ISO image. I did the mdsum check previous to that, and all the hashes check out. When I boot from the cd, and click start or install, I encounter problems. It has been sitting on a blank tan screen for about 3 hours now. I have control of the mouse, but nothing else has loaded.  I know that on the Graphical Install info page ([https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) ) says that booting may take awhile, but is this amount of time normal for the booting process?

---

### Post by smartboyathome on 2008-02-18
This shouldn't be happening. What graphics card do you have?

---

### Post by Linux_Man on 2008-02-18
Try CTRL+ALT+Backspace, this will kill X and then try again. What are your specs for the machine you are trying to install Ubuntu on? RAM and CPU speed and graphics card would be helpful.

---

### Post by OffAxis on 2008-02-18
booting should only take a minute or two...
At 3 hours it's hanging on something.

Did you run the 'Check CD for Defects' scan?

---

### Post by beejnnoz04 on 2008-02-18
Sorry I posted this right before I left for class. I didn't expect so many responses so quickly -thanks guys!- I will post the specs of my computer when I get back. I'm not entirely positive on them at the moment and don't want to give incorrect information.

---

### Post by beejnnoz04 on 2008-02-18
Okay here are the specs of the computer:

It is an older Dell Desktop
Graphics Card: Intel(R)82845G/GL/GE/PE/GV Graphics Controller
Processor: Intel (R) Celeron (R) CPU 2.20GHz
RAM: 256 MB

I just ran the CD error test, and it found some errors, so I am re-burning the image at a slower rate.  Hopefully that was the only problem. We'll see if it works out.

---

### Post by beejnnoz04 on 2008-02-18
Alright I made a new CD. When I ran the CD defect check it claimed there were no errors at the end of the check. However at the very beginning my attempt to 'start/install Ubuntu' i get these messages

[241.409010]  Buffer I/0 error on device fd0, logical block 0
[279.434448]  Buffer I/0 error on device fd0, logical block 0

And with the CD that is apparently defect free, I'm still getting that blank tan screen.  Anyone got any ideas?

---

### Post by OffAxis on 2008-02-18
Do you have a flash drive connected?
That'll usually pooch an install.

---

### Post by beejnnoz04 on 2008-02-18
> **OffAxis said:**
> Do you have a flash drive connected?
That'll usually pooch an install.

No flash drive, but my printer was plugged in. Is it any USB device that can mess things up?

---

### Post by OffAxis on 2008-02-18
Usually it's just USB flash drives.

fd0 is usually a floppy drive. Anything like that? (Floppy, Zip, Jazz, etc)

---

### Post by beejnnoz04 on 2008-02-18
> **Linux_Man said:**
> Try CTRL+ALT+Backspace, this will kill X and then try again. What are your specs for the machine you are trying to install Ubuntu on? RAM and CPU speed and graphics card would be helpful.

I tried this, and it took me to a login screen. Since I had no username or password, I let it log me in as user: Ubuntu which seems to be the default. It then took me straight back to the blank tan screen I am continually on.

---

### Post by beejnnoz04 on 2008-02-18
> **OffAxis said:**
> Usually it's just USB flash drives.

fd0 is usually a floppy drive. Anything like that? (Floppy, Zip, Jazz, etc)

I installed an ancient floppy drive on this computer a few years back so I could attempt to get some old games from my youth onto it. There is no floppy disk in the drive, but the drive is connected. I don't think it is functioning however, it hasn't displayed an icon in 'My Computer' for a year or so.

---

### Post by Sinkingships7 on 2008-02-18
256 MB isn't really enough ram to install ubuntu. you may want to think about xubuntu. it's lightweight. even still, you'll have to use the text-based alternative installer. you could use the text-based alternative installer for ubuntu as well, but there's no speed guarantees there.

---

### Post by OffAxis on 2008-02-19
> 256 MB isn't really enough ram to install ubuntu
sure it is. 
192 MB is recommended for desktop effects (in Feisty), so 256 should be able to handle a basic install just fine (certainly the installation process).
[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

---

### Post by OffAxis on 2008-02-19
> I don't think it is functioning however, it hasn't displayed an icon in 'My Computer' for a year or so.
If you haven't already done so, pull the power or data cable on that drive and try again.

Generally speaking, Linux can be more particular than a windows system, and a problematic piece of hardware that windows overlooks (perhaps "can't figure out" is a more apt way of putting it) linux will point to with a "that's broken and you need to fix it" by hanging or erroring out.

---

