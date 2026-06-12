---
title: "messed up file system"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by thecaptainjs on 2006-08-21
Help!!
I tried to install ubuntu and after i set up the partitions.. it totally ignored what i had set and screwed up everything. 

I want to restore my old file system or something! I need my files!

I tried gpart. when i run gpart /dev/hdc 
I get permission denied

when i try to fdisk it i get unable to open... 

Please! Help me!

---

### Post by encompass on 2006-08-21
> **thecaptainjs said:**
> Help!!
I tried to install ubuntu and after i set up the partitions.. it totally ignored what i had set and screwed up everything. 

I want to restore my old file system or something! I need my files!

I tried gpart. when i run gpart /dev/hdc 
I get permission denied

when i try to fdisk it i get unable to open... 

Please! Help me!
are you sure?
Can you tell us how you set up your system?
What partitions, did you dual boot.
You must be more detailed.
and you need to use those commands with sudo BUT don't go doing that till you tellus what happened.

---

### Post by meng on 2006-08-21
Usually a bad idea to access partitions that are mounted ... are you doing this from the installed ubuntu or a live cd?
But anyway I think you may need root privileges, are you sudo-ing these commands

---

### Post by nalmeth on 2006-08-21
You need to use sudo to get those commands do work

what is the output of:
sudo fdisk -l

---

### Post by thecaptainjs on 2006-08-21
Basically I ran live CD. 
Then I manually went to set up the partitions. I have read a few guides so I knew how i wanted to set it up. 

I then I set it to resize the windows partition, setup a linux swap and a linux partition. 
Hit next within the linux install and at the next part it was totally confusing because nothing seemed to be how I had just specified it. 

So I canceled out and restarted... couldnt boot to windows. 

Ran back into live CD again. 
I go back into the install to view the partitions and it has 3 0.00MB partitions of unknow filesystem
and a 4th with 149 GB but unknown filesystem.

---

### Post by thecaptainjs on 2006-08-21
Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       19457   156288321    7  HPFS/NTFS
/dev/hdc2           19458       19458           0+  83  Linux
/dev/hdc3           19458       19458           0+  83  Linux
/dev/hdc4               1           1           0+  83  Linux
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        7649    61440561    7  HPFS/NTFS
/dev/hdd2            7650       14592    55769647+   f  W95 Ext'd (LBA)
/dev/hdd5            7650       14592    55769616    7  HPFS/NTFS

---

### Post by thecaptainjs on 2006-08-21
I am runing a scan to see what it says using gpart right now.

---

### Post by thecaptainjs on 2006-08-21
How long should this take?

---

### Post by encompass on 2006-08-21
what is that output from... I wantto knowthe command you entered... and is this after you setup the partitions?
If so looks like they may still be there.
Windows doesn't play well with others.

---

### Post by thecaptainjs on 2006-08-21
I ran: Sudo gpart -f /dev/hdc 


like 24 minutes ago. its a 160 gig drive so i can understand it might take a while.

---

### Post by thecaptainjs on 2006-08-21
its still going... sh ould i be worried!!

---

### Post by thecaptainjs on 2006-08-21
!!!!

---

### Post by thecaptainjs on 2006-08-21
Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

---

### Post by thecaptainjs on 2006-08-21
Here is to hoping that running it again without the -f makes a difference.. if not i dont know what to do.

---

### Post by thecaptainjs on 2006-08-22
Yea... um why am i talking to myself!

---

### Post by thecaptainjs on 2006-08-22
I wish someone would respond...

---

### Post by encompass on 2006-08-22
your kind of annoying...
Look...
Did you backup your data?
Most of us are very happy to respond to peoples problems.  Infact... I let people IM me personaly and I can help them out.  (You may do that now)
Let's try a few things to see what the issue is... Starting from the top...
type this at the terminal:
```
sudo fdisk -l /dev/hdc
```
I know that you did it before... just relax and do it again
tell me the output.
Remember that we are not your minimum wage paid techsupport that wait for your response at any moment.  Odd's are you in bed while I type this because I am in Finland.

---

### Post by thecaptainjs on 2006-08-22
I do apologize, however i dont have recent backed up stuff. its been a few weeks and i have done a lot. 

but when GPart comes back with what it did, I kinda freaked out... because I had spent a few days working on a website that i hadnt finished/ uploaded. 

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

---

