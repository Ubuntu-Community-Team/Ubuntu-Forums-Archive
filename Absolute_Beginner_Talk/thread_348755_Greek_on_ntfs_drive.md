---
title: "Greek on ntfs drive"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by sikrip on 2007-01-29
Hi all,

I have mounted a disk with ntfs file system that has some folder/files with filenames in greek language and I am not able to see these folders. The other folders that have non greek filename are normaly shown.

I have added support for greek language(after installing ubuntu) and I am able to create files/folders in the ubuntu disk(i.e. in my home folder).

The ntfs disk was not automatically added, I changed the fstab adding this line:

/dev/hdb1 /media/data ntfs umask=0222 0 0

Please help, thanks.

---

### Post by louieb on 2007-01-29
Thats a strange one. I would not think the language of a file name would matter. I wonder if the Greek files are hidden. In the file browser Try View>Show Hidden...

---

### Post by btdown on 2007-01-29
NTFS does not seem to like "strange" characters. I have had problems with filenames with Czech, Slovak and Russian characters on NTFS drives. I tried numerous "fixes" found by searching the web and these forums, and none of them worked. I finally wound up buying a new drive, formatting it with ext3, and then copying everything on the ntfs partition onto the new drive and then used that. I also mounted it so windows could see/use it as a network drive. Not the answer you wanted to hear, but I was not able to solve the problem.

---

### Post by sikrip on 2007-01-29
Solved:

I replaced the 

/dev/hdb1 /media/data ntfs umask=0222 0 0

with

/dev/hdb1 /media/data ntfs      defaults,nls=utf8,umask=007,gid=46 0      1

(Thnks Sergie)

---

