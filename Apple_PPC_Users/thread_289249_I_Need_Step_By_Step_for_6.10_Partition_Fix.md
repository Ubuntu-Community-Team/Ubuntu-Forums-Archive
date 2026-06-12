---
title: "I Need Step By Step for 6.10 Partition Fix"
date: 2006-10-30
forum: Apple PPC Users
---

### Post by amishman on 2006-10-30
I downloaded the live 6.10 and can boot from the CD and play with Linux.  I wanted to install on my external firewire drive but it appears the 6.10 has some known bug regarding partitioning so I can't get 6.10 installed on my external firewire drive.  I am bummed.  I am on Satellite and for those not familiar, Satellite is FAPed.  Therefore, downloading anything above 350MB is nearly impossible.  You cruze at 1000K download and when it hits 350MB, it scales you back to prehistoric days and you get like 5K from that point on.  It kills the whole system and I can't do anything else but wait it out.  It took me all yesterday and up to almost noon today to get the 688MB file downloaded so I could make the CD.  I can't handle doing this again and need to figure out how to get past this partitioning bug.

Anyone in the know here that can give use newbies a step by step.

Thanks

tj
](*,)

---

### Post by ReaderRat on 2006-10-30
You can download gparted, a partitioner (more up-to-date) on a LiveCD, and see/change most anything on your drive(s). Here ia the DL site:
[**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php)

---

### Post by seatea on 2006-10-31
It might be  worth a try to install gparted from the  Synaptic Package Manager,System>Administration>Synaptic, in the  Live Cd of edgy and see if you can do the  partitioning, create an Apple bootstrap partition, less  than  or equal to 1 MB, create an ext3  / (root) partition  and a 500MB swap partition with it, and then install edgy with the installer. I was installing edgy on my internal hard drive with the external firewire drive still hooked up and  even though I was not trying to do anything  to the  external drive, I could not install edgy until I disconnected the external drive. This was with the  Alternated CD for  edgy. Maybe  there is  some  problem with the edgy installer on external drives. I installed Dapper on an external drive with only a little problem. It  helped that I had  an Apple bootstrap partition on my  internal drive though.

---

### Post by linear on 2006-10-31
> **amishman said:**
> I downloaded the live 6.10 and can boot from the CD and play with Linux.  I wanted to install on my external firewire drive but it appears the 6.10 has some known bug regarding partitioning so I can't get 6.10 installed on my external firewire drive.

As far as I know, it's not a partitioning bug that keeps you from installing to (and booting from) an external drive. See these threads:

[http://www.ubuntuforums.org/showthread.php?t=84131](http://www.ubuntuforums.org/showthread.php?t=84131)
[http://www.ubuntuforums.org/showthread.php?t=40536](http://www.ubuntuforums.org/showthread.php?t=40536)
[http://www.ubuntuforums.org/showthread.php?t=91755](http://www.ubuntuforums.org/showthread.php?t=91755)
[http://www.ubuntuforums.org/showthread.php?t=89990](http://www.ubuntuforums.org/showthread.php?t=89990)

---

### Post by amishman on 2006-10-31
These are the issues I mentioned.  Trying to install has a partitioning issue and there is some work around but I am hoping someone can explain it further, as in step-by-step on what to do so the installer can work.  Now it just fails when you try to partition and I can get into the manual mode but what to do next???

#

The advanced partitioning mode of the installer on the Desktop CD cannot create new HFS bootstrap partitions on Power Macintosh systems. This affects only Power Macintosh systems without existing GNU/Linux installations. Possible workarounds are to use automatic partitioning first, which will create the HFS bootstrap partition, and then do a second installation with manual partitioning if necessary, or to use the alternate install CD rather than the desktop CD. [WWW] [https://launchpad.net/bugs/68243](https://launchpad.net/bugs/68243)
#

The advanced partitioning mode of the installer on the Desktop CD has trouble re-using an existing root file system, and will incorrectly claim "No root file system". Since you must reformat the root file system for use by the installer in any case, you can easily work around this problem by deleting and re-creating the partition in question in the advanced partitioner. [WWW] [https://launchpad.net/bugs/67130](https://launchpad.net/bugs/67130)

---

