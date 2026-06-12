---
title: "Dual boot Ubuntu + Mac Os 9.2 classic"
date: 2012-01-11
forum: Apple Hardware Users
---

### Post by loth77 on 2012-01-11
hi all :)
i have this old iMac with mac os 9.2 installed.
i have made a copy of the system on a bigger hard disk and it boots and works well. 
now i'm trying to make it work in dual boot with Ubuntu (i'm trying 8.04) but yaboot keeps ignoring the mac os classic partition and doesn't let me boot it...

does anybody know what i can do to make it dual boot?

---

### Post by rsavage on 2012-01-11
Don't install 8.04 unless you are using your iMac as a server.  You are not going to receive updates for your desktop packages.  
 
See [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) .  I'm in the process of updating it.  Haven't quite completed the dual boot question yet.

---

### Post by loth77 on 2012-01-11
thanks :)
i followed all the suggestion that i have found there
and was almost all already done

but the best i can obtain is a working yaboot and linux
but when i choose to boot macos i have the little icon in the middle of the screen asking for a system disk :(

and before installing linux this was working correctly


maybe i have to put the mac os partition after the yaboot booting partition...
i'm actually new with these things on macos... so i don't reallyknow how to move around :)
what do you think?

---

### Post by rsavage on 2012-01-11
The Ubuntu installer should pick up the Mac OS partition and give it to you as an option at the first yaboot prompt.
 
If it doesn't then you have to specify a line in your /etc/yaboot.conf like this:
 
macos=/dev/hdxn
 
Where x is a letter (usually a, b, c or s) and n is a number, likely between 9 and 12
 
When you you have made changes, you need to run
 
sudo ybin -v
 
It sounds like you have a line in your yaboot.conf, but it is pointing to the wrong partition.
 
You can also specify it like this:
 
macos=hd:3/
 
I don't think the position of your yaboot partition has anything to do with your problem, but I have never ever used Mac OS/Mac OSX!

---

### Post by loth77 on 2012-01-11
i already did all those steps, also tried both ways of specifying the partition
also i tried to put a wrong partition as a test... and it just goes back to yaboot without errors and ask me to choose again
so i'm sure the partition is the right one even if ot doesn't really boot

at this point the sequence of partitions is the only thing i can think about.... even if it sounds silly :)

---

### Post by loth77 on 2012-01-12
update:

i defeated it :D
i connected the 2 hard disks, the original appleone with only macos9 and mine with both macos and linux installed

the first booted and i couldn't see the second
using a partitioning program i clicked on "update driver" don't really know what is.... but it told me to reboot the imac

after rebooting both hard drives were seen by the system.

so i disconnected the apple one and booted succesfully the macos9 from yaboot :)

now i will restart it and check if also linux still works :)

---

