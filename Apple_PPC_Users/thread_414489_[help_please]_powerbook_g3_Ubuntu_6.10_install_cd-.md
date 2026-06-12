---
title: "[help please] powerbook g3 Ubuntu 6.10 install cd-rom problem"
date: 2007-04-19
forum: Apple PPC Users
---

### Post by Bob Bobbio on 2007-04-19
I have a PowerBook G3 233mhz, I've got OS 9 on it with BootX which I use to boot into Ubuntu Hoary Hedgehog which runs fine.  I'm trying to install 6.10, 

I copy the kernal and disk image from casper/powerpc/ to the system folder and system folder/linux kernels  places and then I run BootX but then when the lines of text get to mentioning the CD-rom drive model and speed (20x)  it gets stuck and won't get past it, sometimes it just stays there forever, and others it just says error! but no details.  I'm quite new to linux but I really love it and want to learn more and get the newest version installed on this machine, Thank you to everone who reads this. 

Also I'm going to get eventually a wireless card for this machine could anybody suggest a wireless card that would work? 

If I can't get 6.10 installed I borrowed a wireless card to see if I could get it to work but I couldn't (I have no Idea what to do it won't show up in the network prefrences) its a D-link DWL-G650 (I can see that this might not work but thats okay the thing I was wondering is that when I installed Hoary I accidentily clicked no to the start pci card services I just want to make sure this isn't the reason it's not working and that I don't need to re-install) but again this is only if I can't get 6.10 installed. Thank you so very much for reading my problem! Thank you again!

---

### Post by Madman68 on 2007-04-20
well, I really can't help you with the wireless card problem cuz I really don't know that much about them, so sorry for that. But anyway lets get onto the other part of your question, if your trying to upgrade to 6.10 from Hoary Hedgehog you should really just do all the updates. Ok, here it goes, there are two ways, if you don't like using the terminal you can just go into System->Administration->Update Manager. Or, you can go into the terminal by going Applications->Accessories->Terminal and copying in this first ```
sudo apt-get update
``` and then this ```
sudo apt-get upgrade
```. I know this prolly doesn't explain everything but if you still don't understand or want to find out more information you should just try searching around the site some more, I'm sure you will be able to find a solution to your problem.

---

### Post by Bob Bobbio on 2007-04-21
Okay, thank you very much for responding, I didn't know it would upgrade like that!! thats really cool. Thank you so very much I will try this tomorrow.

---

### Post by Madman68 on 2007-04-21
no problem, but like I said you should also look around through the forums for more information if you want it

---

### Post by Bob Bobbio on 2007-04-21
I upgraded to 6.10 but now when I boot up I get this after it checks the hard drive:

mediabay0: switching to 3
mediabay0: powering up
mediabay0: enabling (kind:3)
mediabay0: waiting reset (kind:3)
mediabay0: waiting IDE reset (kind:3)
mediabay0: waiting IDE ready (kind:3)
mediabay 0, regestering IDE...
hdc: Matshita CR-174, ATAPI CD/DVD Rom drive
hdc: Enabling Matshita BMA 2
ide1 at 0xd501c000-0xd501c007, 0xd501c160 on irq 14
hdc: ATAPI 20x CD-ROM drive, 128kb cache, DMA
Uniform CD-ROM driver Revision: 3.20

(pauses a really long time here)

Done.
ALERT! does not exsist. Dropping to a shell!

(and then a console appears)

It would be great if somebody could help me please because I have no Idea what to do.. Thank you every body.

---

### Post by pxwpxw on 2007-04-22
I am guessing here, but If you are using BootX, have you copied  the new vmlinux and initrd.img to your OS9 partition to replace the Hoary versions for BootX. BootX kernel root configuration may also need changing - 

You would have done this for Hoary. You should be able to copy the kernel images by running the install CD rescue option, or possibly from the command line you get when the restart fails.

---

### Post by Bob Bobbio on 2007-04-22
Thank you for your reply.  Yes I did replace the kernel.  This is the same error I get when I try to boot the live cd too with the live cd kernel earlier before I updated (if that matters any).  Thank you.  I'm not sure what you mean by the BootX kernel root configuration.

---

### Post by pxwpxw on 2007-04-22
My OldMac is a powermac7300, pre G3 with ubuntu610 commandline. I just checked it and
In my BootX 1.2b3 panel there is a place to enter the root partition
More Kernel Args [ root=/dev/hdax ]
 You must have done this for hoary.
The alert you are getting could mean that this entry is missing -
The Options are set to Force Video Settings and Use Specified Ramdisk.

There is also a restart problem with Old World mac scsi drives but i think you have an ide drive.

---

### Post by Bob Bobbio on 2007-04-22
OK thank you,  I actually never did that for Hoary, I only used these arguments
video=atyfb:vmode:14,cmode:32,mclk:71
With out them the screen is rerlly weird and hard to read with a weird glowing bar in the center

I can't figure out how to add the root=/dev/hda11  
I tried

video=atyfb:vmode:14,cmode:32,mclk:71,root=/dev/hda11  

and

root=/dev/hda11;video=atyfb:vmode:14,cmode:32,mclk:71

but they both seem to ignore all the arguments...
I think there is probably a very simple answer to this but I can't find it... I'll keep looking thanks for your help it's very much appreciated. Thank you

I tried 
video=atyfb:vmode:14,cmode:32,mclk:71 | root=/dev/hda11

and the screen seems ok and it gets past where it was stopping before but now it gets stuck at another place 
it says
*Checking root filesystems...
fsck 1.39 (29-May-2006)
/dev/hda11 Superblock last write time was in the future.  FIXED.
/dev/hda11 clean, 24708/448896 files, 206116/89746 blocks.

*Checking filesystems...
fsck 1.39 (29-May-2006)
/dev/hda10 was not cleanly unmounted, check forced.
/dev/hda10 18/15648 files (5.6% non-contiguous), 12954/31250 blocks
fsck died with exit status 1

* Mounting local filesystems...
* Configuring network interfaces...
* Setting up console font and keymap...
* Starting system log...
* Starting kernel log...
* Starting pbbuttonsd
Ubuntu 6.10 macg3 tty1

macg3 login:  *Starting deferred execution scheduler atd
* Starting periodic command scheduler...
* Running local boot scripts (/etc/re.local)

and then it just stays there forever and if I hit enter it says
Ubuntu 6.10 macg3 tty1

macg3 login:

and I can login and it lets me use the console but thats it...

Thank you for your help so much. Thank you

---

### Post by pxwpxw on 2007-04-23
You should be able to sort things out from the console - if you have upgraded from a previous full graphical desktop installation, the xorg and desktop packages should be still there, but stopped from running by some problem, maybe a missing package.
Check if you have xorg files in directory /etc/X11/ and /var/log.
Might also try doing:
```

sudo dpkg-reconfigure xserver-xorg
sudo startx

```
To see what happens.
Maybe a new thread asking for help with that.

---

### Post by Bob Bobbio on 2007-04-26
Thank you, but actually I forgot to mention that I re-partined and installed from the 6.10 disk when I found out that it would boot from the alternate install disk.  It won't start now being just after the installation, I think that maybe it just wasn't made to hold 6.10 I think I'm going to install breezy and live with it.  Thank you everybody!

---

