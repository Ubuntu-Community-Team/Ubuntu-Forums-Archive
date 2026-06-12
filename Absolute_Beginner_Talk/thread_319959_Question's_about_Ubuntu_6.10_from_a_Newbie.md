---
title: "Question's about Ubuntu 6.10 from a Newbie"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by ervyxx on 2006-12-16
Hi All!

After so many days, alas I installed Ubuntu 6.10 on my desktop. Bought a new Hitachi 160 GB SATA HDD specially for Ubuntu.

Installed in no time, Ubuntu boots in 20 - 25 seconds flat and login takes another 10 secs which is cool.

OK, am a total newbie so here are a few questions:

1. What is the user name of Root/Admin? Is it root? also what the default password? (I didn't specify any while installing as it didn't ask)
2. I cannot play my Unprotected DVD. Error message thrown at me is as follows: "Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it."

Regards,

ervyxx

---

### Post by ervyxx on 2006-12-16
Man, the Totem player cannot even play VCDs, AVIs, MPGs

How do i go about it?

---

### Post by taurus on 2006-12-16
1.  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

2.  Install automatix2 and use it to install all the codecs for your media...
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by Bachstelze on 2006-12-16
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by 23meg on 2006-12-16
> 1. What is the user name of Root/Admin? Is it root? also what the default password? (I didn't specify any while installing as it didn't ask)The default user is a sudoer; that is, it can temporarily become root with the sudo command. The root account is disabled by defaut. 

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by ervyxx on 2006-12-16
Hey all,

Thanks. Installed libdvdread3 just now. will try to follow the procedure further.

Also, is there a way to access my NTFS partitions on my other Hitachi 160 GB SATA HDD?

---

### Post by rune_kg on 2006-12-16
1)
Install Automatix2. [Ubuntuguide.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu")
Select the codecs packages and install

Rune Kaagaard
http:/runelyd.dk

---

### Post by Old Pink on 2006-12-16
To play a DVD, I recommend using MPlayer. 

Open a terminal, and type:```
sudo apt-get install mplayer
```if it prompts a password, then simply enter the password you use to log in with.

---

### Post by taurus on 2006-12-16
> **ervyxx said:**
> 
Also, is there a way to access my NTFS partitions on my other Hitachi 160 GB SATA HDD?

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by tom56 on 2006-12-16
> **rune_kg said:**
> 1)
Install Automatix2. [Ubuntuguide.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu")
Select the codecs packages and install

Rune Kaagaard
http:/runelyd.dk

It is not recommended that you install software from anywhere other than the official Ubuntu repositories for several reasons. Automatix and Easybuntu can cause problems in distro updates (i.e. you might have trouble upgrading to 7.04 come April). It is also bad practice for security reasons (though Automatix and Easybuntu are both fine).

---

### Post by ervyxx on 2006-12-16
Hey!

Followed the procedure - 
**Playing encrypted DVDs**

Installed everything yet totem doesn't play anything :(

---

### Post by riven0 on 2006-12-16
> **ervyxx said:**
> Hey!

Followed the procedure - 
**Playing encrypted DVDs**

Installed everything yet totem doesn't play anything :(

Hey, why don't you try:

> sudo apt-get install libdvdread3 gxine gstreamer0.8-dvd

Or you can search for those programs in synaptic package manager and install them through there.

Welcome to Ubuntu! :D

---

### Post by ervyxx on 2006-12-16
Hey the synaptic package manager is gr8. I can now open individual VOB files.

:)

---

### Post by ervyxx on 2006-12-17
> **taurus said:**
> [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Hey taurus,

Went through it. Most of it passed over my head :P

Fdisk command reveals the following:

[PHP]Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391    6  FAT16
/dev/sda2              14       20022   160722292+   f  W95 Ext'd (LBA)
/dev/sda5              14       10212    81923436    7  HPFS/NTFS
/dev/sda6           10213       20022    78798793+   7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19669   157991211   83  Linux
/dev/sdb2           19670       20023     2843505    5  Extended
/dev/sdb5           19670       20023     2843473+  82  Linux swap / Solaris
[/PHP]

I've installed Ubuntu 6.10 on sdb harddisk and partitions are created automatically by the installer.

sda is where my Windows XP Pro SP2 is installed. It has 3 partitions.
1. 100 MB FAT32
2. 80 GB NTFS
3. 80 GB NTFS

I have Windows and Ubuntu on two separate Hitachi 160 GB HDDs.

Can you guide me through to mount the two NTFS partitions so I can access my files and so on.

---

### Post by rune_kg on 2006-12-20
> **tom56 said:**
> It is not recommended that you install software from anywhere other than the official Ubuntu repositories for several reasons. Automatix and Easybuntu can cause problems in distro updates (i.e. you might have trouble upgrading to 7.04 come April). It is also bad practice for security reasons (though Automatix and Easybuntu are both fine).
Well I think automatix2 does a better job of installing stuff than most newbies could themselves. I like the basics to be taken care of instead of having to go through the tedious tasks of installing countless codecs, setting up fonts for mplayer, a.s.o.a.s.f.

Rune Kaagaard
[http://runelyd.dk](http://runelyd.dk)

---

### Post by macogw on 2006-12-20
> **ervyxx said:**
> Hey!

Followed the procedure - 
**Playing encrypted DVDs**

Installed everything yet totem doesn't play anything :(

IMO, Totem kinda sucks.  VLC Media Player will play practically anything though.

---

