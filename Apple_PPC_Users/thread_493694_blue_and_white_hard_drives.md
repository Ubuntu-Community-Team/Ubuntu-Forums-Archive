---
title: "blue and white hard drives"
date: 2007-07-06
forum: Apple PPC Users
---

### Post by kettle fry on 2007-07-06
Hi all   Just got  a blue and white   with a 40 gig maxtor h/d in it  running os9.I want to pull the hard drive and put a  9 gig from a intel pc,then use the  40 gig in a Amd machine.Is this possible or are the hard drives for ppc apples and intels  different? or is the only difference in firmware on the motherboard
  Im not worried about putting os 9 back on. Im downloading  feisty for ppc now.I want to use the  G3 as a server.
  Also is the iso ok downloaded and burnt on  a intel running windows or does it have to be done on the apple?

---

### Post by scav2000 on 2007-07-06
As long as the 9 gig is an ata/ide drive, you're golden.
With the B&W, Mac's went to ide from SCSI.

---

### Post by kettle fry on 2007-07-06
Yep the 9s a ide so the maxtors  just a normal 40 gig  hard drive great.just a thought tho do i have to put os9 on the ide to get it to load ppclinux or does pushing c access a clean boot and format from a bios?

---

### Post by kano on 2007-07-07
> **kettle fry said:**
> Yep the 9s a ide so the maxtors  just a normal 40 gig  hard drive great.just a thought tho do i have to put os9 on the ide to get it to load ppclinux or does pushing c access a clean boot and format from a bios?

if it's NewWorld, you don't need OS9. it can be pure linux.

---

### Post by kettle fry on 2007-07-14
Well i loaded kubuntu on the 40 gig to check it out it went fine so i pulled the 40 out and put the 9 gig in.  the live cd starts to load  but i get a lot of  errors about hda  and squashhfs or something like that i suspect the live cd does need a mac os on the hard drive  1st to load into the ram correctly Also once the os was loaded on the 40 it wouldnt load to live cd again which is a pain if you want to repair something by way of reinstall. i noticed this same problem years ago with ubuntu 5.04 back then i used to wreck the partition with  a mepis  live cd to reinstall ubuntu. I think the problem is the 9 gig is formatted with a ntsf partition and its stuffing up the kubuntu installerif i cant find my os 9 disk to put on the  drive 1st. Can i format the 9 gig from the kubuntu on the 40 gig?

---

### Post by pxwpxw on 2007-07-14
If you get the ubuntu Alternate install CD, it will probably let you partition the 9GB drive from scratch (write a partition table and then partition the disk). It does not require Macos, but the PPC live CD might be having other problems as well as (possibly) the non-apple disk confusing it. If you have a Macos install disk you could just use that first to partition the 9GB (to get an apple partition map on it), and try again, but the ppc Alternate install should do the job.

---

### Post by dagnabit dang doohickey on 2007-07-14
If you haven't already done so, check that the jumper on the hard drive is set correctly. The jumper should be set to the master position. Your Mac doesn't work with the jumper set to cable select, and since you pulled the 9G from a PC, there's a good chance it is set for cable select.

---

### Post by kettle fry on 2007-07-14
hey thanks all. yea Dagnabit just reset the jumpers this morning realised that was  one of the probs when a gentoo disk told me it was set to slave after using the alternate install and setting to master  now have a feisty mac. many thanks. Now just needto read up on linux networking coz its telling me no network hope its not a incompatible network card have one thats works with linux from  a pc will that fit a into a mac?
 you know the funny  thing is i looked at the jumpers while i was putting the hard drive in yesterday  and  was to lazy to google.thought i would regret that. :-)

---

