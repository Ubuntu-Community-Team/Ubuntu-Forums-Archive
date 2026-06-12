---
title: "Warning: Leopard won't like your triple boot"
date: 2007-10-25
forum: Apple Intel Users
---

### Post by xIke on 2007-10-25
I've just tried to upgrade to Leopard, and it didn't like my OS X partition.  It said it would have to reformat it in order to install.  I'm assuming that doing so will kill refit (which can just be installed again), but not harm anything else.  I have to have my triple boot right now so I won't have a chance to try it again until Sunday or so.  Just wanted to warn anyone planning to do this upgrade.

Feel free to use this thread to discuss your successes/failures with Leopard/Ubuntu.

---

### Post by cyberdork33 on 2007-10-25
I have already used Leopard in this scenario, it works fine. It will likely remove rEFIt, but that is an easy reinstall.

---

### Post by xIke on 2007-10-25
Ok, great.  I just need some time to backup any differences between my laptop and tower before reformatting.

---

### Post by ethien on 2007-12-30
I'm having troubles setting up a triple boot Leopard/Gutsy/XP.

I've made different attempts using other tutorials, but always had problems, mostly Windows not booting after installing Ubuntu.

I am now using this tutorial ([http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)), and although it is for Tiger (the diskutil "Linux" command doesn't work in Leopard), I still managed to format in Target Mode from another Mac running Tiger.

I've got all partitions looking ok with "diskutil list", both Linux and Windows ones called "Microsoft Basic Data", which I understand to be correct at this point.

I installed Windows OK.

The rest of the instructions in the link provided above do not include Ubuntu and its graphical installer, and advise the use of LILO. I have read somewhere else that LILO wasn't required and GRUB would do.


So to my questions:

1. being new to Linux, I would like to know exactly what to do when I get to the partitioner, especially with respect to the mount point. I assumed that I had to select root ("/"), but is that correct? Absolutely any help there would be greatly appreciated.

2. Do I then need to install and configure LILO?


Thanks a lot in advance, I have pulled an all-nighter on this one, as my 3 yr-old would not let me do this during the day....

---

### Post by ethien on 2007-12-30
got it right, but not sure how...

I could not wait for a reply, so went ahead with Ubuntu install, figured what the hell do i need Windows for anyway? If I hose it once more, I'll dump Windows for a Ubuntu/OSX setup.

So in the partitioner I did the same I'd done before, manually partitioning, filesystem ext3 and root "/". Not forgetting the Bootloader in /dev/sda3 instead of (hd0). Everything I'd done before, but this time for some reason, it worked.

I guess I'm so tired (still haven't slept) I can't remember how many times and how I've tried to install today   i¬/

Anyhow, to sum up if someone else tries:

YOU NEED ANOTHER MAC RUNNING TIGER FOR THIS.

1. Fresh install Leopard (or use current install if no BootCamp has been installed yet)
2. Install rEFIt
3. Re-boot computer as firewire drive. (as in holding "T")
4. in Terminal type "diskutil list" and identify the drive of the target computer. It should be something like "disk1s2", or "disk2s2" if like me you have an external HD.
5. run the partitioning command (see my link for complete syntaxe) MAKE SURE YOU GET THE DRIVE CORRECTLY OR YOU'LL PARTITION THE WRONG DRIVE!!! Run "diskutil list" again and you should now have 4 partitions (1. EFI, 2. Apple_HFS, 3. Microsoft Basic Data, 4. Microsoft Basic Data) 
6. Install Windows (pop in the cd, and select Windows from rEFIt menu, when Windows Setup asks you, install to "C:")
7. Install bootcamp drivers (from Leopard DVD) in Windows
8. Start from Ubuntu Live CD, and launch Installation
9. At Partitioner select the correct partition, click Edit and select "ext3" and "/" (you might have to do this in two times, select ext3 first, click OK, then Edit again and "/")
10. last but not least, when you see an "Advanced" option, click it and change the bootloader to whatever the drive you're installing Ubuntu to is (if you did exactly what I've done, it should be /dev/sda3)

---

### Post by p0rtlandcubsfan on 2007-12-31
I have had success with gutsy on my 2nd gen macbook, down to right-clicking and two finger scrolling.  However, when I update the time in gutsy, it changes the time in leopard as well, but to the wrong time, and vice versa.  Is there any way to share a correct timestamp between gutsy and leopard?

---

