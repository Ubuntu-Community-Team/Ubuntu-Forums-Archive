---
title: "Accessing secondary NTFS hard drive in Linux?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by tudedude on 2006-08-03
I just installed 6.0.6 server. command line interface.
This box has 2 hard drives installed. One has the linux OS and the other is a drive I previously used on a Windows machine and has NTFS file system. 

Am I able to access the second drive from within Linux at all? How do I see what files are on that second hard drive from within Linux? 

I also have Samba installed. My Windows XP Pro machine can see the Linux box in Explorer. How can I get the XP Pro machine to see that second drive?

---

### Post by kurniawands on 2006-08-03
> **tudedude said:**
> I just installed 6.0.6 server. command line interface.
This box has 2 hard drives installed. One has the linux OS and the other is a drive I previously used on a Windows machine and has NTFS file system. 

Am I able to access the second drive from within Linux at all? How do I see what files are on that second hard drive from within Linux? 

I also have Samba installed. My Windows XP Pro machine can see the Linux box in Explorer. How can I get the XP Pro machine to see that second drive?

tudedude.... hehehehehhehe

first u can use ntfs-3g to read/write your ntfs drive. than share it on samba  so windows user can see it on the network...

---

### Post by OU812 on 2006-08-03
Try this

[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

john

---

