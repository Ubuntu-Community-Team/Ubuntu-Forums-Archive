---
title: "vmware with existing installation?"
date: 2007-07-13
forum: Apple Intel Users
---

### Post by tchorix on 2007-07-13
Hi guys,

I have a dual boot with 25GB for macosx and the rest for Ubuntu... Is it possible to run the linux partition from macosx using vmware fusion? or do I have to make a new instalation of Ubuntu in the macosx partition?

cheers
Tch

---

### Post by cyberdork33 on 2007-07-13
I believe that is only possible with windows, but if you can get it working there are others that would like to do that too.

---

### Post by thully on 2007-07-13
It can be done, but it requires editing config files by hand.  I don't know off hand how to do it, but I remember seeing something on this on the VMware Fusion forum at vmware.com.

---

### Post by cyberdork33 on 2007-07-13
The way I would attempt to do it is be creating a "windows" vm to book from bootcamp and set it to the correct partition somehow. I really have no idea of how to go about that though. This would be very interesting to setup though.

---

### Post by cryptocoryne on 2007-07-15
I looked in the vmware forums and I couldn't find anything.  But maybe I didn't pick the right keywords.  I have ubuntu installed on one partition and Tiger on another. It would be so cool to be able to run my existing ubuntu system from OS X or by rebooting.  I remember running windows 98 installed on a separate partition with vmware under linux.  This was in 2003, so I don't remember exactly what I was doing. 

Looking at the GUI to the OS X beta version of vmware, I am really surprised by  how limited its functionality appears to be.  There were a lot more options in vmware linux, at least in 2003.

---

### Post by tchorix on 2007-07-16
Well, I also spent a couple of hours searching in forums and documentation, but I didn't find anything about this. I just read that it was possible to do it with an existing windows partition, but I'm not interested in doing that. And as cryptocoryne mentioned, the options are really limited in vmware fusion.

thanks anyway for the replies.
cheers
Tch

---

### Post by cryptocoryne on 2007-07-16
I gave up on vmware and started experimenting with Q and virtualbox.  Neither of the three seems to be able to boot from a partition, at least via GUI-configurable settings. Virtualbox seems to be more efficient than Q; my macbook's fan does not come on as much and things feel more responsive. But I am concerned about virtualbox: it keeps connecting to websites I've never heard of.  When Little Snitch  caught virtualbox trying to connect to paypal.com, I got suspicious and stopped running it.

I'm going back to vmware because:
1. Q makes my fans blow like a hair dryer.
2. Virtualbox is up to something.

btw, I am using the 50MB iso image of Damn Small Linux for testing. It's a quick download and doesn't require me to create massive virtual drives(500MB+ vmdk files or whatever) and there's no tedious installation process.

---

### Post by cyberdork33 on 2007-07-16
Q (actually Qemu with a nice GUI) may be able to boot from a real partition. You would have to manually edit a config file though I am pretty sure.

---

### Post by tchorix on 2007-07-17
cryptocoryne and cyberdork33,

Thanks for the feedback. At the end of the week I will have some time to play with Qemu and its configuration files. I'll let you know if I can make it run.

cheers
Tchorix

---

### Post by dfennell on 2007-07-30
Hi tchorix,
the documentation page for using host drives with a QEMU guest system is [here]("http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC21"). The details for a Linux host are clear, but not a Mac host. I suspect that the parameters for a Mac host would be something like 'qemu -hda /dev/disk1', but I would test this on a non-critical disk first. Also note the recommendation in the Linux host section regarding the '-snapshot' option.

If you get this going and want to share a Mac folder with the client Ubuntu system, check out my How-To article [here]("http://qemu-forum.ipi.fi/viewtopic.php?t=3910&sid=5bfd698d11913456bf1a282eb4fad80e").

David

> 3.6.5.1 Linux
On Linux, you can directly use the host device filename instead of a disk image filename provided you have enough proviledge to access it. For example, use `/dev/cdrom' to access to the CDROM or `/dev/fd0' for the floppy.
   . . .
Hard disks
    Hard disks can be used. Normally you must specify the whole disk (`/dev/hdb' instead of `/dev/hdb1') so that the guest OS can see it as a partitioned disk. WARNING: unless you know what you do, it is better to only make READ-ONLY accesses to the hard disk otherwise you may corrupt your host data (use the `-snapshot' command line option or modify the device permissions accordingly). 
   . . .
3.6.5.3 Mac OS X
`/dev/cdrom' is an alias to the first CDROM.
Currently there is no specific code to handle removable medias, so it is better to use the change or eject monitor commands to change or eject media. 

---

