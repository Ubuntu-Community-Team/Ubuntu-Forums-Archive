---
title: "How to enabled services to start at run time"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by soleblazer on 2006-08-25
Hi all,

I am a Redhat admin and am new to Ubuntu, so far I love it.

I have everything setup the way I like, with all my software compiled and running.

Quick question, on redhat there is a command called chkconfig that automatically enables a service to start at a particular runlevel, all it does is create the symlinks for you in /etc/rcX.d , but its nice.

Is there a similair tool in ubuntu?  Also, in redhat there is a utility named services that allows you to simply type something like ''service nessusd status'', just looks for the init.d script, again very nice.

Does that exist in some other fashion on Ubuntu?  I am very impressed so far, on fedora getting my ATI Radeon cards working was a chore, not on Ubuntu!!

---

### Post by meng on 2006-08-25
Try sysv-rc-conf.

---

### Post by djsroknrol on 2006-08-25
You might also try initNG...

---

### Post by soleblazer on 2006-08-26
Thanks, I will try those out.

---

