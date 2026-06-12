---
title: "File Permissions-- Locked Files"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by ben0r on 2007-09-19
here is my problem.

I have an ftp server running on my bu. proftpd.  I believe its running as non-root, it's been awhile since I've installed it.

whenever a ftp user sends files to my server, it locks their files down to their username.  My default OS user cannot delete/move/rename the files.  The only way i can modify the files is via root.  I want my default ubuntu user to be able to have full ownership over the files my ftp users creates.

I tried putting the ftp users in the same "group" as my ubuntu login, but it did not work.

Any ideas?

---

### Post by ben0r on 2007-09-19
ttt

---

### Post by 900donuts on 2007-09-19
try saying the owner is your ubuntu login name thats what i do to extra hard drives

---

### Post by ben0r on 2007-09-19
i have the hdd "owner" set to my ubuntu login (user, non-root account).  Even when the owner is "ben" (my username) it still locks the files to my ftpuser. 

Thats why this is confusing me so much!

---

### Post by tech9 on 2007-09-19
> **ben0r said:**
> i have the hdd "owner" set to my ubuntu login (user, non-root account).  Even when the owner is "ben" (my username) it still locks the files to my ftpuser. 

Thats why this is confusing me so much!

try setting up a samba share...

sudo mkdir /mnt/ftp
sudo mount -t cifs -o username="username",password=xxx //IP/SHARE_NAME /mnt/ftp

---

### Post by ben0r on 2007-09-19
> **tech9 said:**
> try setting up a samba share...

sudo mkdir /mnt/ftp
sudo mount -t cifs -o username="username",password=xxx //IP/SHARE_NAME /mnt/ftp

Actually, I need a samba share for a different application!!
this might be a stupid question...but by doing that will i have access to that folder via
smb://user:pass/share_name
??

let me see if it will do the trick for my ftp problem though...

---

### Post by tech9 on 2007-09-19
> **ben0r said:**
> Actually, I need a samba share for a different application!!
this might be a stupid question...but by doing that will i have access to that folder via
smb://user:pass/share_name
??

let me see if it will do the trick for my ftp problem though...

There are no stupid questions... we all are learning:)

You will have access to your share that you created on the windows side "ftp" (shared folder) via path /mnt/ftp

The problem with this is, it only lasts until next reboot - so you may want to look into setting up a script so that it mounts it every time you restart ubuntu

---

### Post by ben0r on 2007-09-19
weird....same thing...files are still locked :/

did i do something wrong?
sudo mount -t cifs -o username="ftpuser",password=mypassword //myexternalip/FTP /media/mr500gig/upload

---

### Post by tech9 on 2007-09-19
> **ben0r said:**
> weird....same thing...files are still locked :/

did i do something wrong?
sudo mount -t cifs -o username="ftpuser",password=mypassword //myexternalip/FTP /media/mr500gig/upload

When you say your files are locked, do you mean that a lock symbol is showing on your file from your ftp server? Can you still access them? I show locked files on my thumb drive, but I can still access them

---

### Post by ben0r on 2007-09-20
yes, i can still access them.  I can even copy them into something else.  They are READ ONLY when I need 777!

---

### Post by tech9 on 2007-09-20
> **ben0r said:**
> yes, i can still access them.  I can even copy them into something else.  They are READ ONLY when I need 777!

> **900donuts said:**
> try saying the owner is your ubuntu login name thats what i do to extra hard drives

In this case what 900donuts stated should work. Make your user the owner under permissions and specify read and write rights.

---

### Post by ben0r on 2007-09-20
the hdd owner is my ubuntu user (i set that through root when i installed the hdd), i even gave "others" read & write access.

and what you say WILL work for the files that I currently have.

But any NEW files being sent are still owned by the ftpuser :(

ughH!

---

