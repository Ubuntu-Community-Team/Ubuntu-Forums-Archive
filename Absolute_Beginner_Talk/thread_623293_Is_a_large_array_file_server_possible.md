---
title: "Is a large array file server possible"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Droidling on 2007-11-25
I have been running a 2 TB Raid 5 array on Win2k Server for several of years now. I have been tempted to switch over to Linux for a while, mainly due to a general distaste for Microsoft’s manipulation of the market. I recently upgraded the array to 6 Seagate 750GB drives for a total of 3.75TB.  I’d really like to put Ubuntu on this system but I can’t find enough detailed specs to know if it will meet my needs. 

Are there any size limits for the total size of a single hardisk volume? I need 3.75TB now, but will want 5.25TB in the near future. There is a chance I might want to go as high as 11.25TB some day.

I have to share files with windows computers on a network. I believe SAMBA will do this. Will I have problems because of the raid array size above? Would the file system be NTFS, or does SAMBA convert the data from a Linux native file system? 

Is SAMBA also capable of replacing a windows domain controller? I saw a reference to setting up a DNS server using SAMBA. Does that include password authentication and file access permissions?  This isn’t essential but would be a plus.

My current hardware is:
Tyan Trinity GC-SL S2707 Motherboard (integrated ATI Rage XL)
1GB DDR Non-ECC Ram
80GB PATA drive on Promise PDC20276 IDE RAID controller
Highpoint Rocketraid 2220 in PCI-X 133 slot
6 x Seagate 750GB 7200.10 ST3750640AS

Thank you in advance for taking the time to heip me.

Terry 

P.S. Is there a recommended guide, tutorial, or book I can read to get started using Linux? I booted up the live CD, but really didn’t know what to do from there.

---

### Post by funkyFlash on 2007-11-26
Welcome to the fold!

You will be fine running an array that large.  [XFS supports up to 8 EiB]("http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits").  XFS is also reputable for wasting the least amount of space on MFT, so with an array that large, you'll get the most out of your disks.

Samba will treat you well.  You can have the array be whichever filesystem you like, and Samba will do all of the legwork for you.  Samba does have the capability of replacing a domain controller, but I have no experience doing so.  A quick search revealed [this guy]("http://www.howtoforge.com/ubuntu-gutsy-samba-domaincontroller"), which may help you out.

Take note that there is a ubuntu server, and ubuntu desktop.  The server has quite a bit less overhead, and less "pretty", but also has a bit steeper of a learning curve.

You may have an "experience" setting up the raid5 on the rocketraid, my sysadmin just fought a similar issue with centos 5, but he got it working pretty easily.

Google is a great resource, as well as these forums.  Good luck, and I hope you make the switch!

---

### Post by the-edmeister on 2007-11-26
[http://en.wikipedia.org/wiki/Network-attached_storage](http://en.wikipedia.org/wiki/Network-attached_storage)
That page has a lot of links to different packages near the bottom of the page.

I am putting together a small 500GB file-server that runs off a floppy disk running NASLite using junk-shelf components with 4 disco'd drives I got for like $27 a piece at Staples this summer.
[http://www.serverelements.com/](http://www.serverelements.com/)
I don't know if they have a package for that 3.75B though, and beyond the Floppy-based packages there is a fee involved.

Ed

---

### Post by Droidling on 2007-11-26
> **funkyFlash said:**
> Welcome to the fold!

You will be fine running an array that large.  [XFS supports up to 8 EiB]("http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits").  XFS is also reputable for wasting the least amount of space on MFT, so with an array that large, you'll get the most out of your disks.

Samba will treat you well.  You can have the array be whichever filesystem you like, and Samba will do all of the legwork for you.  Samba does have the capability of replacing a domain controller, but I have no experience doing so.  A quick search revealed [this guy]("http://www.howtoforge.com/ubuntu-gutsy-samba-domaincontroller"), which may help you out.

Take note that there is a ubuntu server, and ubuntu desktop.  The server has quite a bit less overhead, and less "pretty", but also has a bit steeper of a learning curve.

You may have an "experience" setting up the raid5 on the rocketraid, my sysadmin just fought a similar issue with centos 5, but he got it working pretty easily.

Google is a great resource, as well as these forums.  Good luck, and I hope you make the switch!

Thanks. As long as I know I'm not going to get stuck on some file system limit I don't mind spending the time to work out the details. This is a project for my home network so if it takes a month or two to figure out I'm fine with that. 

I'll be back when I get stuck. 

Thanks again

Terry

---

### Post by Droidling on 2007-11-27
> **the-edmeister said:**
> [http://en.wikipedia.org/wiki/Network-attached_storage](http://en.wikipedia.org/wiki/Network-attached_storage)
That page has a lot of links to different packages near the bottom of the page.

I am putting together a small 500GB file-server that runs off a floppy disk running NASLite using junk-shelf components with 4 disco'd drives I got for like $27 a piece at Staples this summer.
[http://www.serverelements.com/](http://www.serverelements.com/)
I don't know if they have a package for that 3.75B though, and beyond the Floppy-based packages there is a fee involved.

Ed

I may look into this for an office file server. I have a lot of old P2's & P3's  hanging around and this looks like a decent way to make use of one of them.  I am looking at my current home file server upgrade as a chance to get to know linux, so I would kind of like to stay with a full distribution, just to be able to check things out. If I like it I may want to convert some of my other computers to Linux. 

Terry

---

### Post by h0ax on 2007-12-01
Hi Droidling, are you having any luck?
I am having power supply issues, but I did find a great resource for updating the drivers/getting ubuntu to function properly with the rocketraid card.
check this guy's page out:
[http://www.eightypercent.net/Archive/2007/09/18.html](http://www.eightypercent.net/Archive/2007/09/18.html)
i'll post more when I get my setup working.

---

### Post by Droidling on 2007-12-01
> **h0ax said:**
> Hi Droidling, are you having any luck?
I am having power supply issues, but I did find a great resource for updating the drivers/getting ubuntu to function properly with the rocketraid card.
check this guy's page out:
[http://www.eightypercent.net/Archive/2007/09/18.html](http://www.eightypercent.net/Archive/2007/09/18.html)
i'll post more when I get my setup working.

No luck yet. This is my first Linux system, so I expect to spend a couple of weeks reading up on Linux basics.

Thanks for the suggestion.  I had found this web page. It was my main reason for looking at Ubuntu over the other linux distributions. Although it appears that Highpoint has tested their drivers with SuSE and Red Hat. If I can't get the instructions from this web page to work. I may end up with one of the other distributions for the server. Whatever I decide I will definately be keeping Ubuntu on one of my desktops. 

Terry

---

