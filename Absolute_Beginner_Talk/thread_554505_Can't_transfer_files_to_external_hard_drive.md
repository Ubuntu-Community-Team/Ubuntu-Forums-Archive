---
title: "Can't transfer files to external hard drive"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by danih131 on 2007-09-19
:confused:

Please help - I've been at this all day. I put the Ubuntu live CD into the infected laptop (won't boot because hal.dll file is missing or corrupt). I just want to transfer important files to my external hard drive. Ubuntu promised they could do that. I'm having all these problems with permissions and administrative issues. It's not as easy as chaning the folder from read only to read & write. It won't even let me do that. I'm so frustrated....Anyone, can you help??

---

### Post by splintercellguy on 2007-09-19
Are you sure you burned the Ubuntu LiveCD properly? You should get a LiveCD boot menu. That said, personally, and this is just me, I like the Linux System Rescue CD for data recovery.

---

### Post by danih131 on 2007-09-19
Well, I know I burned it as an ISO image.  That's the most important thing, right? When I load it, it doesn't say anything about it being a Live CD menu, but there's definitely a menu. At first I was trying to download knoppix, but it was going to take 8 hours!!!! Where can I find a link for Linux System Rescue CD? 
Thanks!



Are you sure you burned the Ubuntu LiveCD properly? You should get a LiveCD boot menu. That said, personally, and this is just me, I like the Linux System Rescue CD for data recovery.
__________________

---

### Post by splintercellguy on 2007-09-19
Are you trying to transfer your data to an NTFS partition? If that's the case, you'll probably have to download the ntfs-config package in the LiveCD session to allow ntfs-3g to mount the device read/write. Here is the link to Linux System Rescue CD ([http://downloads.sourceforge.net/systemrescuecd/systemrescuecd-x86-0.3.8.iso?modtime=1188857499&big_mirror=1](http://downloads.sourceforge.net/systemrescuecd/systemrescuecd-x86-0.3.8.iso?modtime=1188857499&big_mirror=1)). While it does have an X Server, it is a lot more minimal and less user friendly, but more powerful.

---

### Post by danih131 on 2007-09-19
Splinter cell guy, are you on? I had a little emergency last night, & had to get off. Anyway, I'm trying to transfer data to an external hard drive. So it's not a partition of the computer's hard drive. It's just a removable device. But Ubuntu won't let me transfer.
Also, when I tried to open the the external hard drive folder, it just keeps giving me this stupid Mount

Does the Linux System Rescue CD have an option for just tranfering files to the external? I don't know why this is so hard. I couldn't do it with Spotmau either! That didn't even recognize the external. 

COULD SOMEONE HELP ME?????

---

### Post by danih131 on 2007-09-19
Oops, I forgot to finish the sentence...It says "MountPointRemoteManagerDatabase" in the System Volume Information folder of the external hard drive window (or disk 2 on the desktop)

---

### Post by danih131 on 2007-09-19
HELLO???????????????????????????????????????????????????????:mad:

---

### Post by danih131 on 2007-09-19
Anyone?????

---

### Post by Lacrimstein on 2007-09-19
ok, lets do this step-by-step. boot your computer from the Live CD. Plugin your hard drive. do you see it appear on the desktop? if not, does it appear in Places>Computer?

---

