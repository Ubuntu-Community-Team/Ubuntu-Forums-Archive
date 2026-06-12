---
title: "Ubuntu 11.10 ppc installation on a G5... no joy :("
date: 2012-03-02
forum: Apple Hardware Users
---

### Post by motoroller on 2012-03-02
I'm trying to install 11.10 64bit for powerpc using the "minimal" live cd install. I'm running a 1.8GHz G5 dual CPU with a 80 gb hdd (16gb free space) and nvidia fx5200 graphics card. 

For some reason, I can't hold down "C" or any other key combination in order to start up from a cd, so I am forced to start from open firmware and do it that way. Ok, fair enough... I managed to get it started that way, and the text-based installer was pretty straightforward and easy to use. I set a few configuration options, and everything was going well until it came to the point when it said "starting up the partitioner". Below the progress bar it said "scanning disks", and got to 48% before stopping. While the partitioner was starting up, the fans ramped up to full power and stayed there.

I hoped this was just a fluke, so I rebooted the computer and started again. The EXACT same thing happened again-- it got to 48% for scanning the disks, and then stopped.

I also tried using the install onlyonvid (or whatever it's called :P) in the hope that it would avoid the same problem, but no... it did the same thing again.

I've been searching for an answer but so far I'm stumped. Does anybody have any ideas? Or any similar experiences?

---

### Post by motoroller on 2012-03-02
Here's some additional information you might find useful...

While stuck at 48% for the partitioner scanning disks, I checked the log and the last message was "partman-lvm: no volume groups found"

Also, a few days prior I tried installing Fedora 16 for PPC and it froze in the middle of installation too, giving me the message "starting remount root fs failed"

I'm starting to think maybe it's some kind of disk error?

Any ideas would be greatly appreciated!

---

### Post by Double.J on 2012-03-02
Hi there motoroller,

Hmm several different installs all failing at the disk check level is worrying - and probably is a sign of hard drive troubles. The best way to edit the drive is get it out of the mac and connect it to a pc to check for errors - if you have an old powermac G5 this is pretty easy... if it's an imac G5... this could be more of a problem!

Does the machine still have an OS X installer? you could check the disk with disk utility? if you don't have one you could borrow a leopard disk off someone to check - all retail leopard disks were dual intel and ppc, and G5's should be able to boot from the dvds.

Unfortunately if several vanilla OS report the same fault, it's nearly always hardware - and the HDD by far the most likely. These machines are getting on... I removed my G4's Hdd to external and put a new drive in for the main OS last year just to be safe!

Hope it helps!

---

### Post by motoroller on 2012-03-02
> **gnu/mirow said:**
> Hi there motoroller,

Hmm several different installs all failing at the disk check level is worrying - and probably is a sign of hard drive troubles. The best way to edit the drive is get it out of the mac and connect it to a pc to check for errors - if you have an old powermac G5 this is pretty easy... if it's an imac G5... this could be more of a problem!

Does the machine still have an OS X installer? you could check the disk with disk utility? if you don't have one you could borrow a leopard disk off someone to check - all retail leopard disks were dual intel and ppc, and G5's should be able to boot from the dvds.

Unfortunately if several vanilla OS report the same fault, it's nearly always hardware - and the HDD by far the most likely. These machines are getting on... I removed my G4's Hdd to external and put a new drive in for the main OS last year just to be safe!

Hope it helps!

Thanks for your help!

To be specific, it's a powermac G5, and while it would be easy to remove the hdd, I don't have a PC handy to connect it to.  I also tried the OSX leopard install disk, booted it from the disk and ran disk utility (just did that a few hours ago), and it DID find two minor disk errors. One of them was a header issue, and I can't recall the other one. Disk utility fixed both, and I optimistically hoped it would solve the problem. However, I tried to install Ubuntu again and the same problem remained.

It seems likely it's the hdd, seeing as how it's almost 8 years old now. I want to build a new machine (running linux, of course!) and I think I'll start with getting a new hdd. It seems cheaper when you buy one part at a time, hehe...

---

### Post by MisterGaribaldi on 2012-03-05
If Disk Utility reports anything other than permissions-type errors, that is usually a sign of some kind of drive failure.

Another possibility (though unlikely) is it could be a RAM-related issue. Unfortunately, any of the RAM-checking utilities available all require that you are using x86-based hardware.

If you're anything like me, you might have a spare HDD (or two, or three...) laying around. Try using one of those, just for experimentation purposes, and see what happens. If not, then it's off to the store to buy a new HDD.

---

### Post by chrislu5tic on 2012-11-18
Hi there, late reply,    

I have a powermac G5,  I successfully installed, Ubuntu 12.04 ppc,  


 problems with a white screen and such, but you can

go to Top right corner, log out, 
hit enter for you cannot see the confirmation box asking you to log out, 
log into ubuntu under the 2d desktop environment,  and you can install ubuntu 12.04 and work out the kinks,   


 I could not get the wireless working and large problems with unity and such, Lubuntu 12.04 ran amazing, but no wireless, 
I have to revert back to Ubuntu 10.04 ppc for the drivers to install wireless.  

 If you cannot get your g5 to boot from disc you have to kind of trick is, 
unplug the internal HDD and start it with the disc in it,  once it recognizes the disc plug the hdd back in right away,   

my two cents.

---

