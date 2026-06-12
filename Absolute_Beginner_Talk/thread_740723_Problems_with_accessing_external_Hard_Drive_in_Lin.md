---
title: "Problems with accessing external Hard Drive in Linux"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by kashmirxincx on 2008-03-31
How do I connect my external hard drive to my computer? Is it plug and play like windows, or do I have to go about doing some configuring? Also, what file systems can be used with an external hard drive with Ubuntu?

forgot to include I am a complete noob to forums, and Linux. I have only come as far as to install VLC and Flash with Synaptic package manager.

---

### Post by ad_267 on 2008-03-31
Should just be plug and play I think but I haven't tried this myself. Someone else might no better.

The native linux file system is ext3 but ubuntu also supports fat32 and ntfs which is the default windows file system. There's probably other file systems that are supported too but those are the ones I know. If you want to format the file system to something else you will need to use gparted which can be installed from synaptic.

---

### Post by kashmirxincx on 2008-03-31
So then how do I access the hard drive? again, I apologize, this is the second distro of Linux I have tried.

---

### Post by Lord Illidan on 2008-03-31
Welcome to the forums! I moved your post here as it was unrelated to the other discussion.

As to accessing your harddrives in Linux, well, just plug in the harddrive, and a new entry should appear under the Places menu. It might (depending on your settings) also appear on the desktop, but I'm not sure if Ubuntu has this by default.

---

### Post by kashmirxincx on 2008-03-31
Thanks for the help, but unfortunately, It seems ubuntu has not recognized the drive is plugged in. I can't find in Places, or Computer. Is there a setting that needs to be changed?

---

### Post by ad_267 on 2008-03-31
Can you open up a terminal and post the output of "sudo fdisk -l", "mount" and "cat /etc/mtab"

---

### Post by kashmirxincx on 2008-03-31
Never mind. But thank you for the help. The problem was i needed to connect the power after i connect my EHD. Thank you for your help Lord and Ad, sorry for the noobishness.

---

### Post by bumanie on 2008-03-31
I have an external hard drive that just plugs and plays. You can format the drive with FAT16, FAT32 or ntfs or ext2/3 if you are not going to share it in a windows machine. 
I am assuming you use gutsy gibbon, if so, if you want to use the drive in both windows and ubuntu, format in ntfs. Since gutsy, ubuntu has been able to read/write natively to ntfs.
When it doesn't mount when plugged in to usb, is there an error message? If so could you please output the error.
PS: You sorted it out while I was writing, please disregard.

---

### Post by ad_267 on 2008-03-31
Good to know you got it working fine :)

---

