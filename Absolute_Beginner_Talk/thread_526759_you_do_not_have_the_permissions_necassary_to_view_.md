---
title: "you do not have the permissions necassary to view the contents of &quot;recup_dir*&quot;"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by zibeezibeehey on 2007-08-15
I just used the Photo rec and its donenow but how do i access the recup_dir* files. I have no clue, i imagine I have to get permissions. What are permissions? How do I get the proper permissions?Pleasehelp

---

### Post by jamvegan on 2007-08-16
This is software to recover pictures from a digital camera?  What you probably want to do is change the ownership of the directory or directories to you (I assume that the software either assigned ownership to "root" or to its own user, if any).

In a terminal (Applications->Accessories->Terminal) you can type:
```
ls -ld recup_dir*
```
to view the permissions and ownership of the directories themselves, and:
```
ls -l recup_dir*
```
to view the permissions and ownership of the contents of the directories. You'll get output that looks something like:
```
drwxr-xr-x 2 loginname loginname 4096 2007-08-15 21:51 recup_dir
-rw-r--r-- 1 root root 0 2007-08-15 21:51 filename
```

(Note that the commands above will work if you are in the directory that contains the recup_dir* directories.  Otherwise, you would need to provide the path to the directories.)

If you see your login name for both the directories and the files, then ownership is not the problem.  However, if you see "root" (or anything other than your login name) then you can use the following command to change the ownership to you:
```
sudo chown -R loginname: recup_dir*
```
where you replace "loginname" with your actual login name.  You will be asked for your password.  After entering it you should be able to view the files.

---

