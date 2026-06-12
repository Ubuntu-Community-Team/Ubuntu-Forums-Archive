---
title: "Installing OS X under ubuntu"
date: 2007-07-02
forum: Apple PPC Users
---

### Post by Simon_ on 2007-07-02
Hey, I have a PowerBook G4 running ubuntu linux and I want to have a multiboot with OS X and Ubuntu.
I tried this the first time I tried to install ubuntu, with os X allready installed but it seemed like it wasn't doable, so I just wiped the harddrive and installed ubuntu.
After the clean install  I have the yaboot bootloader (it installed automatically with ubuntu).
I've never touched linux before, and not really os X either so is there anything I should know?
Like how should I partitionate, etc.

Thanks a bunch.

---

### Post by pxwpxw on 2007-07-02
Hi,
What size is your drive?

---

### Post by Simon_ on 2007-07-02
I think its either 50 or 60.
I have around 40 available.
Just one partition.

---

### Post by tcrroadie on 2007-07-02
Since I have never tried installing OS X after an installation of Ubuntu, maybe I can help you on your dual boot installation issue of installing Ubuntu after an installation of OS X. 

Installing Ubuntu on a PowerPC Mac with an installation of OS X requires a fresh installation of OS X.  

The OS X installation DVD contains partitioning tools in the "Disk Utility" menu.

After booting into your OS X installation DVD, open Disk Utility, and select your hard drive.  Select the partition tab and under the Volume Scheme menu select 2 partitions.  Select the second partition and from the Format menu choose "Free Space", this will be used for your Ubuntu installation.  Resize this partition to your needs. 

Then select the first partion and select HFS Extended for your OS X installation.  Click partition at the bottom of the screen and then exit Disk Utility.  

Then install OS X.  After you have installed OS X, you should easily be able to install Ubuntu to the Free Space partion you created.  

Hope this helps.

---

### Post by Simon_ on 2007-07-02
thanks but I don't want to wipe my ubuntu allready installed...

---

### Post by sethdotcom on 2007-07-02
You have to install OS X first, in my experience that is the only way to multi-boot linux and osx.


Good luck

---

### Post by Simon_ on 2007-07-02
Oh, allright.
I was thinking I had to have yaboot in first (wich ubuntu does).
Atleast that was what it seemed like when I used the ubuntu cd (not fiesty but 6.10 or something).
And os X doesn't come with a bootloader, so how do I chose what os to load...
Guess I'll just have to try and find out

---

### Post by pxwpxw on 2007-07-03
**Simon_**

If you install MacoX in  part of the hard drive ( say a 20 GB partition), and leave the other part free, ubuntu can create its partitions in the free space and install there, including installing yaboot and  the selection to start MacosX or ubuntu. You maybe had  problems at your first attempt because MacosX was installed in the whole disk - leaving no free space for ubuntu. The best thing to do now is to reinstall Macox from scratch,  as  in t**crroadie's** post above, and then ubuntu. Should be easy on the PowerBook G4.

If you wanted to, when you install MacosX, you could also make a 2nd  macos extended but not journalled partition, say 10GB, for common use by MacosX and ubuntu, but only if you want that facility.

---

### Post by Simon_ on 2007-07-13
(sorry for the very late reply, in my vacatin).

Thank you, I will do that tomorrow!
But this seems like what I did the first time i installed ubuntu!
I had osX installed, and with the cd I made a partition for ubuntu , right format and all.
When I chose it to install it told me I needed yaboot for booting both disks but it like just said that...
but didnt install it. And im 100% sure I had two partitions.
one with OSX and one ready for ubuntu.
Could the fact that I was using 6.10 and not fiesty cd have anything to do with this?
The fiesty cd wont load for me (not sure if I allready mentioned this, sorry)

But yeah, I'll try formatting the whole thing, installing osX and make a partition for ubuntu and I'll see how it goes.

-cheers

---

### Post by Auria on 2007-07-13
> **Simon_ said:**
> 
I had osX installed, and with the cd I made a partition for ubuntu


no, actually, don't make a partition for ubuntu, just leave empty space and tell the installer to use empty space - then it will create all partitions itself so it will make them as it wants them and you're happier ;)

---

