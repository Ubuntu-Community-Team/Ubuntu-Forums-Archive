---
title: "Authorisation failure !"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by jonnieH on 2008-02-23
Tried to add mp3 support about an hour ago using the following command in a terminal window

sudo apt-get install ubuntu-restricted-extras

All went well until during install, the system froze on a screen concerning the licensing of some of the java components. Eventually, I closed the terminal window and now I get :-

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


BUT went trying to "clean up" I am refused su privileges thus

john@john-desktop:~$ su
Password: 
su: Authentication failure
Sorry.
john@john-desktop:~$ 

Any ideas where I go from here please??

---

### Post by taurus on 2008-02-23
Just run these two commands from a terminal.

```
sudo dpkg --configure -a
sudo apt-get update
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by radiocognition on 2008-02-23
There really should be no reason that having a failed install would change your super user password - all that important stuff is pretty well protected.  I take it that you are SURE that you are typing your password correctly (Linux is case sensitive).

If you have other Super Users registered on your system (i.e. ROOT) you can log in as that user and then change your password.  Once you are looged in as the other user just go to users and groups and change your password.

System --> Administration --> Users and Groups

---

### Post by radiocognition on 2008-02-23
> **taurus said:**
> Just run these two commands from a terminal.

```
sudo dpkg --configure -a
sudo apt-get update
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I think the problem is that he cant run a command with sudo.  Either he is typing in the wrong password or something on his system went bonkers.  40 years of stable UNIX computing though makes me think that his account and account password is safe (pretty sure password security was a big deal to the people who wrote this stuff :))

---

### Post by jonnieH on 2008-02-23
Many thanks Now back functioning as normal (apart from broken sun-java6-bin)

JonnieH

---

