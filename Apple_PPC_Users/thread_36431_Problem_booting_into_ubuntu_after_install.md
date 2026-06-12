---
title: "Problem booting into ubuntu after install"
date: 2005-05-23
forum: Apple PPC Users
---

### Post by Mighty3k on 2005-05-23
Hi!

Yesterday I managed (I think) to install Ubuntu on my old powerbook G3 (wallstreet).
The problem however is that I do not know how to boot up into the installed system.

I have OS9 on one partition and while booted in os9 I can't detect the linuxpartition..

any ideas?

---

### Post by joelito on 2005-05-23
Try setting the partition where you installed the Bootloader as active (I did that in a PC)

---

### Post by Mighty3k on 2005-05-23
bootloader?
hehe.. I'm kinda new to this..

I have to boot linux using BootX, and I can't chose my linux to boot from since BootX is running under os9 and os9 can't detect my linux partition!

---

### Post by Len on 2005-05-23
Wasn't the powerbook G3 a newworld machine? If so, yaboot should work...

Anyway, to use BootX you must have the Ubuntu kernel on your Mac partition and set the Ubuntu boot partition with a comment like /dev/hda6. You can use Mac pdisk (google around a bit) to get the linux name of the linux partition. You can also start from the installation CD and look up the name in the partition program.

---

### Post by Mighty3k on 2005-05-23
[QUOTE=Mighty3k]bootloader?
hehe.. I'm kinda new to this..

I have to boot linux using BootX, and I can't chose my linux to boot from since BootX is running under os9 and os9 can't detect my linux partition![/QUOTE]
 No.. It's and old world.. black and all :P read somewhere that the new world starts with the colored macs..

I have the kernel from the cd on my mac partition.. but when I load linux from that while passing all the parameters (like root=/dev/hda10 in my case) I end up with a black screen and nothing more.. :/

---

### Post by Mighty3k on 2005-05-26
I changed the video settings in BootX
now I can see an error message telling me that ubuntu can't boot from the partition /dev/hda10 but when the ubuntu installation was finished it said that it had installed ubuntu there...

the error is something about VFS being unable to open root device /dev/hda10 or "unknown-block(0,0)"

then I end up with a kernel panic caused by VFS being unable to mount root fs on unknown-block(0,0)

could this have something to do with how I partitioned the HD?

---

### Post by Len on 2005-05-26
First of all, get Mac pdisk (for Mac OS 9, OS X already has pdisk, open a terminal and type 'pdisk') and verify you really have entered the path to the correct partition (pdisk lists the linux partition 'codes' for every partition).

This isn't hard to do, just read the instructions on the site before downloading:
[ftp://cfcl.com/pub/ev](ftp://cfcl.com/pub/ev)

On my 5500 I think I copied the installed kernel to the mac side instead of using the one of the CD. You can do that by switching to another terminal (alt+F2), mounting your mac and linux disk and transfer the kernel. The one provided on the CD should work too however, it shouldn't give that error at least.
I just put 'hdxx' into the root field of BootX, although a root=/dev/hdxx does the same. I haven't used any other arguments and no RAM disk either. I use Warty on that machine though, not Hoary.

Good luck!

---

### Post by daristotle on 2005-05-27
I'm also having the same problem. I'm try to use bootX on a Powerbook 2400c and get the same error. I tried the pdisk thing. But it shows that hda10 is something like Apple Boot Strap. Should I try reinstalling?

---

### Post by Len on 2005-05-29
"Apple Bootstrap" is the boot partition for newworld macs. You shouldn't choose that one, but the linux one (probably hda11).

---

### Post by kberrien on 2005-09-30
Ditto same here, on a Wallstreet powerbook, Hoary release.  I've installed YDL 3 & 4 with success so I'm familiar with boot X.

I've install twice, first from an existing OS9/Linux partions & wipe, 2nd repartitioning the drive blank except for the os9 install.

I did have two errors, issues in the install.

1. Multiseat system (never even hear of this in linux, gotta look it up)
2. Warning about ide modiles not available, but might be further in install.

I boot into not being able to find /dev/hda11, and kernel panic.  IDE is detected, etc...

Was psyched to try a new distro, and was sick of YDL but I'm getting nowhere now.  Tried many version of BootX up to 1.1.3.  Booting off kernel from /target/boot.  Also tried some kernels from the net from the oldworldmac wiki article, no dice.  :confused:

Kevin

---

### Post by jdp on 2005-10-02
The problem is that the kernel *doesn't* include drivers for the IDE and SCSI controllers.  Thus, when the kernel boots it can't find any drives to try to boot from.  Read the rest of the output and you'll likely not see any messages that show the drives being found.  You'll need the initrd from the installed system to boot.  You *don't* have to specify your root partition if you use the initrd.  It'll load the correct modules and find the drives and start with root at the correct partition.  I've done installs onto a G3MT (oldworld) and a 7600/132 (oldworld) and had to use BootX on both.  
[My thread on applefritter.com](applefritter.com/node/8936)

---

### Post by kberrien on 2005-10-03
[QUOTE=jdp]The problem is that the kernel *doesn't* include drivers for the IDE and SCSI controllers.  Thus, when the kernel boots it can't find any drives to try to boot from.  Read the rest of the output and you'll likely not see any messages that show the drives being found.  You'll need the initrd from the installed system to boot.  You *don't* have to specify your root partition if you use the initrd.  It'll load the correct modules and find the drives and start with root at the correct partition.  I've done installs onto a G3MT (oldworld) and a 7600/132 (oldworld) and had to use BootX on both.  
[My thread on applefritter.com](applefritter.com/node/8936)[/QUOTE]

Ok, I've reviewed your walk through on applefritter.com.

My setup, following[https://wiki.ubuntu.com/Installation/OldWorldMacs](https://wiki.ubuntu.com/Installation/OldWorldMacs) was:

cp boot/vmlinux hfs/System\ Folder/Linux\ Kernels/vmlinux
cp boot/initrd.img hfs/System\ Folder/ramdisk.image.gz

Your walkthrough calls for:

cp /boot/**initrd.img-2.6.10-5-powerpc** /target/mnt/hfs/System\ Folder/ #this is where "tab" helps a lot. You can type the /boot/i and hit tab to get **/boot/initrd.img** then press '-' and hit tab again to get the rest of it. For the rest do /target/mnt/hfs/S watch the capitals here, hit tab and it'll fill in the rest with the slashes and all.
umount /target/mnt/hfs

At first it seems to suggest to grab specifically initrd.img-2.6.10-5-powerpc, but the line below seems to suggest using just initrd.img as I already did.  Do I have to specify the 2.6.10-5 img specifically and copy that.  And does that have the ide modules compiled in?

If I'm missing modules, I would assume I have to have a kernel with the modules compiled in, else, how could I ever get access to those modules if I can't mount the volume where they reside.

Thanks for picking up my issue... Kevin

---

### Post by jdp on 2005-10-03
My post had instructions on some basic tricks of the command line, to help Mac users who might be UNIX/Linux noobs.  By typing the inital **/boot/i** you can hit **tab** to get **/boot/initrd.img** and then, if you hit **-** and **tab** again, it'll fill in the rest.  If you scanned over it and just looked for file names it does seem like I only specify the **initrd.img**.  From what I saw of the file sizes of the **vmlinuz** on the install CD and the **vmlinuz** on the installed system, the file sizes are nearly identical.  It's the **initrd** that makes the difference.  The installed **initrd** seems to be able to load modules form within it's own RAM disk and then find and mount a root filesystem without one being specified in BootX.

If installing an upgraded kernel, I would certainly copy over botht he newly installed kernel and the initrd before rebooting.

I ran out of space on my 7600/132 before the install finished unpacking all the standard packages, so I'll have to redo it with a bit more given to Ubuntu.  Otherwise, it seemed to boot just fine.

---

### Post by kberrien on 2005-10-03
I understand what your saying.

There is an initrd.img in /target/boot, thats what I copied for BOOTX to use.  My question was if there really is an initrd.img-2.6.10-5-powerpc file as well, and THAT is the proper to copy (under the name initrd.img) to your hfs partition?

I'm not sure what to think now, reading some other threads that suggest you CAN'T install Hoary on the a Wallstreet, and must install the older verison, then upgrade.... stumped.  I might give that a try, otherwise I guess I've stuck snoring through and older version of OS X, as I'm sick of YDL.

Kevin

---

### Post by jdp on 2005-10-03
Ah, ok!  The initrd.img that you see is a sym-link to the initrd.img-2.6.(blah) file.  It should become the sym-link the any newer version that gets installed during a kernel upgrade.  THe reason I has the whole file name in my wlak through, is that you end up with the whole original filename, and not just the initrd.img.  That helps a lot when you want to upgrade and your original kernel/initrd isn't working.  You'll have the full version info in the filename of each one you copy over.  Can you imagine 6 months from now and trying to remember what version your latest working initrd was when you upgrade and blew away the file 'cause you didn't keep the version names and seperate files?  ;)

---

### Post by kberrien on 2005-10-03
Well, then I copied the correct file.  While the output shows detection of the IDE interface, your correct and it does not show recognition of the drives.

Still leaves me nowhere... but I found some more Wallstreet threads, and I'll give those a look too.

Kevin

---

### Post by kberrien on 2005-10-04
[QUOTE=kberrien]Well, then I copied the correct file.  While the output shows detection of the IDE interface, your correct and it does not show recognition of the drives.
Still leaves me nowhere... but I found some more Wallstreet threads, and I'll give those a look too.
Kevin[/QUOTE]

Well, I gave Warty a try, had to use the pivot_root trick.  Got the kernel over to the HFS side, and still get kernel panic unable to mount /dev/hda11.

Just the kind of stuff that makes me hate linux sometimes.  I'm off to see how slow Jaguar is on this thing, I'm hoping it isn't as buggy as Tiger is.  If so, I can always put YDL 3 back on.

Thanks for everyones help, but as I read this and other threads, there are a lot of problems getting Ubuntu to install on Wallstreets and I just don't have the time, and a definative answer doesn't seem comming. :???:

---

### Post by king_arthur on 2005-10-05
[quote=Len]Wasn't the powerbook G3 a newworld machine? If so, yaboot should work...

Anyway, to use BootX you must have the Ubuntu kernel on your Mac partition and set the Ubuntu boot partition with a comment like /dev/hda6. You can use Mac pdisk (google around a bit) to get the linux name of the linux partition. You can also start from the installation CD and look up the name in the partition program.[/quote] 
No, the wallstreet needs Xboot to start linux however, you would be much much better off using Xpostfacto and Tiger OSX.
If speed is your concern, forget Ubuntu, OSX on macs is faster than Linux. 
Let's stop this myth of "speed" which is total rubbish.
(please note that I am a strong Linux supporter. But not on the mac)

OSX is faster than Ubuntu on a low end mac, no matter what they tell you, because OSX is optimised for that h/w and runs better than any Linux distro. Forget Graphic acceleration with x.org on a mac!

You better check this out by yourself as I found it also hard to believe.

/P

---

