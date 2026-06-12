---
title: "Question regarding cd-rom drive permissions"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by lckeeper1 on 2006-09-19
Hey all,

I've gotten Ubuntu up and running and pretty well customized to do just about everything I want to. Soooo impressed with it and its features. So...on to my question.

I was trying to copy files from a cd earlier, and after I popped it in the drive I got the following message:

"The folder contents could not be displayed. You do not have the permissions necessary to view the contents of 'cdrom0.'"

I then went into the terminal and did the following to try to find out permissions for it without the cd in the drive.

ubuntu@ubuntu-desktop:~$ cd /media
ubuntu@ubuntu-desktop:/media$ ls -l cd*
lrwxrwxrwx 1 root root    6 2006-09-10 14:57 cdrom -> cdrom0

cdrom0:
total 0

I then put the cd in the drive again and did the same thing and got this:

ubuntu@ubuntu-desktop:/media$ ls -l cd*
lrwxrwxrwx 1 root root    6 2006-09-10 14:57 cdrom -> cdrom0

ls: cdrom0: Permission denied


Now to show my noobness. I'm not sure how it can say that i have full permission, yet it says my permission is denied. I would like to try to get these files onto my computer at some point, so any help would be appreciated.

---

### Post by ominousluv on 2007-09-01
I am having the exact same problem.

---

### Post by feardotcom on 2008-04-29
yeah me to...im trying to copy files from my quake cds

---

### Post by feardotcom on 2008-04-30
what i'v found as a work around is is going through command line...its a pain in the *** big time but it works.

If you know the directory structure of the cdrom thats great saves a little hassle. but in my case where im copying files from the Quake 4 cds not so sure about the directory structure so i have to type *cd /media* to get the media folder where the cdroms are mounted to and then type*sudo ls cdrom0/* to get the list of files and folders, so lets say i need to goto a folder called *feardotcom* i have to type again *sudo ls cdrom0/feardotcom* now lets say iw ant to copy a file out of that folder called *ubuntu.doc* i now have to type *sudo cp cdrom0/feardotcom/ubuntu.doc /home/username/documents*

and in short term cp stands for copy....to copy files in command line you use this structure:

cp  file  dir

to copy multiple files(if copying from cdrom in sudo i wouldn;t recommend it, it gets confusing because you have to type the where its located on the cd for each one for example to copy that way it would be sudo cp cdrom0/feardotcom/ubuntu1.doc cdrom0/feardotcom/ubuntu2.doc cdrom0/feardotcom/ubuntu3.doc /home/username/documents

i dont know if theres a way to copy all files on the cd with out typing in each file, but this was my solution anyway.

---

### Post by hellonull on 2008-04-30
Open the terminal and type
```
gedit /etc/fstab
```

Find the line for your CD drive (it will say cdrom0 in it somewhere) and paste it here.

---

