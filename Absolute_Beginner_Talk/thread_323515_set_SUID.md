---
title: "set SUID"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by nikito on 2006-12-22
Hi I tried to change the owner and to set the SUID with the chown and chmod command. But it didn't work. Of course I used sudo, but still I got the error message "operation not permitted" in both cases. So where is the problem?

---

### Post by Arndt on 2006-12-22
> **nikito said:**
> Hi I tried to change the owner and to set the SUID with the chown and chmod command. But it didn't work. Of course I used sudo, but still I got the error message "operation not permitted" in both cases. So where is the problem?

That's impossible to say from your description. Show us which commands you tried and what happened.

---

### Post by nikito on 2006-12-22
I tiped in "sudo chown root XXXXX" and "sudo chmod +s XXXXXXX" and got the message "chown: changing ownership of `XXXXXX': Operation not permitted" in both cases. I can't figure out what the problem is. So thanks for the help.

---

### Post by TyphoonJoe on 2006-12-22
Please post the exact commands and output from your terminal.  Also, please perform a

ls -al XXXXX  


and provide that output as well.  

Worst case, you can "sudo su -" and perform the work...

---

### Post by nikito on 2006-12-22
-rwxr-xr-x 1 c37t root  718 2006-11-15 00:18 GetUrlContent.class
-rwxr-xr-x 1 c37t root  391 2006-11-15 00:18 GetUrlContent.java
-rwxr-xr-x 1 c37t root 1069 2006-11-14 20:44 URLReader.class
-rwxr-xr-x 1 c37t root  445 2006-11-14 20:44 URLReader.java
[email]c37t@me:/media/home/codeshare/EclipseWorksp/Java.Net[/email]$ sudo chown root URLReader.class
chown: changing ownership of `URLReader.class': Operation not permitted

and I found out that this problem only occurs on certain directories. This directory for example is on a FAT32 partition. Could this be the problem?

---

### Post by steve.horsley on 2006-12-22
Yes that's the problem. FAT doesn't store file owner and group and permissions, so you can't change them. If you copy the files to a proper Linux filesystem you will be allright.

But setting SUID on a java .class file won't make any difference, as the class file is a data file, not an executable. java is the executable that interprets the class file, so you would have to SUID on the java interpreter - a **very bad** idea. Better would be to compile a small lancher executable (in C probably) that launches "java URLReader" and SUID that launcher.

---

