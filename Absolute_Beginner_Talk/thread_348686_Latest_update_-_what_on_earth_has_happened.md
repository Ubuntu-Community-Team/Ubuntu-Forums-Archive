---
title: "Latest update - what on earth has happened?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Fishkeeper on 2007-01-29
Hi all,

My first visit and post here, recommended by a "friend" at work.

I must confess I'm a longstanding Microsoft user (not a customer!), not through any loyalty or other affinity though.  Simply cos that's what I've always used, and it's always been relatively easy to get hold of software.

My network at home includes 3 desktops and two laptops, all running Windows.  There is also a network storage device (which I believe runs some flavour of Linux), and my Linux test machine.

The Linux test machine (which was previously used as a data storage server using Samba) had Suse, Red Hat and Ubuntu installed.  Grub used to offer me the option to run whichever OS I wanted.

The so-called friend mentioned above gave me a disk with 6.10 on it so that I could try it out.  I wasn't sure how to use it, considering the status of the above system, but he told me that it booted to a live system with the option to install from the desktop.

So I had a go.... nothing ventured, and all that!  

The first time the installer froze at the point where you select your geographical area.  The installer window wouldn't advance, cancel or even close.  The desktop was still responsive though.  So I did the only thing I could - I restarted he system.

The second time was much more successful, though I didn't change anything in the way I did things.  The installer proceeded without too much trouble, but it was only when it started actually writing everything that I realised it hadn't asked me where it should go!  No option for Automatic or Custom install, no questions about which partition to use, no option to overwrite the previous Ubuntu (Hoary, I think).  Oh well, I thought - let's see what happens.

When it had finished I restarted the PC to find that it booted straight into 6.10 - no Grub choices.  It was late and I was so annoyed that I just shut the thing down and went to bed.

So, after a very long story (sorry!), I don't know what's happened - 

[LIST=1]
[*]Did 6.10 simply update Hoary and just assume I wouldn't want to ever run the other distros?
[*]Did it somehow wipe the other distros, so that now I've only got one Linux?
[*]How do I find out what's happened?
[/LIST]

The last one is really important to me, but if anyone can offer help please remember that despite my dabblings I'm a long long way from being a Linux techie.  Messing around in text files to change settings is scary to me, and I'm gonna need some understanding guidance!

If I can't find out what's happened and/or fix it then I'm dreading the prospect of wiping everything and starting again so that I can get the diversity I want.

Many thanks for reading, and even more if you can offer help!

Fishkeeper.

---

### Post by xhaan on 2007-01-29
It's possible that it wiped everything else out and just installed by itself...
I don't know about Edgy live cd as I used alternate cd to install Edgy, but I know with Dapper... I forget exactly how it goes but you have to watch carefuly for the option to set up partitions manually, if you dont click that option and instead click next by accident, it installs itself using the whole drive.

Id check and see if you have any other partitions left on that drive... if there is only one, 6.10 probably hijacked your whole drive.

---

### Post by randiroo76073 on 2007-01-29
Check in disk manager and see if you have any other partitions showing, if so it will take some editing of menu.lst to get your other boot options back.

---

### Post by jvc26 on 2007-01-29
The live cd does give you the option to select manually edit partitions table etc, but its easy to miss if you're not concentrating on it. I'd check your partitions table to see whether the other partitions are there:
```

sudo fdisk -l

```
Where l is L as in Larry.
If they are still there its just a matter of altering the grub menu to put the other boots back on.

The other thing - you mentioned a crashing live cd what are the specs of your computer? It may be that your RAM is low and hence the live cd is sluggish/unresponsive.
Il

---

### Post by Sef on 2007-01-29
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").  It might be able to recover your Window's partition.

---

### Post by Fishkeeper on 2007-01-30
Thanks for the replies all.

I looked at the thing called Device Manager, and then looked at the master IDE device.  There are just 3 volumes on there, configured as Volume, Volume (swap) and Volume (ext3).

Then I also ran the sudo fdisk -l in a terminal window.  That tells me that hda1 is the boot device, and is called Linux.  hda2 has the Extended label on it, while hda3 is called Linux swap/Solaris.

I don't know where to access the Disk Manager referred to - can someone help with that?

Doesn't look good does it?  :( 

Any further comments or ideas?  :confused: 

Fishkeeper.

[B]EDIT: I just tried booting from a Suse 10.xx disk loaned to me by a friend at work.  The system hung just after recocnising that the disk had a boot capability and reported something about ISOLINUX.  Maybe my PC is broken?

To answer another earlier question, the PC has 512Mb of RAM.[/B]

---

### Post by louieb on 2007-01-30
From what you said about the output of fdisk. Edgy has taken the whole hard drive over.
Hope you had a backup. If not you can try Sef's suggestion of Test Disk.
> If I can't find out what's happened and/or fix it then I'm dreading the prospect of wiping everything and starting again so that I can get the diversity I want.

If you have to set up again use the Gparted  CD and create a few 2  to 7 gig partitions for later installation of whatever distro. Also create a 1/2 gig partition and format it as swap. (all the future distros can share the swap partition). 

Also checkout the Dual Boot site in my signature for some ideas on how to set GRUB up to easily  change the configuration when a distro is added or replaced. I have a PC with a 40 gig hard drive it can boot up to 8 different distros at any given time.  It works alright and you will find the installs for most Linux distros works almost the same.

---

