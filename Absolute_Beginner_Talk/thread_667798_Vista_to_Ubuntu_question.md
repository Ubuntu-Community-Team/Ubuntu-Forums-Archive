---
title: "Vista to Ubuntu question"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by AppaTime on 2008-01-14
I'm tired of Vista, and I'd like to remove Vista from my laptop and put ubuntu on it.  For background, I do not have or want a dual boot, just Ubuntu.  I downloaded the ISO(7.10) and checked the MD5 hash, then burned the image and tested it, it booted into live mode and worked just fine, sound video and internet all worked.  Will the installing process from the live boot give me the option to wipe vista off my HDD, or is there another way I need to do it?  I don't currently have any sensitive data that needs saving.  Thanks in advance for any help.

---

### Post by -grubby on 2008-01-14
yes it will give you the option to use the whole drive. Just choose "guided-use entire disk"

---

### Post by SOULRiDER on 2008-01-14
Theres an option to use the free space on the drive, that will resize the vista aprtition but it will take some time to do it.

---

### Post by nikoPSK on 2008-01-14
> **SOULRiDER said:**
> Theres an option to use the free space on the drive, that will resize the vista aprtition but it will take some time to do it.

You could always just do a fixed partition too.. :)

---

### Post by Bartender on 2008-01-14
Before you wipe out Vista, at least burn the recovery DVD's.  
You might hate Vista, but it's something you paid for and there may be some point in time that you want it back on there.

---

### Post by AppaTime on 2008-01-14
So when it asks "How do you want to partition the disk?", I choose "Erase entire disk: IDE1 master(hda) - 40.0 GB ST9402112A" ?

---

### Post by nikoPSK on 2008-01-14
> **AppaTime said:**
> So when it asks "How do you want to partition the disk?", I choose "Erase entire disk: IDE1 master(hda) - 40.0 GB ST9402112A" ?

NooO!!OO!!O That will kill it... Create a new partition and format it :)

nikoPSK

---

### Post by Sef on 2008-01-14
Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").  Even though the title refers to dual booting, it tells you what to use to get a single boot.

---

### Post by hilariousness16 on 2008-01-14
Good move. I wiped out xp on my laptop, and installed Ubuntu also. Besides, my laptop has too little hard drive space to dual boot(80G)

---

### Post by nikoPSK on 2008-01-14
> **hilariousness16 said:**
> Good move. I wiped out xp on my laptop, and installed Ubuntu also. Besides, my laptop has too little hard drive space to dual boot(80G)

hehe, nice man. 8-)

nikoPSK

---

### Post by azad on 2008-01-14
AppaTime, use a flash drive to backup the important stuff you have in your computer. (You could also burn a disk). And then, start the Ubuntu installation.

Create 3 partitions
hda1 -> mount point /
hda2 -> mount point /home
hda3 -> swap space

If you don't want to partition your drives manually, just use Guided - Use Entire Disk.

Cheers. I hope you enjoy the Ubuntu ride.

---

