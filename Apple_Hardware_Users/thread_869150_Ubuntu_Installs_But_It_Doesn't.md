---
title: "Ubuntu Installs But It Doesn't"
date: 2008-07-24
forum: Apple Hardware Users
---

### Post by TedPacyga on 2008-07-24
Hey I have a 15" Macbook Pro and I decided to install Ubuntu on it and I follow the guide in the macbook pro ubuntu documentation step by step using refit double boot.  I have os x installed and then I partition in os x for ubuntu and then I go to ubuntu live cd and delete the partition I made and make a new one that uses ext3 and then a swap one, the progress bar showed everything partitioned and installed but then I look and nothing is on the partition ext3 so I can't boot into linux.  Help please.

---

### Post by Car60n on 2008-07-24
sounds to me like something went wrong with the installation,
you could try re-installing.

---

### Post by cyberdork33 on 2008-07-24
> **TedPacyga said:**
> but then I look and nothing is on the partition ext3 so I can't boot into linux.  Help please.And how are you going about "looking" on the partition?

---

### Post by TedPacyga on 2008-07-24
I have tried it twice already, I am using 8.04 btw, once with refiit and once without with the same result both times.  I have also checked the disk for integrity and everything checked out ok.  To look on the partition I go to my os x install and use disk utiliy.  It sees the linux swap but not the ext3, it thinks it is fat32 and there is nothing on it.

---

### Post by cyberdork33 on 2008-07-24
> **TedPacyga said:**
> I have tried it twice already, I am using 8.04 btw, once with refiit and once without with the same result both times.  I have also checked the disk for integrity and everything checked out ok.  To look on the partition I go to my os x install and use disk utiliy.  It sees the linux swap but not the ext3, it thinks it is fat32 and there is nothing on it.
Having rEFIt is not going to make a difference either way.

You have no issue that I can tell. DiskUtility ignores the ext3 partitions... It doesn't know what to do with them...

Does rEFIt not show a Linux icon?

---

### Post by estyles on 2008-07-24
Does grub load?  When you start up your computer, it should say something like "GRUB Loading...", maybe "press ESC for menu".  If it does, press escape.  If not, then grub didn't install correctly.  In that case, boot from the LiveCD and choose "Try Ubuntu without installing", then go to Places and look for your Ubuntu partition.  If it's there, you should be able to install Grub.  Your best bet would be to do a search for how to do that.

---

### Post by TedPacyga on 2008-07-24
refit does show a linux icon, but when I click it to boot into it, it starts going and then says no boot disk found or something like that, I can't remember from the top of my head and I am at work so I can not check the exact message. 

I will check for the grub loading thing when I get home, but I do remember it said like iso linux loading or something like that.

---

### Post by cyberdork33 on 2008-07-24
> **TedPacyga said:**
> refit does show a linux icon, but when I click it to boot into it, it starts going and then says no boot disk found or something like that, I can't remember from the top of my head and I am at work so I can not check the exact message. 

Ok, in that case you have a normal Hardy install. There is a bug, please check the FAQ:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by TedPacyga on 2008-07-24
That looks exactly like my problem, I will try it out when I get home.  Also when installing Ubuntu, when you select what partition to install on, is it ok to delete the partition made by boot camp and use ALL the free space, or do you have to leave those small little free spaces for it too work.  Also why when I look at partitions in ubuntu it shows a 0mb free space at the beginning, just wondering about that.

---

### Post by cyberdork33 on 2008-07-24
> **TedPacyga said:**
> That looks exactly like my problem, I will try it out when I get home.  Also when installing Ubuntu, when you select what partition to install on, is it ok to delete the partition made by boot camp and use ALL the free spaceThat's usually what I tell people to do.

> **TedPacyga said:**
> Also why when I look at partitions in ubuntu it shows a 0mb free space at the beginning, just wondering about that.What are you using to check that?

---

### Post by TedPacyga on 2008-07-24
When installing ubuntu for the first time it showed that, but when I use gparted from livecd it doesn't so it's not a problem, just not sure why it did that.

Yay, I got it to boot now.  Now I have to do all the stuff to make everything work, thanks alot.

---

### Post by TedPacyga on 2008-07-25
Ok, well I decided to just go single boot, please don't ask why I would do that because I just wanted to, and I have everything up and running and it works.  However, whenever I open or close windows, or minimize and maximize them they lag once in a while and it is unpleasing to my eyes.  Is this just because I am running this on a mac or is it just a 8.04 bug, is there a fix?

---

### Post by cyberdork33 on 2008-07-25
> **TedPacyga said:**
> Ok, well I decided to just go single boot, please don't ask why I would do that because I just wanted to, and I have everything up and running and it works.  However, whenever I open or close windows, or minimize and maximize them they lag once in a while and it is unpleasing to my eyes.  Is this just because I am running this on a mac or is it just a 8.04 bug, is there a fix?
What graphics driver are you using?

PS, you are free to do what you want on your Mac, though, if you wanted to single boot, it would have been a lot easier to covert your drive to a normal MBR disk rather than dealing with the EFI issues.

---

### Post by TedPacyga on 2008-07-25
I am using the restricted driver.  Also what do you mean by convert to MBR?  I thought EFI was just a BIOS replacement made by intel.  I would like to hear more about this, I would probably want to do that.  Oh yeah another question, is there any way to upgrade the mac firmware even if I don't have osx installed, like use the install disk and comman prompt or something like that?

---

### Post by cyberdork33 on 2008-07-25
> **TedPacyga said:**
> I am using the restricted driver.  Also what do you mean by convert to MBR?  I thought EFI was just a BIOS replacement made by intel.  I would like to hear more about this, I would probably want to do that.  Oh yeah another question, is there any way to upgrade the mac firmware even if I don't have osx installed, like use the install disk and comman prompt or something like that?
See the link in my sig about EFI / GPT. Your disk carries a GPT format. This has limitations that are especially unnecessary if you single boot.

No, you need an OSX install to do firmware updates. The way to get around this is to install to an external hard drive and boot from it when you need to update.

---

### Post by TedPacyga on 2008-07-25
Ok I understand mostly now, thanks.  So if I do convert my drive to MBR (how do I do that by the way, I saw something when partitioning using disk utility in os x, but..), EFI won't have any problems using it?

And yeah having an external hard drive is what I was thinking of if there was no other way, thanks.

---

### Post by cyberdork33 on 2008-07-25
> **TedPacyga said:**
> Ok I understand mostly now, thanks.  So if I do convert my drive to MBR (how do I do that by the way, I saw something when partitioning using disk utility in os x, but..), EFI won't have any problems using it?You would have to start from scratch again as it requires wiping the entire disk. Unless you absolutely have a reason to, I would just leave it. EFI will boot from MBR disks just fine.

> **TedPacyga said:**
> And yeah having an external hard drive is what I was thinking of if there was no other way, thanks.That or leave a partition on your internal harddrive.

---

### Post by TedPacyga on 2008-07-25
Well I already erased all the data on my hard drive, so I guess I will be doing mbr, where do i do that tho?

---

### Post by cyberdork33 on 2008-07-25
> **TedPacyga said:**
> Well I already erased all the data on my hard drive, so I guess I will be doing mbr, where do i do that tho?
just boot from the Ubuntu CD, start the isntaller, and tell it to use the entire disk (unless you want some special partitioning scheme like separating boot and home to their own partitions.)

---

### Post by TedPacyga on 2008-07-25
Oh ok, I think I did that then.  I went into Ubuntu installer and then selected manual install and deleted all partitions and then made my own, is that ok or do I have to actually select the option for guided install use entire disk?

EDIT:
Also, what can be done about the lagging opening and closing of windows?

---

### Post by cyberdork33 on 2008-07-25
> **TedPacyga said:**
> Oh ok, I think I did that then.  I went into Ubuntu installer and then selected manual install and deleted all partitions and then made my own, is that ok or do I have to actually select the option for guided install use entire disk?

What does the output of ```
sudo fdisk -l /dev/sda
``` show? It should give a warning at the top if you have a GPT disk.

> **TedPacyga said:**
> EDIT:
Also, what can be done about the lagging opening and closing of windows?

I have no idea, If you are using the proprietary video drivers, you shouldn't having an issue. You are the only one that I have really seen complain about this.

---

### Post by TedPacyga on 2008-07-25
This is what I get:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00058a3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2490    20000893+  83  Linux
/dev/sda2            2491        2739     2000092+  82  Linux swap / Solaris

So, I am guessing everything looks good.  Hopefully I will figure something out with the lagging issue. Thanks anyway you helped me out so much in the past couple of days.

EDIT:
I just set desktop effects to none and it stopped lagging, I don't know if that can help me out somehow, I want desktop effects btw.  My graphics card should be able to handle graphic effects easily as it is not that bad.  It is a NVIDIA GeForce 8600M GT 256 MB.

---

### Post by cyberdork33 on 2008-07-25
yep looks good.

---

