---
title: "How to Configure Cisco Aironet 340 Card"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by lawless38 on 2008-02-27
I am relatively new to Linux. I toyed with it several years back with RH 7.2 and am now trying out Ubuntu.

I had the luxury of RH recognizing my Cisco card at installation but Ubuntu is not.

#1 Should Ubuntu be recognizing my Cisco Aironet 340 card or not?

#2 If not, can someone, in not so many words, tell me what I need to do? Do I need to load additional drivers/firmware? Is it merely a configuration issue? If so, can someone provide a small bit of guidance on how to configure?

Pointing me to an information resource online would also be great as I know everyone's time is short and I am a newb. Thanks everyone.

Lawless38

---

### Post by jan quark on 2008-02-27
first this:
[http://ubuntuforums.org/showthread.php?t=89517](http://ubuntuforums.org/showthread.php?t=89517)

but let's see what we can do

please post the output of these terminal commands:
```

sudo lshw -C network
```

```
iwconfig
```

---

