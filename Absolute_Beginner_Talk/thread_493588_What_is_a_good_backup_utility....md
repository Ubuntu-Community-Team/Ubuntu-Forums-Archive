---
title: "What is a good backup utility...?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by veeateme on 2007-07-05
Hi I running the 6.06 Server Ed - LAMP. as a development server for web development, now with GUI desktop making it alot easier 4 me..:D , thanks to those that helped me get that setup...

My current problem is 2 fold...

1) I need a good backup program.

 I have followed the install path on the Ubuntu web site for Installing and Running Kdar... it installed ..OK no errors.
Except that I can't back up anything as the program doesn't have access rights and it doesn't ask for my admin password...*sigh*

So this is my second problem

2) How do I rectify this Kdar access issue, or is there something better to use... I want to be able to backup to disk, CD/DVD-RW. I want to be able to backup my system files, create an image file for complete system recovery, and database backups too (MySQL)

Mark :(

---

### Post by the.phantom on 2007-07-05
have you tried running it as root?

from the terminal

sudo kdar
OR IF IT HAS A GUI 

gksudo kdar

for a full backup
what about 
g4L
or 
partimage?

i use part image from a system rescue disk and it is pretty fast and you can verify

---

### Post by veeateme on 2007-07-05
thnx will try it

another problem is some how I samba isn't working... I can see my windows computers and their shares but windose can only see the sever box not the shares ( at the momment it is only /home/*uname* ) windows asks for a user ID and PW but when I give it the admin one it just says wrong user name or password


Mark :(

---

