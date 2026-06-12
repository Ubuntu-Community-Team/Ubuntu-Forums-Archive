---
title: "Dual Booting - Vista/Ubuntu"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by ThirstyBrain on 2007-11-07
After not getting any advise regarding installation issues on my previous computer for 7.10, [http://ubuntuforums.org/showthread.php?t=590319](http://ubuntuforums.org/showthread.php?t=590319), I decided to try and install it in my new computer:
HP
2GB PC2-5300 DDR2 Memory
360GB 7200rpm SATA Hard Drive
NVIDIA GeForce 6150SE Integrated Graphics

But before I do, I just want to know everything possible of installation issues or how to avoid them.  Dont want to have my hd wiped or lose windows, at least for now.
I had a little problem when I ran the live cd.  After restarting, it gave an error message saying that my hd failed and needed to be replaced.  It was weird as I did not choose to install, only ran the livecd.  Then windows wouldn't load so I guessed the boot.ini somehow got corrupted then had to restore.  Which is why I ask for the following advise.

After getting a general idea of the process and reading several guides, I've seen many users complain of losing vista loader or having their boot corrupted and not being able to load linux or vista or losing vista altogether.  I want to avoid this if possible.
It seems simple enough to shrink the partition and free space for linux and then install linux in that partition.  The only thing I am worried of is getting the boot up running smoothly. It doesn't matter if linux handles it or windows, just want it to work when I choose which os to load.  How do I avoid having any issues with the bootloader?  Would it load fine upon installation or will I have to do some tweaking? Also, are there other issues I should be aware of when installing?

Thanks for any advise.  

Also, what should I have ready (programs or commands) in case things get a little messy?  I've heard of ntfsfix or something like that.  Just want to be prepared and ready.

---

### Post by fhqwhgads on 2007-11-07
Defrag & back up (at least the important stuff!) the Windows partition first. Use a live CD to shrink the partition (GParted or Parted Magic are good). Create your swap and root partitions, and /home if you choose. 

Reboot into Windows again before you install Ubuntu. Your disk will need to be checked for consistency after resizing the partition, so don't cancel CHKDSK. If you skip this step, it won't be recognized and GRUB won't have an entry for it.

After that it should be smooth sailing. If you want to get rid of Ubuntu, just delete the partitions and use your Windows disk to boot into Recovery console and restore the bootloader. Hope that helps.

---

### Post by Pumalite on 2007-11-07
Do not use Gparted to shrink the partition. With Vista you have to use Vista partitioner to allocate space for Ubuntu first; otherwise Vista will not let you run anything in that computer. Then install Ubuntu and let Grub install to MBR (by default). This will give you a menu to boot either OS.

---

### Post by jrharvey on 2007-11-07
I had no problem using gparted with my vista and machine. I was able to shrink it down to half the size.

---

### Post by jrharvey on 2007-11-07
There is also WUBI 7.04 and WUBI 7.10(alpha) that worked wonders on 2 other friends computers. The alpha worked fine for me. The only problem is distribution upgrades did not work. Other than that it is the easiest way to dualboot windows and ubuntu. (easiest not best) It is still very good if you are new to ubuntu and dont know if you want to take the switch.

---

### Post by Pumalite on 2007-11-07
You can also run Ubuntu in Windows with Virtualbox. Use your iso or CD.(need 1 GB RAM)

---

### Post by ThirstyBrain on 2007-11-08
I'll attempt to install Ubuntu for now, virtualization is a totally new concept to me and would need to get my feet wet first before I dive in though I find it interesting,
first Ill need to create restore disks in case of any mishap, dont need backup as I just got the computer not too long ago and dont have any important stuff in there....
One quick question, the computer came with a separate partition for recovery....will I be able to access it if anything goes wrong??? will create restore disks anyways just in case, just wanted to know

Summary:
Defrag drive
Use windows partition to resize and make space for Ubuntu
Restart Computer
Let Chkdsk run and ck for consistency
Restart with LiveCD
Install
Live happily ever after........
Am I missing anything?
On installing, will it automatically detect the space that I have made for Ubuntu or will I have to manually configure? Also is this where root/home/swap come into place?   Will it give me the option of the size of the root/home/swap? I have 2 GB mem, so I give 2 GB for the swap right, even though it is stated to give 2X the mem, heard 2GB is the max....
Thanks

---

### Post by candtalan on 2007-11-08
> **ThirstyBrain said:**
> After not getting any advise regarding installation issues on my previous computer for 7.10, [http://ubuntuforums.org/showthread.php?t=590319](http://ubuntuforums.org/showthread.php?t=590319), 

It looks like there were a number of detailed replies
> 
I decided to try and install it in my new computer:
HP
2GB PC2-5300 DDR2 Memory
360GB 7200rpm SATA Hard Drive
NVIDIA GeForce 6150SE Integrated Graphics
But before I do, I just want to know everything possible of installation issues or how to avoid them.

As you have seen, vista is not quite so easy to handle as xp. (why would ms make it easier anyway?)
> 
  Dont want to have my hd wiped or lose windows, at least for now.

Obviously there is a small risk. The lowest risk is to use a spare machine - separate from the machine you rely upon.
The *worst* that can happen is that you may have to re install vista. 
> 
I had a little problem when I ran the live cd.  After restarting, it gave an error message saying that my hd failed and needed to be replaced.  It was weird as I did not choose to install, only ran the livecd.  Then windows wouldn't load so I guessed the boot.ini somehow got corrupted then had to restore

I  would be most suspicious of this and would not proceed until more was known about why this is happening. Is it repeatable?

---

### Post by Pumalite on 2007-11-08
Backup everything before the installation of a new OS as a matter of good practice.

---

### Post by nicolito on 2007-12-09
May be a little late, but before doing any multiOS-instlation [http://multibooters.co.uk/]("http://multibooters.co.uk/") is a very good place to read thoroughly to understand what happens, what might happen and why. Might spare anyone some headache later on.

Cheers

---

