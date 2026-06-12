---
title: "can' t try kubuntu 6.10, text screen login showing up"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by timothy_duncan on 2006-11-11
hi all k/ubuntu users,

i'm a newbie, desperately needing help regarding kubuntu.  i got a live cd of kubuntu6.10 but when i tried booting it up, all i get is a blank black screen.  i waited for 5 mintues and when nothing happened, i hit enter, and then a text login screen shows up (it seems..)  with this command line

**ubuntu@ubuntu:~$**

well... im lost and dont know what to do or what to type in.. i tried searching the forum but can't get an answer on my problem..  thanks in advance..

---

### Post by Sef on 2006-11-11
Follow the steps in this command after inputting it:

```
sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by timothy_duncan on 2006-11-11
thnanks sef for the quick reply.  i will try it again..

---

### Post by timothy_duncan on 2006-11-12
> **Sef said:**
> Follow the steps in this command after inputting it:

```
sudo dpkg-reconfigure xserver-xorg 
```

Hi Sef,

I tried the above command and followed the steps..  after the last step, i was back to the same command line: ubuntu@ubuntu:~$

i restarted my computer and even chose safe graphics but i still can't start the GUI

---

