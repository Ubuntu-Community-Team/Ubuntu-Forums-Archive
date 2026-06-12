---
title: "Which *buntu for my hardware"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by FriscoSoxFan on 2006-11-02
I'm completely blowing away windows server 2003 for my home server. I don't need dual boot as 2003 is ridiculously slow on the server. I rarely use it anyway as most of our basic web browsing and email is done in a La-Z-Boy with a laptop.

The server is used for the following: Download pictures from Canon SD550 digital camera. Store photos to big secondary hard drive. Accomplish basic editing such as rotation and red-eye removal. Upload pictures to winkflash for sharing with family. Scheduled backup to DVD +/- R/W (Which we swap out to fire/flood proof safe weekly). I was running DotNetNuke and hosting a personal website, but since all I care about is sharing photos, I'm switching over to the unlimited space (and free) winkflash service. That will save about $30 a month in power bills alone.

Here's the hardware:

Dell Poweredge 1400SC
Dual - PIII 800 Mhz
Memory 512MB
16 GB 7200 RPM SCSI primary drive (on-board SCSI)


I ran Dapper (6.06) and it seemed to run fairly well, although there seemed to be a bit of lag based on the DVD drive spinning up. 

My gut tells me dapper will work after it gets on disk and I upgrade the kernel to take advantage of the two processors.

Is this gut feel accurate, or should I consider Xubuntu, Kubuntu, or some other version?

Unfortunately, the secondary 300GB HD that all the photos are on is formatted NTFS, so I'll have to burn everything to DVD so I can reformat FAT32.

Anything else that I'm not thinking of?

---

### Post by Klaidas on 2006-11-02
Well, i'd recommend... Ubuntu server .iso!

And if you want... sudo aptitude install xubuntu-desktop

---

### Post by compmodder26 on 2006-11-02
The lag you were experiencing was just becuase of the live cd.  I would be willing to bet that installing it would yield much better performance.

The specs of your server seem perfectly fine for running Dapper.  I would normally suggest not using a GUI for a server, but since this is just a home server, it shouldn't be much of a concern.

One thing though, why not do all your photo editing from your laptop?  You can use Samba on the server to set up a shared folder that you can save to from the laptop.  Then your server would simply be a fileserver.

---

### Post by Bartender on 2006-11-02
You have enuf memory to run either Ubuntu or Kubuntu.  An interesting trick (there are so many things you can do in the Linux world) is to install one or the other, say Ubuntu, then go into Synaptic and search for 'Kubuntu-desktop'.  Download that program and you can switch back and forth between Ubuntu or Kubuntu.  Cool
Here's a nice [write-up]("http://www.linuxjournal.com/article/9369") on that feature.

---

### Post by kvonb on 2006-11-02
Why FAT32?  Do you like living dangerously?

FAT has major problems with file corruption and fragmentation, why not format it EXT3?

Or leave it NTFS and use the NTFS wrapper, it is read/write!

---

### Post by machoo02 on 2006-11-02
Don't forget to search the forums for threads on ntfs-3g and fuse, which will give you full read/write access to your NTFS drive.  I've been using it for a while on my dual-boot laptop without a problem, and it could save you a bunch of DVDs.

---

### Post by dbott67 on 2006-11-02
> **FriscoSoxFan said:**
> My gut tells me dapper will work after it gets on disk and I upgrade the kernel to take advantage of the two processors.

Listen to your gut! :) Just install **linux-686-smp**

> **FriscoSoxFan said:**
> Is this gut feel accurate, or should I consider Xubuntu, Kubuntu, or some other version?

Personally, I prefer Gnome vs. KDE (or XFCE, Enlightenment, Flux/Blackbox, etc.).  I've tried them all, but I keep gravitating back to Gnome as it seems much more intuitive to me.  Again, this is strictly a preference choice (perhaps based upon 15 years of working in the computer field dominated by MS Windows on the desktop).


> **FriscoSoxFan said:**
> Unfortunately, the secondary 300GB HD that all the photos are on is formatted NTFS, so I'll have to burn everything to DVD so I can reformat FAT32.

Anything else that I'm not thinking of?

There are utilities in development that allow r/w access to NTFS, but you may be better off backing up & re-formatting FAT32.  I purchased a [NexStar LX NAS device]("http://www.vantecusa.com/") (for about $90.00 CDN) & dropped in a 160 GB drive.  The nice thing is that it's accessible via SMB, FTP, web and has 10/100 Ethernet & USB 2.0 connectivity.  I can mount the SMB shares in Ubuntu and keep all my data accessible from any computer in the house or even from work ([review here]("http://www.guru3d.com/article/network/379/1/")).

Of course, you're installing Ubuntu on the former server to do just what this thing does, but this is a nice add-on for backups & additional storage.

-Dave

---

