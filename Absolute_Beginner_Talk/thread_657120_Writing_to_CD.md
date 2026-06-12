---
title: "Writing to CD"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Victoriakhf on 2008-01-03
Hi,

My CD drive (Matshita UJDA360) reads CDs fine, but doesn't want to seem to write - any tips?


Thanks!

---

### Post by hyper_ch on 2008-01-03
did you insert an empty cd?

---

### Post by WearZeeP on 2008-01-03
> **hyper_ch said:**
> did you insert an empty cd?
Im sorry, but isn't that obvious that he did? (Well, shame on me if he didn't, but as I see it, he wouldn't be posting here if he didn't already check these kind of things)

I also have this problem, but with a CW058D ATAPI CD-R/RW, and any help would be greatly appreciated.
I believe that we have almost the exact same problem, so i didn't thinks its of much use to create an exact same thread about my problem.

---

### Post by cecure on 2008-01-03
Can you describe how you have been trying to write to the cd?
Do you get a prompt when the cd is inserted?
Does the blank cd mount? (it will make an icon on the desktop that identifies it as a blank cd)

---

### Post by hyper_ch on 2008-01-03
> **WearZeeP said:**
> Im sorry, but isn't that obvious that he did? (Well, shame on me if he didn't, but as I see it, he wouldn't be posting here if he didn't already check these kind of things)

I also have this problem, but with a CW058D ATAPI CD-R/RW, and any help would be greatly appreciated.
I believe that we have almost the exact same problem, so i didn't thinks its of much use to create an exact same thread about my problem.

With that description of the problem I tend to start thining of all things...


Anyway, did you try to write to another empty disc?

---

### Post by Victoriakhf on 2008-01-04
Well, I tried k3b (instead of the "CD creator" in places menu) and that seems to have worked fine - at least for one CD. So maybe that will help other people.

---

### Post by WearZeeP on 2008-01-04
Well, now maybe I could steal this thread as it is almost the exact same issue.
I have a CW058D ATAPI CD-R/RW which I have had the exact same issues with, i can read cd's just fine but whenever i insert an empty disc and try to burn it, i get an error.

This is what i get from lshw:

> *-cdrom:1
                   description: CD-R/CD-RW writer
                   product: CW058D ATAPI CD-R/RW
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: V110D
                   serial: NC000000Q0
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw
                   configuration: mode=udma2 status=nodisc

I have tried two different brands of discs, the first one is Verbatim CD-R, 700mb 52x, and the second one, Fujifilm, with the same specs, although, this one says "Multispeed" if that makes any difference.
Maybe i should try a CD+R if i get a hold of one, if that could work, I don't know the difference between them, but the CD-R's worked fine in Windows.

Now, if I insert an empty disc, the  "You have put in an empty disc, what would you like to do?-dialog" comes up.
If i choose "create a data-cd" or whatever, i'm roughly translating from Swedish now, in opens nautilus with burn:///, and if i put some files there and try to burn, the window where i can select speed, name on the cd and such shows up, then when i press burn, a window pop ups, saying "an error occurred while writing to the disc", nothing more.

If i  do cdrecord -scanbus, i get this:

> scsibus1001:
        1001,0,0 100100) 'SAMSUNG ' 'DVD-ROM SD-616F ' 'F100' Removable CD-ROM
        1001,1,0 100101) 'ADAPTEC ' 'ACB-5500        ' 'FAKE' NON CCS Disk
        1001,2,0 100102) *
        1001,3,0 100103) *
        1001,4,0 100104) *
        1001,5,0 100105) *
        1001,6,0 100106) *
        1001,7,0 100107) *

Now, I don't really get why it says that my CD-Writer is "FAKE"

If i try gnomebaker, i get approximately half-way burning, then it stops, giving me:

> cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 Jörg Schilling
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'schily-0.9'.
atapi: 1
Device type    : Removable vendor specific 7 Printer
Version        : 4
Response Format: 15
Capabilities   : AENC TERMIOP RELADR WBUS32 WBUS16 SYNC LINKED CMDQUE SOFTRESET 
Vendor_info    : 'âéìÿâéìÿ'
Identifikation : 'âéìÿâéìÿâéìÿâéìÿ'
Revision       : 'âéìÿ'
Device seems to be: unknown.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
SCSI buffer size: 64512
cdrecord: Sorry, no CD/DVD/BD-Drive found on this target.

And this is where I don't know what to do more.
Should i just give up, and get a new CD-writer, or is there hope?
Btw, sorry for the long post.

Oh btw, I have tried k3b, but that didn't make any difference, although I believe that k3b didn't even discover the cd, it just kept asking me to put in a n empty disc.

---

### Post by slaabrockband on 2008-01-05
> **WearZeeP said:**
> 
If i try gnomebaker, i get approximately half-way burning, then it stops, .


Samme problem here, samme happen with kb3, serpentine, they writes happily half-through and then they stop.

Code
lshw: gives nothing about a cd romdrive in , despite the burningprograms all recognize my writer:CyberDrv cw088d-cd-R/Rw.

There must be someone outthere who can solve this little problem ?

---

### Post by bfkeats on 2008-01-08
I have the same problem on two different machines.Help!

---

### Post by Virtual_Ron on 2008-04-25
I was having this problem, and pulled out most of my hair.   Would burn DVD's fine, but failed on CD's.   I was using fujifilm cd-r's.  Soon as I tried a different brand, my problems went away.

Weird... I thought of fujifilm as a good "name brand", but apparently don't' work with my brand spanking new drive.   Ended up using some super-cheep brand of cd-r I liberated from work.

---

