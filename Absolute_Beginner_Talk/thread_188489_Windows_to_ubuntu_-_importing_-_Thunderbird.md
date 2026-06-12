---
title: "Windows to ubuntu - importing - Thunderbird"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-04
Hi,

I need to import my Windows Thunderbird mail to my ubuntu Thunderbird mail.

I have access to an XP box for conversion if needed. I am unsure how to do this.

Thanks.

---

### Post by soc on 2006-06-04
just copy your profile to /home/--your name here--/.thunderbird/

---

### Post by u.b.u.n.t.u on 2006-06-04
Danke.

I'll give that a try. I thought it better to ask instead of messing around.

---

### Post by u.b.u.n.t.u on 2006-06-04
For anyone searching for this topic, here is some more info.

Thunderbird profiles are Windows/Linux compatible.

You need to click view/show hidden files in the File Browser to reveal Thunderbird.

I choose to store my data on a separate HDD. So we open the 

profiles.ini

file found here (as soc said above)

/home/--your name here--/.thunderbird/

here is my profiles.ini file linking to my data stored on my data HDD

```
[General]
StartWithLastProfile=1

[Profile0]
Name=XXXXXXX on ubuntu
IsRelative=0
Path=/media/storage/XXXXXXX thunderbird/profile.default
Default=1
```

I sent myself an email to make sure it all works.

:D

---

