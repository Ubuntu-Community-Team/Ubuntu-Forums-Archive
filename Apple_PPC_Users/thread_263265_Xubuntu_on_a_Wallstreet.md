---
title: "Xubuntu on a Wallstreet"
date: 2006-09-22
forum: Apple PPC Users
---

### Post by linuxuser28 on 2006-09-22
I have a old Wallstreet PowerBook I am  not using and I would like to know if this would be a good machine to run Xubuntu on. It is a 233 MHz G3 with 192 MB RAM and a 2 GB hard drive (I'll probably put a bigger hd in).

---

### Post by auximini on 2006-09-23
I think you should be OK. Xubuntu doesn't use that much ram.

You can also boot up the Xubuntu Live CD to see if your hardware will work correctly.

---

### Post by ponzio on 2006-09-23
Unfortunately the livecd won't boot, because wallstreet is an old world mac. I recommend visiting this site:

[http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/](http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/)

Even though the guide is for installing Breezy Badger on a wallstreet, I believe it will be useful no matter which release you are going to install. The guide also contains a few good links which I also recommend checking out.

Good luck!

---

### Post by deweese on 2006-09-23
I don't think Xubuntu will work on it.  I think the CPU isn't powerful enough
to run Xubuntu.  I installed Xubuntu on a Sony Pentium 2 with 366 mhz
and 128 mb of ram and it would not load the OS.  I was able to get Xubuntu
to work on a Celeron with 633mhz. and only 64 mb. of ram.  My conclusion:
The cpu must be bigger. 633mhz. is the smallest working I have tested.
I made the 633mhz. to have 512 ram.  The computer has amazing speed now
with Ubuntu Dapper Drake.

---

### Post by Hyötypyörä on 2007-08-15
How did this work out? I am interested to know. I am trying to install Xubuntu on a 400MHz/192 mt/6gb HD WallStreet. I have done the partition, installed BootX which starts ok but I am clueless as to what are the proper kernel arguments to use. The machine freezes after BootX selection. I am trying via Xubuntu alt.install PPC CD as the live cd does not work

---

### Post by pxwpxw on 2007-08-15
> **Hyötypyörä said:**
> How did this work out? I am interested to know. I am trying to install Xubuntu on a 400MHz/192 mt/6gb HD WallStreet. I have done the partition, installed BootX which starts ok but I am clueless as to what are the proper kernel arguments to use. The machine freezes after BootX selection. I am trying via Xubuntu alt.install PPC CD as the live cd does not work

This is from memory, it is some time since I did an OldWorld install. (Is it definitely a Wall Street, 400MHz?)
You should not need any kernel args with the Alternate PPC install CD, unless you want an expert install. 
Depending on the BootX version (I last used 1.2b3) there is a checkbox for using video drivers, may need to try with and without.
But from what you report, I think you are having a problem with running BootX, have you got both the Control Panel BootX and the extension BootX, with the kernel and ramdisk installed correctly.
The link in a post above seems to describe the process well. Also there is the original Zcats Howto, see the Ubuntu PPC Howto.
Of course, on a NewWorld, BootX wont go.

---

### Post by thevictor390 on 2007-08-17
This may be irrelevant, but I have a successful install of Ubuntu (not Xubuntu) on a 300 MHz G3 "clamshell" with 128 MB RAM. This is a new world mac however, although the specs are similar.

---

