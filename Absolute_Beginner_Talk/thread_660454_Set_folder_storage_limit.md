---
title: "Set folder storage limit?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by spydon on 2008-01-06
Hi.
I want to limit a folder so it can't storage more then 10 gb because it's an folder used by anon ftp users and it wouldn't be nice if they filled my harddrive... I'm using vsftpd, maybe there's a way can set it in vsftpd.conf?
Is it possible to do this?

---

### Post by Blutack on 2008-01-06
You want a little piece of software called quota.  Looks like a bit of a pest to set up though!

---

### Post by spydon on 2008-01-06
right....
Anyone who knows which parameters to use or have a gui for it? :P

---

### Post by Blutack on 2008-01-06
quotatool?
It's below quota in Synaptic...

---

### Post by spydon on 2008-01-06
> **Blutack said:**
> quotatool?
It's below quota in Synaptic...

Seems to be about the same as quota... :/

---

### Post by spydon on 2008-01-06
I tried ```
sudo edquota -u ftp
```
And it told me:
```
No filesystems with quota detected.
```
Please help! My ftp folder will be so spammed tomorrow when I come to school and I've heard that ubuntu will act weird if the harddrive gets full :(.

---

### Post by Blutack on 2008-01-06
Hmm, looks like you need to put something in your /etc/fstab
Look at the section called 3.5 Modify Fstab
[http://tldp.org/HOWTO/Quota-3.html#ss3.4](http://tldp.org/HOWTO/Quota-3.html#ss3.4)

---

### Post by spydon on 2008-01-06
Well I did that and now i can open edquota but nothing happend when I passed the limit... :(

---

