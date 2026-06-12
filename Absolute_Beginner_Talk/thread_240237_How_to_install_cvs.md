---
title: "How to install cvs"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Timur on 2006-08-20
Hello,
I am trying to install my WUSB11 v2.8 wireless adapter and following the guide I found that I need to have CVS installed. How can I install CVS? Is it in the Ubuntu CD? 
I tried to options:
sudo aptitude install cvs
but it seems this needs a network connection, which I don't have.
And I downloaded cvs-1.11.17.tar.gz and followed the install instructions but it seems that I need to login as root to create some folders, but I don't have a root password.
Any ideas?
Thank you
Diego

---

### Post by baldy1324 on 2006-08-20
the reason you dont have a root acount is b/c ubuntu uses something called sudo which means it substitutes you for root whenever you type it in. when it says type su - you have to type sudo in front of each command. if that makes you mad (like me) you can run ```
sudo passwd root
``` and then type in root's password to make a root account.

---

### Post by Timur on 2006-08-21
So do I have to type something like this to install it?
```

$ sudo ./configure
$ sudo make
$ sudo make install

```
Thank you

---

### Post by baldy1324 on 2006-08-23
if you dont have an internet connection you cant use cvs b/c cvs downloads the source code for the driver so you have to have an internet connection for that. also look on the drivers website and see if they supply source code and download the tar.gz file.

---

### Post by LadyDoor on 2006-08-24
> 
```

$ sudo ./configure 
$ sudo make 
$ sudo make install

```


Nope! Close, though. You do *not* need to use sudo for **./configure** or for **make**--just for **make install**. And anytime you don't absolutely *have* to be root or use sudo, be your regular user! It's much safer and better.

Good luck!
--Door

---

