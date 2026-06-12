---
title: "What packages put files into /boot?"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by ronly on 2006-07-02
I updated my sources.list from breezy to dapper and then updated the whole system but ran into trouble: My /boot is on a separate partition and it became full during the update and consequently some files that should've gone there didn't and I don't know what those files are. The first indication of a problem was that the new default kernel 2.6.15-25-k7 didn't boot at all whilst the old 2.6.12-10-k7 worked as before. Once I realized what had happened I removed some of the old unused kernels from /boot to make space and then tried to reinstall what I thought I should to fix the problem and did notice that when I had reinstalled linux-image-2.6.15-25-k7, /boot/initrd.img-2.6.15-25-k7 increased in size and the date was updated. Then I managed to boot a little bit further than before with the new kernel since previously I got nowhere, now I got to mounting before the system hung. I've tried reinstalling linux-restricted-modules-2.6.15-25-k7 too and a few other packages that I've considered possible but according to the dates on the files the only one I manage to reinstall is initrd.img-2.6.15-25-k7. So I'm wondering what I should reinstall to update all the files in /boot? And if you can tell me how to find that out I'd obviously learn more, too. My problem could of course be caused by something else as well but at the moment I consider this a quite plausible cause. Thanks in advance!

---

### Post by catlett on 2006-07-02
Boot holds grub, kernels,initrd files and some text files (config and system map). You will have issues if you don't have a matching kernel and initrd. You may have gotten the kernel but not the initrd when you updated. Then if you deleted an iitrd and tried to boot it's matching kernel, you would also get an error.
I would keep trying older kernels until I got one to boot properly (by simply going down the ubuntu list in grub's menu). When I got into the system I would erase all the kernels and initrds except the one I was using. This will clear your boot folder.
Then I would do a dist upgrade.
```
sudo aptitude update
``````
 sudo aptitude dist-upgrade
``` That will update and install the new kernel and initrd. Next time you boot the new kernel will be there and you will still have the old one as a failsafe.

FYI  It is a good policy to keep at least one old kernel. That way if the new kernel has issues you can still boot with the old one. But more than that isn't needed unless you are making custom kernels.
Kernels and initrds can be aded and removed with Synaptic Package Manager. They are listed as "linux-headers" and "linux-image"

Good Luck.

---

### Post by ronly on 2006-07-02
I have one kernel with which I can boot and I did what you told me to, I removed the later versions and then sudo aptitude update but unfortunately the new one got stuck at
"Mounting root file system..." just like before so I booted with the old one (which, however, seems to be problematic with my sound card so I'm eager to update in case that would solve those problems). What I previously had as the newest one was 2.6.15-25-k7 but now the newest is apparently 2.6.15-23-386. After the update my /boot contains:

-rw-r--r--  1 root root  238155 2006-06-13 01:32 abi-2.6.12-10-k7
-rw-r--r--  1 root root  266619 2006-05-23 19:56 abi-2.6.15-23-386
-rw-r--r--  1 root root   63637 2006-06-13 00:58 config-2.6.12-10-k7
-rw-r--r--  1 root root   69878 2006-05-23 16:47 config-2.6.15-23-386
drwxr-xr-x  2 root root    1024 2006-07-03 04:18 grub
-rw-r--r--  1 root root 5642046 2006-07-02 17:47 initrd.img-2.6.12-10-k7
-rw-r--r--  1 root root 6764148 2006-07-03 04:18 initrd.img-2.6.15-23-386
drwxr-xr-x  2 root root   12288 2006-04-20 17:25 lost+found
-rw-r--r--  1 root root   94760 2005-10-25 13:32 memtest86+.bin
-rw-r--r--  1 root root  876312 2006-06-13 01:32 System.map-2.6.12-10-k7
-rw-r--r--  1 root root  725460 2006-05-23 19:56 System.map-2.6.15-23-386
-rw-r--r--  1 root root 1270426 2006-06-13 01:32 vmlinuz-2.6.12-10-k7
-rw-r--r--  1 root root 1414477 2006-05-23 19:56 vmlinuz-2.6.15-23-386

That is, what was updated was initrd.img-2.6.15-23-386 and grub obviously but nothing else :(

---

### Post by catlett on 2006-07-02
I was hoping for a quick fix.
You can manually add kernels and initrds from synaptic package manager.
Open up Synaptic and search for "linux-headers" and "linux-images". Just be sure to add the same version.
They will have little details when you select them. Try and match one to your system.
I would try a couple of kernels that were compatible with my system and then if there are still problems it may be something else.

Did you use the update manager to update to dapper? I lost my whole configuration when I upgraded through the update manager. I eventually downloaded the Dapper install ISO and did a fresh install.
You have a boot partition, do you have a home partition? If you have a home partition then you data will be safe from a fresh installation.
You may want to consider upgrading by installing dapper by running the install CD and just choosing to leave your home partition unformatted.
But first I would try another kernel from synaptic.

---

### Post by ronly on 2006-07-02
I'm trying that but I noticed this when I reinstalled with aptitude:

Not touching initrd symlinks since we are being reinstalled (2.6.15-23.39)
Not updating image symbolic links since we are being updated (2.6.15-23.39)

What symlinks should there be? Could that be part of the problem?

---

### Post by catlett on 2006-07-02
I'm not totally certain but the image symbolic link should just be the usplash you get when booting. That would be in your boot folder as well. Meaning the link to the ubunttu splash screen with the text running underneath when you are booting that says (loading essential drivers ...etc)
I recommended aptitude because it deals with dependency issues. Where apt-get doesn't keep track as well and you can up up with broken packages. So I recommend aptitude because it is safe. It won't do anything that will create a dependency issue.
Did you try a different kernel?

---

### Post by az on 2006-07-02
[QUOTE=ronly]I updated my sources.list from breezy to dapper and then updated the whole system but ran into trouble: My /boot is on a separate partition and it became full during the update and consequently some files that should've gone there didn't and I don't know what those files are. 
[/QUOTE]
sudo apt-get install --reinstall linux-image-2.6.15-25-k7

I'm a big fan of all-on-one-partition for this reason.

Also, remove older kernels using apt or synaptic, not by deleting the images yourself.

---

### Post by ronly on 2006-07-03
I have tried 

sudo apt-get install --reinstall linux-image-2.6.15-25-k7

and now also linux-image-2.6.15-23-386 but it didn't help. It still hangs at "Mounting root file systems..." - i.e. almost immediately. It is of course possible that it's some other problem but how could I find that out?

---

### Post by ronly on 2006-07-03
Some progress in investigating this problem but not solving it: 
A little bit of Googling led me to let the system wait for a really long time at the point at which I thought it had hung and that resulted in something:
After the "Mounting root file system..." it eventually (after several minutes) showed
"Waiting for root file system..." and then a while later:

Alert! /dev/sda3 (which is my root file system) does not exist. Dropping to a shell!

In the shell I took a look at /dev and noticed that it didn't contain anything at all. Some more Googling then revealed that this is a common problem on many machines (e.g. a PPC whilst mine is an Athlon64 although I don't run it as 64 bit since it's unfortunately still more trouble than I want to go through) and some think it should've been a show stopper for dapper. So thanks for all the advice how to install a new kernel - I'm sure I got all the files in /boot fixed when I manually moved *-386 elsewhere and then reinstalled until I had them back (the working kernel is -k7 so I knew I could do that). I'll search for a solution to that problem now and since it's common I might find a solution as well but I obviously appreciate it if you can tell me what to do straight away.

---

