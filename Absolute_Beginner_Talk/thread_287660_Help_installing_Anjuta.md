---
title: "Help installing Anjuta"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Ronfar on 2006-10-29
Frist off I'd like to express my graditude for anyone taking the time to help me out with my problem.

Ok I seem to be having trouble trying to install this program "Anjuta v.1.2.4, anyways frist off I tried to compile everything from source which was very torturing and difficult for someone who only has one week of Linux experience. However someone was kind enough to notify me of a simpilier way using the apt-get install command. Anyways my problem is that when I use this command it says it can't find the package. So obviously I guess I am using the wrong package name, but I can't seem to find it? I've tried apt-cache search anjuta also with no success and searched around for it with no sucess. 

So perhaps someone who has installed this program or someone with more knowledge could be kind and offer some advice to me. Thanks alot I really apperciate any replys.

---

### Post by randomi on 2006-10-29
Edit your sources.list file to open the universe repositories.

```
sudo nano /etc/apt/sources.list
```

Then update and try installing it again. BTW I would use aptitude over apt-get as it handles dependencies better. If you ever decide to remove something it will remove its dependencies as well as opposed to apt-get only removing what you tell it to.

---

### Post by Ronfar on 2006-10-29
Forgive my ignorance, but what exactly do I need to add or edit to this? So what I am guessing this does is allow certain programs to be registered by Ubuntu?

---

