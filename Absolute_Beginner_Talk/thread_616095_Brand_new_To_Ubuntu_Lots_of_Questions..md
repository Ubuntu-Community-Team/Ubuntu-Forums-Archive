---
title: "Brand new To Ubuntu Lots of Questions."
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by jordan89ca on 2007-11-17
So after thinking that this would be a fairly easy walk in the park Im surprised that I am having trouble with it at all:P.

Ok well heres a couple things Im looking for help with.

Firewall?  Pretty sure I need one of those even on Ubuntu:P...I found something called Lokkit? and GuardDog? i do believe but I have no idea how to go about installing them. 

Anti-Virus? as well. 

I guess thats all I need for now..I will try and figure out the rest but now a days not having a firewall on the internet is pretty much computer suicide haha at least for windows haha:)

Oh Also..Wondering if theres anyway to have a boot menu for 2 seperate os on 2 different hardrives.  Or do i just have to keep going to the boot menu and selecting a harddrive?

I am running a HP Pavilion a1610n 

AMD Athlon 64x2 (Dual Core) 
Nvidia XN 7300LE 256mb
20 gig hardrive (For Ubuntu) And a 250 Gig Hardrive (For Xp)
1.5 gigs of ram.

Hopefully all that information is good enough to get a perfect answer. Ive learned that included the specs help haha:) I am also running version 7.04 Fiesty??

---

### Post by oilchangeguy on 2007-11-17
> **jordan89ca said:**
> So after thinking that this would be a fairly easy walk in the park Im surprised that I am having trouble with it at all:P.

Ok well heres a couple things Im looking for help with.

Firewall?  Pretty sure I need one of those even on Ubuntu:P...I found something called Lokkit? and GuardDog? i do believe but I have no idea how to go about installing them. 

Anti-Virus? as well. 

I guess thats all I need for now..I will try and figure out the rest but now a days not having a firewall on the internet is pretty much computer suicide haha at least for windows haha:)

Oh Also..Wondering if theres anyway to have a boot menu for 2 seperate os on 2 different hardrives.  Or do i just have to keep going to the boot menu and selecting a harddrive?

I am running a HP Pavilion a1610n 

AMD Athlon 64x2 (Dual Core) 
Nvidia XN 7300LE 256mb
20 gig hardrive (For Ubuntu) And a 250 Gig Hardrive (For Xp)
1.5 gigs of ram.

Hopefully all that information is good enough to get a perfect answer. Ive learned that included the specs help haha:) I am also running version 7.04 Fiesty??

ubuntu has a built in firewall, iptables.
this isn't windows. no need for anti-virus, or anti-spyware software. if you do install it, all it will look for is a windows virus. and they have no effect on linux.

---

### Post by jordan89ca on 2007-11-17
wow that was a fast response lol.  thats what i figured.  but just wanted to be safe.  
Thansk!

now just gotta figure out if i can just select what os i want instead of having to catch it loading and bring it to the boot screen:P

---

### Post by mellowd on 2007-11-17
you can use grub as a boot loader to choose which os to startup

---

### Post by jordan89ca on 2007-11-17
Ok ..which Os should I install this on??

Also which version should should I download?

---

### Post by oilchangeguy on 2007-11-17
> **jordan89ca said:**
> Ok ..which Os should I install this on??

Also which version should should I download?

please tell us what os(s) are presently on your computer. have you already install ubuntu? and version of what?

---

### Post by jordan89ca on 2007-11-17
In the above post i posted it all:) now in signature i think.

Ubuntu7.04 is what I installed of the disk (fiesty is what the browser said)

---

### Post by oilchangeguy on 2007-11-17
in what order did you install windows, and ubuntu?

---

### Post by jordan89ca on 2007-11-17
windows came on my computer.

just installed ubuntu today.

If I let my computer boot up all by itself it defaults to ubuntu now.  But Im pretty sure thats just because of the order of my hardrives?

---

### Post by oilchangeguy on 2007-11-17
> **jordan89ca said:**
> windows came on my computer.

just installed ubuntu today.

If I let my computer boot up all by itself it defaults to ubuntu now.  But Im pretty sure thats just because of the order of my hardrives?

by order of hard drives. do you mean jumper settings? (we have to all be on the same page, with standard terms) is ubuntu on the master drive?

---

### Post by jordan89ca on 2007-11-18
Both hardrives are listed as "master drive" there independent harddrives nothing to do with one another...other then the rest of the computer parts. 

Windows - original harddrive - installed first-

Ubuntu - New hardrive - Installed second - 

Both Master....No slave.

---

### Post by LaRoza on 2007-11-18
If they are SATA, there is no master or slave.

You can have Grub remember what OS you used last, and use that by default. Edit grub:

```

gksudo gedit /boot/grub/menu.lst

```

And set "savedefault" to true. Uncomment it first.

---

### Post by geirha on 2007-11-18
Ubuntu should have detected the presence of a windows installation and added it to the boot (grub) menu during install, is there no windows entry in your /boot/grub/menu.lst?

As I understand you dual boot by switching the boot order in the bios at the moment?

---

