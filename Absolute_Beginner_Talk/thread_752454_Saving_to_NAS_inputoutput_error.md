---
title: "Saving to NAS input/output error"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by myotis on 2008-04-11
I have a QNAP NAS connected via a Draytek Router to UBuntu 7.1 box. The QNAP is formatted as NTFS.

I can read files from the QNAP, but trying to save them gives me:

Error saving Document
General Error
General Input/Output Error


I have been trying this with Open Office, and the file actually appears on the NAS. But if you try and open the file by double clicking on it, you get an error saying that it is incorrectly identified as an ODT file when it is actually a txt file and to open it from the application.

Opening it with OOo gives me a blank file. I can then add text, but trying to save gives me the same error.

I can  read and write OK to the Windows partition (NTFS).

Any obvious solution for this ?

Many thanks,

Graham

---

### Post by myotis on 2008-04-11
To reply to my self.

I wondered if this was related to mounting the drive and have followed the instructions at

[http://www.marcus-furius.com/?p=25](http://www.marcus-furius.com/?p=25)

except added the line

//192.168.1.1/graham /media/svn/ smbfs uid=graham,gid=user 0 0

to my fstab file. the share on the NAS is called graham and my user name is graham. But I get the following error when I run sudo mount -a

timeout connecting to 192.168.1.1:445
timeout connecting to 192.168.1.1:139
Error connecting to 192.168.1.1 (Operation already in progress)
8436: Connection to 192.168.1.1 failed
SMB connection failed

Graham

---

