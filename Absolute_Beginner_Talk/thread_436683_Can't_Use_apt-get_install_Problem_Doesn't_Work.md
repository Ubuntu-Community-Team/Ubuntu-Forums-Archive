---
title: "Can't Use apt-get install Problem Doesn't Work"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by ZodiacfreaK on 2007-05-08
Hey guys, I am new to all this and have been oing crazy tonight installing everything on the latest version of Ubuntu Feisty Fawn 7.04. I am trying to install some software now, but now anytime I run something like this

apt-get install deskbar-applet
apt-get install amarok
apt-get install checkgmail

If I run any of those three, I get the following message.

```
zodiacfreak@ZodiacfreaK-Ubuntu:~$ apt-get install deskbar-applet
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

---

### Post by Perfect Storm on 2007-05-08
You need to put sudo infront of apt-get to get root permission.

---

### Post by quinnten83 on 2007-05-08
Hi, 
being a newbie myself, I am not quite sure if the answer I will give you is correct. 
It seems to me that you haven't entered a verification key. Are these software part of the normal repository or did you have to add them to the sources.list?
Have you tried installing with synaptics or with the add remove programs also?

I'm sure someone will come along to give you some definitve answers.

---

### Post by ZodiacfreaK on 2007-05-08
wow...... I just figured it out, I have to use sudo before that command so instead it would be

sudo apt-get install name

---

### Post by ZodiacfreaK on 2007-05-08
thanks everyone for helping out!!!!! I am loving Ubuntu so far.

---

### Post by quinnten83 on 2007-05-08
Oh yeah, try tyoing sudo apt-get install
I see that ubuntu also asked if you were root..

---

