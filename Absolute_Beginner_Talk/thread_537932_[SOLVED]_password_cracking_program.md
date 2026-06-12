---
title: "[SOLVED] password cracking program"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by jon zendatta on 2007-08-29
is there anything along these lines in the repositories

---

### Post by jordanmthomas on 2007-08-29
John the Ripper is in a repository called admin.
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=john&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=john&searchon=names&subword=1&version=feisty&release=all)

As far as others go, I guess google (or the Ubuntu package search) is your friend.  Also, they're usually pretty easy to compile or install yourself if they're not in the repositories.

---

### Post by Sp4freel on 2007-08-29
well  I have a question,  what kind of password are you trying to crack.

---

### Post by jon zendatta on 2007-08-29
user admin pass on linux.
does it differ depending on type of password i need?not to worry i'm not planning anything illegal.

---

### Post by DM was on fire! on 2007-08-29
> **jon zendatta said:**
> user admin pass on linux.
does it differ depending on type of password i need?not to worry i'm not planning anything illegal.

You don't need a password cracking program to get into root.
Just change it via Users and Groups.

Let me get a screenshot. :)

EDIT - No screenshot needed, it seems.

Go to System -> Administration -> Users and Groups. 
Click the checkbox that says "Show all users and groups". It should then show root. Click properties, check "Set password by hand" and type your password into the box. :)

---

### Post by russell.h on 2007-08-29
If you can install the program then you already have root privileges. Open a command line and type in "sudo su" and enter your password and you should end up as root.

---

### Post by jon zendatta on 2007-08-30
thanks everyone for your advice.just one final question please!
so if i do "sudo su" & become root, what is the command to exit root?

thanks.what an awesome community.:):)

---

### Post by aquavitae on 2007-08-30
I've never used that particular command to become root, but if you type "exit" it exits the current shell, in this case exits root and reverts to your normal user.

---

### Post by splintercellguy on 2007-08-30
sudo -s does the trick also. In general, root HAS no password, you simply cannot login as root unless you set a pass.

---

### Post by jordanmthomas on 2007-08-30
> **jon zendatta said:**
> 
so if i do "sudo su" & become root, what is the command to exit root?


```
exit
```
Simple as that.

---

### Post by HermanAB on 2007-08-30
Hmm, you cannot practically crack Linux passwords (Unless you work at the NSA, in which case, you won't be here).  You can guess Linux passwords, if you have used a bad quality password to begin with (8 characters or less).  You don't need to crack a Linux password if you have physical access to the machine, since you can boot into single user mode and reset the passwords.

You can crack Windows passwords, if you have used a bad quality password (14 characters or less).  This can be done using 'rainbow tables'.  Google for 'rainbow tables'.  If you have physical access to the machine, then you can reset Windows passwords by booting with Linux.  Google for 'Offline Linux NT Password Tool'.  These utilities are also contained in Knoppix.

When dealing with ordinary mortals and their common PC troubles, you can recover most Windoze usernames and passwords very easily using tcpdump or wireshark.  People frequently use the same username and password for everything including POP email, which sends it in clear.  Install wireshark, look at port 110 and press the 'Send/Receive' email button on their mail client to get their username and password.

Cheers,

Herman

---

### Post by Sp4freel on 2007-08-30
> **HermanAB said:**
> 
You can crack Windows passwords, if you have used a bad quality password (14 characters or less).  This can be done using 'rainbow tables'.  Google for 'rainbow tables'.  If you have physical access to the machine, then you can reset Windows passwords by booting with Linux.  Google for 'Offline Linux NT Password Tool'.  These utilities are also contained in Knoppix.

also L0pht crack is a windows based Nt hash auditing tool.  but I know that this has no relavance

---

### Post by jon zendatta on 2007-08-31
thanks team

---

