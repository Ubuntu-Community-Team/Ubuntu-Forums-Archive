---
title: "No disk detected on 8.10 alt 733 G4 install"
date: 2009-05-01
forum: Apple Hardware Users
---

### Post by nbs2005 on 2009-05-01
Hi Folks,

I tried to install 8.10 alt on a 733 G4 with a 80 gb Western drive.  The drive is one I installed from a friend who tested it and said it was good (he's reliable).

I got through the no common cdrom problem (thanks!) and was humming along until the disk detection was unable to read my disk.  I played around with selecting several divers from the list.  It finally detected using one of the SCSI drivers (sorry, I don't remember which and did not write it down) but read it back as an 8.4 gb drive.   For giggles I tried to partition that, but it came back unable to partition.  Is was late so I shut her down.

I'm wondering what I should try next?  I'll throw the drive into an xubuntu machine to format and verify, but as I said, I'm pretty sure the drive is good.  The connections all look good on the drive and it appears to be jumpered correctly (master, it's the only drive).

This is my first attempt at a Mac install.  My other two PC's installed 8.10 ubuntu and xubuntu no problem.

Thanks for your help,

Jeff

---

### Post by pxwpxw on 2009-05-01
> **nbs2005 said:**
> Hi Folks,

I tried to install 8.10 alt on a 733 G4 with a 80 gb Western drive.  The drive is one I installed from a friend who tested it and said it was good (he's reliable).

I got through the no common cdrom problem (thanks!) and was humming along until the disk detection was unable to read my disk.  I played around with selecting several divers from the list.  It finally detected using one of the SCSI drivers (sorry, I don't remember which and did not write it down) but read it back as an 8.4 gb drive.   For giggles I tried to partition that, but it came back unable to partition.  Is was late so I shut her down.

I'm wondering what I should try next?  I'll throw the drive into an xubuntu machine to format and verify, but as I said, I'm pretty sure the drive is good.  The connections all look good on the drive and it appears to be jumpered correctly (master, it's the only drive).

This is my first attempt at a Mac install.  My other two PC's installed 8.10 ubuntu and xubuntu no problem.

Thanks for your help,

Jeff

It may need to set the drive up with an Apple Partition Map, which is what Mac normally uses on PPC, possibly it is uing msdos partiton scheme. 8.4GB was an old limit in MSDOS partitioning.

---

### Post by nbs2005 on 2009-05-01
Can I download an app to do that?  I don't have a working Mac OS.

---

### Post by tiresia on 2009-05-01
If it's true what pxwpxpw says - does the installer detect the HD, or it sees a wrong/unattended partition?
Do you come to the point, when you can choose for installing the whole HD?
Are you using an alternate installer cd?
(to generate an apple partition map you can format the HD with the Apple Disk Utility or you can use mac-fdisk, a GNU/linux utility - but you don't need to do this, the installer usually takes care of this, if you use a guided installation)
If you are not experienced with mac, I would use a LiveCD (how musch RAM do you have - you could use also Jaunty 9.04), erase the HD using GParted, and then install Ubuntu

---

### Post by nbs2005 on 2009-05-01
> **tiresia said:**
> If it's true what pxwpxpw says - does the installer detect the HD, or it sees a wrong/unattended partition?

It did not detect the installer until I selected the SCSI driver, it then read the HD as 8.4 GB

> Do you come to the point, when you can choose for installing the whole HD?
Are you using an alternate installer cd? Yes, yes

> (to generate an apple partition map you can format the HD with the Apple Disk Utility or you can use mac-fdisk, a GNU/linux utility - but you don't need to do this, the installer usually takes care of this, if you use a guided installation)
If you are not experienced with mac, I would use a LiveCD (how musch RAM do you have - you could use also Jaunty 9.04), erase the HD using GParted, and then install UbuntuI'm not very Mac savvy.  I'd love to find a LiveCd for 8.04 or 8.10 but could only find the alternate CD.  I have 1 gb of ram.

---

### Post by tiresia on 2009-05-01
Why not installing Ubuntu Jaunty 9.04?
Here you find the LiveCD (also called Desktop CD) - http or torrent
[http://cdimage.ubuntu.com/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/ports/releases/jaunty/release/)

If you prefer Kubuntu 
[http://cdimage.ubuntu.com/kubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/kubuntu/ports/releases/jaunty/release/)

or Xubuntu
[http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/)

---

### Post by stream303 on 2009-05-01
733 mhz G4 - is that a PowerMac with an nvidia graphics card?

You can get 8.10 to work, but there were a few problems above and beyond the norm with that release, so I'd recommend using 9.04 Jaunty, or fall back to the 8.04 LTS release.

(Tiresia beat me to it! :) )

Either the Live-CD or "alternate" text-based installer should do fine.

Your installation should be very easy since you are dedicating the whole disk to Ubuntu.  When it comes time for partitioning, choose "Guided Partitioning" and then let the partitioner "use the whole disk", and it will create not only the standard root and swap partitions, but also the special apple partitions that are needed for you automatically.  

Unlike most pc's, we need special additional partitions specific to apple hardware to function.  Fortunately guided partitioning on PPC makes that easy when you allow it to do it for you.

If that machine is using an Nvidia graphics card, it is more likely that you'll be up and running without having to mess around too much with a custom /etc/X11/xorg.conf file - but this will depend if you are using a PowerMac with an external monitor - but you can cross that issue after install.

---

### Post by nbs2005 on 2009-05-01
Thanks for the info on Jaunty, I'll give that a go!

---

### Post by nbs2005 on 2009-05-02
Well Jaunty worked like a charm, thanks!  The 80 gb drive was toast though.  Had to swap a 20 gb in and then no trouble. 

J

---

