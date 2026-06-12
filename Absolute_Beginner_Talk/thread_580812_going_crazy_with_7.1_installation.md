---
title: "going crazy with 7.1 installation"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by thespankguy on 2007-10-19
i have two hard drives, a 40 gig and a 120. the 40 is the factory hard drive that is connected via its own IDE cable. the 120 was one i purchased and is hooked up as a slave to the dvd-rw drive, although i had to position the jumper in the "cable select" position to be able to access the 120 when i was running xp from the 40. i just installed 7.1 on the 120 (partitioned it into 90, leaving 30 for a possible xp installation so i can get rid of the 40 and maybe have the 120 hooked up correctly, just a small dream). 

i restarted after the installation and got GRUB loading... ERROR 21. after quickly jumping to my laptop i found that 21 means that it cannot find the drive. so i've been messing around with the two hard drives' positions on the IDE cable and with jumper settings and absolutely cannot get it to work. i even completely removed the 120 gig and positioned the jumper to the single (neutral position) and figured that i'll deal with xp until i can do more research and figure out what i can do. however, xp won't load. this is also when i get the error 21.

i've also tried only using the 120 and running strictly ubuntu, but i get "error loading OS" . i thought "maybe i should just reinstall and see what happens, this time with only the 120 gig hooked up." when i got to the partitioner, i only had the ability to partition the 30 gigs that was left over from my initial installation. i could also see the 90 gig partition. 

any ideas? i'm freaking out. the wife's going to kill me if she can't do her homework. when she went to bed she specifically told me NOT to install it tonight. oops

---

### Post by conehead77 on 2007-10-19
> **thespankguy said:**
> i even completely removed the 120 gig and positioned the jumper to the single (neutral position) and figured that i'll deal with xp until i can do more research and figure out what i can do. however, xp won't load.
If you do this again and insert the XP disc, there should be a repair option to make XP work again.

I also suggest to have 1 partition for a stable OS and another where you can try new versions.

---

### Post by thespankguy on 2007-10-19
PS my 40 gig is a western digital wd400 and the 120 is a maxtor diamondmax 16

---

### Post by thespankguy on 2007-10-19
> **conehead77 said:**
> If you do this again and insert the XP disc, there should be a repair option to make XP work again.

i booted from the xp cd, ran the repair option, the computer then restarted and said "GRUB loading, please wait...Error 21".

i'm going to sleep on it, and wake up with no options

---

### Post by thespankguy on 2007-10-19
bump

---

### Post by DiagDirt on 2007-10-19
Boot with the xp disc again and use the repair console , type "fixmbr" .
This will override the corrupt boot record with a fresh one and allow you to boot back into windows.
[Microsoft Documentation.]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true")


Good Luck

---

### Post by LowSky on 2007-10-19
figure you might want to know what the error message your getting means
> Grub Error 21: Selected disk does not exist 
This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system

In my experience haveing a Hard drive and a disc drive share the same cable is a bad idea. Maybe its just my own superstition, but it hasn't failed me yet.

What you should do is have the 40GB as the master Hard Drive, the 120GB as the slave on the same IDE channel. Then reinstall Ubunutu with the Live CD and use Gparted to reformat and resize the hard drive you want to use for installation. I dont like choosing cable select or nuetral because it can lead to these odd issues. Also make sure that your BIOS settings are correct make sure that the correct hard drive is set to boot.


Good luck

---

### Post by thespankguy on 2007-10-19
i don't have any other IDE cables. if i run to best buy real quick will they have them of varying lengths?

i also still cannot get xp to boot. i don't know the administrator password to log in to the recovery console, and leaving it blank to just press enter restarts the whole process. i've googled and googled and have found options to make bootable cds, however i can't do that because i can't log onto xp (or ubuntu for that matter) to make the cd. the laptop i'm on doesn't have a burner

---

