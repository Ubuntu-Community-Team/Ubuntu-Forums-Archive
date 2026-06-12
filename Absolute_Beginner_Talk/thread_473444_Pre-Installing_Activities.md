---
title: "Pre-Installing Activities"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by chinx21 on 2007-06-14
Are there things I need to do in my computer before I start installing Feisty Fawn? If yes, what are they?

note:
my computer specs:
• Current OS - XP
• INTEL CELERON 331 2.66 GHZ
• A96MP-C2D MOTHERBOARD
• 64 MB INTEGRATED GRAPHICS PORT
• 256 DDR2 667 MEMORY
• 80 GB WESTERN DIGITAL HARD DISC
• 15” MONITOR 
• CDRW/DVD COMBO
 

Thank You in advance!

---

### Post by Outrunner on 2007-06-14
In my opinion, it's more important to know if the internet will work. The best way to test it is to download and burn a LiveCD image and boot into the OS(you don't have to install). Then you can see if everything works as it should(especially the 'net...).

---

### Post by Kobalt on 2007-06-14
You need to get more info, reading [this guide]("http://psychocats.net/ubuntu/installing") for example. Other than this, you've got all you need.

---

### Post by Outrunner on 2007-06-14
Is there anything wrong with your [other]("http://ubuntuforums.org/showthread.php?t=473444") thread?

---

### Post by KIAaze on 2007-06-14
Yes and no.
You can install directly and it should work. (if the disk is not too fragmented or if you plan to use the entire disk for Feisty)

However, it is always recommended to back up important data first. And defragmenting is a necessary step for a successful partitioning of the disk.

So:
1)Back up important data
2)Defragment your Windows partition either with the default windows defragmenter or with another defragmenter of your choice.

---

### Post by ajgreeny on 2007-06-14
256 MB ram is a bit low, better if you can up it to 512, specially as 64 MB of that will be used for graphics.  You don't say which graphics card so no way to know about that, but the live CD will let you know if there is a problem with that.

---

### Post by chinx21 on 2007-06-14
Thanks KIAaze! :popcorn:Anyway my computer is brand new and I've just finish installing XP. What I want is to install Ubuntu to use when I'm surfing the net and XP for home use only.Can you give me a good choice regarding partition? What i want is to be able to use any of the two OS without rebooting my computer and access all files in my computer whatever OS i am using. Thanks!

---

### Post by jvc26 on 2007-06-14
You have to reboot the computer to change between the two OSs. (Unless you virtualise, but then you won't have as good a performance as native)

The psychocats Ubuntu page in my sig has a good guide to planning out partitions etc. Welcome to ubuntu.
Il

---

### Post by frodon on 2007-06-14
duplicate threads merged.

---

### Post by chinx21 on 2007-06-15
Thank you guys and sorry I asked twice.

---

### Post by chinx21 on 2007-06-15
What will be the partition that will fit in my computer?among these:

Create a separate /home partition in Ubuntu/ Separate home

Ubuntu+FAT32

Ubuntu+NTFS


Thanks in advance!;)

---

### Post by KIAaze on 2007-06-16
Any partitions will fit on your 80GB hard disk. It's more a question of how much space you want to assign to each of them.
I have XP+Ubuntu+Debian on a 40 GB HD and already had XP+Ubuntu+Debian+OpenSUSE on it. Currently I have 6 partitions on my PC.

The one tip I can give you from my personal experience with a "small diskspace"(40GB) is to _not use a separate /usr_!
You will probably want to install a lot of programs once you start having fun with Ubuntu and those are usually installed in /usr.

So I recommend leaving at least 10GB for the Ubuntu root partition ("/") (which will also contain /usr unless you specify another partition for it).
For Windows, it's up to you. I reduced it to 10GB since I started using Ubuntu a lot, leaving enough space for game installations.

Having a separate /home is a good idea. But I would put it on an ext3 partition and not a FAT32 one and _certainly not an NTFS one_!

To share data between Windows and Ubuntu, I recommend either using a separate FAT32 partition (not /home) or install the FS-Driver on Windows to access your /home from Ubuntu.
_But keep in mind that read/write Windows access to your /home might eventually make your Ubuntu less secure!_

As suggested before, this guide is very good:
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

Here's what I would recommend for your HD:
10GB NTFS primary ->XP
10GB ext3 primary-> Ubuntu
extended:
1GB ext3->/home
58GB FAT32 ->shared data
1GB swap ->swap

Note: I don't use a separate partition to share data between Windows and Ubuntu since I don't generally need to, so I don't have an idea of how much space /home requires.
[Explore2FS]("http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm") is enough for me if I need to access some Ubuntu file while under Windows (note: when accessing a file, it will copy it onto the Windows partition, so it's not practical for big files).

Of course, if you want more space for data, you can reduce the sizes of the other partitions.
I don't know the exact minimum sizes for Windows and Ubuntu, but I think you shouldn't go under 5GB for both since you have to take into account system updates and minimal program installations.
For the swap, it is generally recommended to use at least twice the size of the RAM, i.e: 512MB in your case.

---

