---
title: "Are you root? Please Help!"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-02-14
Ok I'm trying to install windows on Ubuntu but I can't get by "are you root?" in the terminal, what can I do to solve this problem?


joe203@joe203-desktop:~$ apt-get install build-essential
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
joe203@joe203-desktop:~$ uname -r
2.6.17-11-generic
joe203@joe203-desktop:~$ apt-get install linux-headers-'kernel version'
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
joe203@joe203-desktop:~$ apt-get install gcc-3.4
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
joe203@joe203-desktop:~$ apt-get install g++-3.4

Thank You.

---

### Post by aysiu on 2007-02-14
Install Windows on Ubuntu? That's weird.

What you're looking for is *sudo*: ```
sudo apt-get install build-essential
``` That gives you root privileges. More info here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can also do things the point-and-click way:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Repent on 2007-02-14
No not weird at all, I have some programs I payed allot of money for I can no longer use. This way I can use them and that would make me happy. :) 

Thank you.

---

### Post by tronica on 2007-02-14
I'm confused, what do you mean install windows on ubuntu?

---

### Post by aysiu on 2007-02-14
Why are you compiling from source, then? How exactly are you "installing Windows" on Ubuntu? Are you using VMWare? Or did you intend to use Wine (which is not Windows)?

---

### Post by Ptero-4 on 2007-02-14
What you`re probably wanting is wine. For that you don`t need to compile anything, instead add the wine repository to your sources.list (automatix2 does it for you automatically) and install wine. Or if you really need to use the actual Windoze you`ll need either Qemu with the kqemu accelerator (it`s somewhere between universe and multiverse) or VMWare (commercial).

---

### Post by aysiu on 2007-02-14
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by Repent on 2007-02-14
I'm doing as the tutorial  says I hope it works.
[http://www.ubuntuforums.org/showthread.php?t=84275](http://www.ubuntuforums.org/showthread.php?t=84275)

---

### Post by CompShrink on 2007-02-19
> **Repent said:**
> I'm doing as the tutorial  says I hope it works.
[http://www.ubuntuforums.org/showthread.php?t=84275](http://www.ubuntuforums.org/showthread.php?t=84275)

While that will work, running windows in VMPlayer will be pretty slow. I'd suggest you try running the programs through wine first, that runs much faster. A lot of programs work under wine, but not all.

---

