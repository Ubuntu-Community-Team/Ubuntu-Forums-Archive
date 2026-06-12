---
title: "[SOLVED] kernel update broke manual installs"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by ThunderRd on 2008-01-19
In this thread:
[http://ubuntuforums.org/showthread.php?t=660806](http://ubuntuforums.org/showthread.php?t=660806)

I got some help to manually install support for some local SATA drives, and also to manually install sound packages into 7.04.

Subsequently to that, update manager asked for some downloads, which I allowed.  After the downloads, I found another entry in the GRUB menu for a kernel update to 2.6.20.16 from 2.6.20.15.  Now, both the manual installs are broken in the new kernel only.  I can still boot to the old kernel and everything is OK, so it's not a serious problem, but I'm trying to learn the right way to do things.

For now, I would like to get the drives working in kernel.16, then after that the sound.  As you can see by the original thread, after trying many things I finally reinstalled Ubuntu and started over with the driver installs before they settled down.

Attached are three text files.  One is the output of the sata install in the new kernel-it looks ok, but the drives aren't seen afterwards, according to fdisk.

The other files are the boot syslogs of both kernels.

If and when I can get these installs working, I will try to mount the network shares on the remote machines.

---

### Post by rkd on 2008-01-19
I don't see the attached text files. Am I overlooking them somehow, or did you forget to attach them?

---

### Post by ThunderRd on 2008-01-19
ooops...

---

### Post by ThunderRd on 2008-01-19
I don't think those files will be formatted correctly.  Try this one if they aren't.

---

### Post by rkd on 2008-01-19
I think I understand why the update for the SATA controller didn't have any effect. It is specifically for kernel 2.6.15. At least the message in the build output said it was updating 2.6.15, and the documentation that comes with it says it is for 2.6.15. There are more complicated instructions in the documentation about how to apply the patch to other versions of the kernel. We may have to perform the more complicated update procedure. But let me look around a bit to see whether there is anything easier.

---

### Post by ThunderRd on 2008-01-20
Ahh, ok.  Then I didn't do anything wrong ;)

---

### Post by rkd on 2008-01-20
Okay, I couldn't find a prebuilt module for 2.6.20-16, so it looks like we need to compile it ourselves. The procedure is pretty long. It comes from section 4 of the readme.pdf file that was among the files you used successfully to get the SATA drive working on 2.6.20-15. I found a couple of mistakes while working through it, which should make it a bit easier for you.

At a high level, we download the Linux kernel source, copy a few of the files into a temporary directory, apply patches from VIA to two of those files, compile them to produce updated modules, move those updated modules into the directory where Linux expects them to be, then do a little magic I don't completely understand to get them installed.

I don't understand this process completely. It appears to me that we are taking the 2.6.20 base source files and applying VIA's patches to them. So if there were any bug fixes applied to those two files in the updates between 2.6.20 and 2.6.20-16, we would be losing them. I don't know where those updates come from, so I don't know where to go look to see whether there are any bug fixes for the files we are patching. I suppose the chances are small that there are bug fixes in the few files we are recompiling, but I think it is a theoretical possibility that I'd like to know what to do about. I think, though, that it is safe to proceed without figuring out that detail.

We need a Makefile when we are compiling the patched source files. Let's set it up now, before starting the main procedure. To do that, put the following lines into a file named Makefile (capitalized exactly as I wrote it - capital M, the rest lower case) in your Desktop/sata directory:
```
KERNVER = `uname -r`
KERNELDIR = /lib/modules/$(KERNVER)/build
obj-m := sata_via.o ahci.o
PWD := $(shell pwd)
all:
	$(MAKE) -C $(KERNELDIR) SUBDIRS=$(PWD) modules
```
I don't know whether the forum will preserve it, but there MUST be a tab character as the first character of the line following the line containing "all:". Substituting spaces for the tab will not do. This is a peculiarity of the make program, which reads the Makefile and uses it as directions for how to do the compilations and other steps.

When you work through this procedure, my suggestion is that you copy one line at a time into your terminal window, so that in case there is an error, you don't let things run ahead until you have a chance to fix it. It would also be a good idea to copy the output from each command and paste it into a text file, so we can look at it later, if necessary to review what happened.

I suggest you logon as root to do this whole procedure. Perhaps most of the steps could be done with sudo, but we saw that didn't work for some things when compiling from source in the sound software build you did. Let's assume we need to do this whole procedure as root.

You need to be booted from the 2.6.20-16 kernel when doing this procedure so that the places where it uses `uname -r` to construct directory names ends up pointing at the new kernel directories, not the old ones.

First, we get the things we need to compile the kernel and the kernel source:
```
apt-get update
apt-get install linux-kernel-devel
apt-get install linux-source-2.6.20
apt-get install linux-headers-`uname -r`
```
Next, untar the Linux source:
```
cd /usr/src
tar xvjf linux-source-2.6.20.tar.bz2
```
This tar run extracts a LOT of stuff, and so displays a lot of filenames. That tends to hide error messages. I don't know whether there is a way to get it to work silently and display only error messages. I'm pretty sure it will tell you at the end whether there were any errors, so errors won't go completely unnoticed. 

Next, we create the work directory in which we'll do the compilation and copy the files we'll need into that directory. We copy some source files from the Linux source, the patch files from VIA, and the Makefile we created above. The directions from VIA said that all the files from the Linux source would come from ...../drivers/scsi, but I found that two of them come from ....../drivers/ata. I don't know whether that is a danger sign or not. I hope I guessed correctly the full path name for your directory in which are the patch files and Makefile.
```
mkdir /tmp/viapatch

cd /usr/src/linux-source-2.6.20/drivers/ata
cp sata_via.c /tmp/viapatch
cp ahci.c /tmp/viapatch

cd /usr/src/linux-source-2.6.20/drivers/scsi
cp scsi.h /tmp/viapatch
cp scsi_typedefs.h /tmp/viapatch

cd /home/thunderrd/Desktop/sata
cp sata_via_ubuntu7.04_V130.patch /tmp/viapatch
cp ahci_ubuntu7.04_V130.patch /tmp/viapatch
cp Makefile /tmp/viapatch
```
Now we switch to the working directory and apply the patches to the two source files.
```
cd /tmp/viapatch
patch <sata_via_ubuntu7.04_V130.patch
patch <ahci_ubuntu7.04_V130.patch
```
Now its time to compile:
```
make
```
The make produced about 14 lines of output in my test. It has a C compiler warning that in function 'svia_init_one', 'bar_sizes' may be used uninitialized. I looked at the source and it appears to be a warning that can be safely ignored.  Most of the rest of the make output are CC or LD lines that report making various .o and .ko files in the /tmp/viapatch directory.

If that seemed to go okay, we go on to move the modules into the place where Linux needs them. I had to stop at this point because I haven't upgraded my system to the new kernel yet.
```
cd /lib/modules/`uname -r`/kernel/drivers/ata
mv sata_via.ko sata_via.ko.orig
mv ahci.ko ahci.ko.orig

cp /tmp/viapatch/sata_via.ko .
cp /tmp/viapatch/ahci.ko .
```
Note those last two commands are copying into the current directory, denoted by a '.' standing alone. Don't overlook it or try to close up the space before it.

Next comes some magic I don't fully understand.
```
depmod -a

modprobe libata
rmmod ahci
rmmod sata_via
modprobe ahci
modprobe sata-via
```
depmod builds some kind of module dependency information. I don't know what uses that information. The rmmod commands remove a module from the current running system. The modprobe commands load a module into the current running system. I don't know why it has to do something with libata, but the other four commands simply remove the old modules and load the ones we just built.

At this point, the SATA disks should be accessible.

Something I don't see is a step to update the initramfs image. We saw a message about that when running the install of the prebuilt modules for 2.6.20-15. I believe initramfs is the initial ram filesystem that is used for a short time during the booting of Linux. If it does not get updated with the new modules, I imagine you could not boot from the SATA disks. I don't know whether it would also prevent automounting them -- that would depend on whether the boot process does the automounting before switching from the initramfs to the normal filesystem or after. 

Perhaps we can learn how to do the update of initramfs by mounting the disk image that contains the 2.6.20-15 prebuilt modules install and looking at that install script. I didn't have time to do that today. Even if the update of initramfs is missing, I think that won't keep you from using the disks.

Okay, I think that covers it all. I hope I didn't overlook something.

---

### Post by ThunderRd on 2008-01-20
Wow.

I have looked at this monstrosity and am really wondering if it's worth the risk of breaking stuff, when everything is working in kernel .15.

I mean, it's no problem to edit GRUB and default boot to that kernel, and wait for a prebuilt package.  I mean, I like to learn, but I wonder if this is too much at this stage...

What are the risks to break kernel .15?  If it's safe enough, I'll try it.  You have put a massive effort into this and I'd love to see it work just because of that :)  What do you think?

I guess there's another question that begs answering.  When update manager bugs you for an update allow, how do you make your decision?  I mean, how crucial is it to update daily or weekly, and should it really be done?

Or would it be better to go to 7.10; I wonder if these sata and sound problems are already taken care of?

Too many new user questions ;)

---

### Post by rkd on 2008-01-20
I think it is pretty safe to experiment. As far as I can tell, Linux keeps the files for each kernel version clearly separated. That is why the kernel version from uname appears a number of places when building directory names. So the 2.6.20-15 kernel ought to be pretty safe. Except for the time required to download the kernel source and other packages, the process goes very quickly, too, so you won't have to spend a lot of time to try it unless you run into some error I didn't anticipate.

The worst case I can imagine is that if it does mess up your 2.6.20-15 installation, you'd have to wipe the partition clean and do a fresh install. You just did that a short time ago with 2.6.20-15, so you know you can get that set up again pretty easily, right? 

Well, I guess there is a worse possible outcome: The update might make the 2.6.20-16 system go crazy and write all over your non-Linux partitions on some of your disks. I think the chance of that is very small.

I don't have very much experience with using Ubuntu or any other Linux systems, so I don't know what to advise about accepting updates. For a home user, it ought not to be as critical to keep updated as it is with Windows systems simply because there are so few threats from people trying to attack Linux systems. I haven't looked closely at it, but I believe I saw something in the update manager that allows you to choose between security updates and enhancement updates. I imagine that if you accepted only security updates, there would be less chance of an update breaking something, but I don't have enough experience with it to say that with confidence.

When I was searching for solutions to this and the sound problem, I don't remember seeing any clear indication that either was fixed in 7.10, so I don't believe that is an easy answer. If the bandwidth you have doesn't make downloading the 7.10 Live CD a problem, it would be easy enough for you to boot from the live CD to check your sound and SATA operation to be sure on that point. Also, it seems that 7.10 has had a bit more problems with it than earlier Ubuntu releases did -- things that used to work stopped working for quite a few people. I don't know whether that's an accurate impression or just the result of fairly loud complaining by the people who did run into problems. On the other hand, since you are just starting out with experimenting with Ubuntu, it might be reasonable to adopt the most recent version as your starting point, just to be on the most recent release. I think the procedure for updating the SATA driver module and the sound software would be no harder than they are on 7.04.

I'm so new to Ubuntu that I can't give very authoritative advice on that subject, but those are my impressions.

---

### Post by ThunderRd on 2008-01-20
OK then, it doesn't sound too bad.  I'm at my shop now but I will get on it when I get home, then I'll post back.

AFA the new version, I'll wait until the CD arrives, and make a decision then.

---

### Post by ThunderRd on 2008-01-22
I've been working on this and have run into the first snag.  It's in the "magic" stage:

> **rkd said:**
> 
Next comes some magic I don't fully understand.
```
depmod -a

modprobe libata
rmmod ahci
rmmod sata_via
modprobe ahci
modprobe sata-via
```
depmod builds some kind of module dependency information. I don't know what uses that information. The rmmod commands remove a module from the current running system. The modprobe commands load a module into the current running system. I don't know why it has to do something with libata, but the other four commands simply remove the old modules and load the ones we just built.

OK, everything weht ok up until this point;  there weren't any error messages of any kind that I saw.  But  rmmod ahci returned a module does not exist message.

I stopped there to give you a chance to think about it. ;)  Output attached.

---

### Post by rkd on 2008-01-22
Since the purpose of the rmmod command is to remove the module from memory, I think it is okay to ignore the error, since the error is just telling us that the module isn't loaded.

If you still have the computer running on the 2.6.20-16 kernel, continue with the last three commands. If you get any error messages, copy them but continue to the end and see whether the SATA disks work.

If you have shutdown or switched to the older kernel, when you boot the 2.6.20-16 kernel, you probably won't have to do any of the remaining commands -- it should try to load those modules during the boot. But if the SATA disks don't work after a boot of 2.6.20-16, it won't hurt to try those last three commands (though I doubt they would make a difference in that circumstance).

So continue when you have a chance and let me know the result. If the SATA disks don't work, post the recent part of the system log, in case there are any clues there.

I might not be able to respond very quickly -- the apartment I live in is to be fumigated because of termites and I am packing up to move out for a couple of days. I should be able to get internet access at the motel, but I can't be certain that will work until I try it.

---

### Post by ThunderRd on 2008-01-22
Result: it works.

Maybe I'm easily impressed, but I have given and taken help on forums for many years; I have rarely had it so easy as this ;)

I hope that the help I have given others was half as effective.

Care to install some audio drivers?  Let me know when you have time, I know you're tied up in knots about now.  Thanks again.

-tr

EDIT:
Realtek sound package installed ok and without problems.

Next step; I have to get some help with mounting remote drives and editing fstab;  I will organize my thoughts about what I need and post back here.  Or maybe better to open a new thread and I'll PM you.  Not sure I want another teacher. :)
BTW: the 7.10 CD arrived today.

---

### Post by rkd on 2008-01-22
Good! I'm glad it worked. The main credit should go to Via, since I just had you follow the directions they gave in their readme.pdf file.

I'm happy to see that you went ahead with the installation of the audio stuff without waiting to hear from me. I would have told you to repeat exactly the procedure that worked on the previous kernel. I assume that's what you did.

You are right that you ought to start a new thread for your questions about mounting drives and editing fstab. Someone else might be able to figure out your problem faster than I could. Please do send me a PM when you have posted it to be sure I don't miss it.

---

