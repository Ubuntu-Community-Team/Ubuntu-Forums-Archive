---
title: "Grub error 22, not detecting Ubuntu partition"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Pizzasrgo on 2007-05-08
My hard drive set up is as follows:
Primary master (hda) 80gb has one partition: hda1 with Windows XP on it.
Primary slave (hdb) 250gb has three partitions: 
hdb1, which is NTFS and is used for file storage.
hdb2, which is ext3 and I installed Ubuntu on.
hdb3, which is swap.

I installed GRUB into the MBR of the slave drive when I installed Ubuntu. I can access it by using the BIOS boot menu to boot from the slave drive. However, none of the first two default options in GRUB (Ubuntu, Ubuntu (recovery mode)) allow me to boot into Ubuntu. Instead I get error 22, saying it cannot find the partition. If I edit the commands for the options, GRUB shows me "root(1,1)" and then some other commands. root(1,1) should boot from the second partition of the second drive, if I understand correctly? This is the Ubuntu partition, so why do I get an error? The install went fine as far as I know, and I was able to view the contents of the partition from the Live CD..

Also, GRUB recognizes Windows XP but when I attempt to boot it (from root(0,0) which is where I know it is located), I get a message saying NTLDR is missing. This isn't true, because if I boot from the primary hard drive where it is installed, NTLDR is clearly there because Windows starts fine. The fact that this option doesn't work doesn't bother me, but it makes me wonder if GRUB is working properly or not, because it can't seem to find things that I know are there.

Can anyone help me?

---

### Post by LaurelLynn on 2007-05-08
Try adding the following to the end of the file "/boot/grub/menu.lst":

```

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

Then use the bios to set the default boot drive to the one with Ubuntu. You should now get a grub menu on boot that has XP as an option.

---

### Post by Kay The Bantu on 2007-05-08
hi see if these help. goodluck

1.[http://ubuntuforums.org/archive/index.php/t-24113.html]("http://ubuntuforums.org/archive/index.php/t-24113.html")
2.[https://help.ubuntu.com/community/Re...tallingWindows]("https://help.ubuntu.com/community/Re...tallingWindows")
3.[http://www.shahidhussain.com/wordpress/index.php?p=33]("http://www.shahidhussain.com/wordpress/index.php?p=33")

---

