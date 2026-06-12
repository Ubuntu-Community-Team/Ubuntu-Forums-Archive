---
title: "Grub:  Error 18:  Selected Cylinder exceeds maximum supported by BIOS"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-07-26
I got  a new SATA 500GB hard drive.  I made this HD into 3 partitions:
/dev/sdb1  = 250GB
/dev/sdb2 = 1GB Swap
/dev/sd3 = 250GB

I copied my existing Ubuntu OS to the 250GB and tried to boot.

I get two kinds of errors:

Most boot attempts give me:  Error 16:  Inconsistent Filesystem Structure

About every 3-rd attempt:  Error 18:  Selected Cylinder exceeds maximum supported by BIOS

and about ever 5-th attempt, I can get Ubuntu to boot and it works just fine then.  I know I am booted on this new hard drive partition because I can do a df -h to verify the the new size.

What is the issue here?  I checked my BIOS and everything looks fine.  Is there a maximum size that Ubuntu can handle?  Anyone else experienced this?

Carl

---

### Post by logos34 on 2007-07-26
Maybe it's something to do with the Bios, check if there is a update available--I know my board had an issue a while back not being able to recognize certain 500GB sataII drives, which a bios update fixed.  

If this is a sata II drive, maybe you need to switch the jumper for sata I mode to make it backward-compatible with your board.

Your filesystem could have gotten messed up when you imaged over the root partition.  You could fsck /dev/sdb1 and 3 (but you've probably already done that).  TestDisk is another utility you could try, buit be very careful using it--read the faq/docs on usage.

See these links:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#16](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#16)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

---

### Post by cwmoser on 2007-07-27
Solved.  My BIOS had a "Boot Order" sequence and when I cabled in my new Hard Drive it moved it to the third position -- so a boot off of /dev/sdb1 would not work.  Strange that it intermittently worked.  Perhaps my third drive being an external USB device is the reason.

Carl

---

### Post by logos34 on 2007-07-27
> **cwmoser said:**
> Solved.  My BIOS had a "Boot Order" sequence and when I cabled in my new Hard Drive it moved it to the third position -- so a boot off of /dev/sdb1 would not work.  Strange that it intermittently worked.  Perhaps my third drive being an external USB device is the reason.

Carl

Didn't you install grub to the MBR of the new drive?  Maybe you were/are booting to grub on the old drive. (or maybe you have grub on the root partition instead of the mbr?)

---

### Post by cwmoser on 2007-07-29
> **logos34 said:**
> Didn't you install grub to the MBR of the new drive?  Maybe you were/are booting to grub on the old drive. (or maybe you have grub on the root partition instead of the mbr?)

Grub is one animal that I don't feel confident with.  At the moment, I have 2 hard drives and the Ubuntu partition I am using is on /dev/sdb1.  When my PC boots, a Grub menu from an older partition at /dev/sda3 is displayed.  I traced it to this by putting a distinct string in both the old partition at /dev/sda3 and another in my current partition at /dev/sdb1.  I would like for Grub to point to my /dev/sdb1's /boot/grub/menu.lst but can't figure that out.  

A possibility is that my old /dev/sda3 partition is 20GB and my new /dev/sdb1 partition is 250GB.  I read something about Grub failing if the first partition is greater than 1024 cylinders.

Carl

---

### Post by logos34 on 2007-07-29
Double check your bios--make sure the new drive is being recognized correctly and set for 'auto' (detect).  

This is a newer board with sata--the 1024 cylinder limit error is not right, it's a legacy bios error.  That can't be the problem here.

You can reinstall Grub pointing to the new root partition.  

[B]sudo grub
find /boot/grub/stage1[/B]
(it will print out both /boot locations--hd0,2 and hd1,0--use the newer in the next command)
**root (hd1,0)**  -->i.e. sdb1
**setup (hd0)** --> this reinstalls it to MBR of sda/hd0
**quit**

---

### Post by Genefreak on 2007-09-07
Hi there.

I've had the same error message come up but I haven't changed over any drives etc.

I did have an issue a few days ago with my linux partition being full and it not allowing me to access X... But I deleted a few movie files through commands and managed to get back in. X worked for about a week and then I had this error for no reason... and no matter how many times I boot up I can't get past this bios message. As I've been a Windoze user for many years, my first instinct was to re-install... and I may still do so when Gutsy comes out on the 18th Oct, but until then I'd like to access/backup my email.

Do you have any ideas how to get round this - or how to repair my current install with the Live CD?

Thanks

Steve.

---

### Post by wombat20 on 2007-09-09
Just a suggestion but sometimes grub can get confused if you have a USB pen drive in when you boot up.

I got an error 18 recently and I think this might be related.

---

