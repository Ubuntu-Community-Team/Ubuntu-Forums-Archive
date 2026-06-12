---
title: "Need help checking Feisty .iso file please."
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-04-22
I am running Dapper, have just downloaded the Feisty .iso file and would appreciate a little help with these instructions.

Learn how to create a CD from your newly downloaded file: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Learn how to verify that your CD download ok: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
Read the Ubuntu documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)

Most Linux distributions come with the md5sum utility, so there is usually no need to install it. To check an iso file, first go the correct directory: 
cd download_directory

The .iso file is on my desktop so I do:-

qwer@qwer-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory

This isn't the answer I wanted so I do:-

qwer@qwer-desktop:~$ cd download_directory
bash: cd: download_directory: No such file or directory

This isn't the answer, either, so I would appreciate some words of wisdom.

---

### Post by heimo on 2007-04-22
Try
```
cd
cd Desktop
```
or alternatively
```
cd ~/Desktop
```

And use uppercase D, not lowercase d.

---

### Post by bobplano on 2007-04-22
> **L Campbell said:**
> 

qwer@qwer-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory



linux is case sensitive so you need to put cd Desktop. that small difference is the reason why it didn't work

---

### Post by kinematic on 2007-04-22
> **L Campbell said:**
> 
This isn't the answer I wanted so I do:-

qwer@qwer-desktop:~$ cd download_directory
bash: cd: download_directory: No such file or directory

you can't expect the system to know what your download directory is by just saying download directory.
and dont download large files like the ubuntu cd to your desktop but use a proper directory such as /home/username/downloads.

---

### Post by Drakkor on 2007-04-22
Easy way, just put```
md5sum
``` in the terminal, then drag the .iso file into it !  :)

---

### Post by L Campbell on 2007-04-22
> **heimo said:**
> Try
```
cd
cd Desktop
```
or alternatively
```
cd ~/Desktop
```

And use uppercase D, not lowercase d.

Many thanks, that fixed it and I'm on a roll now.   :-)

---

