---
title: "Help. Grub will not load past stage 1.5"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by tinnies on 2008-01-17
Please help before I pull all of my hair out.

Six weeks ago I  bought a new Dell inspiron with an AMD Turion64 dual core processor, 2gigs ram and twin hard drives with Vista preinstalled. The graphics card is an ATI Radeon Express 1270.

This was going to be superfast right? Wrong. Even after stripping vista of everything I could it was still snail paced so I decided to bite the bullet, back up my data,  format the hard drives and install Ubuntu.

First I tried installing the 64bit version of 7.1.0. The install went fine until I tried to reboot and was confronted by this screen:

GRUB loading stage 1.5

GRUB loading, please wait

Error 2

Unperturbed I tried installing the i386 version. Same result.

Please advise before I just give up and install xp instead

---

### Post by kaan on 2008-01-17
Use the 64 bit version. At the boot screen go to check installation medium. If your CD checks out fine, then try using the Live CD to check and repair your hard drive, reformat, reinstall. 

As far as I can tell from a quick google search, you probably have a bad sector on the hard drive but it could also be a bad CD. 

According to [http://www.gnu.org/software/grub/manual/grub.html#Stage1-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage1-errors)

Error 2 is:
Bad file or directory type
    This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO.

---

### Post by tinnies on 2008-01-17
Thanks for that. 

I've checked the cd and it passed the test. I'm currently running a memory test.

I'll try Live cd.

Am I right in thinking that I'll need to give ubuntu it's own partition on one of my drives?

---

### Post by kaan on 2008-01-17
> **tinnies said:**
> Thanks for that. 
Am I right in thinking that I'll need to give ubuntu it's own partition on one of my drives?

I don't see how you would complete an install without creating a partition for ubuntu. If you want to keep things simple it should be on the drive you boot off of.

---

### Post by tinnies on 2008-01-17
Sorry if I appear obtuse, but let me get this straight as partitioning is not something I'm entirely sure about.

Live cd is the same as the iso I burned off with ubuntu on it? And I can use this to format my drives?

The drive I boot from will generally be the one with the lowest number?

Do I format the entire drive and install ubuntu on that, or do I parttiton the drive and install ubuntu on the partition?

I'm not really thick. Honest

---

### Post by Sef on 2008-01-17
> Sorry if I appear obtuse, but let me get this straight as partitioning is not something I'm entirely sure about.

That's ok. You're asking questions to learn.

> Live cd is the same as the iso I burned off with ubuntu on it? And I can use this to format my drives?

Yes, and yes.

> The drive I boot from will generally be the one with the lowest number?

Not necessarily.  If you have a dual boot, it could be either os.

> Do I format the entire drive and install ubuntu on that, or do I parttiton the drive and install ubuntu on the partition?

You can do it either way.

> I'm not really thick. Honest

We all had start at the bottom, so you are in good company.

---

### Post by Sef on 2008-01-17
> First I tried installing the 64bit version of 7.1.0. The install went fine until I tried to reboot and was confronted by this screen:

GRUB loading stage 1.5

GRUB loading, please wait

Error 2

This is error 2 from the [GRUB Error Collection]("http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html"): 

> 2 : Bad file or directory type
    This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO.

With the Live CD, open the terminal (Applications > Accessories > Terminal), then type this code:  ```
sudo fdisk -l
``` (Small L.)  Paste what you see in here.

(I'm thinking that you may have tried to install Ubuntu onto an NTFS partition instead of formatting it to ext3.  NTFS is a Microsoft propriatery file system, which Ubuntu cannot install on without having problems.)

---

### Post by azad on 2008-01-17
Try installing Ubuntu again.

This time try manually partitioning drives. Since you don't want Vista, it will be easier.

Create 2 partitions. sda1 and sda2. Format them as ext3 and set mount points / and /home

Since you have 2 GB of RAM, you don't need a SWAP partition.

Let is know how it goes.

---

### Post by tinnies on 2008-01-17
Sorry about the delay,I had to go out.

This what terminal had to say:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000836b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7128    57255628+  83  Linux
/dev/sdb2           13710       14593     7100730    5  Extended
/dev/sdb3   *        7129       13709    52861882+  83  Linux
/dev/sdb5           13996       14593     4803403+  82  Linux swap / Solaris
/dev/sdb6           13710       13995     2297232   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

In the meantime I'm going with Azad's advice and attempting to manually partition the drives before installing.

I'll keep you posted

---

### Post by tinnies on 2008-01-17
Tried formatting and partitioning the drive as suggested. Both with and without a swap partition.

Same result:

Error 2

Don't knoiw if this makes any difference but the names of the partitions were set as sda1 and sda5 rather than sda2.

I didn't seem able to edit these.

Am rolling my sleeves up and giving it another go

---

### Post by tinnies on 2008-01-17
Tried formatting and partitioning the drive as suggested. Both with and without a swap partition.

Same result:

Error 2

Don't knoiw if this makes any difference but the names of the partitions were set as sda1 and sda5 rather than sda2.

I didn't seem able to edit these.

Am rolling my sleeves up and giving it another go.

Stop press+++++++

I just loaded up live cd again and the disk usage analyser told me there are no mount points on the disc therefore it cannot analyse.

I opened the installer again and the / and /home mount points I'd set had changed to /mediasda1 and /mediasda5

Have changed them back and am now trying again

---

### Post by dstew on 2008-01-17
The error you are getting is from grub's stage 1.5. That means that grub is not installed properly, and cannot find or load its stage 2. The only way to solve this is to re-install grub.

---

### Post by tinnies on 2008-01-17
How do I re-install grub? Is it from the live cd?

By the way another install attempt and the partitions were both renamed same as last time again.

---

### Post by dstew on 2008-01-17
To re-install grub, boot a live CD and open a terminal. Enter **grub**. This should get you the grub command line, with the grub> prompt. At the grub prompt, enter```
find /boot/grub/stage1
```In your case, you might get more than one answer, maybe (hd0,0) and (hd1,0) and maybe even (hd1,2). Use the first result in a grub root statement```
root (hd0,0)
```Then setup grub in the MBR of your first disk```
setup (hd0)
```After that, enter **quit** and reboot. See what happens.

---

### Post by tinnies on 2008-01-17
Tried that and after entering:

find /boot/grub/stage1

I got:

Error 15: File not found


I'm thinking that the partitioner is not having a good time with my hard drives and that the problem lies there.

I've no idea how to remedy this though...

---

### Post by dstew on 2008-01-17
Seems like something is wrong with the disk partitions. From the LiveCD, do another sudo fdisk -l and post the results.

---

### Post by tinnies on 2008-01-18
After typing sudo fdisk -l  all I got was another command line prompt.

I'm going to work now and when I get home I'm going to install xp and be done with it. 

It would have been great to go open source but however hateful it may be at least windows works. Consistently.

Thanks for your help

---

### Post by azad on 2008-01-18
Hey tinnies, sorry you decided to go back to XP.

Ubuntu installs and runs smooth on my hardware. Never had any issues whatsoever,

Have a go at other Linux distros. Try PCLinuxOS "Minime".

Maybe have another try at Ubuntu. During installation, Use the option "Use Entire disk".
If that doesn't work. I'm sorry mate.

---

### Post by philinux on 2008-01-18
> **tinnies said:**
> After typing sudo fdisk -l  all I got was another command line prompt.

I'm going to work now and when I get home I'm going to install xp and be done with it. 

It would have been great to go open source but however hateful it may be at least windows works. Consistently.

Thanks for your help

It sshould have been

[FONT="Times New Roman"]sudo fdisk -l[/FONT]

ie -l small L

---

### Post by tinnies on 2008-01-18
What really strikes me about this whole experience of trying to go open source is how vanity gets in the way of really useful information. It's a little like visiting a digital gym, where the guys (as they invariably are) with the biggest digital pecs like to stand in front of a mirror i.e. someone like me who has limited technical knowledge but would like to be included in the open source world, and flex those beefcake muscles proclaiming the ease with which all this technoliberation comes to them and how if that is unattainable on a lesser (mine for example) setup then what a shame, but still, let the techno-illuminati admire themselves for just a split second as they aren't the ones dealing with a Dell-piece-of-****-laptop (as is proclaimed by comparison in parenthesis at the bottom of each posting).

I'm sure (no really) that ubuntu is a fantasic operating system and I'd love to be able to use it and at the same time steer clear of that awful man Gates, but unfortunately windows is going to win due to the simple fact that it works, without any technical knowledge from the user, albeit within a limited and expensive framework.  Surely this breeds a climate of computer users and possibly members of society at large who have no detailed knowledge or ability to influence in a meaningful way a core part of their existence i.e. computers, but without a little more inclusion for the uninitiated then linux remains an elitist haven where the hopes of the masses are dashed by the waves of totalitarianism upon the rocks of hubris.

All in all a thoroughly dispiriting experience.

---

### Post by azad on 2008-01-18
Hi tinnies, I understand your frustration.

I installed Ubuntu on my desktop 6 months ago. The installation was done in 6 to 7 clicks, within less than 20 minutes. Everything is working flawlessly. I must be really lucky.

Linux does not go well with many people. I've given Ubuntu CDs a lot of friends and many are facing various issues with it. One guy can't get his wireless working. Another guy can't use his webcam.

I'll have to admit that installing Windows XP/Vista works out of the box for most people. That's because hardware makers develop drivers for Windows. Linux is often overlooked. Linux developers use reverse engineering techniques to make them work. 

This is why Windows has better hardware support than Linux.

But Linux is no longer an elitist haven. I myself am a new linux user and there thousand of us here. Linux community is full of helpful individuals willing to help newbies.

I strongly recommend that you give a shot at a different distribution. Try Mandriva or PCLinuxOS. With Mandriva, you can buy the Powerpack and get legal Multimedia and DVD support.

Give Ubuntu another try in April, when Hardy Heron comes out. Maybe that will work out of the box on your machine.

Anyways, good luck.

---

