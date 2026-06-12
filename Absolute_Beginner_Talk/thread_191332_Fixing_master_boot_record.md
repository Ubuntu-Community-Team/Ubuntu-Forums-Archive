---
title: "Fixing master boot record"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by RogerD on 2006-06-07
Hi

I've got a dual boot system Suse 9.1/XP, and I want to replace Suse with ubuntu 6.06. I think I need to start by getting rid of GRUB and I understand I can do  this by running XP in repair mode and running fixmbr from the command line. Anyway, I keyed in 'fixmbr' pressed ENTER, and the got some terrible warnings about how I appear to have a non-standard master boot record and preceeding carried the risk of destroying access to all my partitions.

I didn't proceed. Are these messages standard in this situation, or is there something wrong.

All advice appreciated.

Roger D

---

### Post by uzi09 on 2006-06-07
hmm, not sure why that's coming up, but if i were you, i'd just stick an ubuntu install cd in there, and wipe the suse partition clean. leave grub on. the last thing you'd want to do is put MS's mbr on there.

if you can back out of this and follow the above method, that should get things running for yah, but if you're stuck and it won't let you back out, let us know.

---

### Post by Jagot on 2006-06-07
Yep, those warnings seem fairly standard.  Having said that, along with uzi09 I'd go ahead and install Ubuntu over the SUSE partition.  I believe 9.1 used Grub, so you should have no problems overwriting that.  Occasionally there can be problems when trying to overwrite GRUB with LILO or vice-versa.

---

### Post by bruenig on 2006-06-07
I had a similar situation, I had fedora core installed and was using grub on the mbr to dual boot between it and xp. All I did was put in the ubuntu install cd, delete the fedora partition, and put ubuntu where it was and then grub was overwritten and everything worked fine.

---

### Post by Robgould on 2006-06-07
That is a normal warning. I used to do it all the time when I dual-booted. Just proceed. It will be fine.
 
If it was me, I would quit dual-booting (I did). Install Ubuntu as your OS. Downloand and install vmware server for free. Then run XP or whatever else you want as a virtual machine. 
 
After that, try all the distro's you want as VM's and never have to mess with your MBR again.
 
Works great.
 
I am serious about that warning being normal. I got it everytime I ever did fixmbr from XP. At least 50 times.
 
If want to try VMWare and need help, just let me know.

---

### Post by RogerD on 2006-06-07
Many thanks for all the advice.
I was under the impression that the Ubuntu install wouldn't work unless I removed the current GRUB. Nice to know I don't have to take the risk of running fixmbr.

I'll wait a day or so, nice to have a clear few hours for these things, then go straight ahead with the 6.06 install.

One last thing - I'm planning to manually edit the partition table - I guess if I want to keep XP I have to go with this option  - I currently have three partitions:
hda1 ntfs - for Windows, hda2 for linux swap, and hda3 reiserfs, which I take to be my linux installation. Having recently lost all my linux working files, my own fault, but still unfortunate, I'm planning to create a partition for /home. I'll re-size the existing linux partition and create a spare 10GB or so for /home. Obviously I'll leave the Windows partition untouched, but do I have to reformat the three Linux partitions?

Thanks for all your help to date.

Roger D

---

### Post by uzi09 on 2006-06-07
here's a good guide to help you along:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
(it has guides for creating seperate /home partitions too, so look for those as well)

one thing it failes to mention (the last time i checked anyway) was that you can't resize an NTFS partition with the Ubuntu CD (i think this may have changed with Dapper, but if it hasn't) try gparted from [http://www.sysresccd.org/](http://www.sysresccd.org/)
be sure you run defragmentor a couple of times first!

let us know if you need anything else...

---

