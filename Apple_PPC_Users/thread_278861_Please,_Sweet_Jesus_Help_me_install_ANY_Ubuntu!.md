---
title: "Please, Sweet Jesus Help me install ANY Ubuntu!"
date: 2006-10-17
forum: Apple PPC Users
---

### Post by st4rscream on 2006-10-17
Please can someone help me. I have a Mac 300Mhz G3 B&W It has no OS I replaced the HD with an old one I had. The old HD had OS 8.6 but it sucked. I want to install Linux on it but I can't afford Yellow Dog or Mandriva. No matter what flavour of Ubuntu I try.. Xubuntu, Kubuntu, Ubuntu.. I get the same error. I know sqaut about Linux except I like Slax. this is what it says:


/pci@80000000/pci-bridge@d/mac-io@5/ata-3@20000/disk@0:2,yaboot.conf: Unkown or corrupt filesystem 
can't open config file
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information
boot:_

And when I try to enter anything it says

Please wait, loading kernel...
run:2,/bmlinux: Unable to open file, Invalid device
boot:_


](*,) ](*,) ](*,) HELLLP I THINK I AM GOING CRAZZZZZZZZZZZZZZZY!!!!

---

### Post by yman on 2006-10-17
> **st4rscream said:**
> Please can someone help me. I have a Mac 300Mhz G3 B&W It has no OS I replaced the HD with an old one I had. The old HD had OS 8.6 but it sucked. I want to install Linux on it but I can't afford Yellow Dog or Mandriva. No matter what flavour of Ubuntu I try.. Xubuntu, Kubuntu, Ubuntu.. I get the same error. I know sqaut about Linux except I like Slax. this is what it says:


/pci@80000000/pci-bridge@d/mac-io@5/ata-3@20000/disk@0:2,yaboot.conf: Unkown or corrupt filesystem 
can't open config file
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information
boot:_

And when I try to enter anything it says

Please wait, loading kernel...
run:2,/bmlinux: Unable to open file, Invalid device
boot:_


](*,) ](*,) ](*,) HELLLP I THINK I AM GOING CRAZZZZZZZZZZZZZZZY!!!!

I'm no expert but-
did you download and burn the disc youself? it sounds to me like your copy of the disc is currupted.

---

### Post by st4rscream on 2006-10-17
Yeah I have downloaded them from the main Dling sites... you think i should um.. try burning it again?


But the thing that is wierd I get this same error no matter what version on Ubuntu I try Also I tried the desktop cd and the other install one.

---

### Post by yman on 2006-10-17
> **st4rscream said:**
> Yeah I have downloaded them from the main Dling sites... you think i should um.. try burning it again?


But the thing that is wierd I get this same error no matter what version on Ubuntu I try Also I tried the desktop cd and the other install one.
that is weird, and very unlikely. maybe theres a problem with the burner? I'm just guessing here, but I would try downloading again and burning from a different computer.

when exactly do you get the error message?

try typing help when it asks you and post the output.

---

### Post by jclmusic on 2006-10-17
order 1 from shipit.ubuntu.com and see if that works any better.

---

### Post by st4rscream on 2006-10-17
Well i ordered one but its gonna take 4-6 weeks...
Does anybody know of any other free OS I can put on it? My main PC died so this is all I'm stuck with.

---

### Post by Peter76 on 2006-10-17
Hi, it might be that your firmware is not up to date; use the disk with macos 8.6 to see if there are updates; or it might be that the harddisk you are using is broke? Good luck

---

### Post by st4rscream on 2006-10-17
You know whats funny.. I just reconnected the HD with os 8.6 to update the firmware and now it won't start. God I want to throw this mac out the window.

---

### Post by justin whitaker on 2006-10-17
I think the installer is having issues with the existing OS partition on the Mac. Which version are you using? The live CD? If so, get the Alternate Install disc, and try that.

---

### Post by st4rscream on 2006-10-17
Well I tried both Cds.. And I have had the same error with 2 different Harddrives One with os 8.6 on it and the other with nothing on it. Its wierd It goes into the yaboot black screen and thats it. it says (what I posted the first time) and stops agian I have tried 3 or 4 different disks with Xubuntu Ubuntu and Kubuntu. It might be a firmware issue but now that OS 8 wont load I dont know how to update it. And I dont have the install disks for the mac os. Thats kinda why I was trying to switch.

---

### Post by justin whitaker on 2006-10-17
> **st4rscream said:**
> Well I tried both Cds.. And I have had the same error with 2 different Harddrives One with os 8.6 on it and the other with nothing on it. Its wierd It goes into the yaboot black screen and thats it. it says (what I posted the first time) and stops agian I have tried 3 or 4 different disks with Xubuntu Ubuntu and Kubuntu. It might be a firmware issue but now that OS 8 wont load I dont know how to update it. And I dont have the install disks for the mac os. Thats kinda why I was trying to switch.

When things get really, really bad with my systems, I break out the [Slackware]("http://www.slackware.com/") install disk. I don't run Slack because I really do not feel like fiddling with every little aspect of my system, but the install disk will help you immensely if you are having partition or disk issues. 

Run CFDisk, and rebuild the partitions, then try to install Ubuntu.

---

### Post by dagnabit dang doohickey on 2006-10-17
If you'd like to get 8.6 to boot, try zapping the PRAM:
Power on the Mac, then immediately hold down these keys: Command + Option + P + R
Let the Mac chime about five times, then release the keys.

If that doesn't work, you can try resetting the Cuda button on your motherboard. Take a look at the attached diagram. Unplug the Mac if you're gonna do this.

As for your Ubuntu problem, this may sound silly, but make sure your HD is jumpered as Master. Those Macs don't do cable select.

---

### Post by bodycoach2 on 2006-10-17
I don't think Jesus posts on this part of the forum. You might try the Christian edition. For the moment, I'll blasphemy, and try a few ideas:

1. The HD you installed might not work with the older hardware.
2. I've loaded Xubuntu 6.06.1 on two 333Mhz iMacs. The original 6.06 version wouldn't boot; live or install CD's. Make sure you've burnt the 6.06.1 verson.
3. Try adding 'baby' to the pray. As in "Sweet Baby Jesus". It worked for my grandmother.



> **st4rscream said:**
> Please can someone help me. I have a Mac 300Mhz G3 B&W It has no OS I replaced the HD with an old one I had. The old HD had OS 8.6 but it sucked. I want to install Linux on it but I can't afford Yellow Dog or Mandriva. No matter what flavour of Ubuntu I try.. Xubuntu, Kubuntu, Ubuntu.. I get the same error. I know sqaut about Linux except I like Slax. this is what it says:


/pci@80000000/pci-bridge@d/mac-io@5/ata-3@20000/disk@0:2,yaboot.conf: Unkown or corrupt filesystem 
can't open config file
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information
boot:_

And when I try to enter anything it says

Please wait, loading kernel...
run:2,/bmlinux: Unable to open file, Invalid device
boot:_


](*,) ](*,) ](*,) HELLLP I THINK I AM GOING CRAZZZZZZZZZZZZZZZY!!!!

---

### Post by shadie on 2006-10-17
I also had problem trying to install 6.06.1, in the end it turned out to be the type of CD I was using, I had an old copy of 5.04 which worked so burned a new image to a KodaK disc that worked.

---

