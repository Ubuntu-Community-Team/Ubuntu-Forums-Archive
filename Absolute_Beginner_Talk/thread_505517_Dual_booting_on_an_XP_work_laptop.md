---
title: "Dual booting on an XP work laptop"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by thebaron2 on 2007-07-20
I'm following this online guide to installing Ubuntu alongside Windows so I can dual boot (I'll post the link to the guide when I log-in under Windows - right now I'm writing this from Ubuntu cause I booted from the CD).  I need Win XP to work flawlessly because I have a lot of work stuff on there that I can't lose.

I am at the Partition step and the guide says to do it manually.  The problem is that the guide only has a selection for "free space" under /dev/sda.  Here's what I have:

/dev/sda
   /dev/sda1   fat16   /media/sda1   73mb   33mb
   /dev/sda2   swap                        79949mb   66000mb


Do I need to "Edit partition" on the /dev/sda2 line?

The guide is telling me to first create a 512MB swap file (Use as: option to SWAP, partition primary, location beginning) and then to create another new partition for Ubuntu (>2GB, Use as: ext3, partition primary, location beginning.

Can someone point me in the right direction here?  I'm planning on freeing up more HD space for the Ubuntu partition right after I post this, so that's not an issue.  But I really can't afford to screw up my XP install or getting everything running correctly again so I can log into work programs will be a pain in the ***.

I'm on a Dell Latitude D610.  Thanks for any help - I'd really like to get this installed so that I can start learning/using linux when I'm using the laptop in my free time.

EDIT: Here's the link to the guide I was using.  Is there a better one?
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

---

### Post by VoiceOvGod on 2007-07-20
Um....

Is this your own personal laptop that you do work-related activities on?

If it is a work-issued computer, I wouldn't feel comfortable helping you install Ubuntu on it, coz it might get you fired....

---

### Post by thebaron2 on 2007-07-20
It's a work computer but I can tinker with it.

There's only 1 person above me that can fire me and that's my father, so I'm not too worried about it.

If there's a good chance that it will interfere with XP then I may pass, but I would think that if I can just create a relatively small partition for Ubuntu to live in then I should be fine.  I just don't want to screw anything up during the partition creation process.

I've read that defragging before partitioning is also recommended - I defragged 2 nights ago I think but I can do it again.  I've got Diskeeper.

---

### Post by Di@blo on 2007-07-20
> **thebaron2 said:**
> It's a work computer but I can tinker with it.

There's only 1 person above me that can fire me and that's my father, so I'm not too worried about it.

If there's a good chance that it will interfere with XP then I may pass, but I would think that if I can just create a relatively small partition for Ubuntu to live in then I should be fine.  I just don't want to screw anything up during the partition creation process.

I've read that defragging before partitioning is also recommended - I defragged 2 nights ago I think but I can do it again.  I've got Diskeeper.

Well, the easiest way and safest method, which I used, is to install a second hard drive, and then install to that. I had an old 40GB that I put Ubuntu on, and I have XP on the 250GB drive it was originally on.

---

### Post by nitro_n2o on 2007-07-20
Dont be afraid of playing with partitions edit them as you wish BUT don't touch the windows partition and you are fine :) 
You can do the partitioning from the gparted GUI and it'll tell you which one is the windows.. have fun

---

### Post by thebaron2 on 2007-07-20
This is on a laptop, so installing another HD isn't an option.

"You can do the partitioning from the gparted GUI"

What is gparted?  Is that the screen that comes up when going through the install steps or is that another partitioning program altogether?

---

### Post by p_quarles on 2007-07-20
gparted is the partition editor that comes with the installation disk. I.e., your first post describes the step right before it starts doing its thing. 

Partitioning, unfortunately, can be very dangerous to your data. If, as you say, you have important data on this HDD, and you can't back it up to another drive, then I would advise against installing Ubuntu.

---

### Post by thebaron2 on 2007-07-20
It's not specific files that I'm worried about, but more applications still working.  I think there's a VPN on here that I connect to if I'm not plugged in at work, there are some shared drivers and printers, etc...

I have ~27 gigs of free space right now.  I was hoping that I could just designate a 15GIG partition or something like that just for Ubuntu without screwing with Windows at all.  I have a rarely used desktop at home I plan on installing this on, but I really use the laptop the most so I **really** want to get it installed on here.

There must be a way to create a separate partition for Ubuntu and its swap file without screwing Windows' data up. :confused:

EDIT: Oh and I can back data up - either to an external HDD when I get home or to a CD.

---

### Post by thebaron2 on 2007-07-20
Would it be safer to create a partition from within Windows with some partition program as opposed to doing it from the Ubuntu CD?

---

### Post by p_quarles on 2007-07-20
Yeah, and it's really easy to do. It's just that partitioning the disk can be risky. Make sure you have everything either backed up or replaceable before you do this. 

After that, you should defrag the drive twice. This will greatly reduce the chances that you'll corrupt anything while editing the partitions.

Finally, you don't really need to choose the manual partition option. Just go for the automatic option, and then choose the option to "resize existing partition and use freed space" (something like that). 

Ubuntu will ask you a few more questions, and then it will install itself in about 15 minutes. Super easy. 

Other things you might want to know:
Some wireless cards work out of the box, but most will require some fiddling with to get working. An ethernet connection will probably come in handy for this part of it. (Of course, if wireless works on the CD boot, it'll work after installation, too)

There are several VPN clients for Linux, so you'll still be able to log in at work. I don't know what other apps you have in mind, but many things do have good replacements in Linux. 

So, go for it. Just be careful, and make sure you can fix things if they break.

---

### Post by p_quarles on 2007-07-20
> **thebaron2 said:**
> Would it be safer to create a partition from within Windows with some partition program as opposed to doing it from the Ubuntu CD?
No, not at all. Gparted is one of the best of its kind.

---

### Post by balleyne on 2007-07-20
Wait... why do you need to manually edit the partition tables?

I've installed dual-boot XP / Ubuntu on my laptop (though I'm wiping XP this weekend :D) and I just selected the "resize current partition" option during the installation. I actually started by giving Ubuntu (Dapper, originally, though I've upgraded to Feisty, and done the same thing from the Feisty Live CD on another laptop) 8 gigs to start as a trial. Once I decided that I liked it, I used gparted (yes, different program - I just burned a gparted Live CD which helped to resize partitions) to shrink windows and grow Ubuntu.

Resizing the current partition is pretty straightforward in the Live CD install, but there are a few things you should know:
1) You should probably defragment your hard drive first from Windows XP. I think you right click on your C drive, go into Tools or Properties or something, and you should find it in there somewhere (sorry, don't have a windows machine nearby right now)
2) Definitely back everything up. There's only a slim chance that things will go wrong, but if they do go wrong, then it could be difficult to try and fix.


I think the guide you're looking at is a bit more complicated and detailed than is necessary for your situation. You should just be able to (1) defragment, (2) backup, (3) run the feisty live CD - selecting "resize the current partition" during the installation.

HTH

---

### Post by armandh on 2007-07-20
ubuntu is the first linux I have tried that works well
I have a few work bench junkers and it is on these i have tried knopix, linspire, ubuntu, etc.
I would NOT advise anyone to try it on mission critical hardware [at first] or at all without a working immage.

while the live cd workes with 128M mem the install requires 256 to partition while there is no swap file [while you are partitioning]
resolved with an old small hard drive for the swap file while the main HDD is setup

---

### Post by thebaron2 on 2007-07-20
OK, thanks so much for the tips.  At the very least, its comforting to know that there are helpful people providing extremely rapid support at these forums!

I think I'll back up my important docs, run defrag a few times, and try the automatic resize partition option.

My wireless worked fine off of the CD (which impressed me, because that's the biggest issue I've heard of w/Linux: driver compatibility.  My optical mouse worked also) so I'm not worried about that.

After it's done partitioning, do I need to do anything else to be able to dual-boot?  I want to be able to turn on the laptop and just choose Ubuntu or Windows from a boot list, depending on whether or not I'm working.

Thanks again for all the input, it's greatly appreciated (and comforting!).

---

### Post by p_quarles on 2007-07-20
Ubuntu will install a program called GRUB in the master boot record. Every time you turn the computer on, you'll get a menu allowing you to select which OS you want to run. 

And, yeah, these forums are one of the best things about this distribution of Linux.

---

### Post by thebaron2 on 2007-07-20
Alright.  Now I did some reading awhile ago and I remember GRUB being mentioned.  If/When I uninstall Ubuntu (it is a work computer after all, so down the line I'll need to remove it, I'm sure) will there be any boot issues?

I seem to remember something about the MBR being overwritten by Ubuntu or something like that.  Is that easily fixable or is there a way to avoid the issue in the first place?

---

### Post by p_quarles on 2007-07-20
I've never tried it, but I believe you can restore the MBR by using the Windows disk. It's very easy, supposedly.

---

### Post by armandh on 2007-07-20
I have NOT tried dual boot with ubuntu but it was a problem with others.
as cheap as an small used HDD is I would go that route first
try dual boot from one hdd only on one you can afford to reload
some times the linux MBR cannot be cured by xp's fdisk
98's fdisk /mbr will remove the boot loader  but you will still need to get the xp back on

---

### Post by fatcoin on 2007-07-20
I install Ubuntu 6.10 yesterday on USB HD (15GB system partition and 2GB swap - total 80GB). Instalation (think its GRUB) made some change on my main HDD on laptop, dual boot menu. So the problem is when USB disk is not connected there is no boot menu (system halted, GRUB Error 21). Could I use Win boot menu, or reconfigure GRUB so there is no need to plug USB disk.

Second question is can I reinstall UBUNTU 7 over 6 (reformat partition) and do something else on the end of installation so it don't mess with my win boot on main HDD.

I am new..., want to try UBUNTU, but win is my basic OS on laptop and I need it to work

Thanx

---

