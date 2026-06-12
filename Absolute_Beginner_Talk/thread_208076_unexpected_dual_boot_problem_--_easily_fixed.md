---
title: "unexpected dual boot problem -- easily fixed?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2006-07-03
I hope someone can help me with my GRUB problem.  This problem was unexpected as I have done dual boot on other machines.

I made a backup of my MBR (446 bytes) before doing the stuff mentioned below.  Also, please note that below I have used the following variations of root in my attempts to be able to boot into XP:  (hd0,1) , (hd0,4) , and (hd0,5) <none have worked>

Windows XP was previously the only OS on the machine.  When I installed XP, I purposefully put it onto the second partition, so that the volume looked like this:
 ...  Partition 1 - 50 GB NTFS empty but formatted NTFS
  ... Partition 2 - 200 GB NTFS with Windows XP install

Today I used the LiveCD of GParted, and I purposefully deleted that 50 GB partition at the beginning of the volume.  I am aware this wiped out my MBR.  I deleted this 50 GB partition so that it would become unallocated space.  I did this so that when using the Ubuntu DesktopCD, I would be able to install Ubuntu into that 50 GB unallocated space.

I successfully installed Ubuntu/GRUB into that 50 GB unallocated space today.  It works great.  So now my hard drive looks like this to Ubuntu:
  ... Partition 1 (/dev/sda1) (Extended 3) (/root) 48 GB
  ... Swap Partition (/dev/sda6) 2.0 GB
  ... Partition 5 (/dev/sda5) (Windows NTFS) (/tmp/disks-conf-sda5) 200 GB

I edited the GRUB menu.lst file as I have in the past - so far, this is all stuff I have done before on other machine.  In menu.lst , I added the following commands in the appropriate section: (added this text above the Ubuntu kernel title mentions in that section)
        [SIZE="3"]title		Windows XP sp2
        root		(hd0,5)          <-- also tried (hd0,1) and (hd0,4)
        makeactive
        chainloader	+1[/SIZE]

Unfortunately, when I use the GRUB boot menu, it won't boot into Windows XP.  It gives an Error 12 Invalid device requested error.  It also gives a Filesystem type unknown error first, but I think the problem is that I for some reason do not have it pointing to the correct device.  

Thanks in advance for any help!

---

### Post by Apple 101 on 2006-07-03
/dev/sda5 is the beginning of the logical drive partition sequence.  Did you install Windows XP to a logical partition? To find out what partition is on: System --> Admin --> Disks (something like that).  Select Partitions and check your Windows partition. You can also use *sudo fdisk -l*.

---

### Post by Average_Joe on 2006-07-03
Apple 101 -

Thanks for the reply.  I'd like to know through what console can I use the fdisk command.  I cannot boot into Windows at this time.

Thank you!

---

### Post by Apple 101 on 2006-07-03
Sorry -  Do that in Ubuntu.  Use the GUI or the bash shell for that.  If worst comes to worst, you can view the information in recovery mode.

---

### Post by confused57 on 2006-07-03
Pardon my intrusion, but you can open a terminal(Applications---Accessories---Terminal).

```
sudo fdisk -l
```
The -l is a small "L".

This should show your partition tables...Apple101 is right, it does look like Windows is installed on a logical partition(sda5).
It's really difficult to dualboot Ubuntu and Windows, if Windows is installed on a partition after Ubuntu...Windows always wants to be on a partition before any other OS.

Edit:  Rather than bumping this thread...glad to hear you got it working.  I don't think I've seen anybody get a dual boot of Ubuntu/Windows working, if Windows is on a partition after Ubuntu.  I've used gparted before, it's a handy partitioning utility to have...easy to use.  The Ubuntu installation partitioner has always worked for me resizing Linux partitions, haven't tried on Windows...I dualboot with 2 hard drives.

---

### Post by Average_Joe on 2006-07-03
Thanks to you both.  I didn't answer Apple 101's earlier question about logical partition, because I don't know what that is.  Nonetheless, I can attest to the truth of the comment of Confused57 regarding the difficulty to boot Windows XP in the case where XP is installed after Ubuntu. ('after' meaning the order of partitions on the disk).  I attempted a few hours worth of learning trying to boot back into Windows XP and realized eventually that it wasn't going to happen.  [Among my attempts: (1) Windows Recovery Console; (2) GAG Boot Manager; (3) restore of my MBR backup, etc...]

Anyway I reformatted overnight and started from scratch.  The adventure was worth it as I learned a lot of good stuff.  Today I am up and running with dual boot of XP and Ubuntu and it's working great.  Thanks in so small part to forum threads by you two gents.

I did run into one Ubuntu problem which was unexpected, and unexplainable, even after my fresh volume reformat.  But I think I will make a new thread for it.  So that you two can find it, it will be titled (green arrow) "Ubuntu doesn't like single partition? "  Thanks.

---

