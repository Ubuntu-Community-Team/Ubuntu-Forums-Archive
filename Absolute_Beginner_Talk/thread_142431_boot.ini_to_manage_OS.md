---
title: "boot.ini to manage OS"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by trorion on 2006-03-10
I'd like to try using boot.ini to manage my OS selection rather than GRUB or Lilo.  Guess that mostly I'm doing this to get more understanding of the MBR process.

So if my HD is:
HDA
partition 1 fat32 backup (on the end of disk1)
Partition 2 /home (next to fat32 backup)
Partition 3 / (next to /home)
Free Space (beginning of disk)

I currently have the linux written to the drive but I don't mind blowing it away and re-installing.  I need to leave the fat32 backup alone if possible.  Don't have the windows written in yet and am willing to Fat or NTFS the partition.

Now, my understanding is that I want to put LILO or GRUB on /boot (in partition 3) instead of in the MBR so that I can use windows boot.ini.

When I install my w2k I will want to copy my BOOTSECT.LNX from my /boot to my C: drive then append the boot.ini file with a reference to that (C:\BOOTSECT.LNX="Ubuntu") right?  Windows will automatically blow away anything I have put on the MBR with their own loader right?  Then the LILO or GRUB on /boot will take over if I select "Ubuntu" on the boot screen.

Then if I ever mess up my windows drive I can practice figuring out how to write a MBR...hmm.   Guess I better make a backup boot disk for linux..

---

### Post by lha on 2006-03-10
You seem to have a(n) (almost) working plan. Note that /boot isn't / and there is no file called BOOTSECT.LNX, you need to copy the *boot sector* of the bootable linux partition into a file in Windows. (I guess you already knew this, I just wanted to make it sure.)

You may want to take a look at [BootPart]("http://www.winimage.com/bootpart.htm"), it does most of the job for you.

---

