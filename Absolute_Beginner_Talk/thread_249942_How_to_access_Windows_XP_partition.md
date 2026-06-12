---
title: "How to access Windows XP partition"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by elpuerco on 2006-09-03
Hi,

I have Kubuntu up and running and want to always use it at home rather than XP.  

Problem is there are many files I would like to access from Ku that are on the Windows partition.

I found a link that will allow me to access the Ku partition from within Windows which will be great (once I install it) but can someone point me to a link where I can learn how to go from Ku - XP please?

Thnx

---

### Post by chippy99 on 2006-09-03
Hi, to access a XP partition you need to mount it. I presume it is an NTFS partition so you would need to do the following. replace hdc1 with whatever the device name is for your partition.

sudo mkdir /mnt/winxp
sudo mount -t ntfs /dev/hdc1 /mnt/winxp

then do 'sudo ls /mnt/winxp' and you should see your files. Linux can only mount an ntfs partition as read only.

---

### Post by elpuerco on 2006-09-03
Thnx, I will give this a go.

I just came back here to say I found this link on this site and am just starting to read it.....

[http://ubuntuforums.org/showthread.php?t=249920](http://ubuntuforums.org/showthread.php?t=249920)

---

### Post by elpuerco on 2006-09-03
Execellent =D> 

I can now access Kubuntu partition when in XP and XP when in Kubuntu.

I went for the pmount.allow approach for now whilst I am learning etc and will try the ntfs approach later

---

