---
title: "Ubuntu won't boot after install on blue &amp; white G3"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by star-affinity on 2005-08-08
I just installed Ubuntu 5.04 on a blue & white Power Mac G3 and it won'y boot after the install (which seem to have gone fine). It the part where the install CD has been ejected and the system is going to start up from the hard drive. This is what come up:

audit(here's alot of numbers that change every time i try to boot:0): intitialized
Starting Ubuntu...
pivot_root: No such file or directoty
sbin/init: 426: cannot open dev/console: No such filr
Kernel panic - not syncing: Attempted to kill init!
-

After displaying this a few minutes the computer restarts itself.

I formatted one of the the slave hard drives in the computer when booted from the Ubuntu install CD. This is the drive which Ubuntu is installed on. The machine has some extra hard ware, an Acard ATA 66 card, an ATI 7000 garphics card and 512 MB of RAM.
It boots fine to the master drive running Mac OS X 10.4.2

Any ideas?
Thanks in advance guys!  :)

---

### Post by autocrosser on 2005-08-08
Well-I'd say that you have a problem with the install location--Linux installs work best "first" in the food-chain--You could try changing the drive order to put Linux as the "master" drive--how many drives do you have?--I'm running four inside my Dual 1G Mirror-Door & Linux is the first partition on my 120G "master" drive (mirror-doors use cable-select)--I remember my B&W G3 400--was easy to swap drives--give it a shot & post back---

---

### Post by star-affinity on 2005-08-09
Thanks for your reply!
Did as suggested, but now after pressing "l" att the Yaboot screen there's a line of text the comes up repeatedly. Something like:

"DEFAULT CATCH!, code=330 at %SRR0: ff(numbers here)"

This also happened when removing all other drives and using only the Linux drive in the computer. The number "330" was changed to "300" and some other numbers were different as well (whatever that means...)

---

### Post by star-affinity on 2005-08-09
Tried to reinstall Ubuntu whith just one drive in the computer. Same problem as in my first post. Do you thin the Acard ATA card I have has got anything to do with it?

---

### Post by autocrosser on 2005-08-09
Very possible--try with a "stripped" system--just the 'nix drive & nothing else to see what happens--then if that works--add until things go away-- You might look at  [http://www.linuxhardware.net/](http://www.linuxhardware.net/)  to see if there are "issues" with your Acard--

Luck!!!

---

### Post by star-affinity on 2005-08-19
Oki, I have now removed the ATA card and have just one master hard drive installed. I managed to install everything fine and got to the nice Ubuntu log in screen, but for some reason it wouldn't accept the password, so I thought I just reinstall everything and reformat the drive. Now after all is installed it just comes to a black screen with the white Ubuntu cursor and stops there. The log in screen doesn't show. How can this be?

I've tried 2 times. Same thing...

---

### Post by autocrosser on 2005-08-22
Sorry I haven't replied before now-was busy over the weekend (moved my system into a bigger drive)---Couple of questions--Are you using the "stock" keyboard? "stock" mouse? What option(s) on install did you use? 

I know that I've had problems with the early (300/350) B&W's with keyboards--on one I was using a later USB 'board & it wouldn't be "found" untill late in the boot-up, caused problems with non-apple discs--

I'd try to re-install with "install-powerpc" & when it comes to partitioning--you need 3 partitions--a "new or old"  world boot partition (100MB), a Swap (about 1G) & your / partition --you can use others, but that is the basics. I don't remember if the B&W is "new" or "old" world--I tend to lean to new.

---

### Post by star-affinity on 2005-08-22
No problem! I'm happy that youreply at all! :)
It is Apples small "default" G3 keyboard and a 2 button + scroll wheel Microsoft mouse. Maybe the maouse is the reason that it doesn't work? :p :)

No, but seriosly. There's also an ATI Radeon 7000 grapichs card inside (64 MB VRAM, flashed PC card) which might be the cause of things acting strangely, because other than that things are all stock.

I tried booting from OS X install CD, erase disk and then boot from Ubuntu install CD to erase and partition from there. Now not even that work. The progress bar stops just at the end and nothing happens. :(

Thank you for trying to help, but I've given up on that machine running Ubuntu. At least for now...

---

### Post by autocrosser on 2005-08-22
No Prob--THAT'S why we are here--I want to get you into Ubuntu--I've been Linux for quite a while now & I try to change everyone over that I can----

As to your prob---try to reset the PRAM--keys are <Apple--Option--P--R> Hold all four down BEFORE the start-up chime, during a reboot--you will wait until the unit "chimes" 3 or 4 times--then let it boot normally--see [http://docs.info.apple.com/article.html?artnum=86194](http://docs.info.apple.com/article.html?artnum=86194)  for more info---This is known in the Mac World as the "four-finger salute"

I think your PRAM is corrupted---so this & then a clean install "should" get you on your way:)

I don't think that the mouse is a prob--is the keyboard USB or ADB (multi-pin round connector)?

---

### Post by star-affinity on 2005-08-23
Thanks. I know about PRAM. I did try to zap it before. No difference.
Now the machine is back with the other two hard drives installed (using ATA card) running OS X again. We'll see if I go back and fiddle with things later. Maybe I'll try Ubuntu on my main machine. A G4 "Quicksilver" 867 MHz. Maybe it'll work better there. But the problem is I'm using this computer all the time and the 2 hard drives in it is full with stuff. I do have an ATA card so I can pop in another drive, but Ubuntu ddidn't seem to like the ATA card in the G3, so I don't know.

Anyway, thanks again!
I'm definitely not giving up on Ubuntu as a whole. Just for the time being. I'm in the middle of moving to another apartment...  :)

---

### Post by autocrosser on 2005-08-24
Sorry it didn't happen for you--I'm on a dual 1G Mirror-Door & works great--even works with a "hacked" ATI Pro 9600 I got from OtherWorld Computing--You might wait the couple of months for Breezy to be out (Mid-Oct)--Lots of cool new stuff including a graphical installer--should be able to cope with more types of hardware.

---

