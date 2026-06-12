---
title: "USB Hard Drive - where is it?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Spaced Monkey on 2007-01-19
Hi all,

I have an Acer Aspire laptop, which to my incredible surprise runs Ubuntu better than XP, and so far it has all been going well, with one or two exceptions.

The main one is that I have a USB ext HDD, which has worked fine on the same laptop under XP for ages, but Ubuntu just doesn't seem to acknowledge it's existence.   Do I have to do anything in particular to encourage it?   

For the record, I'm not trying to boot from it, it's purely a storage drive.   Filesystem is unknown with certainty, but I'm fairly sure it would be FAT32.

The other thing that is slightly baffling me is accessing shared folders from my other XP box, I set them up with permissions such that my previous XP laptop user could access them over the network.   Straightforward shared folders with no restrictions are fine, but these ones are refusing the username and password which worked previously.   Two possibly relevant details - the username has a space in it, and the workgroup name is probably different now (if Ubuntu even does that).   I have a feeling it's something simple.

I'm very impressed with it overall, as all previous attempts to install Linux have been nightmarish (touchpad never worked, wireless, networking, video hell).   This morning I've been playing WMV files in gXine :)

Ubuntu version, 6.06

Thanks,

Spaced Monkey

---

### Post by JamieC on 2007-01-19
Could you please open a terminal window and post the output of the following command:
```

sudo fdisk -l

```

---

### Post by Spaced Monkey on 2007-01-19
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7108    57094978+  83  Linux
/dev/hda2            7109        7296     1510110    5  Extended
/dev/hda5            7109        7296     1510078+  82  Linux swap / Solaris

---

### Post by JamieC on 2007-01-19
> **Spaced Monkey said:**
> Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7108    57094978+  83  Linux
/dev/hda2            7109        7296     1510110    5  Extended
/dev/hda5            7109        7296     1510078+  82  Linux swap / Solaris

It does not appear to be connected, you definitely ran fdisk as root (using sudo), right?

Shutdown your computer and disconnect the drive. Then power up and wait for Ubuntu to boot. Login, wait a few seconds and then connect it, then try and run the command again. Are there any lights on the drive that indicate activity?

Do you have a live CD, say Knoppix on which you could test the detection with (since it has very good hardware support)?

---

### Post by Spaced Monkey on 2007-01-19
Hi Jamie, 

Thank you!   Power cycling the drive again worked, but hot plugging didn't.   How peculiar!   

I have sda's :)

Spaced Monkey

---

### Post by JamieC on 2007-01-19
Ah, that's good to hear. I'm glad it's working now.

I have no idea about Windows shares I'm afraid, I'll leave this for someone with knowledge in that area.

---

### Post by Dave-C on 2007-01-19
You Could Use 
"type in terminal":

Sudo fdisk -L 

"hit return key"..
"info will show"
"type in terminal":

pmount \dev\sda EXTHD

The Hard Drive Should Show Up On Your Desktop

Note The "EXTHD" In (pmount \dev\sda EXTHD) Is What You Would Like To Call The Drive. So If You Would Like To Call The Drive D: Or My Hard Drive Replace The EXTHD With Wot You Would Like To Call It Like This ...

Pmount \dev\sda1 My hard Drive



The Device Will Be That Name

---

