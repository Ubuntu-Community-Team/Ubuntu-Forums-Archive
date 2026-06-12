---
title: "Installing ubuntu"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Terrigal on 2008-03-26
I have a Ubuntu 7.10 cd
I would like to install it onto a second hard disk  that I have installed in my Computer My C drive has windows xp 
Can anyone help please?

---

### Post by Paqman on 2008-03-26
All you need to do is put your LiveCD in and boot from it. For this you might need to go into your BIOS and change it to boot from CD before the hard drive.

Ubuntu will boot up and run from the CD. This lets you check for any hardware compatibility issues. Once you're happy, hit install. The installer should take care of creating partitions on your drive(s), or you can tell it where you want it to install to.

---

### Post by bumanie on 2008-03-26
If I were you, I would choose manual at the partitioning stage and set a mandatory / and swap and an extra /home partition. This way if your file system ever got corrupted, you would only have to reinstall to / and all data in /home would be safe. Make / 5-6g; swap 1-2g and /home as large as you like. If you need any more specific help with partitioning, post any queries. It is easier for someone new to let ubuntu decide how to partition but it will only make a / and a swap, a separate /home does bring advantages.

---

### Post by Terrigal on 2008-03-26
Thank you for your replies.
Got to where Ubuntu asked for me to partition hard drive c.  No screen allowed me to select alternate hard drive.
Just wondering if I allowed the partition could I then use use 'send to' 2nd hard drive.???

---

### Post by bumanie on 2008-03-26
If you choose manual at the partitioning stage you should then be able to manually choose the second drive which should be designated hdb1 or sdb1, depending on whether you have ide or sata drives. There is a radio button at the bottom of the list to choose manual.

---

### Post by zen_waters on 2008-03-26
If you are able to install the OS to a second drive, where does the MBR go that will boot grub?  On the first HDD?  Will you be prompted for that option, to put the boot code on the first drive?

---

### Post by kesman on 2008-03-26
Yes, it overruns the current windows start manager in the MBR, which is located in the first section of the first HD.

---

