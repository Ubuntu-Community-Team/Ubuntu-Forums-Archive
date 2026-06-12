---
title: "Installing Gutsy on External USB Drive"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by HDave on 2007-11-07
Hi -- Total newbie here.  I just spent the last couple days trying to install Ubuntu on an external USB drive such that when that drive is plugged into my laptop my computer boots Ubuntu and when the drive is not plugged in, my it boots Windows XP.

I never heard of GRUB or the Master Boot Record (MBR) before, but unfortunately, this experience has forced me to go to school on all this.

Bottom line, even if you instruct the Ubuntu installed to put Ubuntu on an external drive it will still mess with your internal hard drive by replacing the contents of your MBR with GRUB (the linux booting system).  This is more than inconvenient, if your external hard drive is not around, because you left the drive at home before leaving on a three day business trip, you will learn the hard way that you are unable to boot your laptop into windows -- ARRRGGGGHHHH.

Through much googling and reading I found out how to make it all work.   Afterwards (of course) I found this thread (which is quite long) that contains the exact answer...so for all you newbies that want to dip their big toe in Ubuntu without messing up your hard drive at all...read this:

[http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-21-when-trying-to-boot-xp-after-installing-ubuntu-7.04-on-seperate-hdd-552043/]("http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-21-when-trying-to-boot-xp-after-installing-ubuntu-7.04-on-seperate-hdd-552043/")

You can avoid some of this hassle if when installing Ubuntu you click on the "Advanced" button (can't recall which step) and tell the pop-up window to put Grub on HD1 instead of HD0.  Then you will not mess up your internal hard drive, but you will also not be able to boot from the external drive without sprinkling some extra pixy dust as covered in the link above.

---

### Post by MrFSL on 2007-11-07
Excellent post. For a self proclaimed Linux "noob" you are already doing a wonderful job as the member of the community.

That's what is great about Linux for me.

---

### Post by ARhere on 2007-11-08
pretty cool.

Now remove your hard disk and just run your laptop off of USB memory sticks and tell us how much longer the battery lasted!  W00T!

-ARhere

P.S.  Still don't understand why a [8GB solid state drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820609252") costs $300 where two [4GB memory sticks]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820171246") will cost you $100.  Sheesh!

EDIT:  Just saw a [8GB flash stick]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820211181") for $55!!!

---

### Post by HDave on 2007-11-09
> **MrFSL said:**
> Excellent post. For a self proclaimed Linux "noob" you are already doing a wonderful job as the member of the community.

Hey -- thanks for the pat on the back...I too like the community and I love the idea of a free-as-in-speech operating system with all the polish, but I have to say that the folks who put Ubuntu together, need to take another pass through at making it even easier.

There is NO WAY my wife, my mom or anyone in my family could have figured this out...to them a computer is a tool, not a hobby -- if you know what I mean.  I, on the other hand, am not planning on giving up...I know I can make this work, but I expect its going to take a lot of effort before my fix all my problems:

a) external monitor issues / graphics card issues
b) can't find wireless verizon card
c) on board camera and microphone to work
d) email client for Exchange Server 2007
e) hardware volume/mute/play/pause buttons
f) Gige PCI card

But at least now I can begin the process....

---

### Post by MrFSL on 2007-11-09
> but I have to say that the folks who put Ubuntu together, need to take another pass through at making it even easier.

There is NO WAY my wife, my mom or anyone in my family could have figured this out...to them a computer is a tool, not a hobby --

Well, hardware support is what usually drives people crazy. If you were trying to install an Apple O/S on non-supported (or not officially supported) hardware you would have problems to. The difference is that there probably would be no fixes.

My 70 year old mother uses this O/S without issue. I just built her a computer with supported hardware. I bought my sister a laptop with supported hardware - etc.

While it might not seem it, Linux has the largest hardware support built in then any other O/S out there. Get through these little hardware issues and you will see.

---

### Post by RexdPont on 2008-04-01
The answer from the suggested post does not work for me.  I installed Gutsy on a usb 120Gig external drive, I first disconnected the other two drives as was suggested in the post that I worked from.  The new drive worked fine.  then when I try to boot to it with the other drives attached (or either one of them) the external drive is ignored.  I have set the BIOS to look first at the external drive.

I have tried adding ehci-hcd, usb-storage,scsi_mod, and sd_mod to /etc/mkinitramfs/modules.  However I can't seem to make a new image file with
mkinitramfs -o /boot/initrd_usb.img /lib/modules/  as was suggested on the post that offered the above changes.

The external drive is listed as /dev/sdc1 when I do fldisk -l.

I have tried changing (hd0) /dev/sdc in /media/disk/boot/grub/device.map

sudo grub-install --root-directory=/media/disk /dev/sdc will not run either.  as suggested in that post, I get the message "xfs_freeze, specified file in not an XFS filesystem...

How do I fix this?

Thanks,

rex

---

