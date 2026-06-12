---
title: "Ubuntu-&gt;Kubuntu Problem"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Northsider on 2008-01-17
I attempted to install Kubuntu over my existing Ubuntu installation.  It locked up halfway through, and now I cannot access the package manager to fix anything.  It says that I now do not have permission to access the Package Manager.  Commands through the terminal give me a similar message.  I will post a screenshot later when I have time.

How can I restore access and get Kubuntu working properly?  I am currently still on Ubuntu.  Thanks

---

### Post by markyb86 on 2008-01-17
what happens when you type

```
sudo apt-get install -f
```   

?

---

### Post by Northsider on 2008-01-21
[IMG]http://i30.tinypic.com/5pr2ip.png[/IMG]

> what happens when you type...
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Then I get this:
john@john-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

I am the only user on this computer

---

### Post by vikram on 2008-01-21
run this command

sudo dpkg --configure -a

---

### Post by markyb86 on 2008-01-21
> **Northsider said:**
> [IMG]http://i30.tinypic.com/5pr2ip.png[/IMG]


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Then I get this:
john@john-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

I am the only user on this computer

You might be but your computer is protecting itself from you (this is good we all need it)

what you need to type then is sudo before a command when it says you need superuser.

so

```
sudo dpkg --configure -a
```

and then put in your password and let us know what happens

---

### Post by Northsider on 2008-01-21
> what you need to type then is sudo before a command when it says you need superuser.

Ok, that's what I am missing...

Thank you for the responses.  I will let you know tomorrow.  :-]  I have to get some sleep.

EDIT:  Successful, I just entered my password and it began chugging away.  However I then got this error:
> Errors were encountered while processing:
 kde-guidance-powermanager


---

### Post by markyb86 on 2008-01-22
If your not using a laptop or anything portable, you probably dont need that package. Did it allow you to continue or did that halt the install?

---

### Post by Northsider on 2008-01-22
The install just halted. I *am *using a laptop.

---

### Post by markyb86 on 2008-01-22
Ok. Heres the next step. Would you be willing to make a backup of your home directory and install kubuntu from scratch??

---

### Post by Northsider on 2008-01-22
> **markyb86 said:**
> Ok. Heres the next step. Would you be willing to make a backup of your home directory and install kubuntu from scratch??
I attempted to reinstall Kubuntu...I guess it was a success.  I logged out and selected KDE, and logged back in.  Seems to be working fine.  Thank you for all the help.

---

