---
title: "ftp directory permissions advice"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by JohnnyAvocado on 2006-12-14
I have a question re: securing user ftp directories. I am running 6.06.1 and proftpd.

I am in the middle of testing the linux server which will be a production ftp server as soon as everything is secured. It is replacing a windows IIS ftp server. I am just starting out with linux and didn't know if I had used the permissions properly. 

My question is what is the best practice for securing the ftp folders as a general rule. 

The requirements:
Each user will have their own folder 
Each user should not be able to view others' folders.
All folders to reside within the /home dir
Read/write capability on their individual folders
The user's folder corresponds to the user's username.

drwxr-xr-x 2 admin admin   4096 2006-12-13 15:13 admin
drwxr-xr-x 2 ftp   nogroup 4096 2006-12-13 14:42 ftp
drwxrwxrwx 2 root  root    4096 2006-12-14 09:54 test1
drwxrwxrwx 2 root  root    4096 2006-12-14 09:10 test2


I put in the "DefaultRoot ~" entry in proftpd.conf to lock in the users to their own folder. I also have the ftp user's shell as /bin/false in the /etc/passwd file. 

I assume that the users should own their own folder? Is it okay to just leave the owner and group as root? What is the downside to that is there is any.

Thanks for any advice.

Johnny.

---

### Post by punx45 on 2006-12-14
> **JohnnyAvocado said:**
> 
...
I assume that the users should own their own folder? Is it okay to just leave the owner and group as root? What is the downside to that is there is any.

Thanks for any advice.

Johnny.

if the owner and group for each user's directory is root, then the only way the user can access their folder is by enabling "other/world" access, which of course would give access to every other user as well.   a more correct configuration would look like:

drwxrwx--- username username *stuff* foldername
or drwx------

---

