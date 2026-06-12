---
title: "Video Driver help"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by yetanotherproblem on 2007-11-27
After a slew of problems, I finally got Ubuntu installed on my slave drive (hdb).  I booted up, watched the bar load under the ubuntu logo, and then the screen went black.  My monitor flashed "No Signal", and then nothing.  I could hear Ubuntu loading in the background, and when i typed my username and pass, it logged me in...I just couldn't see anything.

I read in another post to try these commands after I booted in recovery mode:

aptitude update
aptitude install xorg-driver-fglrx
aticonfig --initial

The problem is when I typed the second line it said it couldn't resolve some web address.  it then asked me for the install cd and proceeded to do something...i'm not sure what.

I expect problems when I install Linux, but this baffles even me.  If I'm coming off sarcastic, I don't mean to.  Frustrated and exhausted would be more like it.

Any help would be great.

I have a AMD Athalon 64 3000+ processor, and an ATI x1300 PCI-E video card.

Again, any help would be awesome.  Thanks!

---

### Post by siciliancasanova on 2007-11-27
Ok, so you're getting "no signal" but you are able to see commands and the output of those commands on the monitor?

---

### Post by yetanotherproblem on 2007-11-27
If I boot in recovery mode, I can see all the things it loads.  It's only when I do a normal boot that the screen says "No Signal" and then goes black.  Like I said, I can type the username and pass and hear the sounds when I'm logging in, but I can't see anything.

Someone said ATI didn't release foos drivers or something, but openSUSE ran fine on this machine, so it has to be an issue with Ubuntu.

Any ideas?

Also, I had to use the alternate CD because the graphical install wouldn't load.  Same problem...no signal, then black screen.  The alternate CD worked fine to install, but when I tried to boot normally, it goes black.  Recovery shows me all the things it's doing, so I'm assuming it's a glitch with ubuntu's GUI and ATI, or a glitch with xorg.

You guys are the experts though.  :)  Any help would be wonderful.

---

### Post by yetanotherproblem on 2007-11-28
Just an update:  I found the answer by sifting through posts here at the forum.  

For this problem, I had to boot into recovery mode and use the command:

lspci

I noted the numbers next to my video card (which happened to be 01:00.0), then used this command:

sudo dpkg-reconfigure xserver-xorg

After a long configuring process, I guess I got some kind of generic driver to work.  At least I could see the desktop when i booted in normal mode.  Once I was logged in, a restricted driver's thing popped up, and it fixed the video card completely with the correct drivers.

Just wanted to let you all know.  :)

---

### Post by borisattva on 2007-11-29
did you use AMD64 distro 7.10 ?

i had this issue when i tried installing 7.04, installing the restricted drivers and THEN upgraded to 7.10 but with a clean direct install of 7.10 it wasn't a problem.

---

