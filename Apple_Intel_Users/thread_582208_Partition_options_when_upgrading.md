---
title: "Partition options when upgrading"
date: 2007-10-19
forum: Apple Intel Users
---

### Post by schauerlich on 2007-10-19
I'm upgrading to Gutsy from Feisty using the alternate CD on a 2nd gen Macbook dual-booting Ubuntu and OS X , and I'm not sure what to do with partitioning. I want to replace my Feisty install with Gutsy without affecting the OSX install. My options are:

Guided - resize SCSI3 (0,1,0), partition #3 (sda) and use freed s
Guided - use the entire disk
Guided - use the largest continuous free space
Guided - Use entire disk and set up LVM
Guided - use entire disk and set up encrypted LVM
Manual

My first guess was the first option, but I'm pretty new and I don't feel like accidentally erasing my hard drive from a wrong guess... Thanks in advance.

---

### Post by cyberdork33 on 2007-10-19
> **EDavidBurg said:**
> I'm upgrading to Gutsy from Feisty using the alternate CD on a 2nd gen Macbook dual-booting Ubuntu and OS X , and I'm not sure what to do with partitioning. I want to replace my Feisty install with Gutsy without affecting the OSX install. My options are:

Guided - resize SCSI3 (0,1,0), partition #3 (sda) and use freed s
Guided - use the entire disk
Guided - use the largest continuous free space
Guided - Use entire disk and set up LVM
Guided - use entire disk and set up encrypted LVM
Manual

My first guess was the first option, but I'm pretty new and I don't feel like accidentally erasing my hard drive from a wrong guess... Thanks in advance.

You are going to have to use manual. then you need to tell it to your your current feisty partition as /

---

### Post by schauerlich on 2007-10-19
Is this correct?

Name:
Use As: Ext3 journaling file system
Format the partition: no, keep existing data
Mount Point: /
Mount options: defaults
Bootable flag: off

Then hit done?

---

### Post by cyberdork33 on 2007-10-19
> **EDavidBurg said:**
> Is this correct?

Name:
Use As: Ext3 journaling file system
Format the partition: no, keep existing data
Mount Point: /
Mount options: defaults
Bootable flag: off

Then hit done?

except you will want to format it, otherwise you will likely get errors from remaining files

---

### Post by schauerlich on 2007-10-20
After that I get:

"The FATs don't match. If you don't know what this means, then select cancel, run scandisk on the file system, and then come back.

ERROR!!!

<Ignore>
<Cancel>"

I hit cancel, and I get:

"The test of the file system with type fat32 in partition #1 of SCSI3 (0,1,0) (sda) found uncorrected errors.

If you do not go back to the partitioning menu and correct these errors, the partition will be used as is.

Go back to the menu and correct errors?

<Yes> <No>"

Any idea what error it could be?

---

### Post by cyberdork33 on 2007-10-20
> **EDavidBurg said:**
> After that I get:

"The FATs don't match. If you don't know what this means, then select cancel, run scandisk on the file system, and then come back.

ERROR!!!

<Ignore>
<Cancel>"

I hit cancel, and I get:

"The test of the file system with type fat32 in partition #1 of SCSI3 (0,1,0) (sda) found uncorrected errors.

If you do not go back to the partitioning menu and correct these errors, the partition will be used as is.

Go back to the menu and correct errors?

<Yes> <No>"

Any idea what error it could be?
It has to do with the Apple EFI partition. You should not allow the installer to mount it in your new system. You will still get a FAT's error message, but you can just ignore it.

---

### Post by schauerlich on 2007-10-20
Also, could I select "erase data on this partition" and do a fresh install of Gutsy?

---

### Post by schauerlich on 2007-10-20
Nevermind - I've got it working now. Thanks for the help!

---

### Post by jamescoy on 2007-10-20
> **EDavidBurg said:**
> I'm upgrading to Gutsy from Feisty using the alternate CD on a 2nd gen Macbook dual-booting Ubuntu and OS X , and I'm not sure what to do with partitioning. I want to replace my Feisty install with Gutsy without affecting the OSX install. My options are:

Guided - resize SCSI3 (0,1,0), partition #3 (sda) and use freed s
Guided - use the entire disk
Guided - use the largest continuous free space
Guided - Use entire disk and set up LVM
Guided - use entire disk and set up encrypted LVM
Manual

My first guess was the first option, but I'm pretty new and I don't feel like accidentally erasing my hard drive from a wrong guess... Thanks in advance.


I'd like to ask the same question, but with regards to installing via Parallels. Is there any danger of wiping data from any other virtual machine, or my OSX installation, if I should choose the wrong option for partitioning for Gutsy?

Thanks.

---

### Post by cyberdork33 on 2007-10-20
> **jamescoy said:**
> I'd like to ask the same question, but with regards to installing via Parallels. Is there any danger of wiping data from any other virtual machine, or my OSX installation, if I should choose the wrong option for partitioning for Gutsy?

Thanks.The VM is limited to the "hard drive" that you give it access to. So you can only 'wipe' data from your hard drive image for that VM.

---

### Post by jamescoy on 2007-10-20
Thanks for the reply - that's what I thought, but wanted to be sure.

Now, one other question...since I, as well as many others, are having video problems with the "live CD" iso, I've been trying to use the alternate iso. The problem is that when formatting that way, I can't seem to get a partition smaller than 33GB....which, I fear, will take up the bulk of the remainder of my drive. I only need about 6GB for this installation. How do I get around this? I don't see an option for sizing the partition down.

Thanks.

---

### Post by cyberdork33 on 2007-10-21
> **jamescoy said:**
> Thanks for the reply - that's what I thought, but wanted to be sure.

Now, one other question...since I, as well as many others, are having video problems with the "live CD" iso, I've been trying to use the alternate iso. The problem is that when formatting that way, I can't seem to get a partition smaller than 33GB....which, I fear, will take up the bulk of the remainder of my drive. I only need about 6GB for this installation. How do I get around this? I don't see an option for sizing the partition down.

Thanks.
You have to use the partitioner to delete the partition, then recreate it the size that you want.

---

