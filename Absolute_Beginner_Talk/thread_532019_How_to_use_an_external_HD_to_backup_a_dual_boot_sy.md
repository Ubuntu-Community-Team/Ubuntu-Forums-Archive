---
title: "How to use an external HD to backup a dual boot system (XP/Feisty)?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-08-22
I had been using an external hard drive to back-up my Win XP system for years. Now that I've switched over to a dual boot (Feisty/XP), is there a way to continue to back up my data on the same hard drive?  I guess if I keep the external HD as a Fat 32 disc, it should be able to accept files from both the XP and the Feisty partitions, right? Is there anything more special I would need to do in order to get this working? Can the files from both XP and Feisty be stored side by side, or do they need to be separated somehow in order for the XP OS to be able to see the disc properly?

---

### Post by jnorthr on 2007-08-22
you should be able to maintain the partition on the removable as fat32. I'd prefer to make another partition on the removeable as ext3, just to keep it in sync with the many utility programs available in ubuntu. That way there is no problem of mixing non-windows bits with unix bits and you can always have ubuntu read/write .zip files in the fat32 if needed.

---

### Post by swarup on 2007-08-22
> **jnorthr said:**
> you should be able to maintain the partition on the removable as fat32. I'd prefer to make another partition on the removeable as ext3, just to keep it in sync with the many utility programs available in ubuntu. That way there is no problem of mixing non-windows bits with unix bits and you can always have ubuntu read/write .zip files in the fat32 if needed.

I see. Ok, I'll set it up with two partitions then, as you suggest. The Windows partition could be either NTFS or FAT32, I suppose? And the Feisty Partition would be ext3. Is there a particular tool I should use to get this all set up? Would the Feisty LiveCD be able to help me with this?

---

### Post by mikeyphi on 2007-08-22
> **swarup said:**
> I see. Ok, I'll set it up with two partitions then, as you suggest. The Windows partition could be either NTFS or FAT32, I suppose? And the Feisty Partition would be ext3. Is there a particular tool I should use to get this all set up? Would the Feisty LiveCD be able to help me with this?

Use gparted in Feisty or the LiveCD. I use sbackup (available with synaptic) for my backups, if you download - you will find it under System/Administration.

---

### Post by swarup on 2007-08-22
> **mikeyphi said:**
> Use gparted in Feisty or the LiveCD. I use sbackup (available with synaptic) for my backups, if you download - you will find it under System/Administration.

Do I have gparted right in Feisty, in my computer? If so, where do I find it? That would be very convenient.

So sbackup once I download it, is strictly for the backup work right? ie that is not for setting up the partitions etc.

---

### Post by mikeyphi on 2007-08-22
[QUOTE=]Do I have gparted right in Feisty, in my computer? If so, where do I find it? That would be very convenient.

So sbackup once I download it, is strictly for the backup work right? ie that is not for setting up the partitions etc.[/QUOTE]

Sorry - I'm working in Gutsy at the moment but seem to remember that gparted isn't there by default and needs to be installed through synaptic - after which (I think) it's under System/Administration.

sbackup is a good program for choosing what & when & where to backup.

---

### Post by swarup on 2007-08-22
> **mikeyphi said:**
> Sorry - I'm working in Gutsy at the moment but seem to remember that gparted isn't there by default and needs to be installed through synaptic - after which (I think) it's under System/Administration.

sbackup is a good program for choosing what & when & where to backup.

I see. That's great. I went to Synaptic and downloaded gparted. It will be very handy to have on the computer. I know I can use gparted to shrink the size of the partition on the external hard drive. Will I then be able to use gparted to establish a second partition on that HD and set the file type as ext3? Or does a different program need to be used for that.

---

### Post by mikeyphi on 2007-08-22
gparted is good for all that!!

---

### Post by swarup on 2007-08-22
> **mikeyphi said:**
> gparted is good for all that!!

Thank you very much. That is extremely helpful information.

---

