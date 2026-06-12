---
title: "[SOLVED] partitions"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-10-14
Here is the partitions of my hard drive. What is the partition /dev/hda4 Extended?? Is this my Home directory. I dual boot with XP.:confused:

  Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         490        4137    29302560    7  HPFS/NTFS
/dev/hda2               1         489     3927861    b  W95 FAT32
/dev/hda3            4138        9565    43600410   83  Linux
/dev/hda4            9566        9729     1317330    5  Extended
/dev/hda5            9566        9729     1317298+  82  Linux swap / Solaris

---

### Post by Pumalite on 2007-10-14
You should be able to see it and mount it with Nautilus. Places>Home (left column)(Filesystem)

---

### Post by dptxp on 2007-10-14
hda5 is the only partition in extended partition hda4, it occupies full hda4.
You will not be able to mount hda4. I t contains hda5.

You can make hda5, hda6 etc in hda4.

---

### Post by dpar on 2007-10-14
Heres a definition........> Extended

An extended partition is secondary to the primary partition(s). A hard disk may contain only one extended partition; which can then be sub-divided into logical drives, each of which is (under DOS and Windows) assigned additional drive letters.

For example, under either DOS or Windows, a hard disk with one primary partition and one extended partition, the latter containing two logical drives, would typically be assigned the three drive letters: C:, D: and E: (in that order).

Extended partitions are useful if you want more than four partitions on a single physical drive. Technically, the number of logical drives is no longer limited in later operating systems, but under Windows there is an effective limit if they are to be assigned drive letters (only 24 letters, C: through Z:, are generally available. Later operating systems may allow more drives to be mounted/accessed by using A-A:, A-B:, A-C:, etc.).

---

### Post by milosz.galazka on 2007-10-14
You can have only four main partitions. Using Extended (treat it like container) partition you can omit this limit.
For example:
1. primary partition
2. primary partition
3. primary partition
4. primary partition
Here you cannot have more partitions to use.

But by creating Extended partition you can have more of them.
For example:
1. primary partition
2. primary partition
3. primary partition
4. Extended partition
    4.1 another partition
    4.1 another partition
4.3 ...
...

---

### Post by dptxp on 2007-10-14
Suggest delete hda5 (not hda4) Gparted CD, make one or more data partitions and one 1-2 GB SWAP partition.

You will have to mount the new partitions.

---

### Post by skyjacker on 2007-10-14
> **dptxp said:**
> Suggest delete hda5 (not hda4) Gparted CD, make one or more data partitions and one 1-2 GB SWAP partition.

You will have to mount the new partitions. Does hd4 contain my home file stuff, or is that in hd3?? Can i make hd4 my home directory stuff, mount it as /home, and the /swap in the sa4e hd4? Sorry for all the questions about this. When I installed ubuntu, I shrunk my Xp partition, and used g-parted to install to the remaining free space. tThats why I didn't knoe what the Extended partition was.

---

### Post by Pumalite on 2007-10-14
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by vanadium on 2007-10-14
> **dptxp said:**
> Suggest delete hda5 (not hda4) Gparted CD, make one or more data partitions and one 1-2 GB SWAP partition.

Do not touch your partition table! It is absolutely fine!

Your Ubuntu system partition is sda3. It contains all system files, and also your /home directory. You already were explained what hda4 is. It is an extended partition, which is just a "container" that can contain several logical partitions as a "trick" to have more than 4 partitions on a drive.

---

### Post by skyjacker on 2007-10-14
> **vanadium said:**
> Do not touch your partition table! It is absolutely fine!

Your Ubuntu system partition is sda3. It contains all system files, and also your /home directory. You already were explained what hda4 is. It is an extended partition, which is just a "container" that can contain several logical partitions as a "trick" to have more than 4 partitions on a drive. So iwhen I install Kubuntu I will lose all of my home file stuff? If I back it up on a disc can I then put it bak in hd3? I plan on doing a "Clean" install. Thanks for your help.

---

### Post by Pumalite on 2007-10-14
You can save your /home, including 'Hidden Files' to CD or DVD and later restore it.

[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)

---

### Post by skyjacker on 2007-10-14
> **Pumalite said:**
> You can save your /home, including 'Hidden Files' to CD or DVD and later restore it.

[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm) I appreciate all of everyone's help. I think I can safely install Kubuntu 7.10 Thanks again:)

---

