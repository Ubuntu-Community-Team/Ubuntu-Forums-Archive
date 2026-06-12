---
title: "Just installed Ubuntu"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Karlocls on 2006-07-24
hello everyone,

      This is my first post here, I am totally new to linux. I have just installed ubuntu and it looks great, but I seem to missing something. I need to install the NVIDIA graphics card drivers and have some documentation on howto do it, but the problem I am having is the sudo command does not seem to be working as it suppose to. Whenever I try and run a command using sudo, it asks for a password, I just hit enter, it appears to accept the password, then nothing happens. For example if I type "sudo ls" it will ask for the pass, accepted it, then back to the commandline not performing the command. I tried booting from the ubuntu install CD, when I tried to perform the same task there, it worked perfectly. 

If anyone can help, I would be very grateful.

Thanks,
Karl

---

### Post by aysiu on 2006-07-24
Can you try this and see if it makes a difference?
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by glinsvad on 2006-07-24
You need to enter the password of your own account when you use sudo.

However, I agree it is a little confusing that sudo doesn't yield "Password incorrect" or something like that. If you type the wrong password (not just enter) it will actually print "Sorry, try again."

---

### Post by aysiu on 2006-07-24
> **glinsvad said:**
> You need to enter the password of your own account when you use sudo.

However, I agree it is a little confusing that sudo doesn't yield "Password incorrect" or something like that. If you type the wrong password (not just enter) it will actually print "Sorry, try again."
[I made a proposal](http://www.ubuntuforums.org/showthread.php?t=214393) that this lack of feedback change--precisely because it confuses new users. I also filed a bug report on it, but the idea got shot down by the developers.

The lack of feedback is here to stay.

---

### Post by underdog512 on 2006-07-24
By the way,  you might want to try this in order to install your NVIDIA drivers.

[http://easyubuntu.freecontrib.org/index.html](http://easyubuntu.freecontrib.org/index.html)

It will also help you get Mp3, Flash, java, dvd codecs, etc

---

### Post by Karlocls on 2006-07-24
thanks very much, that has sorted it.. I tried typing the wrong pass on purpose and it said it was wrong, so when it didn't say anything when I just hit enter, I wrongly presumed it was the right pass! Thanks everyone else, I will look at your suggestions :) > **glinsvad said:**
> You need to enter the password of your own account when you use sudo.

However, I agree it is a little confusing that sudo doesn't yield "Password incorrect" or something like that. If you type the wrong password (not just enter) it will actually print "Sorry, try again."

---

