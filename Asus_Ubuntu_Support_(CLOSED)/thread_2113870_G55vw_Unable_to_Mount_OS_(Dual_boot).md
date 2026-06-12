---
title: "G55vw Unable to Mount OS (Dual boot)"
date: 2013-02-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by jmcoyy on 2013-02-08
I've been running Win 7 along side ubuntu for a few months now with any problems. Getting the dualboot to work was a bit tricky and required some modifications of the boodloader. 

Today, Win7 comes to a near halt and I hard restarted the laptop. Upon restarting I was met with options to repair startup problems. Needless to say, Win7 is no longer working. After modifying the bootloader startup repair can no longer find the OS.

But the real problem is now in ubuntu, before I had three drives visible (OS, Recovery and DATA). Now, I only have OS visible but when I click it returns "Unable to mount OS".  I am not able to save any files nor login as root do to the fact that my computer is "unable to find XAuth file". 

I've done some searching but I can't find a solution specific to this problem. Advice is appreciated.

---

### Post by ambdeep on 2013-02-19
check with gparted if it shows the other partitions, if not you might have accidently deleted or corrupted them. if so the only way you can fix this is by re-installing windows from scratch using either the recovery partition or a installation disc. if on the other hand gparted does show the various partitions, try using boot repair(available on software center).

---

### Post by binary00mind on 2013-02-27
> **jmcoyy said:**
> I've been running Win 7 along side ubuntu for a few months now with any problems. Getting the dualboot to work was a bit tricky and required some modifications of the boodloader.
Did you manually edit Win Bootloader to boot into Ubuntu or while installing Ubuntu you installed Grub to the MBR? Thus you had Grub interface before choosing the OS.  

> Today, Win7 comes to a near halt and I hard restarted the laptop. Upon restarting I was met with options to repair startup problems.
Bad move, shouldn't do that (repairing)
>  Needless to say, Win7 is no longer working. After modifying the bootloader startup repair can no longer find the OS.
Find some DOS partitioning tool or boot from Ubuntu Live CD and take a peek which partition is active. Install gpart and/or testdisk which will give you the answers.

> But the real problem is now in ubuntu, before I had three drives visible (OS, Recovery and DATA). Now, I only have OS visible but when I click it returns "Unable to mount OS".  I am not able to save any files nor login as root do to the fact that my computer is "unable to find XAuth file".
To login as a root is a last resort. (in this scenario) 
You mentioned or used the word "visible" visible to what? What program? under which OS?
Plus you mentioned:
Quote:
before I had three drives visible (OS, Recovery and DATA).
I assume that your Asus came with Win 7 pre-installed. Has the Win 7 also have/had a "System Reserved" small partition? Some have some don't (if you would install Win 7 from DVD then 100% you have the small partition unless there are no more primaries left)
In any case. More info is needed. 
How is you Hard Disk partitioned?
I give you an example from mine.
/sda1 -Recovery
/sda2 -System Reserved
/sda3 -Win 7
/sda5 / Ubuntu 13.04 (I don't need swap)
second Hard Disk
/sdb1 /root - Ubuntu 10.04
/sdb2 /home
/sdb5 /swap
/sdb6 /var
/sdb3 -Win 8

Do this Boot from live Ubuntu CD. Install gpart and testdisk.
Note "testdisk" you must run via terminal..but it will find you all your partitions (even the lost ones) and if needed it will restore them (with ease)
After you find your lost partitions, reinstall grub plus make sure that your Win 7 partition is active.

Let us know.

---

