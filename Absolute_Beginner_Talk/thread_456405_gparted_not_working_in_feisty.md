---
title: "gparted not working in feisty"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by marbobj on 2007-05-27
I upgraded to 7.04 and instaledl the Gparted partition editor from the synaptic manager.  Everything went well and the Gnome partition editor showed up on the admin list.  However, the only function I can get to work is the New partition function across the header.  All the others stay subdued.

I've highlighted the different partitions, but the only one I get a response one is the "unallocated space."  That's when the "new" partition function will respond, but nothing else.  

I've tried different versions, but nothing works.

When I installed Ubuntu (a couple of times) the partition editor worked fine.

Need help, 

Thanks in advance,

Bob

---

### Post by indytim on 2007-05-27
My recommendation is to download and burn the ISO to a CD for GParted LIve at

[http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")

You may be running into a problem with trying to effect changes to mounted partitions (just a guess).

IndyTim

---

### Post by marbobj on 2007-05-27
Tim:

I _was_ trying to change a mounted partition.  I take it that isn't the way a newbe can get it work?  If I unmount it, and it shows that as an option, how do I get it mounted back after resizing it?

Thanks,

Bob

---

### Post by indytim on 2007-05-28
Bob,

As far as unmounting, at the terminal mode:

```
$ sudo umount /dev/sda4
```

Assumes the partition that you want to modify via GParted is sda4 (insert the appropriate partition id in place of sda4).

Go back to GParted and you should be able to re-size the partition that you just unmounted.

To remount the partition after you have finished doing the GParted thinger:
```
$ sudo mount /dev/sda4 /media/sda4
```

If you are attempting to modify your working ops partition, the above will not work.  Again, I would recommend getting and using a copy of GParted Live. Going this route, all of you partitions are open to modification.  Make sure you backup all critical files etc before doing any serious partition work as things can go "south" on you.

Hope this addresses your situation.

IndyTim

---

### Post by ron999 on 2007-05-28
That's good advice from indytim.
But you don't need to make a GParted disc.
You can use the Ubuntu Live CD.
Boot from it and look in System > Administration > Gnome Partition Editor.
It will work while you're running from CD, hard drives aren't mounted.

---

### Post by ramjet_1953 on 2007-05-28
By far the best way is to either use the LiveCD or download the stand-alone version of GParted.

Like has been said before, you can't partition a mounted drive.

It's like trying to change a tyre on a car while it is being driven!

Regards,
Roger :cool:

---

### Post by marbobj on 2007-05-28
Thanks a lot to all of you,

really appreciate the help,

Bob

---

