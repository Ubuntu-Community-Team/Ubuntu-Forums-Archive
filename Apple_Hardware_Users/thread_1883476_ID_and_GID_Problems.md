---
title: "ID and GID Problems"
date: 2011-11-19
forum: Apple Hardware Users
---

### Post by rolodoom on 2011-11-19
I have installed OSX Lion and Ubuntu 11.10 on my Macbook. 
I succesfully mount the HFS partition on Ubuntu as read/write.

The problem is the user and group id, default on OS X Lion are:
id=501 and gid=20
On Ubuntu side are:
id=1000 gid=1000

I have already change Ubuntu user to id=501 so it matches OS X User, and the question is:

Is it possible that Ubuntu user could be gid=20 as default, knowing that gid=20 is dialout group??

If not, is there any chance to force ubuntu user to write all files on HFS partition as gid=20 ??

---

### Post by ceratophyllum on 2011-11-20
You are trying to write to your home directory in OS X from Linux?
Just curious what the specific objective is here. I'm not sure it is a good idea to let linux write HFS+ filesystem at all. Has the hfs+ module gotten good enough for regular R/W use? Journal still has to be disabled. On the other hand, I don't know how robust OS X is if you mess up the ownership/permissions on the files in your home directory.  Could it prevent you from booting or logging in? 

Could you make an additional FAT partition and store the shared files there, free from Unix filesystem hassles? 

> Is it possible that Ubuntu user could be gid=20 as default, knowing that gid=20 is dialout group??

Why not just try to create a new ubuntu user with UID=501 GID=20, log in as that user,  and see what happens? (You might have to use the command line tool useradd instead of the "Users and Groups" preference dialog.)

---

