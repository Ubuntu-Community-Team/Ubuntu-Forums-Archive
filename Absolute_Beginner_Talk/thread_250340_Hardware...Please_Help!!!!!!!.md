---
title: "Hardware...Please Help!!!!!!!"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Brahman on 2006-09-03
Hello, 

I have been trying to install Ubuntu for about 3 hours. Everytime it would load (this is the Desktop CD) and after the rectangle box loaded (the one that says 'Window Manger', Nautilus or something like that.) Well, after that the screen goes to a brown background and just the mouse. Nothing else. But once it loaded both panels, they stayed white and one little icon in the bottom left of the bottom panel apppeared, but now it won't. 

What should I do? I was told I need at least 192 MB of RAM. Are there any other distros like Ubuntu, that require less RAM that I could try. 

Here's some basic specs of my computer:  AMD-K6(tm) 3D processor and 400 MHz, 128 MB of RAM. 

I hope all this makes sense. 


Also, when I click ' Start or install Ubuntu' after the CD boots and after it says Loading Linux Kernel, it says beneath where it says ' Ok, booting Linux kernel' that it was unable to detect ACPI then it says cannot locate RSDP or something. 

Thanks.

---

### Post by szf on 2006-09-03
You may be on the cusp of being too underpowered to run Ubuntu 6.06.

Maybe [xubuntu]("http://www.xubuntu.org/") fits your hardware?

---

### Post by bodhi.zazen on 2006-09-03
You may be able to do it with the "alternate" cd.

---

### Post by szf on 2006-09-03
I just stumbled upon the earlier thread for this... the recommendation looked like it was leaning toward increasing the RAM if possible.

An AMD K6 prolly uses PC100 RAM (anyone correct me if I'm wrong)... if a RAM upgrade is in the cards, you'd be wise to consider a complete "yesterday's pc" (Pentium IV, no HT etc.; AMD Sempron) rather than a used RAM module from ebay.

---

### Post by Brahman on 2006-09-04
Do you think Xubuntu would run off of 128 MB of RAM? 


But what is this RSDP and ACPI stuff that it says it cannot locate?

---

### Post by szf on 2006-09-04
> Do you think Xubuntu would run off of 128 MB of RAM? 
Yes.

> But what is this RSDP and ACPI stuff that it says it cannot locate?
I *think* that may have to do mostly with the age of the hardware. The BIOS can't handle functions that the modern Linux kernel tries to use out of the box.

There's a acpi=no boot option available for GRUB that may quiesce those messages (if you ultimately had a working Ubuntu system).

---

### Post by Brahman on 2006-09-04
I tried to see what would happen if I just let the brown background and mosue sit and the panel at the top loaded, it was white with nothing on it and vanished and then this popped up in the top right corner: Computing polyhedra.

---

### Post by eternalis on 2006-09-04
You might be able to install from the LiveCD, by creating a swap partition first. The install CD automatically detects it and uses one to make the install process faster.

---

### Post by Brahman on 2006-09-04
How do I create the swap partition?


Do I have to use a program like "Partition magic" on Windows and then boot the Ubuntu CD again?

---

### Post by eternalis on 2006-09-04
You can use the GParted LiveCD:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

You can also use QParted.

---

### Post by Brahman on 2006-09-04
So can I download this to a reg. CD or DVD and then take it to my other comp. (the one I'm trying to install Ubuntu) and open windows and install this program and partition and then try isntalling again?

---

### Post by bodhi.zazen on 2006-09-04
Download -> burn to CD -> boot computer from CD (not windows) -> create swap partition.

Note: The "alternate" CD may be easier.

---

### Post by szf on 2006-09-04
To add a swap partition, you may be able to use the Live Dapper CD. Taking from this thread on [parted]("http://ubuntuforums.org/showthread.php?t=247128&highlight=parted")
Start at step 3... 
[I]
3. Open up terminal and type in "sudo parted"
4. Type "print" and make a note of the # of the drive that you want to shrink.
[/I]
Instead of step 5, utilize the command **mkpartfs *part-type*  linux-swap *start  end***. Linux swap partitions are usually 2x larger then the physical RAM on the system, so consider the following partitioning scheme for a disk with only primary partitions:
[I]
/boot start at 0MB - end at 100MB
swap  start at 101MB - end at 357MB
/     start at 358MB - rest of the disk
[/I]
The command would be: **mkpartfs *primary*  linux-swap *101  357***. Then exit parted by typing quit.

---

