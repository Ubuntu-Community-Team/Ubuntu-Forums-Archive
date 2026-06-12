---
title: "Error Message when running Synaptic/apt-get"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by bubbadawg on 2006-02-20
Hello All ----

I am getting the following message when attempting to install via apt-get or via the Synaptic Pkg Mgr - 

```
W: Couldn't stat source package list ftp://ftp.free.fr breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.free.fr breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
```

I have tried apt-get update, but it doesn't correct the problem. Can I just remove the line from the sources.list file?

Thanks for any and all replies.

---

### Post by Jucato on 2006-02-20
could you post your /etc/apt/sources.list?
There might be something wrong in there. Thanks.

---

### Post by bluevoodoo1 on 2006-02-20
If you want to "remove" something you can do this...

First make a backup (if you want)
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

then open it...

```
sudo gedit /etc/apt/sources.list
```

put 
```

##
```
in front of the lines to want to exclude, here's an example.

```

## deb-src http://blah blah blah blah
```

then
```

sudo apt-get update
```

---

### Post by rudiz on 2006-02-20
one # is sufficient before the source line u want to disable.

NOT ## ;-)

---

### Post by bluevoodoo1 on 2006-02-20
[QUOTE=rudiz]one # is sufficient before the source line u want to disable.

NOT ## ;-)[/QUOTE]

Indeed, though ## won't hurt :-D  (mine have ##)

---

### Post by bubbadawg on 2006-02-20
Thanks for all of the replies and assistance. Here is the sources.list:

```

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb http://people.ubuntu.com/~doko/OOo2 ./

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://kubuntu.org/packages/kde351 breezy main

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

```

---

### Post by rharris on 2006-02-20
Hi:

A few days ago, I was having the same problem. I believe that the "plf" repos are offline. They might be having server problems.

Maybe someone that has better info on the "plf" servers will post a reply.

At any rate, if the error bugs you, you can just comment out the offending lines in your sources list as mentioned above or remove them as you see fit. I just removed mine as there is nothing at the "plf" repos that I need right now.

Take care............

Rob

---

### Post by Jucato on 2006-02-20
yes, I do recommend disabling/commenting out the PLF repositories temporarily. Unless there is something there that you need to install. As a matter of principle, I don't enable repositories that I don't need, and sometimes disable them after I've gotten what I need.

oh... and don't forget to backup your sources.list when you modify it. It's a good habit that needs to be developed. :D

---

