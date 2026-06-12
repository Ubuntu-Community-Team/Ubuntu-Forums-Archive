---
title: "I need root access."
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by feelexit on 2006-07-22
I just download lamp server suit online. ready to get my lamp installed.

but their instruction ask for root access.

-------------------------------------------------------------
Go to a Linux shell and login as the system administrator root:

su
-------------------------------------------------------------

I dont have it, whats the password for root, if i cannot login as "SU" what can I do ?

thank you.

---

### Post by taurus on 2006-07-22
Try using sudo instead.  For instance, if it tells you to run a command as root, then run it with

```

sudo <command>
(use the same password that you use to log in...)

```
However, I believe there is version of LAMP in the repo so why not install it with apt-get/aptitude/synaptic!!!

---

### Post by Sef on 2006-07-22
> dont have it, whats the password for root, if i cannot login as "SU" what can I do ?


sudo -i will give you a root shell

For more info, read this: [Rootsudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by feelexit on 2006-07-22
[http://www.apachefriends.org/en/xampp-linux.html#377](http://www.apachefriends.org/en/xampp-linux.html#377)

check out this page. they got lamp server ready for you, i think this one is better than the one ubuntu have.

let me know your opinion.

---

### Post by OU812 on 2006-07-24
If you still don't have it installed, open a terminal, navigate to the directory where you downloaded xampp, and do

sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt

Then follow the rest of their instructions.

john

---

