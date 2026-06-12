---
title: "Dual boot partitions FAT32 Ubuntu &amp; Windows XP"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Mokha on 2006-08-28
Hello,

Thanks for all the helpful suggestions that all of you have been posting. Well let me tell you a bit about my Linux experience.
I first bought Xandros, the problem was that it did not recognize my ethernet card. So I went to a Linux Expo in my area. Got Fedora Core 5 & Ubuntu version 6.06. No luck with Fedora, it too didn't recognise my ethernet card. But Ubuntu was a success. I managed to partition my hard drive in the following order.
C: NTFS (Windows XP)
Linux Ext3 (Ubuntu Installation)
Linux Swap (For Ram)
E: FAT32 (As this link suggested_http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/
)
Now I am wondering E:FAT32 is empty, do I need this? Cause I could use the Space for something Else. What is the purpose of this FAT32 Partition. 
The Current allotment of my Partitions are as follows. 
C:NTFS (Windows XP): Size:21GB Used: 5GB
Linux EXT3: (Ubuntu): Size:14GB Used:2.3GB
Swap Space: (For Ram): Size:1.2GB
E:FAT32: Size: 5.15GB Used:10.1MB
F:Multimedia: Size:10.14GB Used: 53.8 (Currently Empty)
G:Data: Size:5.18GB Used: 28.2MB

My question is do I need to keep this E:FAT32 Partition or can I use it for other things such as increasing my F: Multimedia Partition by adding additional capacity to it & getting rid of FAT32. 
Any help would be appreciated. I am a beginner to Linux (Ubuntu)

Thanks
Mokha

---

### Post by JimmyJazz on 2006-08-28
you really should not double post like this.

---

### Post by Mokha on 2006-08-28
Well I did it cause no one responded. I apologize.

---

### Post by professor_chaos on 2006-08-28
Many suggest a fat partition because its read/writable by both linux and windows. So, it serves as a shared partition. If you don't need it, then use gparted to delete this fat partition and then resize your "multimedia" partition.

---

### Post by Mokha on 2006-08-28
Thanks. I guess I'll get rid of it then.

---

