---
title: "Try to install kubuntu on Macs; It won't detect OSX"
date: 2009-06-07
forum: Apple Hardware Users
---

### Post by ktritty on 2009-06-07
I am trying to install kubuntu side-by-side on my Macintosh computers at home.

The problem I am having is that the kubuntu installer will not detect that I already have OSX on my computer, so the only partitioning options are "use entire disk", "use largest free space", or "partition manually"

It does not have the "install side-by-side with windows" option that I was hoping for and have seen with windows PCs I have installed ubuntu on (but with "OSX" in place of "windows" of course).

Choice 1 is unacceptable, as I do not want to erase OSX
Choice 2 is unacceptable, since there is only a tiny amount of free space, and the disk utility in the installer won't let me resize the OSX partition (it comes up with an error message that my disk format is not supported for resize).  AND Mac OSX Disk utility will not let me resize nor partition/split/edit my Macintosh HD volume (neither when booted in OSX, obviously, nor when running OSX Disk Utility from a Bootable CD-Rom with Macintosh HD unmounted)
Choice 3 is unacceptable, because, as mentioned, it won't let me make the changes to a disk with that type of file system.

I am hoping that you might be able to help me figure out how to get the kubuntu installer to work, without annihilating my OSX installation.

Thanks!!

---

### Post by tattrat on 2009-06-07
Are you running Tiger or leopard? Do you have a windows partition already?

If you are running Leopard, you can resize your OS X partition using disk utility. If I remember rightly, if you are running tiger, you can only do this destructively.

Either way, you need to create the partiotion first (i.e. from Mac OS or from Mac OS disc) and then boot up the Kubuntu disc. Then you need to select 'partition manually' and choose to install in dev/sda3, and opt to repartition.

In the sixth page of the kubuntu installation you MUST select advanced and make sure you install grub in dev/sda3, to avoid messing up the whole system.

---

### Post by ktritty on 2009-06-07
Let's start with my iMac first (runs TIGER), since that is my secondary computer at home, and I have moved all of my essentials to my MacBook for now.

Before your reply, I figured out how to resize the Macintosh HD partition to leave myself some free space (about 30GB), after which I had to fully reinstall Tiger, as you indicated.

After Tiger was reinstalled,

I was able to select "install kubuntu in largest free space" and I let it do its thing.  (I did not manually specify to install GRUB on the kubuntu install partition).  Everything worked fine, except now when I reboot, it always just starts Tiger, I can't boot kubuntu.  (I think that is why I should've put GRUB on there?  I still don't know what GRUB is, but I can guess the G is related to GNU and B for booting?

That aside, is there a way I can fix this installation without destroying either of the OS's?  I am fairly sure that Tiger and kubuntu are successfully side-by-side on the hard drive in neighboring partitions, I just need to fix the install so I have a boot menu at startup.

Note that I can run KDE from the install disk by quitting the install.  I can run Bash, and I see sda1-sda4 in /dev/ directory.  I'm thinking there might be some hope here.

I am having trouble understanding the manpages for "mount".  A good start may be to help me understand how to mount sda3 from Bash, that way I can explore it and maybe run an installer for GRUB?

Thanks

---

### Post by ktritty on 2009-06-07
Okay, I think Boot Camp may have bailed me out.

I thought I would just try holding "alt" when the iMac boots.  It comes up with "Macintosh HD" and "Windows" as options.  I used to have XP on this machine, so I thought this would be a dead-end.  But I tried booting from "Windows" and, you guessed it, kubuntu sucessfully boots.  Slowly, indeed, but it boots.

I will now take a couple of days to get settled in, and then I will try to put kubuntu on my MacBook (Leopard).  Hopefully I can resize Macintosh HD without destroying Leopard as you say.

[SOLVED] for now.

Thanks!

---

### Post by tattrat on 2009-06-07
Try installing rEFIt it gives you a nice boot menu.

[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

---

### Post by ktritty on 2009-06-08
Thanks, rEFIt is working smoothly to get the system started.  Now I just need to make it so I can shut down kubuntu smoothly (hangs about 1/3 of the time).  Issue for another thread.

[SOLVED!]

---

