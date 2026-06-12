---
title: "Gutsy Broke my desktop"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by gantww on 2008-02-12
Hello all,
Saturday morning I decided to upgrade from Fiesty to Gutsy on my desktop machine. The direct upgrade failed with a message about repositories that I didn't particularly understand. Since I figured I'd rather have a clean install anyway (I had everything backed up and didn't have much in the way of custom settings), I popped in the new Gutsy disk. Everything went fine, until I tried to reformat. After formatting, it said it couldn't load the ext3 partition. Attempting to boot from the live cd thereafter produced an error talking about sda1 and something about block 0. I have a secondary hard drive, which I switched over to be master and tried again, with the same result.

Did Gutsy just brick both of my hard drives, or am I missing something? Could they have been bad before, but stable with my Fiesty install due to just plain luck? Is it possible that the drives just don't support something that is needed for ext3? 

Thanks,
Will

---

### Post by billgoldberg on 2008-02-12
You can check the disc for errors when you boot from the cd.

It could just be a bad iso or bad burn.

---

### Post by oilchangeguy on 2008-02-12
> **gantww said:**
> Hello all,
Saturday morning I decided to upgrade from Fiesty to Gutsy on my desktop machine. The direct upgrade failed with a message about repositories that I didn't particularly understand. Since I figured I'd rather have a clean install anyway (I had everything backed up and didn't have much in the way of custom settings), I popped in the new Gutsy disk. Everything went fine, until I tried to reformat. After formatting, it said it couldn't load the ext3 partition. Attempting to boot from the live cd thereafter produced an error talking about sda1 and something about block 0. I have a secondary hard drive, which I switched over to be master and tried again, with the same result.

Did Gutsy just brick both of my hard drives, or am I missing something? Could they have been bad before, but stable with my Fiesty install due to just plain luck? Is it possible that the drives just don't support something that is needed for ext3? 

Thanks,
Will

an operating system can't kill your hard drive. I had an issue recently, while trying to upgrade my laptop to 7.10. it runs 7.04 perfectly. both the online upgrade, and cd install failed. so after a fresh install of 7.04, no more problems.

---

### Post by gantww on 2008-02-12
That's what I was thinking too, but I was halfway wondering whether my drive wasn't already half dead beforehand. However, I don't know enough about how filesystems are constructed to know whether it was possible that it could already have been broken. For instance, if something happened to the drive that made it impossible to write to the part of the system where the partition table is, but still left it where it could read, then perhaps wiping the system would make it unusable from here on out. But it does seem to be a pretty unlikely circumstance statistically.
Could it be something flaking out on the motherboard? Or a driver missing/incorrect for it? That would mess up hard drive access wouldn't it?

Will

---

### Post by rkd on 2008-02-12
Some sort of hardware failure, either of the disks or the motherboard, is a possibility, but I think it is less likely than you have a bad CD. Did you try booting the live CD and choosing the verify CD option from the boot menu? That's the first thing I would do. If that check doesn't find anything wrong with the CD, boot Ubuntu from the live CD, open a Terminal, then enter```
gksu gparted
```and see what it can tell you about the disks.

---

### Post by gantww on 2008-02-12
Hmm. This is interesting. I couldn't even get it to boot with the live cd. I was able to pop in a windows XP disc and reformat NTFS with no problem. I have it installing windows, since my experience indicates that if windows is good for anything, it's good for blowing up in some way over the least little thing.

Will be posting back when once Windows is done doing it's thing. Then hopefully the live disc will work and I can get a real OS back on this thing.

I thought I'd go ahead and post this just in case it gave somebody an idea.

---

### Post by gantww on 2008-02-12
Hmm. I was able to get a Fiesty CD to boot after I used the XP disk to blow away the partitions. It still the funky errors on boot (the sda1 stuff). Anything else I can do diagnostic-wise?

---

### Post by gantww on 2008-02-12
Hmm. Now I can go back and verify the integrity of the CD. It says no errors found. I did see a brief message about "Cannot allocate resource region...." It flashes up so fast I can barely see it. Is there any way to get at that message?

---

### Post by rkd on 2008-02-12
If the message that goes by too quickly to see is from Ubuntu, you might be able to find it in the system log. After the system boots, open a terminal and type the command dmesg and read through the output. Or another way to look at the log is go to the System menu, select Administration, then System Log. When the window opens, click on syslog in the left pane of the window and messages should appear in the right pane.

If the message is from the BIOS, there are a couple of things to try. Sometimes the scroll lock key on the keyboard will stop messages from scrolling off the screen. That doesn't always work, but sometimes it does.

Another trick that sometimes works is to put a nonbootable floppy disk in the floppy drive (if you have a floppy drive). When it stops to ask you to put in a bootable floppy, that stops scrolling stuff off the screen.

If you do get to read that message, copy it down carefully and post it here and we'll help you figure it out.  Same with the message about block 0 on sda1 -- copy it down exactly and post it here.

---

### Post by gantww on 2008-02-13
Well,
I stuck another hard drive in there and it works. Guess it was the drive after all. So, this one is handled.

Thanks everyone!

---

### Post by rkd on 2008-02-13
You are probably right that something about the original hard disk was causing the problem. There is a chance that there is nothing wrong with the disk itself. The problem might be some data on the disk is inconsistent and that is making the software misbehave when it sees data it doesn't expect.  Think a bad partition table.

Before you discard that disk, it might be worthwhile to run the manufacturer's drive diagnostic program on it to see whether the drive really is bad. If it isn't bad, you could use that disk again in this or another computer.

---

