---
title: "Mounting an ftp drive with write access"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by arashb on 2005-11-25
Hello, I am brand new to linux. I was trying to switch over for a while because I was getting tired of windows always crashing, viruses, and the whole bit. I tried ubuntu last week, and I love it. When I was using Windows before, I was using a program called NetDrive to mount an ftp folder to a certain drive letter (X:) with full read/write access. I am looking for a similar feature in linux. I know the nautilus has a "Connect to Server" feature but I am unable to write to my ftp folders, nor am I able to access it within other programs. I want to mount it to the /media folder (is that correct) as webdrive or something like that so I can access it anywhere. What do I have to do (and how would I have to have it saved so it would do it automatically everytime my computer starts up).

Thanks

---

### Post by xristos on 2005-11-25
You should put a new line in your /etc/fstab file .
I don't remember what exactly that line should read but taking a look at the fstab manula help will help you further on .

---

