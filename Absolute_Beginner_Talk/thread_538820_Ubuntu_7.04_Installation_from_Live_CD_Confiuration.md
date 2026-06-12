---
title: "Ubuntu 7.04 Installation from Live CD Confiurations"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by orang_redux_777 on 2007-08-30
Hi, People:

I'd appreciate some help from those who are far more accomplished than myself.

I have a Fiesty Fawn (Ubuntu 7.04) Live CD from a Netherlands sub-contractor.

The CD works fine in both running atop a WinXP Pro SP2 OS and from  a BIOS-configured CD-ROM Boot.

My questions revolve around two central issues:

1) Does the Live CD, following the U .04 partition/format/install phase, write-back to the new partitioning data to the Live CD disk?

2) If so, how does one remove the new partiioning/installation data from the Live CD ***without*** it affecting the actual HDD partitions?

I've sought to, upon 9 different occasions, and using both the Guided and Manual partitioning sub-utilities, install the 7.04 OS on two different HDDs. 

The first partitioning C:\ Drive "go-round" via Guided went just fine, except for the fact that the disk percentage of the Free Space I assigned via slider was *not* replicated by the actual installation (even allowing for the Swap File.)  In fact, the space allocation of 30% was
doubled; that is, including the Swap file, it came out to be in reality over 60% of the System Drive HDD.

Subsequent attempts (#s 2-9,) via Manual partiitoning\MB assignment configuration\installation, have yielded further anomalies, including:

1)  the faux "read-back "of assignment of non-logical and system drive desiginations;

2)  the inaccuracy of the actual partition(s) size(s) of respective drives which do not in fact exist (either virtually or physically;) 

3) the continued misassignment of the partition-allocation sizes that I specified for the SATA 000 P-2 (Secondary Partition on the Primary System Drive.)  

All of the 9 attempt's worth of partitioning\installation data is still contained on the Live CD, making it a bit hard for me, a doofus-brain when it comes to using the Live CD, but not to drive partitioning per se, to get things right. 

I would sincerely value any help you can give me.

My best 2 all.

:-)

/.\ Orang /.\

{- On the h'ware compatibility/driver end of things, there are no discernible problems with my "rig," which I must say, is a very welcome change from the "days of yesteryear,"  from compiling and assembling various Linux-based distro sub-components, etc., etc.  For this I am sincerely grateful and sincerely applaud all the many, many contributions of the Ubuntu Open Source crew, be they curerntly housed in South Africa or in any other points of origin.}

[{ Basic H'ware\non-Ubuntu OS & Complete System Specs Data will be supplied if you deem it to be of pertinence.  THX again.  }]

---

### Post by mikeyphi on 2007-08-30
Quote: My questions revolve around two central issues:

1) Does the Live CD, following the U .04 partition/format/install phase, write-back to the new partitioning data to the Live CD disk?

No the Live CD just allows you to use Ubuntu as though it was installed - it uses the computers hardware so that you can see the OS in action....it's just a CD, there is no data input back onto the CD.

2) If so, how does one remove the new partiioning/installation data from the Live CD ***without*** it affecting the actual HDD partitions?

If you have begun the install process it is possible that you have allowed the installer to partition your disk. If you quit the install process, you can reboot your computer and use a disk partition tool to reconfigure the disk. Gparted, the ubuntu disk partitioner, is available through the Live CD.

---

### Post by eapache on 2007-08-30
Please go into the install process, select manual partitioning, take a screenshot, and post it here. Other system specs would also be useful.

---

