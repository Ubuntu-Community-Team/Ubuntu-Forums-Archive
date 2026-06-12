---
title: "applications not starting (sudo related?)"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by mxbrunet on 2006-03-17
Hi everyone,

I'm trying to install xinetd and cvs via apt-get and nothing is working. I type "sudo apt-get install xinetd cvs" and it just returns. I type sudo -s to go root and nothing happens.

Even when I try to start synaptic - the software asks me for my password - and  then nothing happens. 

Ever seen this behavior before? What could be the problem?

thanks a lot.

Max

---

### Post by bscbrit on 2006-03-17
This sounds like you have lost 'root' access.  Have you been modifying your /etc/sudoers file?  What have you done since you were last able to use sudo - it might give us a clue where to look to correct the problem?

---

### Post by mxbrunet on 2006-03-18
Thanks for the reply. 

I basically just installed CVS using apt-get. Rebooted and then it was downhill from there. If the /etc/sudoers file is bad, is there any way to change it if I don't have access anymore ?

---

### Post by egorgry on 2006-03-18
boot a live cd and you should be able to fix it from there or activate the root user using passwd root *(not recomended)* but it does give you a failsafe way to log in if this occurs in the future.

---

