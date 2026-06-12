---
title: "Dual boot on Micro Form Factor"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by theRevMom on 2007-03-09
Is this possible?  I want to have two HD: One with Edgy, one with XP.  My box is a micro form factor, however (Dell optiplex sff gx 260 P4 2.27GHz 1Gig DDR, HDD0 80 GIG Edgy), so I can't install a second HD.  I have a 200 Gig SATA HD in a USB external box.

Here's the reasoning:  All my financial stuff (turbo tax, quicken, etc), my Nero back ups, and my Palm stuff is windows dependent. I know I can transfer the Palm over to Edgy, but not the Intuit stuff. I don't know about the Nero. The 200 Gig SATA drive is 90% full. It is backed up on DVDs  using Nero's back up feature.

So, I'm looking for suggestions, advise, direction.  Is it possible to do a dual boot using a USB drive?  If so, would it be better to use the Windows or the Edgy as the USB drive?

If it's not possible, is there a way to restore the data files from the Nero backup in Edgy?  Or do I need to just burn the files to DVDs in a copy format rather than the backup format?

I'd appreciate any insights you more expert folks can give me.

thanks

---

### Post by dstew on 2007-03-09
Yes, you can do what you want with either Edgy or Windows as the primary disk. There will be some issues when you install, though.

If Windows is on the primary disk, you should install the boot loader grub to the master boot record of that disk. This makes some people nervous, because you will be overwriting the first part of the windows booter, but it is really OK. Grub can boot windows just fine, and if you change your mind later you can easily restore the original windows booter using the windows recovery console and the fixmbr command.

If you make Edgy your primary, install Grub on it the same way. To boot windows, you might need to change the grub configuration file /boot/grub/menu.lst to fool the windows disk into thinking it is the primary by using the map command.

---

### Post by theRevMom on 2007-03-09
[I]Dstew wrote:
If you make Edgy your primary, install Grub on it the same way. To boot windows, you might need to change the grub configuration file /boot/grub/menu.lst to fool the windows disk into thinking it is the primary by using the map command.
[/I]

Whoa... I'm not that fast.  I need some explanation.  

Install Grub.... I've installed Dapper on 4 computers and Edgy on 2.  But I don't know what you mean by Install GRUB.... help me out.

And how would I change the grub configuration  to fool the windows disk?  What is the Map command.  

Sorry to be so slow.  But I am still quite wet behind the ears.

thanks for your patience

---

### Post by dstew on 2007-03-10
What operating system do you have on your system at present? How do you boot it? That is, do you get a grub menu at startup? If you have Edgy installed, you should see a grub menu when you start the computer.

---

### Post by theRevMom on 2007-03-11
I'm currently operating out of edgy.  But I do not get an option in grub when it boots, probably because I do not have the second   hd   attached.  I'm waiting for an external case for the SATA HD to arrive from Tiger Direct.  

My OTHER box has just XP, but two HD.  I plan to copy data to the second HD, then I want to re-install XP on the primary for the new box using the USB external box.  That's why I asked the question.  There are three programs I use regularly for which there is no  comparable software (that I've found) in Linux.  So I need the second boot option to use those.

Will I get an option in Grub once I attach the second drive?

Thanks.

---

### Post by dstew on 2007-03-11
So if I understand correctly, your micro form factor box will have the first (internal) drive as Ubuntu Edgy, and the external USB drive will have windows.

First, are you sure your BIOS can boot the external drive? Some can, some can't. On my son's laptop, the USB 2.0 ports can boot, but not the USB 1 ports. Both can read the disks, however. If you want to boot the USB drive from the Grub menu, you need to add the boot instructions to grub's configuration file, which is /boot/grub/menu.lst, in order to see a menu choice for Windows. The exact statements will depend on your final configuration, but something like this works most of the time. If the USB drive is numbered by your BIOS at boot time as (hd1), then the following lines should be added to boot Windows from the first partition:

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)
makeactive
chainloader +1
boot

The map statements fool the Windows OS into thinking it is the first disk. Rootnoverify mounts the partition so grub can access it, makeactive allows it to be booted, and chainloader +1 tells grub to jump to the Windows booter on the second sector of the harddisk and go from there.

---

