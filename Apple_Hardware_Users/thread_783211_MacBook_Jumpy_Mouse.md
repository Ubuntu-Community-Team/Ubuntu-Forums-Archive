---
title: "MacBook Jumpy Mouse"
date: 2008-05-05
forum: Apple Hardware Users
---

### Post by mattgaunt on 2008-05-05
Hey everyone,

I just installed hardy heron on my laptop, main problem im having with it is the mouse is very jump/erractic/sometimes feels likes its following a grid and not moving smoothly.

Has anyone else found this or is it just me? I hav one of the new macbooks, (5th gen I think its referred to :-S but got it this easter)

Any help would be great

Gaunt

p.s. only just realised there was an apple section - Happy Times :-)

---

### Post by cyberdork33 on 2008-05-05
you should have a Macbook4,1

Have you read though this:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by mattgaunt on 2008-05-05
yeah that was the one i looked at and i used that to set up the track pad as mentioned in that how to

---

### Post by cyberdork33 on 2008-05-05
> **mattgaunt said:**
> yeah that was the one i looked at and i used that to set up the track pad as mentioned in that how to
Did you get that kind of behavior before you changed the config? There may be an option listed that is not needed anymore.

---

### Post by mattgaunt on 2008-05-05
yeah it was pretty much the same during the live CD

---

### Post by cyberdork33 on 2008-05-05
backup your config file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
then run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then restart xorg. if you get the same issue, then I don't know what else the issue might be.

---

### Post by mattgaunt on 2008-05-08
cheers for the help, ill give it a go and let you know the results


Gaunt

---

### Post by mattgaunt on 2008-05-24
Yeah I got round to doing this last night (Been busy with coursework and exams) Still get a weird sense of the mouse following a bit of a grid rather than following. Its usable either way, jus not as nice as it is in OS X.


Thanks for the help though

Gaunt

---

### Post by barnex on 2008-05-24
I have a somewhat similar problem with my mouse. It's also 'jumpy', in the sense that it freezes for about a second every time I've pressed a key. My trackpad is not affected, only the mouse. I did not have this problem prior to 8.04.

Does anybody have similar problems? Hope we can help each other out.

---

### Post by Brightbelt on 2008-05-24
Hi, 
I've had this problem in the past with PC laptops and I found one post just now (not enough info worth copying) where this was suggested to do on a macbook: 

You could try installing Gsynaptics (Install it through the Synaptic Package Manager)...

Gsynaptics will enable you to either 1) Disable the trackpad and leave it that way; this will most likely "Cure" the jumpy mouse for sure, or 2) Disable the trackpad and re-enable it, which the one post I read suggested *might* work. 

There's a snippet of code that you might have to put into a Gsynaptics file after installing it to "activate" the program; you would do this through the terminal...
this might guide you... [http://ubuntuforums.org/showthread.php?t=271052&highlight=Gsynaptics](http://ubuntuforums.org/showthread.php?t=271052&highlight=Gsynaptics)

I hope this helps,...I'm less familiar with this being done on macs, but it might be possible, (What do you think Cyber?)...Frank B.

---

### Post by cyberdork33 on 2008-05-24
> **Brightbelt said:**
> I hope this helps,...I'm less familiar with this being done on macs, but it might be possible, (What do you think Cyber?)...Frank B.That should work. I tend to edit things manually in xorg.conf though.

---

### Post by mattgaunt on 2008-05-24
Well when I have plenty of free time Ill give them go or maybe just play around with the xorg file and see if I can fix anything.

Thanks for the help guys

---

