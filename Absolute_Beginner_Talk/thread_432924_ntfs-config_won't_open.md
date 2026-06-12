---
title: "ntfs-config won't open"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by aldago on 2007-05-04
I'm using kubuntu 7.04 and I used Adept Manager to install ntfs-config so that I can pass information between Windows and Kubuntu. The Adept Manager says that the install was successful and I noticed that ntfs 3G was also installed. Problem is that when I go to KMenu/System/ntfs configuration tool and click on it nothing happens. I've also typed gksu ntfs-config into the run command and I get the message "could not run the specified command". I've tried the run command changing to root user and I don't even get the mentioned message. Anybody know what I'm doing wrong??

---

### Post by russianbandit on 2007-05-04
Try:

kdesu ntfs-config

It works for me.

---

### Post by aldago on 2007-05-04
Thank you. That did it.

---

