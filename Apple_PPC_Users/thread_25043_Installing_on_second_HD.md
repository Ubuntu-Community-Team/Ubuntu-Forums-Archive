---
title: "Installing on second HD"
date: 2005-04-09
forum: Apple PPC Users
---

### Post by eBeL on 2005-04-09
I am not sure how I would install it on my second HD.  I get to the partition step.  I am afraid to choose the wrong disk, I have only installed Linux a few other times, but on a single HD setup.

---

### Post by Rxke on 2005-04-09
eBel, just to make sure: You want your second disk completely dedicated to Ubuntu?

In that case when you still have your OSX running you can go to the system profile and check which disk is master or slave or primary or secondary disk... Sometimes what you consider your secondary disk is in reality master, so make sure you get it right,,,  I don't know how that is with SATA... SCSI disk is easy, they have their own ID number

Then, in the Ubuntu installer, you can browse for the disks on which you want to install, and the installer tells you if its a master or primary disk or vice versa

Hope this helps

If in doubt, don't risk it and get better advice than mine!

---

### Post by eBeL on 2005-04-09
[QUOTE=Rxke]eBel, just to make sure: You want your second disk completely dedicated to Ubuntu?

In that case when you still have your OSX running you can go to the system profile and check which disk is master or slave or primary or secondary disk... Sometimes what you consider your secondary disk is in reality master, so make sure you get it right,,,  I don't know how that is with SATA... SCSI disk is easy, they have their own ID number

Then, in the Ubuntu installer, you can browse for the disks on which you want to install, and the installer tells you if its a master or primary disk or vice versa

Hope this helps

If in doubt, don't risk it and get better advice than mine![/QUOTE]
 It's ATA

ATA-4 Bus:

ST380021A:

  Capacity:	74.53 GB
  Model:	ST380021A
  Revision:	5.05
  Serial Number:	3HV0ZK6F
  Removable Media:	No
  Detachable Drive:	No
  BSD Name:	disk0
  Protocol:	ATA
  Unit Number:	0
  Socket Type:	Internal
  OS9 Drivers:	No

Home:

  Capacity:	74.53 GB
  Available:	17.46 GB
  Writable:	Yes
  File System:	Journaled HFS+
  BSD Name:	disk0s2
  Mount Point:	/

ST380021A:

  Capacity:	74.53 GB
  Model:	ST380021A
  Revision:	3.10
  Serial Number:	3HV0WWQ0
  Removable Media:	No
  Detachable Drive:	No
  BSD Name:	disk1
  Protocol:	ATA
  Unit Number:	1
  Socket Type:	Internal
  OS9 Drivers:	No

UbuntuPPC:

  Capacity:	74.41 GB
  Available:	74.36 GB
  Writable:	Yes
  File System:	Journaled HFS+
  BSD Name:	disk1s3
  Mount Point:	/Volumes/UbuntuPPC

---

### Post by eBeL on 2005-04-09
[QUOTE=eBeL]It's ATA

ATA-4 Bus:

ST380021A:

  Capacity:	74.53 GB
  Model:	ST380021A
  Revision:	5.05
  Serial Number:	3HV0ZK6F
  Removable Media:	No
  Detachable Drive:	No
  BSD Name:	disk0
  Protocol:	ATA
  Unit Number:	0
  Socket Type:	Internal
  OS9 Drivers:	No

Home:

  Capacity:	74.53 GB
  Available:	17.46 GB
  Writable:	Yes
  File System:	Journaled HFS+
  BSD Name:	disk0s2
  Mount Point:	/

ST380021A:

  Capacity:	74.53 GB
  Model:	ST380021A
  Revision:	3.10
  Serial Number:	3HV0WWQ0
  Removable Media:	No
  Detachable Drive:	No
  BSD Name:	disk1
  Protocol:	ATA
  Unit Number:	1
  Socket Type:	Internal
  OS9 Drivers:	No

UbuntuPPC:

  Capacity:	74.41 GB
  Available:	74.36 GB
  Writable:	Yes
  File System:	Journaled HFS+
  BSD Name:	disk1s3
  Mount Point:	/Volumes/UbuntuPPC[/QUOTE]
 Alright I got it intalled

---

