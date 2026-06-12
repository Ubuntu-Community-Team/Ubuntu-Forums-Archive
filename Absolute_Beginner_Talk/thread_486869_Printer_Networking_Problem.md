---
title: "Printer Networking Problem"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by josethemute on 2007-06-28
Hello,

So I'm new to all forms of Linux, and prior to installing Feisty I considered myself fairly technically savvy.  Now I can't even figure out how to properly network my Feisty installation with a Vista laptop.

My situation is this: I have a HP OfficeJet 5600 printer attached to my Linux desktop.  I would like to access that printer from a laptop running Windows Vista.  I would also like to access shared information on the Vista laptop from my Linux box, and vice versa (I will have a USB HDD attached to my Linux machine).  

So far I have been working on networking my printer.  I have tried editing the CUPS  file using information I've found on the internet, to no avail.  I've tried accessing my laptop's shared folder using samba, to no avail (I ran the following command: sudo mount -t smbfs -o username=ubuntu,password=pass,workgroup=WORKGROUP,gid=smb,uid=$USER,fmask=770,dmask=770,rw //OFFICEDEPOT-PC/harddrive /media/winshares ; I used the guide in the wiki documentation).  I have not tried anything with the usb hdd yet, but I doubt I would have success with it.  Is there any help that you guys can give me?

Thanks,
Jose

---

### Post by josethemute on 2007-06-28
An hour later, still no progress.  I honestly don't know what I'm doing; I've tried following the two guides that are on the Ubuntu community docs wiki; no results.  I've tried internet searches to find samba guides; no results.  This is somewhat critical for our business; anything would help- a working guide that I can follow, something.  

Thanks,
Jose

---

### Post by Seisen on 2007-06-28
Try following these steps and see if it works. 

[http://ubuntuforums.org/showpost.php?p=1561331&postcount=2]("http://ubuntuforums.org/showpost.php?p=1561331&postcount=2")

---

