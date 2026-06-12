---
title: "How can I resize the partition?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by vasili on 2007-05-31
Since I've installed Ubuntu 7.04 and I selected the less space for installing. The partitions that I got are only two, root and swap. How can I resize and add /home partition?

Regards,

---

### Post by mikewhatever on 2007-05-31
Try the link [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by Bigdog60 on 2007-05-31
Try the link [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) this should help you out dude.

---

### Post by KillerBob-it on 2007-05-31
I'm sorry for the *stupid * question, but what's the advantage of having a separate /home partition? :roll:

---

### Post by b1g4L on 2007-05-31
It's no stupid question. The advantage lies in having the ability to save your documents, photos, application settings, etc. while upgrading to a new Ubuntu version. There may be other advantages, but this is the most obvious.

---

### Post by KillerBob-it on 2007-05-31
do you mean that after upgrading, for example from 7.04 to 7.10, all my personal settings would be kept? (themes, sessions, applications settings and other applications I installed like thunderbird 2, for example)

---

### Post by Inxsible on 2007-05-31
> **KillerBob-it said:**
> do you mean that after upgrading, for example from 7.04 to 7.10, all my personal settings would be kept? (themes, sessions, applications settings and other applications I installed like thunderbird 2, for example)
 
If you installed them in your /home partition AND you use the SAME /home while installing 7.10 ...then YES

---

### Post by KillerBob-it on 2007-05-31
thank you very much this is a very good advice, I'm going to follow that guide and move my /home asap! :popcorn:

---

### Post by KillerBob-it on 2007-06-02
> **Bigdog60 said:**
> Try the link [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) this should help you out dude.

This guide has some bug, it should be more precise in some point, anyway I had success in creating a separate /home partition.

The guide suppose to do the operations through a Live CD, but when he says:
> Now, back in the terminal, I'm going to mount /dev/hda1 and /dev/hda7:
```
sudo mkdir /old
sudo mount -t ext3 /dev/hda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/hda7 /new
```

he forgot to say to change the active directory, because using the Live CD the default directory in the terminal is /home of the root user in Live OS, and not the default user of the installed OS, and it's not possible to create a /home/old folder.
For a newbie as I am, it's confusing ;)

---

