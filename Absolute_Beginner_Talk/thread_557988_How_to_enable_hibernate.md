---
title: "How to enable hibernate?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by sixsidepentagon on 2007-09-23
I've just downloaded Feisty using wubi, then switched it to a partition using LVPM. But in the exit button, it doesn't show me a hibernate option. How do I enable it?

Thanks in advance,
Sixside

---

### Post by por100pre1 on 2007-09-23
Do you have a swap partition? Lets see:

```
free -m
```

Sorry for the delay... :-k

---

### Post by sixsidepentagon on 2007-09-23
> **por100pre1 said:**
> Do you have a swap partition? Lets see:

```
free -m
```

Sorry for the delay... :-k

No need to be sorry! 

free -m:

total       used       free     shared    buffers     cached
Mem:           503        390        113          0         10        204
-/+ buffers/cache:        175        327
Swap:          384          0        384

---

### Post by por100pre1 on 2007-09-23
```
gconf-editor
```

and set /apps/gnome-power-manager/can_hibernate to true

---

### Post by FuturePilot on 2007-09-23
I'm not sure, but I think you don't have enough swap.

---

### Post by por100pre1 on 2007-09-23
> **FuturePilot said:**
> I'm not sure, but I think you don't have enough swap.

Yes, that can be the cause... :-k

---

### Post by sixsidepentagon on 2007-09-23
Thanks for all the responses guys!

I tried that gconf-editor, it said it wasn't writable (I did as sudo as well).

Is there a way to increase my swap file size? Perhaps resize my main partition and reformat it with the swap?

---

### Post by por100pre1 on 2007-09-23
Yes, use the LiveCD (be sure to unmount the partitions). The [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") can do the job too.

---

### Post by sixsidepentagon on 2007-09-23
Sounds good, a couple of questions though:
(1) How big should I make it?
(2) What's this unmount business? When I resized my Windows partition, I just hit the resize function. What would happen if I didn't?

---

### Post by por100pre1 on 2007-09-23
1. Give it 1GB if space is not a problem.
2. In GParted right-click each partition and unmount. If mount is the available option then it is unmounted, it is ok.

---

### Post by Delkster on 2007-09-23
> **sixsidepentagon said:**
> (1) How big should I make it?
Probably larger than your RAM if you want to be relatively sure you can hibernate. Judging by the output of the "free" command, you seem to have ~512 MiB of RAM. In that case I'd make swap maybe something between 512 and 1024, probably the latter unless you're low on disk space.

An old rule of thumb is to make it twice the size of your RAM, but generally for use you don't need that much nowadays -- if you use so much memory that you need that much swap, you really need more RAM anyway because a desktop machine in general use would be slowed down to a crawl long before running out of a couple of gigabytes of swap.

> (2) What's this unmount business? When I resized my Windows partition, I just hit the resize function. What would happen if I didn't?

Short answer: It means making sure that the partition is not in use when it's being resized.

Long answer:
Well, I began to write this, but realized that you probably aren't interested in the details, and that I'm getting too tired (and too lazy) to do it properly. If you want the long answer, please ask.

However, I believe [the Wikipedia article on mounting](http://en.wikipedia.org/wiki/Mount_%28computing%29) should suffice. It's probably better written than my babble anyway.


Edit:
Oops, I forgot to address this part:
> What would happen if I didn't?
The partition resizing tool would probably just refuse to perform the operation.

---

### Post by sixsidepentagon on 2007-09-24
This sounds good, a gig of swap will be fine. 
Thanks for explaining this mounting stuff.
So I tried it, clicked unmount in gparted (of a Linux Mint liveCD) for both the linux swap partition and the ubuntu partition, then resized the ubuntu partition. But when I clicked apply, all it said was that there was an error because my ubuntu partition was mounted. Yet I definitely told it to unmount. Am I forgetting a step here?

Plus, i couldn't figure out how to merge the unallocated space with the swap partition. Am I supposed to do that after I resize a parttion first, to get the unallocated space?

If you have time, a step by step procedure would be great, by the way.

Thanks for all the help!
Sixside

---

### Post by Delkster on 2007-09-25
> **sixsidepentagon said:**
> So I tried it, clicked unmount in gparted (of a Linux Mint liveCD) for both the linux swap partition and the ubuntu partition, then resized the ubuntu partition. But when I clicked apply, all it said was that there was an error because my ubuntu partition was mounted. Yet I definitely told it to unmount. Am I forgetting a step here?

At what point did you get that error? At least the Ubuntu 7.04 Desktop CD seems to suffer from a problem where it, after a partition has been resized, detects that partition as new (or something like that) and automatically mounts it. The operation itself is completed succesfully but you still get an error message because after any operations performed GParted wants to run a file system consistency check on the partition (which is a good thing) and that fails because the partition was just automatically mounted.

If you get the error before the actual operation has taken place, make sure that there's no lock symbol next to the partition you want to resize. A lock icon means that the partition is in use (either mounted or otherwise). Unmounting can fail if any files on that filesystem are open, for example if you have the file browser pointed to one of the folders on that partition or if you have a file from that partition open in an application. I suppose GParted should inform you about any problems with unmounting, though.

> Plus, i couldn't figure out how to merge the unallocated space with the swap partition. Am I supposed to do that after I resize a parttion first, to get the unallocated space?
Remember that the space needs to be contiguous in order to be used as a single partition, so in order to grow the swap partition to fill the new space, the unallocated space must be right next to the swap partition with no other partitions in between.

Once you have the unallocated space available, you can either grow the existing partition to fill the space, or you can delete the partition and create a new one that fills the entire space. Even the latter way is quite safe since there should be no permanent data stored on the swap partition anyway, so the partition is pretty much disposable (unless you've hibernated another Linux session to it or something, but I don't suppose that's the case).

Note that the swap partition must also not be in use if you want to perform any operations on it in GParted. The Ubuntu Desktop CD automatically uses an existing Linux swap space if it detects a free one on the hard disk, so it may very well be in use. Check for the lock symbol, and if necessary, right-click on the swap partition and select "swapoff" in the context menu.

Furthermore, if you opt for growing the partition rather than deleting it and creating a new larger one, you can probably only grow it at the end. If you need to grow it to fill up free space that is in front of it on the disk, you probably need to first move the partition to the beginning of the space and then grow it from the end to fill the free space that was moved from the front of the disk to the end.

---

### Post by sixsidepentagon on 2007-09-29
So I grew my swap partition to 1.06 gigs.

I still can't get the hibernate to work through gconf.

And now I can't get to my windows partition. All it says in gparted is the size of the partition. The used and free space information is missing, and a little warning icon is next to it. I can still used Windows though. Do I have to mount the partition again? How do I do that, there's no option for it in gParted.

What do I do?

---

### Post by sixsidepentagon on 2007-09-30
I just went back into gparted and found that the error for my windows partition was that it was unable to read the information on it. Then it asked if I installed the correct plugins.
I need to access the files on my windows partition, I save most of my files there.
Thanks in advance,
Sixside

---

