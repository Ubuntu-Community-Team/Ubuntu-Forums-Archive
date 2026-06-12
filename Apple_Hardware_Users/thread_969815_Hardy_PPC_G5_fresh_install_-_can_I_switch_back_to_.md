---
title: "Hardy /PPC G5 fresh install - can I switch back to OSX and how ?"
date: 2008-11-03
forum: Apple Hardware Users
---

### Post by roybatty on 2008-11-03
hallo all :

Firstly I am green to Linux and dual boot ( Hopefully this is what I did ) 
so be ginger 

Fresh install of Hardy 

I did choose secong option on install NOT to use entire disc - and OS Tiger was already installed 

How do I switch back to OSX ?
Is possible to run both side by side 

cheers in advance:

---

### Post by tiresia on 2008-11-03
At the yaboot prompt, you shoud get the option to choose MacOSX, Linux or CD.
If you press X, you get to OSX.

If for any reason, yaboot (it is the bootloader) doesn't show MACOSX, press at starting the opt-Key. There you will see, which system are still on your computer

---

### Post by roybatty on 2008-11-03
Hallo Tiresia:

ok - went to boot and held option key upon startup

showed one HD with a tiny penguin lower right hand 
a smaller box with a turn around /return arrow  and an arrow pointing to right on right 
when I typed in x in the Yaboot -  said did not exist - just hit return and booted Ubuntu 

will try again and see what go's 

cheers

---

### Post by tiresia on 2008-11-03
I'm afraid that you deleted MacOSX...

---

### Post by roybatty on 2008-11-03
Hallo Again Tiresia:

upon yaboot - no such file or directory 
only 2 options - i or c 

did this install remove my OS X tiger and all my info ?

Cheers :

---

### Post by Frak on 2008-11-03
Press and hold Option on startup after the gong sound. This will bring up the startup disk chooser.

If there are no disks there, or only a Linux HD, you have deleted OS X.

---

### Post by roybatty on 2008-11-03
Hallo tiresia

Cheers for the reply :

Ok - this maybe off your scope -  what about all the information I had on this hard drive before I installed Hardy ?  will that also disappear ?

I will like to delete Hardy and reinstall OSX then start over -  is this possible ?

Cheers:

---

### Post by tiresia on 2008-11-03
> **roybatty said:**
> 

did this install remove my OS X tiger and all my info ?


Yes, I hope you didn't have important data. You should make always a backup, before doing system's change. 
If you want to make a dual-boot, read some docs. I can give some links tomorrow, if you are interested.

---

### Post by roybatty on 2008-11-03
Hallo Tiresia /Frak:

Ok -  i did read - so I though - about a dual boot - guess not as simple as to let the disc run it and choose the option 

I will read some docs on the dual boot - no worries -  I just started this machine with a new HD a few weeks back and have much of the info stored on a backup -  half points for me eh 

cheers/ Dank:

---

### Post by chengzi86 on 2008-11-03
**[Plastic valve](http://www.corrosion-resistant-valves.com)** special for controlling the corrosive media which features low weight, nonpoisonous and no pollution. It has wide temperature adaption, high mechanical stress and can take place of many kinds of expensive rare metal. It is high economic benefit. plastic valve [www.corrosion-resistant-valves.com](www.corrosion-resistant-valves.com)

---

### Post by Henry Higgins on 2008-11-03
The essential thing: before you re-install Mac OSX, partition the hard drive. Decide how much space you want to give to OSX and how much to Ubuntu, then create 2 partitions on the drive (use the disk utility on the OSX installation disk). The OSX partition should be "Mac OS Extended (journaled)" and the Ubuntu one "Free Space".

Now re-install OSX to the newly created partition.

Now install Ubuntu, choosing the option to use the largest available free space.

---

### Post by roybatty on 2008-11-03
Cheers Henry Higgins 
for the reply 

indeed this did before the prior install - actually had 3 partitions - and the rest of the story is moot 

just dunno now if I should continue, try an install of Hardy Heron - maybe 8.10 or try Fiesty Fawn first and just upgrade software later 

cheer

---

### Post by mkvnmtr on 2008-11-04
Henry Higgins has got it right. Form your partition for Mac os from the disk. Install the Mac os. Then when you go to install Ubuntu choose to install in the largest free space.
It might be best to go with 8.04. It is a long term support and has been out long enough to be pretty easy to install. You might have more problems with 8.10.
Don't feel bad I think I reinstalled My Mac os 4 or 5 times while making the change. I reinstalled Ubuntu at least 15 times before I got it the way I wanted and quit messing it up adding software I didn't need or understand. But it was fun.

---

