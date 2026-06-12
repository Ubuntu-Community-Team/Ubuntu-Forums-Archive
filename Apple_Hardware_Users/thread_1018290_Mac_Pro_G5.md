---
title: "Mac Pro G5"
date: 2008-12-21
forum: Apple Hardware Users
---

### Post by terry@softreq.com on 2008-12-21
I have a Mac Pro G5 dual core 1.8ghz machine.

Can I install Ubuntu 8.10 as a dual boot?

If so, where would I find the version to do so?

Or if I install it, will it overwrite the existing Mac OS for good?

Thanks, Terry

---

### Post by tiresia on 2008-12-22
If you don't have much experience with Linux, you may want install Ubuntu Intrepid like this:
1. Back up any important data of you MacOSX partition. You won't loose anything, but it's better to be sure...
2. Download the Intrepid alternate powerpc CD (ubuntu alternate 8.10)
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
3. Burn the downloades iso image with the Apple Disk utility. 
4. Start you powermac g5 (you don't have a mac pro!) pressing C, in order to boot from the CD.
5. At the yoboot prompt, hit TAB. You will get different options. You have a powerpc64 (64 bit). Choose to install with powerpc64.
6. There is a bug with the alternate CD, that doesn't detect the CD-ROM. Read this thread for a workaround:[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)
7. When you will be asked, how and where to install Ubuntu, choose the Manual Configuration. There you can resize the MacOSX partitions according to your needs. After resinzing MacOSX, you have got some free Space.
8. Now you can choose again the option 'Guided on largest free space'
The Installer will make the necessary partitions for you. You are done. Install Ubuntu.

---

### Post by terry@softreq.com on 2008-12-22
Thanks Tiresia, I will give  it a shot!

---

### Post by terry@softreq.com on 2008-12-22
Question: Will Ubuntu make use of the dual processor configuration?

---

### Post by tiresia on 2008-12-22
> **terry@softreq.com said:**
> Question: Will Ubuntu make use of the dual processor configuration?
Yes, there is no problems!
To control the processor's speed (and the fans) you can try two different demons for scaling power: powernowd or cpudyn (you have cpufrequtils also, but you need to configure it a bit)

Anyway, if you prefer, you can try Ubuntu without installing it. 
Just download from the same link above, Ubuntu Hardy 8.04 Desktop (LiveCD).
You can install it afterwards

---

### Post by terry@softreq.com on 2008-12-22
I see, thanks.  If I download 8.04, will I need the special trick to get the machine to recognize the floppy?

Thanks!  Terry

---

### Post by tiresia on 2008-12-22
> **terry@softreq.com said:**
> I see, thanks.  If I download 8.04, will I need the special trick to get the machine to recognize the floppy?

Thanks!  Terry
No, the LiveCD should work smoothly. 
You can get another problem if you install it. 
Remember to choose the option live-nosplash-powerpc64 when you get prompted by yaboot

---

