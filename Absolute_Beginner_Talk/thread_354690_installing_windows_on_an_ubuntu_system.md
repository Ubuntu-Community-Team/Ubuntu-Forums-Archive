---
title: "installing windows on an ubuntu system"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by firstmilkman on 2007-02-06
I recently reformatted my laptop with ubuntu. ubuntu is the best, i absolutely love it, but the problem is, i'm looking to install windows on a seperate partition so i can run it in a virtual machine (vm is alredy set up). now when windows setup asks which partition, it shows me 2 partitions:

28616 mb disk 0 at id 0 on bus 0 on atapi [mbr]

C:  Partition1 [unknown]     27416 mb (27415 mb free)
E:  Partition2 [unknown]      1200mb (1200mb free)

now my HD is only about 28.5 gb, and i want to be able to have plenty of space for ubuntu, so i'm not limited in what programs I install and stuff. also I do not want ubuntu deleted or messed with watsoever. now i kno both of them say they have all the space free (sept the 1mb of c:), but like i said I want to be sure, by formattign it for windows, that i'm not taking away from the space i can use on ubuntu. i'll only need like 5gb for ubuntu, how should I go about doing this.

help is GREATLY appreciated. i'm sitting here waiting for a response with the windows setup alredy loaded (i'm on my desktop right next to my laptop)

plz respond asap

thanx

---

### Post by firstmilkman on 2007-02-06
also I can't install windows on those partitions (hence the [unknown]). maybe ubuntu is partitioned on d?
again, help is greatly appreciated.

---

### Post by zvacet on 2007-02-06
If you want run windows in virtual machine you don´t need separate partition fot that.Just install vmserver on your ubuntu.After that you can install windows in vmserver,and that is it.Sorry if I missunderstend your needs.

---

### Post by renzokuken on 2007-02-06
ok, those 2 partitions are ubuntu's. one is the root filesystem, the other is your swap memory.

did you boot from the xp cd to install it? cos that isnt how vm works.

running XP in a virtual machine does not require a seperate partition. all it requires is a folder in your ubuntu home directory.

---

### Post by Sqwishy on 2007-02-06
Well you need more partitions, i have 4.
One for Ubuntu (probobly mounted in /)
Ubuntu Swap (size of your ram)
Boot (100mb?) (mounted in /boot)
Windowz

Right there you have 2 so im' guessing it's ubuntu and the swap, you'll need to install windows and then your bootloader grub, if you install grub first it won't do much good because windows will overwrite it. REMEMBER windows' partition must be the 1st one otherwise it will bork because it's stupid. :P i honestly can't remember the command for partitioning, i think you run 'sudo gparted' Be VERY carefull you don't mess things up too much.

EDIT: um listen to those up there because i don't know anything about vm ware and my answer probobly doesn't help with your sittuation.

---

### Post by firstmilkman on 2007-02-06
so it can create a vm from the xp install disc or what? cuz I have the install disc, and just want to run the windows operating system in a window while in ubuntu using vmware.

if you could tell me what I need to do, that would be great

---

### Post by renzokuken on 2007-02-06
ok, sqwishy has given a good answer if you wanted to "dual boot", which is not what you are after.

there is a howto thread about windows in vmware i will go find for you now

---

### Post by firstmilkman on 2007-02-06
thank you so much.

---

### Post by renzokuken on 2007-02-06
> **firstmilkman said:**
> so it can create a vm from the xp install disc or what? cuz I have the install disc, and just want to run the windows operating system in a window while in ubuntu using vmware.

if you could tell me what I need to do, that would be great

think of it this way, vmware works by installing XP to a folder in your home directory in ubuntu. you then run xp by opening the vmware player and can have xp running in a window on your ubuntu desktop, as shown here

[http://nateaune.com/wp-content/uploads/2006/06/vmware-screenshot.png](http://nateaune.com/wp-content/uploads/2006/06/vmware-screenshot.png)

---

### Post by firstmilkman on 2007-02-06
o ok. if it's not too difficult i'll get it myself, but if there are some more advanced parts to doing it a guide would be appreciated. if it isnt difficult, then no need to reply.

thanx for all the help

---

### Post by renzokuken on 2007-02-06
ok, here ya go, this is how i did it...........it looks complicated but its really not, just type the commands you see in the terminal and follow the instructions.

EDIT, sorry, forgot to add the link [http://www.ubuntuforums.org/showthread.php?t=183209&highlight=howto+xp+vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=howto+xp+vmware)

any questions just post here or pm me

---

### Post by lamego on 2007-02-06
If you want to install windows on vmware you do not need to create a dedicated partition, inside vmware partitions can be created just as normal file on your host system.

---

### Post by lyceum on 2007-02-06
This might help...

[http://ubuntuforums.org/showthread.php?t=183209&highlight=VMWare](http://ubuntuforums.org/showthread.php?t=183209&highlight=VMWare)

---

### Post by renzokuken on 2007-02-06
ok, so i just read through the thread i linked to above and it appears that may be outdated and you now have to pay for vmware server.

here is an alternative "free" method using vmware player (not server)

EDIT: bugger, forgot the link again [http://www.ubuntuforums.org/showthread.php?t=84275](http://www.ubuntuforums.org/showthread.php?t=84275)

---

### Post by firstmilkman on 2007-02-06
any guides on doing it with vmware workstation (I have it and it's installed)

---

### Post by xpod on 2007-02-06
If you want an easy way to set up a virtual machine i suggest you have a look at VirtualBox.

I`ve not tried any of the other methods but from what i`ve read of those who have VirtualBox  does a much better job of it apparently.
Plus it was easy enough for a novice like myself and thats what counted in my book:)

EDIT:[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by renzokuken on 2007-02-06
impressive xpod, i never heard about it before. i'm playing with it now.

looks good firstmilkman, and straight forward to use.

---

