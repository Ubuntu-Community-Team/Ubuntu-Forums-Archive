---
title: "The problems continue!"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by establishment on 2007-07-06
I installed Wubi earlier today, because I was having some major problems running it off the CD, and i'm not ready to wipe out my entire harddrive yet.
 I'm using a Dell Latitude C800 Laptop, with an Intel III processor.

 When I boot up, And have the choice to load Windows 2k or Ubuntu, Obviously I select ubuntu, and it loads.
 When it comes up, Theres a fuzzy spot in about the middle of the screen, and The right side of the screen is a mirror of the left.

 Diagram:
[IMG]http://img389.imageshack.us/img389/2461/dia1ib3.png[/IMG]



Yellow section diagram/closeup:
[IMG]http://img528.imageshack.us/img528/7929/dia2dv4.png[/IMG]

The Fuzzy line basically screws up everything in its path. It goes across the whole screen.

Blue #2 section diagram/closeup
[IMG]http://img528.imageshack.us/img528/5451/dia3ne7.png[/IMG]

EVERYTHING is oversized, so At the moment i'm thinking it MIGHT be a resolution problem.
The REAL problem is that I can't login to Ubuntu because the screen is so messed up. :(
 I've been wondering if I change the resolution on Windows 2k, will it effect Ubuntu And Possibly fix it?

I'm **VERY** determined to get Ubuntu working on my laptop, so If you have ANY ideas at all, I'll gladly try them. :(

 Thanks in Advance! ;)

---

### Post by establishment on 2007-07-06
Tried Rebooting, No luck. :(

---

### Post by pbaumgar on 2007-07-06
Why not try installing off a Ubuntu CD... it won't wipe your Windows partition unless you tell it to do so.  I'm not familiar with Wubi... but I'd try just the normal install.

---

### Post by kvonb on 2007-07-06
More information required:

1. Which version of Ubuntu are you using?
2. Is the screen "perfect" under Windows?
3. What video adapter is in the Laptop?
4. Which driver are you using in Ubuntu?

---

### Post by establishment on 2007-07-06
Version 7.04.

I suppose its perfect in windows, For me, I guess.

I'm not sure, Is there any way to find out which video card?

Driver as in C:?
  If Yes, Its on the C:. 
  (I'm new to Linux and Ubuntu, Sorry if I seem like an idiot)

---

### Post by establishment on 2007-07-06
See, When I was running it off the disk it did the same thing, So I'm not really sure what'll happen when I try to boot it off the disk and can't log in because the screen is messed up.

---

### Post by pbaumgar on 2007-07-06
> **establishment said:**
> See, When I was running it off the disk it did the same thing, So I'm not really sure what'll happen when I try to boot it off the disk and can't log in because the screen is messed up.

So you booted off a Ubutnu CD and you had the same result?  I'm not sure what you mean by booting off the disk and woudn't be able to login.... did you already install linux on the drive?

---

### Post by establishment on 2007-07-06
When You insert the Ubuntu Disk when the computer is starting up, The ubuntu logo comes up and theres a range of options to choose from. One of them is to run Ubuntu Off the disk without it changing or installing anything on your computer.. It switches back from the CD to memory for it to run as far as I know. 
 So while it was running off the disk, I had the same problem with the fuzz line and mirror on the right side.

---

### Post by Raineer on 2007-07-06
It's a display driver issue, not really a resolution issue.  You can boot just fine in text mode to edit xorg.conf.  Press Ctrl-Alt-F2 after it comes up (even during the horrible graphics/crash) and login with user/pass, then:
```
sudo /etc/init.d/gdm stop
``` this shuts down X
```
sudo dpkg-reconfigure xserver-xorg
``` 
Run through the program and select the "vesa" driver, as it's the bottom-of-the-line-most-compatible-with-anything-driver.  If you know what brand of display chipset the laptop uses that could help.

---

### Post by establishment on 2007-07-06
Thank you very much!
Right now I have another problem, Wubi won't start up automatically when my laptop is turning on, it goes directly to Win. 2k..

  Ah, I'll figure it out. :P

---

