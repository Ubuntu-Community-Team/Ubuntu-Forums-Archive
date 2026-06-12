---
title: "Still got the problem"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by group256 on 2007-09-26
Hello everyone

a few days ago I sent a message to you that after I tried to install my graphic driver card, when I restarted my computer, it didnt boot up to UI and told me that there is something wrong with your x-server for graphic card. One of you guys answered me to use "sudo dpkg-reconfigure xserver-xorg"
and I tried that one and I went through lots of different questions but when I restarted my computer It gave me the same exact error. Could someone please help me. I really need to use my computer. 

Thanks

---

### Post by overdrank on 2007-09-26
> **group256 said:**
> Hello everyone

a few days ago I sent a message to you that after I tried to install my graphic driver card, when I restarted my computer, it didnt boot up to UI and told me that there is something wrong with your x-server for graphic card. One of you guys answered me to use "sudo dpkg-reconfigure xserver-xorg"
and I tried that one and I went through lots of different questions but when I restarted my computer It gave me the same exact error. Could someone please help me. I really need to use my computer. 

Thanks

Ok can you use the same command and choose vesa as the driver and the other questions if you don't know the answer just hit enter. And what ati card are you using and did you use the live cd for the installation?

---

### Post by group256 on 2007-09-26
No, I am using the installed version, and yes, my card is Ati. In fact when I first installed Linux it was working and appearantly had no problem, But when I was trying to watch DVD movies, It had some problems. I thought maybe its driver problem but vividly it wasn't. So how can I recover the file that I have manipulated?????

---

### Post by alienexplorers on 2007-09-26
DO you have a backup of xorg.conf that worked that you can restore.

---

### Post by overdrank on 2007-09-26
> **group256 said:**
> No, I am using the installed version, and yes, my card is Ati. In fact when I first installed Linux it was working and appearantly had no problem, But when I was trying to watch DVD movies, It had some problems. I thought maybe its driver problem but vividly it wasn't. So how can I recover the file that I have manipulated?????

Ok if you can get to the command prompt use the same command as before
```
sudo dpkg-reonfigure xserver-xorg
```
and choose vesa as the driver and if you don't know the answer to the other question  just hit enter.
**Do you know the model of the ati card?**

---

### Post by group256 on 2007-09-26
yeah, this is the model number
ATI® Radeon™ IGP 345M Graphics Controller Driver

Still cant make it work!!!!

one question

after Ive answered all of the questions, how do I have to restart my computer???

I just hold the button to turn it off then turn it on again, is that ok????

---

### Post by dwhitney67 on 2007-09-26
Do you see that red icon in the upper right hand corner?  Click on that... the rest will be obvious.

---

