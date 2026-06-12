---
title: "Need to mount and view a UDF CDROM"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by t2000kw on 2007-05-17
I have a few CDROMs that were written to using the UDF format and now need to access them.

How do I go about doing that?

I have two CD/DVD drives in case that makes any difference.

I can't get to the information using  mount -t UDF /dev/cdrom (tried UDF in either lowercase or uppercase, doesn't matter).

---

### Post by n8bounds on 2007-05-18
udf linux support is a recent and in development thing

sudo aptitude install udftools

Description: tools for UDF filesystems and DVD/CD-R(W) drives
 This package contains a number of user-space tools related to creating filesystems in the UDF (Universal Disk Format), which is
 primarily used for DVDs, but sometimes also CD-ROMs:

 mkudffs - Format a device, creating an empty UDF filesystem
 cdrwtool - Low-level drive management (e.g. set writing speed, format)
 pktsetup - Set up a packet writing device (/dev/pktcdvd0) for a drive
 wrudf - Maintains a UDF filesystem

 Homepage: [http://sourceforge.net/projects/linux-udf/](http://sourceforge.net/projects/linux-udf/)



maybe that will help

other things I found real quick:
[http://gentoo-wiki.com/HOWTO_Packet_Writing_on_CD-RW](http://gentoo-wiki.com/HOWTO_Packet_Writing_on_CD-RW)

[http://www.cdrinfo.com/forum/tm.asp?m=99077](http://www.cdrinfo.com/forum/tm.asp?m=99077)

---

### Post by t2000kw on 2007-05-18
Thanks--that got me partly there, I think. I was able to install udftools. My fstab shows it is there for CDROMs but it's not working for me. I try to view it with Thundar file viewer and it says it can't mount the volume. 

The first link wasn't much help, no docs there to view. 

The second one refers to CD-RWs (this is a CD-R) and requires a kernel rebuild. I'd prefer to not compile a kernel (as a beginner). 

I'm not sure if I understand the third link's suggestion on using "auto." (see bottom of the posts there.)

Do I change "noauto" to simply "auto" and it will work? I don't want to screw something up here.

Here's the pertinent section in my fstab file:

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by t2000kw on 2007-05-18
> **t2000kw said:**
> Do I change "noauto" to simply "auto" and it will work? I don't want to screw something up here.

-------------------------------------------------------------------------------------------
Here's the pertinent section in my fstab file:

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
------------------------------------------------------------------------------------------------

Well, while waiting for a reply, I thought I would try this and it didn't work. I figured that I could back up the original fstab file in case problems arose. 
 
I would think that there would be a way of getting the file system recognized by the GUI. 

If not, I guess I can go back to Windows to do that work. Windows ME automatically adds a UDF driver to read these CDROMs. I was hoping to get away from depending on Windows for things like this. I would then have to get the two computers to talk to each other over the network. Haven't tried that yet. Or, maybe XP can read them and I can save the files on the hard drive, then read them from Linux and save them in a Linux partition.

---

