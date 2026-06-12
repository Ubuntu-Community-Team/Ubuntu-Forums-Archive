---
title: "Cant boot 64bit CD because of video probs"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by TimJBart on 2006-07-28
Hi,

I am dabbling with ubuntu and I tried to get it running on my 64bit machine. I was hoping the graphics drivers would work straight off, but to my disappointment when booting an error came up saying it couldn't load because 

"X Server was probably not set up properly"

Where do I go from here to get it loading?  Surely I can't set up the Xserver if I am booting off the CD!

I have tried booting in 'video safe mode' and it boots ubuntu and I hear the log in sound but the screen is blank.

I have an ATI Radeon x800

Any help would be greatly appreciated! :(

---

### Post by TimJBart on 2006-07-28
no ubuntu64 for me then :(

---

### Post by Frawg on 2006-08-02
Hi ubuntu forums, 
I'm having the same problem as Tim. I can reconfigure my xorg to use vesa drivers, but then I can only use my onboard video. I've tried installing the newest set of drivers, but when i use the method outlined in these forums, it says "architecture not supported". When i just use the official installer (the graphical one), it doesn't solve anything.

I have a Visiontek radeon x800. I would really appreciate it if someone could give me a word of advice, I am really digging ubuntu but i might have to switch back to windows if this can't come through.

-edit-
nevermind, i got the fix from eoin
>  Originally Posted by Phasmagon
it is really rather easier than that.

In a terminal type

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

---

### Post by Frawg on 2006-08-03
tim, are you not able to get into any command line at all?

---

### Post by TimJBart on 2006-08-03
no I do get a command line but because I simple I don't know what to do when I am there!  

I am giving up on getting it running on my 64bit machine.  Instead, I am using ubuntu on a spare pc I had hidden in the garage and it's working great so I'll get to know ubuntu this way.

Maybe when I've got a bit more disk space I'll try ubuntu64 again on my main pc

---

### Post by TimJBart on 2006-08-03
no I do get a command line but because I simple I don't know what to do when I am there!  

I am giving up on getting it running on my 64bit machine.  Instead, I am using ubuntu on a spare pc I had hidden in the garage and it's working great so I'll get to know ubuntu this way.

Maybe when I've got a bit more disk space I'll try ubuntu64 again on my main pc

---

