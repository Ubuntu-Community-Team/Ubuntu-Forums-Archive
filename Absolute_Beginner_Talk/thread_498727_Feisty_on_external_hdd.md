---
title: "Feisty on external hdd"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by lobotomia on 2007-07-11
Hi everyone, 

I installed Feisty Fawn again on my external hdd. Since for the installation I got rid of my internal hard drive on my Dell D600 I did not have any problems with the installation itself. I rebooted with restart several times, everything went fine
However when I shut down, and rebooted afterwards the screen froze with the ubuntu sign when the little orange worm on the screen was only about a millimeter long. 
I did this several times before I realized that plugging the USB 2.0 hard drive in and out when I get the frozen screen solves my problem and Feisty boots fine. 
I have read somewhere on the net that windows unmounts and mounts all USB devices when starting up. Does linux do the same? And if so, how can I stop it from unmounting my USB external hdd at the beginning of the boot process? 
Please help, this is not a big problem and I am incerdibly happy to have ubuntu on my external hdd, but if I could solve this little issue everything would be perfect.

---

### Post by AegisTalons on 2007-07-12
So from what I experience on my computer, I cannot boot or even see external hard drives. It may be a setting in your BIOS. Look through your BIOS, anything about USB support on startup. Also how are you booting up into Ubuntu, using the GRUB booter?

---

### Post by lobotomia on 2007-07-12
What I did was simply boot from the live CD, unplug-replug my USB HDD so it showed up under install and examples on the desktop, then hit install. 
When it came to the partitioning phase I did an unplug-replug again, and fiddled aroud with the installation window arrows going back and forth, and after this the USB hdd was recognized. 
The install went fine. 
The computer on the BIOS level I guess does have USB support when it starts up, because I never have any other hdds attached when I boot. It ginds GRUB and then at the first UBUNTU screen quits. 
That is all I can say to your prob, sorry.

---

### Post by yanqui on 2007-07-18
There is a lengthy thread somewhere in this forum about loading Breezy on a usb hdd.  I used the instructions to load Dapper on a usb hdd, and have never experienced any troubles with it.  I was completely unable to do it, however, using a live distribution.  I had to use the "alternate" installation, a command line installation.  Part of the reason is the way the USB drivers get loaded with the live version as compared to the choice of telling them when to load when you set up the load sequence at installation with the alternate version.  It's not a difficult process, and I'm pretty new to Linux, but I did get it working fine.  I'm going to try the same thing with Feisty in a few days, and I expect that I should get the same results; the kernel is the same, the hardware is the same, I believe that the module load should be the same.

---

### Post by lobotomia on 2007-07-19
Thanks for the advice. I hope this does not mean I have to reinstall the system. Is there some way of editing the boot process for an existing operating system?

---

### Post by AegisTalons on 2007-07-19
> **lobotomia said:**
> Thanks for the advice. I hope this does not mean I have to reinstall the system. Is there some way of editing the boot process for an existing operating system?

What do you mean by editing the boot process for an existing operating system? Do you mean what operations it runs? Do you mean edit the Boot Loader menu? Also which operating system?

---

### Post by yanqui on 2007-07-19
> **lobotomia said:**
> Thanks for the advice. I hope this does not mean I have to reinstall the system. Is there some way of editing the boot process for an existing operating system?


Probably yes.  I'd say follow the thread for installing to a usb hdd, and there's a place to modify the way the usb modules load.  If I'm wrong, I hope the more experienced gurus will correct me quickly, but I would say that to do that, you'd boot from the cd (I used the alternate, not the live) and select the recovery option, which is in that thread about installnig to usb hdd, and go from there.  See, in that thread, following the process, the install goes well, but you do have to modify the boot process, and I don't see why doing that at THIS point would be different for you than if you had done it at the first, because it's the same thing just with more time in between teh install and the modifications.  Did that make sense?

---

### Post by lobotomia on 2007-07-20
It makes absolute sense. I have browsed through the thread and I realized that I already made the modifications I could make but somehow my system could not deal with the step where I had to recreate the initramfs. It could not find directories. In detail it broke down like this: 

I did all editing steps up to this point. It was possible with sudo gedit with the live CD in, I just had to find the right system directories on the attached USB drive.
*INSTALL NOTE: Editing these two files loads the necessary commands to get USB support going so UBUNTU will recognize the external USB drive. But we still need to recompile (or recreate) the initrd.img that UBUNTU uses at startup ... so that these edits actually work.*

And step 10 is where it all went wrong: 

[I]( STEP 10 ) Recompile (recreate) the initrd.img file to include USB support from these edited files ...

mkinitramfs -o /boot/initrd.img-2.6.12-9-386 /lib/modules/2.6.12-9-386

INSTALL NOTE: When you are done with the previous step #9 (and before performing this step), you can run the "ls /lib/modules" command (without the quote marks) from a terminal window to see what kernel version number you should use for this install step. They may be using a kernel version higher than 2.6.12-9-386 that was available when I originally created this help guide. (Kudos to "Saxegaard" for bringing this to my attention in post #235.)[/I]

At step 10, I could not complete these tasks because my kernel folder on feisty ends with "-general" instead of "-386", and when I told ubuntu to recompile that kernel (I found the "-general" directories too, so they exist) it said that this kernel name was invalid. 

([I] STEP 11 ) Edit the GRUB bootloader menu file to correct a small error that looks at the wrong drive to boot from ...

vim /boot/grub/menu.lst

Navigate down this file until you get to a section where there is a menu list (not commented out ... no #s) that has Ubuntu mentioned three times (and possibly an area mentioning Windows XP down below it, if you have XP installed on an internal drive of yours).

There is a line in these three Ubuntu menu choices that has root listed on it and probably has (hd1,0) to the right of it. We need to change this to (hd0,0) on all three of these menu choices. Why? Because according to GRUB, the external USB drive will be our first drive (hd0,0) and not our second drive (hd1,0) because we loaded GRUB on it's bootsector. 

INSTALL NOTE: You will also want to change a "# groot" line in a section of your menu.lst file that may look something like this ...
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3) <<< CHANGE THIS LINE TO READ # groot=(hd0,0)
(Kudos to "archis" for his excellent documentation of this farther down in post #227.)

INSTALL NOTE: You may want to change the root line for the Windows XP section in this file to (hd1,0) just in case you have XP loaded on an internal drive and want the option to boot into XP from the GRUB menu. (See post #2 for more info.) You may have to edit this section whenever you update your kernel version. If you have problems pulling up XP after a kernel update, check this section of your menu.lst file to see if you need to edit it again.

Be sure to save the file changes (using : x)

COMMENT: Feel more comfortable editing this file in Windows? See post #171 for a program that will let you edit files on linux partitions from within Windows. (Kudos to "mickola" for the suggestion.)[/I]

For me this last step was not needed, since my menu.lst file already contained (hd 0,0)

Could the alternate CD influence how a directory is viewed? I don't think so. So what am I to do if I have a kernel running which is actually and invalid name kernel?

---

### Post by yanqui on 2007-07-23
With my limited Linux experience, but with a good bit of other OS experience, I'd have to say, yes, I think it could influence how it's viewed.  I think there's going to be quite a few differences in the way a "live" distro runs and sees things, because of the stuff that has to be already up and running while you're trying to install.  From an alternate distro, nothing is actually "running" from the OS.  I know I'm not putting it very well, but I think your issues will be answered by trying the alternate version.  There's a lot that comes clear when you try to reconcile the install process from the live version and watch teh install process from the alternate version; and from watching the live version boot, and watching the alternate-version-installed version boot.
Also that the live version says "general" instead of "-386" is somehow significant for the process and alterations, but again, nothing i can put into words.

---

