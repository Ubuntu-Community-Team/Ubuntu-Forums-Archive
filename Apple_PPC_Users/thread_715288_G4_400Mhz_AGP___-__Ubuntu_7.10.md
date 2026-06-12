---
title: "G4 400Mhz AGP   -  Ubuntu 7.10?"
date: 2008-03-04
forum: Apple PPC Users
---

### Post by MTiN on 2008-03-04
Hey there!
I want to install ubuntu 7.10 onto an 400mh g4 with agp-graphics!

but I can't even get the cd to boot!
when I just press enter at the boot prompt the screen just goes black....

then read the known issues and tried

live-nosplash-powerpc video=ofonly

that takes me a little further to that busybox shell, but then I can't enter anything, the keyboard is dead! (capslock etc. don't light up to, so its really without power)

so I can't enter anything like modprobe ide-core and so on!
the other tip, to add "break=top" to the boot line gets me to the same busybox console, only a little earlier (I can see less text) but keyboard wont work too!!

whats going on here?

---

### Post by stream303 on 2008-03-04
One thing you can try is to install Feisty 7.04, preferably with the alternate cd, and then upgrade to 7.10.

Are you using an apple keyboard, or is anything else hanging off it?

---

### Post by MTiN on 2008-03-05
ok, I'll try that tomorrow and post back here...

just tried a 6.10 desktop-cd, same problems....but that alternate-cd sounds like a good idea!
yeah, I've just got an apple keyboard connected to the computer, nothing else! (also tried a windows keyboard, doesn't change anything)

---

### Post by sjmacko on 2008-03-06
Hello there...

I picked up an old Sawtooth 400 AGP a couple of weeks ago, and I'm tinkering with it now. I was able to boot Ubuntu 6.10 on the old girl, and install it even though I only had 192 MB of memory. After the install, I applied all of the updates, and then I let it upgrade to 7.04. I was feeling on top of the world, because everything worked! I let it upgrade to 7.10, and that was it... The machine hangs immediately after the ubuntu splash screen comes up. This is a project machine for me, and I haven't decided which OS(es) it will run yet.  So... I headed to the OpenSuse site, and downloaded the network install CD. It took about 2 hours, and in the end I had an OpenSuse 10.3 desktop system. Everything worked fine, and my 22" monitor displayed at a decent resolution.

I now have 448 MB of memory in the old girl, and I think she will be my little webserver. I may take another stab with the server install....

Steve

---

### Post by stream303 on 2008-03-06
> **MTiN said:**
> just tried a 6.10 desktop-cd, same problems

Definitely try the "alternate" disk, and I'd probably use the Feisty 7.04 distro to get up and running.  Hope we don't run into that keyboard issue.

This might not be related, but Rubix Hacker had a good suggestion regarding the keyboard during install - manually tell it that you are using a US Macintosh keyboard, and then maybe change it later - if you run into that problem at all ...

---

### Post by stream303 on 2008-03-06
> **sjmacko said:**
> So... I headed to the OpenSuse site, and downloaded the network install CD. It took about 2 hours, and in the end I had an OpenSuse 10.3 desktop system.

Nice - I didn't know that was available.  I dreaded trying to download a full dvd just to check it out.  I wonder if Fedora ppc has the same network install option?

I have to admit that I'm hooked into the Debian / Ubuntu way of doing things.  It will be hard to let go of apt-get / aptitude / synaptic among other things, but good to know there are alternatives.

---

### Post by slafochmed on 2008-03-06
my signature... :)

I was trying Debian but wanted sth more preconfigured, so I tried ubuntu. I did not manage to install the version 7 of the server edition.

---

### Post by MTiN on 2008-03-07
I think I discovered at least something!
at first, the alternate-7.04-cd showed me this with install-powerpc video=ofonly
[IMG]http://mtin.de/g4ubuntu1.JPG[/IMG]
[IMG]http://mtin.de/g4ubuntu2.JPG[/IMG]
and just broke up there....
but after I pulled out the firewire-pci card that was sticking inside the mac (internal firewire is stopped working long time ago so I put in a firewire-pci card)
the cd bootet into some installer, I could select language and keyboard layout but then it got stuck here:
[IMG]http://mtin.de/g4ubuntu3.JPG[/IMG]

now I pushed in the 6.10 desktop install again(live cd) and wuuuhaaa it booted up fine with live-powerpc-nosplash video=ofonly!!

should I install 6.10? or is that problem with the 7.04 cd easy to solve?

---

### Post by stream303 on 2008-03-07
wow, I felt like I was there. :)

I have heard that when you add and remove cards from a Mac, it is best to zap the pram and/or perform an smu/pmu reset.  I have heard of this data getting corrupted.  Don't know if it would help in your case, but it might be worth looking into.

---

### Post by MTiN on 2008-03-07
[IMG]http://mtin.de/g4ubuntu4.JPG[/IMG]

thats the 7.10 alternate-cd....
it just hangs at that point, the keyboard is working, I can enter text and it even appears there on screen but it just doesnt get any further....

I've done that pvram-delete thingy, but that didn't change anything....

so right now its like 6.10 desktop cd running and booting to desktop
7.04 alternative cd hanging during some IDE-detection (see screen 2 posts above)
7.10 alternative cd  stopping as shown in this screen

I don't really want to install 6.10, its 1.5 years old :-/
hopefully someone can get me another step further, I really appreciate your help :D

---

### Post by xc3RnbFO8P on 2008-03-07
How much RAM do you have?

---

### Post by MTiN on 2008-03-07
384mb

just desperatly tried the daily build of hardy heron, and that got pretty far, further then the 7.xx versions but hangs on Running local boot scripts...(just was away for 2 hours and its still there, so - yeah, damn)
is it correct that there is now alternate install disc for hardy ppc?

[IMG]http://mtin.de/g4ubuntu5.JPG[/IMG]

---

### Post by stream303 on 2008-03-07
> **MTiN said:**
> I don't really want to install 6.10, its 1.5 years old :-/
hopefully someone can get me another step further, I really appreciate your help :D

I suppose you could try doing a dist-upgrade from 6.10, and if that works, do another dist-upgrade...

1.5 year old distros aren't too bad (think about how old OSX Tiger is at this point), especially if you enable the backport repositories.

Do you have any other hardware hanging off that machine / keyboard other than just the ethernet cable / keyboard / mouse ?

Sometimes I'll even forego the mouse initially if I'm doing the alternate install - although this doesn't appear to be the problem.

---

### Post by st0n3cutt3r on 2008-03-07
Hi there, I don't know much about bashing linux into installing itself, but I had similar issues trying to install 7.10 to my newworld G3 iMac.  I got slightly farther than you did with it, but nothing actually worked for me.

I installed Yellow Dog Linux, because it's specifically designed for PPC, but when nautilus wouldn't work I was sick of it after about 3 hours and tried the Ubuntu 7.04 alternate CD.

I know you said you tried 7.04 alt with the nosplash-ppc video=ofonly, but have you tried without all of that?  (just letting it attempt a regular install)  

I wasn't paying attention when the install process started for 7.04 otherwise I would have tried all of the nosplash and video stuff, but just running a normal install it installed with no problems - although I did have to do a text install.  Even so, that was easy enough, and now I have 7.04 running on my G3.

If you do get 7.04 working, be careful about upgrading to 7.10.  I've run it on other computers, and it's great - I like it a lot better than 7.04, but it doesn't seem to work well for PPC.

Good Luck!

---

### Post by MTiN on 2008-03-08
yeah well, the problem with 7.04 alternative is this:

[IMG]http://mtin.de/g4ubuntu3.JPG[/IMG]

doesn't change if I just use install oder install-powerpc or whatever...

---

### Post by MTiN on 2008-03-09
well, hasn't anybody got some more ideas?

just tried to install 6.10 via live-cd, Installation runs until 91% and then does nothing more; Canceling the dialog via 'X' is possible the message displayed is "Loading module aec62xx for IDE chipset Support".

what next :(

---

### Post by stream303 on 2008-03-10
Is this a dual-hd drive Mac?

---

### Post by MTiN on 2008-03-10
no, it has a single 30gb drive...and a dvd drive and a zip-drive, but I already disconnected the zip drive in my various tests cause I don't need it anyway...

---

### Post by stream303 on 2008-03-11
Is this 30gb drive the original or a replacement?  I've heard of replacement problems when they were set with their master / slave jumpers wrong, even if they appeared to operate ok.

---

### Post by MTiN on 2008-03-11
almost looks like it is a replacement, mactracker (huge list of all macs) tells me the G4 Agp Graphics shipps with
10 GB 5400-rpm, 10, 20, or 27 GB 7200-rpm

this is the disc in my g4:
[IMG]http://mtin.de/hd.jpg[/IMG]

there I can see 30.7GB 5400 rpm!

are these jumper settings correct?
(if I see that right its set to be Device 0 - master, wich should be correct right?)

---

### Post by stream303 on 2008-03-11
Looks normal, although that cable looks a bit loose on the left hand side like some of the wires aren't making good contact inside the plastic header.

While you're there, and with the unit unplugged, you might want to blow off some of that thermal-blanket. :)

---

