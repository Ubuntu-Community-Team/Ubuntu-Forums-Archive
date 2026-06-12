---
title: "hibernate (supend to disk) from commandline"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by dolphin_oracle on 2007-05-05
I'm using xubuntu 6.10.  the hibernate function from the shutdown menu works just fine.  Is there a way to initiate that action from the command line?

Thanks.

---

### Post by jfinkels on 2007-05-05
Install the "hibernate" program by typing the following:
```
sudo aptitude install hibernate
```
Then read about it in it's man page:
```
man hibernate
```

---

### Post by dolphin_oracle on 2007-05-06
this works without adding any software:
$ sudo pmi action hibernate

Are there any pitfalls that anyone may know to using this?

Thanks.

---

### Post by Juxi on 2007-10-15
thx that was what I was searching for :)

---

