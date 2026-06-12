---
title: "editing current partitions?"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by eilu on 2006-10-31
After [this thread]("http://ubuntuforums.org/showthread.php?t=289308"), I just realized my current partitions are all wrong... this is what the current HD looks like:

[IMG]http://img250.imageshack.us/img250/3294/currentcr9.png[/IMG]

As you can see, /home is much too small while / is way to big. I want to modify this so that / shrinks down to 8GB, then append the freed space to /home (it's a 40GB HD; swap is ~512MB)

Using gparted on the live CD, I got as far as shrinking / ... then I'm stumped, as I have no idea how I'm going to "move" the freed space (which will be at the end of the drive) in order to add it to /home (which is in the middle) :confused: 

Can someone walk me through this? I wouldn't want to repeat the last mess i got into when I first moved /home to its own partition.

---

### Post by caravel on 2006-10-31
I see what you mean.  You need to achive a contiguous partition and I'm not sure how you can go about it... I'm sure I've read somewhere about gparted moving partitions, but I'm not sure about that.

You might be better off resintalling... :-k

---

### Post by jaytek13 on 2006-10-31
Or you could always just create a new partition on the extra space and mount it in your home directory. A reinstall might be cleaner, though. Make sure to check the "erase entire disk" option.

---

### Post by Bartender on 2006-10-31
Take a look at aysiu's [PartImage]("http://www.psychocats.net/ubuntu/partimage") webpage.  Couldn't you copy your "/" data and drop it into "home" or some external storage, then delete the "/" partition and resize the "home" partition, then rename, etc.?
Might be worth trying, if for no other reason than the learning experience.  If it didn't work you could always reformat.

---

### Post by CatKiller on 2006-10-31
As I understand it, the version of GParted on the live cd is not able to move the start of an ext3 partition, but the version on the [GParted live cd]("http://gparted.sourceforge.net/livecd.php"), which is newer, can.

---

### Post by eilu on 2006-10-31
I think I'll try the gparted live CD first, it seems to be the least drastic option.

Maybe I can move /home back with / then re-partition and re-move? hmmm...:-k

---

### Post by CatKiller on 2006-10-31
> **eilu said:**
> Maybe I can move /home back with / then re-partition and re-move? hmmm...:-k

I wouldn't. If you change the partition number of your / partition, then you'll probably have to reconfigure GRUB. I'm sure it's quite straight-forward and all, but it's one more thing to go wrong. I'd just do what you'd planned before: Make your / partition smaller, move it to the right, and then expand your /home partition.

Don't forget to back up anything important, just in case.

---

### Post by eilu on 2006-11-01
Okay, I'll try the gparted live CD then (but it'll have to wait until I go to school where there's broadband for me to download it). 

If all else fails I'll backup, wipe things clean and re-install. (hope things don't come to that... [-o< )

---

### Post by eilu on 2006-11-03
just wanted to say gparted livwe cd worked like a charm, and thanks again.

---

### Post by CatKiller on 2006-11-03
Excellent. Glad to hear it. Thanks for letting us know.

---

