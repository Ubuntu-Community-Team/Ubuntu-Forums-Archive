---
title: "Problem With Compiz-Fusion"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by tototime on 2007-11-29
Hello All,
I am a complete beginner when it comes to Linux so I need an easy to follow way on how to do this.
I am running Ubuntu 7.10 on VMware player with xp as my main os.

My problem is this Compiz-Fusion will not work for me  I cannot rotate the cube or any of the cool effects.
I typed in this code
sudo apt-get update
sudo apt-get install compiz compizconfig-settings-manager

This is all ive typed in along with running the program originally can anyone tell me whats wrong.

Also I have tried to enable custom dektop and it will not let me any help on this would also be appreciated.

Regards,
tototime

---

### Post by dpar on 2007-11-29
I don't believe 3D effects will work in a virtual environment. I may be wrong though.:)

---

### Post by tototime on 2007-11-29
Ok if that doesnt work is there a way to safely install ubuntu to my computer so that i may still access windows xp and the work will be saved

---

### Post by dpar on 2007-11-29
Yes

[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by tototime on 2007-11-29
ok alos i have 55 gigs of hard drive space left is that enough

---

### Post by dpar on 2007-11-29
Yup, I'm using 60 gig for two distros.

---

### Post by PmDematagoda on 2007-11-29
You don't need to install Compiz-fusion on Ubuntu 7.10 tototime since it is built-in:), you can activate Compiz-fusion by right-clicking on the desktop, clicking the Change Background once the Appearance manager shows up go to Effects and put it to best and Compiz-fusion will be started.

---

### Post by GnomviD on 2007-11-29
Did you check out the Compiz-Fusion wiki? If you're running on a laptop or using a graphics card on the Compiz-Fusion blacklist, you'll have to crunch some code to get it to work. I had some trouble with Compiz, but I managed to get it to work (warning: there's a reason these cards are on the blacklist):

[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)
[http://wiki.compiz-fusion.org/Troubleshooting](http://wiki.compiz-fusion.org/Troubleshooting)

---

### Post by dpar on 2007-11-29
He's trying to run it in a virtual machine.

---

### Post by PmDematagoda on 2007-11-29
Yes, I realised that, but I believe that Compiz-fusion should work even though it is in a Virtual Machine.

---

### Post by dpar on 2007-11-29
Oh,ok. I was just going by what bodhi.zazen said in this post......

[http://ubuntuforums.org/showthread.php?t=624790&highlight=compiz+virtual](http://ubuntuforums.org/showthread.php?t=624790&highlight=compiz+virtual)

---

### Post by PmDematagoda on 2007-11-29
I did not necessarily say that Compiz-Fusion should work on a VM, but I just suggested that it might, I will have to give that a try myself, maybe by some chance I can get Compiz-fusion working on a VM, hopefully:).

---

### Post by Perkins on 2007-11-29
I would expect that some of the effects would work in a virtual machine.  After all, I have a 1999 vintage machine at work, with nothing but the built in video card, and it can manage some of the effects, like wobbly windows.  Anything that makes use of hardware acceleration though is quite likely to fail.  So sorry, no raindrops, probably no fire, and I'm not sure what the cube would do...

As for his space requirements, I have a machine running Ubuntu in a 10 gig partition with plenty of space left over.  You can fit the base system into two or three quite easily.  With 55 gig free on his machine I would suggest he install Ubuntu into a 20 gig partition and use the ntfs side for storing the large stuff.  That does, of course, depend on the current content and how permanent it is and how much of a migration he plans to make to Linux.

---

### Post by tototime on 2007-11-29
not a humoungous migration its just experimental at times im tire dof all the crap that comes with windows so i want to be able to do both

---

### Post by Perkins on 2007-12-01
Well, my current personal machine has a 300GB disk.  I use 80 for Linux and the rest in three partitions for windows.  I did it that way because Linux can easily read and write the ntfs partitions, but making Windows read e3fs is something of a pain.  This way I have enough space under Windows to install large games, and can still use the whole disk from Linux.  I'm using less than 20 of the 80 gig on the Linux partition, so I would guess 20 to 30 would work for you quite well.  You should be able to defragment your windows partition and then shrink it down a bit.  The standard Ubuntu CD has the tools to do the shrinking, and will walk you through the process pretty well.  Defragmenting is best done from the Windows side of things.  Micro$oft programs being what they are you should probably run it several times until it stops moving files around.

---

