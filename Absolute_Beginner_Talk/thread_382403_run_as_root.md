---
title: "run as root"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2007-03-12
this is a dumb question, but how do i run as root in the terminal.  It says that I cannot do something because it needs to be run as root.  what is command to switch to root?

---

### Post by userundefine on 2007-03-12
Preface any command you need root privileges for with **sudo**.

---

### Post by familyjules74123 on 2007-03-12
oh ok thanks.  so whenever it asks me to run as root... just put sudo in front of it? i knew it was a simple answer... lol

---

### Post by Kateikyoushi on 2007-03-12
Depends on what do you try to run in terminal or in gui. Read this for detailed information. [LINK]("https://help.ubuntu.com/community/RootSudo") and this bout graphical sudo [LINK]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by siciliancasanova on 2007-03-12
Yeah you enter **sudo**, and it's going to ask you for a password but when you start typing in your password it will appear as though nothing is going on, but it is being entered.

---

### Post by aysiu on 2007-03-12
If you have a series of commands you want to run as root, you can "log in as root" by typing ```
sudo -i
``` But most of the time, for one or two commands, you can just use *sudo* and not bother logging in as root at all.

**Ubuntu** ```
familyjules@ubuntu:~$ sudo apt-get update
password:
familyjules@ubuntu:~$ sudo apt-get install vlc
familyjules@ubuntu:~$ exit
``` **Other Linux Distro** ```
familyjules@other:~$ su
password:
root@other:~$ apt-get update
root@other:~$ apt-get install vlc
root@other:~$ exit
familyjules@other:~$ exit
```

---

### Post by Najand on 2007-03-12
I just came to help and saw that the replies are all perfect. 
Aysiu! You are now using "apt-get" as the package manager? I used to think you are an "Aptitude" fan before.

---

### Post by aysiu on 2007-03-12
I interchange. *apt-get* has gotten a lot better since Edgy Eft (now with the *autoremove* feature).

---

### Post by Najand on 2007-03-12
Exactly. The autoremove feature is really nice. And you are not supposed to install/remove unwanted packages as aptitude used to do before. I think it is time to update the article: [ aptitude versus apt-get]("http://www.psychocats.net/ubuntu/aptitude")
It was nice to see you around, have a nice day.

---

### Post by aysiu on 2007-03-12
> **Najand said:**
> I think it is time to update the article: [ aptitude versus apt-get]("http://www.psychocats.net/ubuntu/aptitude") I did. There's a line added in there: > Update: Apparently the new version of apt-get in Edgy Eft (Ubuntu 6.10) has a function that allows you to remove unused dependencies when removing an application:
```
sudo apt-get autoremove *applicationname*
``` The page still exists, though, since a lot of people are still using Dapper Drake.

---

### Post by Najand on 2007-03-12
I see.. Sorry I didn't noticed that. You are right.... There are still some people thinking Dapper Drake is more stable than Edgy Eft and still using it. Some of them are still using it, becuase Ubuntu does not send free CDs of Edgy Eft, while they stiill continuing sending Dapper Drake CDs.

---

### Post by kerry_s on 2007-03-12
Did you guys remember when there use to be that "gksuexec" and people were asking about. Well guess what, it's still there but it's just "gksu". I just accidentally typed "gksu" with out putting a command and it popped up. :)

---

