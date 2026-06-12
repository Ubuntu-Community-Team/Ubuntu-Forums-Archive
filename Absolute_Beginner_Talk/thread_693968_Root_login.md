---
title: "Root login"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by gnorthcroft on 2008-02-11
Hi everyone.  I've done a scary thing for me.  I've installed Ubuntu 7.10 on my Acer Aspire 3000 LMI.  I've just downloaded an anti virus package which now requires me to log in as root in order to update the definition files.  From the normal login screen Ubuntu tells me that administrator is not allowed to login using this screen.  Can someone please tell me how I log in as root?  Fear not, I'm am a fast learner.:-k

---

### Post by p_quarles on 2008-02-11
You don't need to log in as root, just run that application as root. You didn't say which anti-virus program this is, but if it were ClamAv, you would open a terminal and run:
```
gksudo clamav
```
By the way, none of the viruses that are scanned for will actually even run in Ubuntu, so there isn't really a need for an AV.

---

### Post by y-lee on 2008-02-11
What anti virus?

you don't need to and shouldn't ever log in as root.

Try running the program as superuser.

---

### Post by gnorthcroft on 2008-02-11
Hi everyone.

I've just installed Ubuntu 7.10 on my Acer Aspire 3000 LMI laptop.  I've just downloaded an anti virus package.  It's asking me to log in as root to update the definition files.  When I attempt to do so, I come up with a message saying "Administrator is not allowed to log in using this screen".  Can someone help me?

---

### Post by jan quark on 2008-02-11
hmm 

you do not need an anti virus software in linux in the first place

---

### Post by skymera on 2008-02-11
run it with sudo from the terminal

and comment above is so so true.

---

### Post by overdrank on 2008-02-11
> **gnorthcroft said:**
> Hi everyone.

I've just installed Ubuntu 7.10 on my Acer Aspire 3000 LMI laptop.  I've just downloaded an anti virus package.  It's asking me to log in as root to update the definition files.  When I attempt to do so, I come up with a message saying "Administrator is not allowed to log in using this screen".  Can someone help me?

HI and welcome, I agree with jan quark & skymera and this link may help
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Edit but if you like
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
And one for security 
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by gnorthcroft on 2008-02-11
Ok, thanks folks.  So how do I change privillages on a program?  To run as a superuser as someone replied above>

---

### Post by nemilar on 2008-02-11
Logging in as root is almost always a bad idea.  Use sudo (or su, if you must) to run commands as superuser.

If I'm not mistaken, most anti-virus programs for Linux just scan for Windows viruses so you don't unknowingly spread them to other users.  It's common to run these on mail servers, for example.  There are no known linux viruses in the wild, to my knowledge.

---

### Post by jan quark on 2008-02-11
this should answer your question

[https://help.ubuntu.com/community/RootSudo?highlight=%28rootsudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28rootsudo%29)


and do not double post

---

### Post by SunnyRabbiera on 2008-02-11
well clamav needs administration privileges so its best not to mess around with it.
if you need updating just make sure to open up a terminal and type in sudo or gksudo to get into administrative mode

---

### Post by jan quark on 2008-02-11
gnorthcroft

for the future
do not double post[-X

---

### Post by p_quarles on 2008-02-11
Duplicate threads merged.

---

