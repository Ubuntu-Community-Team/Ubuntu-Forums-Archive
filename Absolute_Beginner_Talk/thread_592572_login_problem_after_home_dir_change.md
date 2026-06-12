---
title: "login problem after home dir change"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by petegreenhorn on 2007-10-26
hi , help!! after attempting to create a separate home partition i am now unable to login . After a lot of searching , it seems that it could be a / permissions problem .If it is how do i rectify it please

---

### Post by philinux on 2007-10-26
Dont panic it can be sorted

Exactly how was it set up and how is it set up now.

what is the error message

---

### Post by petegreenhorn on 2007-10-26
here goes , your home dir is listed as , /home/pete, but it does not appear to exist . Do you want to login with the root directory as your home directory . It is unlikly 
anything will work unless you use a failsafe session . p.s i-m a newbie and was following instructions downloaded from the web  phycocats  when the problem was created ":
probably by my error
thanks for any help

---

### Post by philinux on 2007-10-26
I see your profile says Feisty but are you by any chance running Gutsy

Please post output of 

```
sudo fdisk -l and cat /etc/fstab
```

---

### Post by petegreenhorn on 2007-10-26
Hi , command did not reveal anything , but that could be as i'm on live cd at the moment due to not being allowed to login  . since i was here a couple of hours ago i've tried quite a few suggestions without a result i.e chmod -R 700 /home/pete , i've also been through the whole process of the home partition routine that i reckon started my problem. and i'm still no further

---

