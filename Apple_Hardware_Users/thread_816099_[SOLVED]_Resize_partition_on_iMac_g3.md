---
title: "[SOLVED] Resize partition on iMac g3"
date: 2008-06-02
forum: Apple Hardware Users
---

### Post by Super TWiT on 2008-06-02
I just recently got an iMac g3 (for $20 at a computer show :)).  This one has 192 mb of ram and a 233 mhz cpu.  I figured that it would be a good candidate for Xubuntu.  However, it already came with OSX 9.2 and I wanted to dual boot the machine.  I need a way to resize the partition on this computer such as gparted.  I have tried the Ubuntu powperpc desktop version, thinking that it would have gparted built in, but, because of video problems the gui never appears.  I really don't want to open up the system, and am looking for a way to do this without plugging the drive in as secondary on my main computer.  (Note to try to start gui, I tried this tutorial [http://ubuntuforums.org/showthread.php?t=405934]("http://ubuntuforums.org/showthread.php?t=405934"),  but I could never find those options in xorg.conf).

---

### Post by Jammy4041 on 2008-06-02
This is great! In fact, i got an Imac G3, slot loading with 128MB RAM (Yikes) and as a matter of fact I did this a few days ago.

What I did was to update my firmware to the latest version, burned a fresh Debian PPC CD (which is very very similar to the Xubuntu Alternate), and then ddisabled journalling.

Then I rebooted my machine. then I pressed C to boot from the Debian CD, then I went through all the processes until it came up with the Partitioner- 

I hit "go back", and then "excecute a shell", then I typed

```
parted print
```

and then I resized my partiton

```

resize MINOR_NUMBER_HERE START_BLOCK_SIZE_FROM_PRINT_OUTPUT NEW_END_BLOCK_SIZE

```

(this should be clear which partition you want to resize
which would look something like this

```

resize 3 128.032 37237.821

```

Where 3 is the number that corresponds to your HFS+ partition, the second number is the position of your Partition [usually in MB- divide this number by 1024 to get it in MB]

And the end size is where you want your partion to now end.

Don't forget to write the changes to disc, or your partitions won't change.

If you want, install Debian in the free space, but I clicked Abort the installation, popped in the Xubuntu 8.04 Alternate CD, and then typed "install", which took me to the Xubuntu Installer. I folowed all the steps up to the partitioner, where there should be an option to install in the free space. i selected that and was as good as home. 

EDIT: This is the iMac model that is tray loading, I presume, so it may have a limit. Be sure to have ALL your partitions within 8GBs. 

EDIT 2: i don't think Mac OS 9 Had journalling.

---

### Post by Super TWiT on 2008-06-02
Thanks for responding.  When I run parted print however, it says Error: Could not stat device print - No such file or directory

---

### Post by Super TWiT on 2008-06-18
I ended up in the end just formatting the whole thing.  I am going to be getting a bigger hard drive, more ram, and installing panther (with Ubuntu of course!) later.  Thanks for your help!

---

### Post by stream303 on 2008-06-18
> **Jammy4041 said:**
> EDIT: This is the iMac model that is tray loading, I presume, so it may have a limit. Be sure to have ALL your partitions within 8GBs.

For those models that have this limitation, it is actually best to keep it at 7gb or so since some manufacturers differ in the way they specify their capacity.  If you partition at exactly 8gb, you run into trouble usually, even though that is the spec.

One option is to put your entire installation at 7gb max, and partition the remaining space as a general purpose ext3 data partition.

Of if you do custom partitioning, (separate /usr /home /var /log etc,) just be sure to keep your root partition  /  near 7gb.

---

### Post by Super TWiT on 2008-06-18
Yes, it is a tray loader.  I have done some research and I believe it is Rev. B.  I have heard they had this limitation and I am a little bit confused.  I don't mean to hijack my own thread, but, does that mean that I need to have OS X 10.3 and Ubuntu within 7 GB and have a separate storage partition, or does that mean that only Ubuntu needs to be within the 7 GB since it is the partition that contains the boot loader.  I have heard that only the startup partition needs to be within this limit, however, I am not sure.  I am not even sure if the partition that contains the boot loader even is the startup partition!

---

### Post by stream303 on 2008-06-19
Well, we're talking 3 OS' here.  It came with Mac-OS9, and if you want to put OSX 10.3 on it, you *must* upgrade the firmware first from the OS9 install running from the hard drive.

DO NOT even put in an OSX disk or OSX utility disk into that machine without first upgrading the firmware.

However, with only 192mb on board, I'm not sure it would be worth it for osx.  But that's another thread. :)

I'm not very good a triple-booting, so I'm not the guy to ask.

All I can say is that either the whole of your Ubuntu installation must not extend beyond about 7gb to play it safe, OR if you custom partition, the boot and root partitions must not extend beyond this either.  After that you can slice and dice it anyway you want.

Personally, I think that Ubuntu or derivative would do much better than OS9, or even OSX on that box, and would be tempted just to dedicate the whole thing to Linux.

YMMV.

---

### Post by cyberdork33 on 2008-06-19
OS X runs OK on G3s just a little slow on bootup :)

---

