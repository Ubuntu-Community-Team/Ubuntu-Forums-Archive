---
title: "Grub NOT starting? Bios sees hdd, menu.lst intact, seperate boot partition"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by dannyboy79 on 2007-01-26
You know the funny thing about forums and trying to get help is that you get yelled at if you create a new thread that's already been answered in another thread but you also get yelled if you try to ask additional questions in someone else's thread. They say, "HEy, don't hi-jack my thread!" So I am creating a new thread since no one helped me in the thread that I quote unquote was hijacking.

I dont' want to hijack this thread but why would I start a new thread for the same problem????? 
So here's my issue. I have had Ubuntu installed since March of 2006. Everything's been great. Lately my machine seems to just lock up (locked mouse, locked keyboard, display is frozen as whatever was last on the screen. Example: nautilus, a terminal session etc etc), the only way to get it to do anything is to either his the reset button on my comp or hit the power button, wait a sec, then turn it back on. Well one day, it just sat there at the Boot to cd screen. (i have my bios set to boot to cd all the time) normally this doesn't matter as if there's no cd in the drive it just continues onto to Grub. Well, for some reason Grrub never starts??? Yes I have checked my bios to make sure the correct hdd is the first boot device, and yes I have made the boot order so that the hdd boots first and just have forgotten about leaving bios to boot to cd first. All the hard drives show up in bios just fine. When i boot to Live CD, the partition is there and is intact! I have a /boot partition that is hdc1 then I have a /root partition that is hdc2, hdc3 is swap, hdc4 is /home. I have reviewed the menu.lst file and everything looks fine. I have even tried to follow a tutorial on how to reinstall grub using Knoppix but i get an error stating the grub-install doesn't exist despite me finding it inside /KNOPPIX/sbin/. The steps I followed were to umount hdc1 if it was mounting auto by Knoppix, then I am to remount it using the -o dev option. then I am to run sudo chroot /mnt/hdc1 grub-install /dev/hdc. as I said, I get an error stating that grub-install doesn't exist??? so I have even tried sudo chroot /mnt/hdc1 /KNOPPIX/sbin/grub-install /dev/hdc and that still says that doesn't exist? Then I tried just sudo grub-install /dev/hdc but it states something about not being able to find /boot? Is this all because I have grub installed on a different partition than /root? Can anyone help please.

---

### Post by dannyboy79 on 2007-01-27
please help. all these ubuntu users and no grub issues???

---

### Post by dannyboy79 on 2007-01-29
i have even played around with that super grub disk, restored grub to the mbr as well as the /boot partition I made and still nothing. the computer goes thru the bios as normal, then all of a sudden nothing. it just sits there doing nothing where as before grub would start?????? i don't know if I fired my mbr or what? i can mount the partition and see everything in it and the menu.lst is fine, the vmlinuz is on the root partition and everything looks intact as I said. I am really getting pissed off here. i ever started another thread a no one wants to help me?? I can boot into ubuntu fine by using the super grub disk and just telling it to boot the mbr. so the only thing I can thinik of is that the bios doesn't know what mbr to boot. so I made sure the correct hard drive is the one being booted and it is? I don't know what else to do? I suppose I can just always boot to a grub floppy first or even the super grub disk but that's gonna take longer is only a temp fix!

---

### Post by louieb on 2007-01-29
It sound like you have done all the normal stuff needed to fix a GRUB problem. Its weird that you boot to Ubuntu using the super GRUB disk, but can't boot straight to the hard drive. I guess you have already looked at the Reinstall grub thread in my signature. If anything I don't think those guys would mind if add your  troubles to it to.  
It also sounds like you know your way around Linux well enough. The one thing I don't think is a problem is the fact that you have /boot on a separate partition unless it is formatted risnerfs. I have heard of some trouble with GRUB and that file system.

---

### Post by dannyboy79 on 2007-01-29
yeah, it's very strange. that's what I said. I have been using linux since march of 2006 so I am really not that smart with it at all. I seem to pick things up very fast though. what's more odd is that this just happened out of no where? ubuntu was running fine and all of a sudden one day I rebooted and grub just wouldn't start? 
I have tried your sig but when I do a search after using a knoppix live cd, it doesn't find anything? I think that's because knoppix automatically mount the partitions under /media/hdc1 and /media/hdc2 etc etc. so it never finds /boot/grub/blah because the /boot folder within /media/hdc2 is empty, that data is actually located within /media/hdc1/grub. so I just realized, maybe I need to search for find /grub/stage1.
or maybe I need to umount hdc1 and hdc2 and mount them like they'd really be mounted. so I would mount hdc1 within the /boot folder that's located within /media/hdc2. i don't know but I am confussed and it shouldn't be this hard, we are only talking about a boot loader here. not authenticating a netowrk user using a mysql database, i mean come on. im just stuck!

is it possible that a mbr is unfixable? that it's trashed and I will only be able to boot from a floppy or cd? 

i am going to run a test. i am going to first use part image to backup all my partitions onto one of the other disks in my server. making sure I label each one very carefully. then I am going to just fill the 20gb hard drive with zeros or what ever I have to make sure that I completely remove all the current data on it, delete all partitions, recreate them, reformat them, etc etc. do a fresh install onto the partitions, using the same scheme. then use partimage and restore only my /home partition and my / partition. this way the install created /boot partition and mbr will be intact. if that works than i know it was obviously a really screwed up mbr that I just couldn't reinstall grub onto. what do you think? cause I am at my last straw here. I have tried everything. i even triewd setting the /boot partition as "bootable" using the sgd.

---

### Post by geek_Man on 2007-01-29
No, I'm pretty sure that an mbr is fixable. You do have astrange setup, y'know. And maybe it's not that hard, maybe you just haven't found the right answer. You still have to try changing your groot line, so not all hope is lost.

---

### Post by dannyboy79 on 2007-01-29
why is mine a strange setup?? i have read it many times that it's a good idea to create a boot partition for grub to sit on. is that why you think my setup is weird? merely because I have a boot partition? or is it because I have a my dvd-rw drive on my frist ide channel as master. I found that to be the solution when I was having burning issues with both winbloz and linux. don't know why, it just worked.

---

### Post by geek_Man on 2007-01-29
It's just that your description of your drive setup in one of your last posts rather blew me away. You'd have to write it down on paper for me to fully understand it. That's all.

---

### Post by dannyboy79 on 2007-01-29
ide channel 0= dvd-rw as master (linux makes it hda) or is it hda1? not sure about optical drives and partition numbers?

ide channel 0= 300GB total as slave, 200GB as fat32 is partition 1 and 100GB as ntfs is partition 2 (linux makes them hdb1 and hdb2) 

ide channel 1= 20GB total as master, 50MB as ext3 is partition 1 mounted at /boot, 10GB as ext3 is partition 2 mounted at /, 1.5GB swap is partition 3, and remaining space as ext3 is partition 4 mounted at /home. (linux makes them hdc1, hdc2, hdc3, hdc4)

ide channel 1= 300GB total as slave, ext3 is partition 1. (linux makes this hdd1)

sata channel 1= 400GB, ext3 is partition 1. (linux makes this sda1)

sata channel 2= 500GB, ext3 is partition 1. (linux makes this sdb1)

totaling 1.52TB. I LOVE IT ALL!!!!

---

### Post by geek_Man on 2007-01-29
:-o

---

### Post by dannyboy79 on 2007-01-29
so geek-man, you're suggesting I change my #groot line to be what? what about the #kopt line? is the kopt line suppose to be the partition and hard drive that contains the / data?

---

### Post by louieb on 2007-01-29
Your right,  because you have a separate /boot partition, when you run the find command from the GRUB prompt,  look for /grub/stage1.

---

### Post by geek_Man on 2007-01-29
Try "#groot=(hd2,1)". I don't know for sure what it should be. But do what louieb said and find where stage1 is. Whatever it is, it's in the second partition. So "#groot=(?,1)" to narrow it down if it's not 2,1.

---

### Post by dannyboy79 on 2007-01-30
WOW, i have no idea why my menu.lst would have changed in the first place but that was it!!!! so now I have # groot=(hd2,1) and it works! YEAH! God, i thought for sure I'd have to mess around and either backup everything up then put it back onto a newq drive or something more serious. I am so glad to have Ubuntu back! I missed her. I was out for more than a week! I played with a little each day for most days, some days didn't but 7 days without Ubuntu isn't fun!!! thanks to everyone for there help!!!!! The super grub disk couldn't even fix this. I wonder if I should tell the creator of the program that the #groot line should be looked at if all else fails.

---

### Post by louieb on 2007-01-30
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

```geek_Man, What made you even think to look at the groot= ...?   I wonder what it does. Just looked at the man page for grub, but the Dapper man page on grub doesn't have anything on it.
When I look for trouble in menu.lst I  just fly by that part of it.    Oh well off to Google y'all.

---

### Post by geek_Man on 2007-01-30
Back when I was dumb and trying to put GRUB on my external hard (so that I could keep Windows and Ubuntu seperate) I learned quite a lot about GRUB. groot stands for "GRUB root" and it says where stage1 is and all that. Glad you're back on, glad I could help!

---

