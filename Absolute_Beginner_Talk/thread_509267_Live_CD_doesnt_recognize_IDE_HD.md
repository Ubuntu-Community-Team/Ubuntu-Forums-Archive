---
title: "Live CD doesnt recognize IDE HD"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by spoolingti on 2007-07-25
Hi guys,

Before I ask my question, I would just like to say hi. My name is Niraj and this is my first experience with Ubuntu. I have been a windows man for as long as I can remember. The only experience I have had with linux was in some of my college IT classes.

I am trying to salvage some files from my broken XP install by running the Feisty Fawn 7.04 live cd. When the OS boots up, I can see that both my IDE DVD drives and my SATA Hd (Windows install on here) is recognized. I have another IDE drive in my PC that doesn't seem to show up. Any clues as to why this is the case. Do I need to physically mount the drive for it to show up? Is it something in the BIOS thats causing it not to show. I just need it to make a My Documents Backup. Thanks.

---

### Post by wpshooter on 2007-07-25
Have you tried to unplug your SATA drive and see what happens ?

How are your IDE drive and CD-Roms jumpered & connected ?

---

### Post by spoolingti on 2007-07-25
The cd rom drives are configured in a master/slave manner on the secondary IDE channel. The IDE HD is set to master and is plugged into the primary IDE channel. Someone at work suggested that I try unplugging my SATA drive as you had mentioned. I will try that when i get home from work. Any other possible causes that anyone could see???

---

### Post by threeonethree on 2007-07-25
auy niraj main bhi india se hu lol

---

### Post by spoolingti on 2007-07-25
> **threeonethree said:**
> auy niraj main bhi india se hu lol

I pretend to be :)

---

### Post by Orochi on 2007-07-25
I believe 'fdisk -l' will give you a list of devices attached to your computer. That will let you determine if the drive just isn't mounted or if it isn't even seen by Ubuntu at all.

---

### Post by spoolingti on 2007-07-25
> **Orochi said:**
> I believe 'fdisk -l' will give you a list of devices attached to your computer. That will let you determine if the drive just isn't mounted or if it isn't even seen by Ubuntu at all.

So if the drive isn't mounted, it should still show up if its plugged into the computer? I know my computer recognizes that its attached because it shows up when it does the POST. It is quite possible when the cd was loading that it threw an error about the hd. I stepped out of my room when the process was going on so i don't know if it spit out any errors.

---

### Post by Cypher on 2007-07-25
Right..do "sudo fdisk -l" and it will list all attached drives and their partitions. This might clue you in as to what's going on..

---

### Post by Orochi on 2007-07-25
> **spoolingti said:**
> So if the drive isn't mounted, it should still show up if its plugged into the computer? I know my computer recognizes that its attached because it shows up when it does the POST. It is quite possible when the cd was loading that it threw an error about the hd. I stepped out of my room when the process was going on so i don't know if it spit out any errors.

Yes. If it's just not mounted, you should be able easily to mount it manually by opening terminal and typing 'mount /dev/hdx /mountpoint' where x is the number of the drive and mountpoint is an existing folder where you want the drive to me mounted. 

Of course, if it didn't mount automatically that probably means some error occurred so maybe you won't be able to mount it manually :(

---

### Post by Cypher on 2007-07-25
> **threeonethree said:**
> auy niraj main bhi india se hu lol
Off-topic: Why would you assume that since his name is Niraj, he can speak Hindi?

---

### Post by spoolingti on 2007-07-25
> **Cypher said:**
> Off-topic: Why would you assume that since his name is Niraj, he can speak Hindi?

Yeah, thats a good question :)

---

### Post by spoolingti on 2007-07-25
This is what i get when i run "sudo -fdisk -l":

Disk /dev/sda: 160.0 GB, 160041885696 bytes
4 heads, 63 sectors/track, 1240404 cylinders
Units = cylinders of 252 * 512 = 129024 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1    17043521  2147483517+  54  OnTrackDM6

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19928   160071628+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 

does it look like ubuntu is recognizing my other non SATA drive?

---

### Post by Orochi on 2007-07-26
Yeah, it seems like it's only detecting 1 SATA drive and 1 IDE drive. I think it's probably a hardware problem (like one of your cables is bad) or a BIOS issue.

---

