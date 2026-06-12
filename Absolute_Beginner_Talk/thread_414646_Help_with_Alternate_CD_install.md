---
title: "Help with Alternate CD install"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by CalvinChile on 2007-04-20
Hi, I tried to install Feisty using the alternate CD but after moving the source.list to a backup file and then done the:

*sudo apt-cdrom add*

 I got this in the xterminal
[I]
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [807b48b95dbcfb1bfcf159f7e300c038-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called:
'Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)'
Copying package lists...gpgv: Signature made Tue 17 Apr 2007 01:15:20 AM CLT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
[/I]

but then got an error on the following command
get the folloging error when I issue
[I]sudo apt-get update

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory[/I]

Before trying the Alternate CD install I had tried the internet upgrade but had to abort due to connection problems.  

How can I solve this?

Thanks in advance

Calvin

---

### Post by jetpeach on 2007-04-20
my best guess: I think the problem is that another program (e.g., synaptic) already has "locked" the apt upgrading files. If you make sure any other upgrading programs are killed/closed, then try the sudo apt-get update again it might work. if you don't know what program might be locking the upgrade files, you could reboot and that might work as well, although i think the default configuration also starts synaptic upgrade on startup. you could also now just use synaptic to upgrade it instead of the terminal, and it should be looking to the CD because your source list was successfully changed to the CD.

---

