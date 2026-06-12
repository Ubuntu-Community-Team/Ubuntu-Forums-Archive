---
title: "Merge two partitions"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Jugney on 2008-01-12
Hi everyone,

I installed Gutsy originally as a dual boot with Vista, but have since deleted Vista. Now I'd like to merge the partition Vista was on so that Gutsy has all that space. I have GParted but can't seem to do it. Can anyone help?

Here is a screenshot of gparted. Ubuntu is on sda6. sda2 is HP's Windows recovery partition, which I was thinking to leave on in case I ever need windows again.

---

### Post by taurus on 2008-01-12
If you want to merge partitions, you have to use gparted from the LiveCD or GParted LiveCD.  You cannot merge a partition while you are using it.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by Rocket2DMn on 2008-01-12
Once you are ien the LiveCD with gparted, I think you will have to delete the ntfs partition which will then allow you to resize your root partition to use the now freed space.

---

### Post by Jugney on 2008-01-12
Thank you!

---

### Post by Rocket2DMn on 2008-01-12
Yeah, have a look here - [https://help.ubuntu.com/community/HowtoPartition#head-f2515acc4fa3a5b463d5a79bb834ded1f3daae4e](https://help.ubuntu.com/community/HowtoPartition#head-f2515acc4fa3a5b463d5a79bb834ded1f3daae4e)
You will do that from the LiveCD to the partition you are resizing (remember it must be unmounted and you should always back up your data before messing with partitions).

---

### Post by Jugney on 2008-01-12
So I'm still struggling here. I resized sda4 to use the unallocated space. But now sda6 (ubuntu) is just existing side by side with the unallocated space within sda4 and I still can't expand the ubuntu partition to use that space. I unmounted sda4 but it still isn't working

Below is a screenshot so you can see how my layout is now.

---

### Post by dcstar on 2008-01-12
> **Jugney said:**
> So I'm still struggling here. I resized sda4 to use the unallocated space. But now sda6 (ubuntu) is just existing side by side with the unallocated space within sda4 and I still can't expand the ubuntu partition to use that space. I unmounted sda4 but it still isn't working

Below is a screenshot so you can see how my layout is now.

When you boot the Live CD and run Gparted, you will have to turn off the Swap space in your list (you will see the little "lock" icon next to it, right-click the partition), once you do that you will be able to expand the whole /dev/sda4 partition.

You also have two swap partitions in your list, this is a waste of space, delete one of them.

I would actually (highly) recommend that you use the spare space to create a separate /home partition, then you will not lose (or have to back up) any of your personal data if you upgrade/install a new Ubuntu version (which will wipe out your existing system).

There are detailed instructions in the forum about creating a separate /home partition.

---

### Post by Jugney on 2008-01-12
Hi,

Having a separate partition for the /home/ folder is a good idea - thank you for that suggestion.

So maybe I will just resize the existing partitions and give most of the free space for /home/. 

But here is the issue now:

After a few failed tries, I was able to get gparted to successfully format the unallocaetd space, to ext3. Upon re-opening Gparted, I get 

The kernel is unable to re-read the partiontales on the following devices: - /dev/sda
Because of this you will only have limited access to these devices. Unmount all mounted partitions on a device to get full access. 

But everything is unmounted.

Help?

---

### Post by dcstar on 2008-01-12
> **Jugney said:**
> 
...........
The kernel is unable to re-read the partiontales on the following devices: - /dev/sda
Because of this you will only have limited access to these devices. Unmount all mounted partitions on a device to get full access. 

But everything is unmounted.

Help?

That seems to indicate that the partition table is corrupted, that is **not** a good sign.

Boot off the Live CD and try Gparted again, and then open a terminal and:
```
sudo cfdisk
```

If there are still errors, you may have to search out a repair CD on the Internet to try and fix things.

---

