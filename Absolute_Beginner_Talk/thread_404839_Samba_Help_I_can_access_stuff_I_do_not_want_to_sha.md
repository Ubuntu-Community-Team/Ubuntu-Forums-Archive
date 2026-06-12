---
title: "Samba Help I can access stuff I do not want to share =("
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by hec1979 on 2007-04-08
I have been able to successfuly setup Samba

I create a folder and I set it so that it is shared over the network using samba and I cretae a samba password 

sudo smbpasswd -a "user-name" and so on 

and I am successfully able to access the contents of that folder from a windows machine.

Now if my shared folder is in /home/ubuntu/shared_folder

when I log in from the windows machine \\192.168.2.1 it will drop me in the following directory

/home/unbuntu and I can access other folders and files that I do not want shared is there a way to prevent this or is this how it is supposed to work?

Thanks,

Hec1979

---

### Post by dantastik on 2007-04-09
I am not the most experienced around - for sure, but mine works as intended...

if you open the smb.conf ( /etc/samba/smb.conf ), and look where it says [MyFiles] do you get the right path?

Mine goes:

[MyFiles]
    path = /home/dantastik/Documents/swap


Dan

---

