---
title: "Creative partioning?"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Buster Reid on 2008-01-20
I've run into a (minor) problem with my installation(s). I made a decision to keep Win98 and proceeded to install Feisty Fawn (Ubuntu v7.04). I found out during the installation that I had a defective DVD and the installation failed. Well I corrected the DVD issue (now using CD drive) and installed Gutsy Gibbon, no problem. So I have Win98 and Ubuntu (v7.10 - Gutsy Gibbon) and I can boot to either. So what's the problem, well, it would appear that my disk was partitioned to account for the failed Feist Fawn and Win98 and Gutsy Gibbon.

[INDENT]partition     filesystem          size             Flags
/dev/hda1  fat32                 9.45GiB       boot, lba
/dev/hda2  ext3                  3.76GiB
/dev/hda4  ext3                  5.12Gib
/dev/hda3  extended          760.89MiB
  -> /dev/hda6  linux swap  290.18MiB
       /dev/hda5  linux swap  470.62MiB[/INDENT]
I'm wondering how I can keep my Win98 and my 7.10 and get rid of failed 7.04 to free up extra space?

Any ideas?

Many thanks,

Buster...

---

### Post by Buster Reid on 2008-01-20
Oh, judging from the boot selection screen it would appear that /dev/hda2 is the failed 7.04 install.

thx

Buster...

---

### Post by mikeyphi on 2008-01-20
> **Buster Reid said:**
> Oh, judging from the boot selection screen it would appear that /dev/hda2 is the failed 7.04 install.

thx

Buster...

Fire up Partition Editor (download Gparted through Synaptic if necessary)
locate hda2
delete the partition!!!!

that's all there is to it....but make double sure you've got the correct partition.

---

### Post by eltama on 2008-01-20
> **mikeyphi said:**
> Fire up Partition Editor (download Gparted through Synaptic if necessary)
locate hda2
delete the partition!!!!

that's all there is to it....but make double sure you've got the correct partition.

If you want to merge the free space with the Gutsy partition you will have to boot from the live cd, install gparted, delete hda2 and then resize hda4. You probably also want to merge the swap partitions.

Instead of gparted you can also use the partitioning tool that comes with the cd. By the way, does any body know how to invoke it from the command line?

---

### Post by Buster Reid on 2008-01-20
What about the "extra" swap, should I do the same with it (i.e. delete and merge)? Is there a sequence that Ubuntu "automatically" sets up/numbers partitions? Which one of the two would logically be associated with the failed install?

Thanks,

...Buster

---

