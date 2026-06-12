---
title: "Missing Patiton Table/Unallocated space? Cannot boot up"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by epi912 on 2007-11-26
Here's what we're messing with:

Dell Inspiron 4000 (I'm sure. It's not here at the moment, I just know it's an Inspiron)
Samsung 40 GIG HD
Intel Pentium III 856 Mhz

All right, here's the story:

So I had Ubuntu 6.10 (perhaps 7.1? It has been a while since I actually used it) dual booting with Windows XP home edition. I reformated Windows and the MBR erased the Grub bootloader. However, right after, I broke my CD-ROM so it was a while before I fixed that problem.

So, after I fixed it, I stuck in the Live cd and opened to G-Parted and it revealed that my HD is unallocated.  After that, I stuck in the actual G-Parted disk and it revaled the same thing. I decided it be best to reboot it without making changes and see on Windows. Nothing would be harmed, right?

Wrong.

When I booted up, following the BIOS splash screen I was greeted by a lovely  

F1 to Try to Reboot F2 for system setup

And now, I want to know what went wrong. I'm guessing that my partition table dissapared, or what. The BIOS is still reconizing the HD so I know it's not that. I really don't want to reformat since I had no backup for my Windows partition. So if reformating is the only choice, any ways I can salvage that info.

Thanks

---

### Post by rabid9797 on 2007-11-26
when you say that you reformated windows, do you mean with a windows install disc or with an ubuntu install disc? also, when you say you broke the cd, do you mean that it broke during installation, or after windows or ubuntu was installed?

---

### Post by epi912 on 2007-11-26
Basically, I just made the track crooked on the CD-Rom, making it unable to open. I straighten that up though, it works fine. I know it has nothing to do with the problem.

I reformatted Windows using the Windows installer. I also used G-Parted before doing that to split my NTFS partition into a 25-5 split. I doubt that had anything to do with it though since I could still access my Windows partition for months.

---

### Post by master_kernel on 2007-11-26
Try checking your CMOS settings to see if it's booting from the CD first.

---

### Post by epi912 on 2007-11-26
It wouldn't try to boot to to the CD unless there was a disk with an ISO file. It's just not picking up on my partitions or boot sector.

---

