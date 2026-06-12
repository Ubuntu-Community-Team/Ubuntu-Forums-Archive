---
title: "Need Apple_Bootloader help"
date: 2007-04-11
forum: Apple PPC Users
---

### Post by mikeweezer on 2007-04-11
Hi,


   I am fairly new to Ubuntu, and this is the 3rd attempt at Ubuntu.  I've made partitions on my pre-existing OSX HD, and I have 1 more hurdle....


I have a Swap partition, an HD space, but it keeps kicking an error that "Apple_Bootloader partition not specified".  What?


I've tried alot of different routes with no luck.  Can anyone offer assistance?  I'm pretty new to this, so please be overly specific.

Thanks!

---

### Post by linear on 2007-04-11
Take the path of least resistance. Don't try to create your own formatted partitions. Instead, create a chunk of unallocated (free) space for Ubuntu, and let the installer do the rest.

---

### Post by SycloneMedia on 2007-04-11
It took me a couple days of online research and about 7 complete wipe/reinstalls to get my Powerbook to dual boot OSX and Ubuntu *with manual partitioning.* Don't give up...

If you are not willing to, or can't erase your hard drive and re-partition it, then letting Ubuntu install itself with the available freespace might be easier.

**If you CAN erase and start from scratch, here's what you need to do:**

**1.** Don't forget to offload and back up all the data that you want to keep.

**2. **Boot up from your OSX System CD (holding down C) at bootup, and open up Disk Utility, select your hard drive and the 'partition' tab.

-You can divy up your space however you want, but you need at least 4 partitions. (bootstrap, linux swap, linux system, osx system) You can add any other partitions you need depending on your hd size. With the exception of the bootstrap partition, make ALL the others in HFS+ (extended). More details below. Don't forget to write down how many partitions and what sizes they are... try to stagger the sizes a little because you'll need a way to identify the partitions later WITHOUT relying on the names.

-The very first partition MUST be the bootstrap and it can be a very small partition. Now you'll find posts that say make it "100 MB" or so, but I just couldn't get Disk Utility to go that small and actually do it. So I made it a 1 GB partition. IMPORTANT: THE KEY IS TO MAKE THIS BOOTSTRAP PARTITION "HFS" (standard), NOT "HFS+" (extended).

-The rest of the partitions should be HFS+. You'll change the Linux partitions later.

**3. **Install OSX onto the partition you designated for it. You must install OSX first, Ubuntu second. I've found that if you install or reinstall OSX after Ubuntu is already on it, it will take over the bootstrap and default boot into only OSX and designate itself as the startup partition. Not what you want.

**4.** Boot up with Ubuntu CD, and before you start the Ubuntu install, we need to change some things...

-Open up the GParted (gnome partition editor) from the System menu. The layout of the partitions WILL look different, don't worry. You need to visually identify which partition is which by the available sizes, etc... Shouldn't be too hard if you wrote down the partition sizes you created. The names will not show up.

-Select the bootstrap partition you created earlier. The ONLY thing we need to do here is set a "boot" flag. You'll see the appropriate menu to assign flags, and select "boot". Apply the changes (click apply). That's it, your bootstrap should be ready for action.

-Now select the rest of your linux partitions (swap, system, etc) and choose to reformat them to "ext3" format using the menus. Also, go ahead and assign a flag for your linux swap partition as "swap" using the same menus as for the bootstrap. Apply changes. We're ready to roll.

**5.** Install Ubuntu with manual partitioning... do the normal question and answer things and when it opens up GParted again, don't change or do anything as we've already set it up... just continue to that last step. Here it should automatically have selected your swap partition as the designated swap, and make sure the linux system partiiton you created is designated as the main install partition. They should both be checked off for reformat, no problem.

Now when you hit continue, or install or whatever, it should go ahead and have no problems with the bootstrap and you'll be good to go...

When you start up your computer, it should give you the option to boot into either, and the default will be linux (if neither is selected). There's good threads around here on how to change that to default into osx if you need.

The only problems I've had is with occassional kernel panics during bootup into both, and that could be because I have bad ram, or something else.

Happy Dualing!
:guitar:

---

### Post by cogitordi on 2007-06-25
CycloneMedia, I know you had much frustration in learning how to do what you have described, but you saved ~me~ many hours and I want to thank you.

I think you should convert this post into a Tutorial.

I can help with one thing: you can use OS X Disk Utility to create a small partition by typing "0.5" in the text box where you specify the size. "GB" will then change to "MB". Someone overthought the usability. ;^)

---

### Post by 0graham0 on 2007-07-03
thank you!

---

### Post by joninkrakow on 2007-07-06
Hi-

Just last night I installed Ubuntu, and I believe you can do what you want to do from the graphical LiveCD install. At the partition part, choose manual, and in the list that shows up, create a small partition at the first--if it doesn't already exist--which I probably does.

Then, choose "Edit" and under the "Mount point" setting (I believe that's what it's called" choose Apple Bootloader from the list. I think I had to first set the mount point as "/" close it, and reopen the Edit window to get it to show up, but I was able, using only the graphical tools, to get both YDL and Ubuntu onto my hard drive. BTW, I bothered with the manual settings, because  I wanted both to share the same swap partition, and Ubuntu kept insisting on creating its own instead of using the swap that was already partitioned as swap. 

-Jon

---

