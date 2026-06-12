---
title: "Sending large files pc2pc over internet."
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by blueglue on 2007-11-25
Hello, I am seeking a way to send large files over the internet from my PC to my friends PC (we are both using 7.10). I have spent several hours trying different ways and the most interesting seems to be iFolders, although I can,t find an upto date .deb or a recent how to. Doe's anybody know of either of these or an alternate solution to my problem. Thanks in advanced and apologies if I've posted in the wrong section!:mad:

---

### Post by approaching on 2007-11-26
i would try to set up some kind of ftp server on the donor computer. i did like 5 seconds of research and found 20 different solutions so i doubt that you will have an issue there. (try this one vsftpd). and after that, get some kind of ftp client. you have one already in your terminal, it's just ftp. i would do a man ftp to learn more about it though. but if you would like a gui for the download, try filezilla.

---

### Post by blueglue on 2008-01-21
Thanks for your advice, Sorry about the slow reply! I did manage to find a solution doing pretty much as you suggested. I installed Gproftpd(server) and filezilla(client) both from the ubuntu repos both were up and working in 5 mins, really quite simple if anybody is considering them.

---

