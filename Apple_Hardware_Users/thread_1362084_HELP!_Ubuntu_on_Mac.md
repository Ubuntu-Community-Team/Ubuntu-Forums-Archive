---
title: "HELP! Ubuntu on Mac"
date: 2009-12-22
forum: Apple Hardware Users
---

### Post by DCuchillas on 2009-12-22
Hello! So I am a noob, and I decided to install ubuntu just to check it out, I downloaded the latest ubuntu 9.10 and burned it unto a cd.

So I installed Ubuntu on an external drive via my macbook.

Now every time i start it, it comes up with : GRUB _

but it doesn't let me type anything. 

Also i can't choose what disc to boot using the option key when starting up, cause automatically boots into "GRUB".

Even if I don't have the external drive connected (via usb) it stills boots the GRUB.

I have already tried by introducing the macbook restore disc, but it keeps ejecting.

So, what should I do.. in order to get into ANY OS..


Thank you

---

### Post by jamesey on 2009-12-22
grub 2 & macs & karmic dont play nicely for beginners. I suggest finding Ubuntu 9.04 and trying that until Grub works. I'm a noob too, and that's what I've done.

if you want to give the technical part a go, read this thread. 
[http://ubuntuforums.org/showthread.php?t=1327758](http://ubuntuforums.org/showthread.php?t=1327758)

---

### Post by tom4everitt on 2009-12-23
That sounds really odd! I've never heard of anything similar, i.e that grub starts as the first thing. 

What happened is that you've installed grub to your hard drive, by, somewhere in the installation choosing: 

Install bootloader to /dev/sda 

or something like that. This is normally not a problem. (In case you didn't do some really advanced manual settings, which I doubt.)


What you could try is to get rEFIt on a cd, and see if you'd be able to boot from that. Get back to me with what happens when you try to do that. You do know how to burn an .iso to a cd, right?

rEFIt:
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

(but it really should allow you to boot your os x installation cd, try it again a few times!)

---

### Post by B_Free on 2009-12-23
How old is the machine? Is it PPC or Intel? If it is PPC, try the old alternative install of 5.10.
[http://old-releases.ubuntu.com/releases/breezy/](http://old-releases.ubuntu.com/releases/breezy/)
Otherwise, you will be beating your head against a wall trying to get things to work. After you install this version and get used to it, go for the upgrade. It took about 5 months to arrive at this conclusion. If you are proficient at the the terminal, you can ignore this post.

---

