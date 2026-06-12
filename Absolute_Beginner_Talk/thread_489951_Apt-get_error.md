---
title: "Apt-get error"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Jem00 on 2007-07-01
Hey guys, I am having a problem with my apt-get.

Everytime I try to run the command sudo apt-get update I receive the error

root@UBUNTU:/home/jem# apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (2 No such file or directory)
E: Unable to lock the list directory
root@UBUNTU:/home/jem# 

By the way I am using Ubunut 6.10.

thanks.

---

### Post by phizikal on 2007-07-01
make sure you have sudo apt-get updates.

---

### Post by scxtt on 2007-07-01
(s)he's running that as root ... try doing **touch /var/lib/apt/lists/lock** (as root) and then **apt-get update** again ...
```
scxtt@kubuntu [/var/lib/apt/lists]
:> ll
total 32M
**[color=green]-rw-r----- 1 root root    0 2007-07-01 06:26 lock[/color]**
drwxr-xr-x 2 root root 4.0K 2007-07-01 00:58 partial
-rw-r--r-- 1 root root  49K 2007-06-21 23:03 us.archive.ubuntu.com_ubuntu_dists_feisty-backports_main_binary-amd64_Packages
. . .
other apt-related repo files
```

---

### Post by Jem00 on 2007-07-01
As you can see I am in root at the terminal already... there is no need for sudo.

---

### Post by Jem00 on 2007-07-01
I tried it and this is my result

```

root@UBUNTU:/home/jem# touch /var/lib/apt/lists/lock
touch: cannot touch `/var/lib/apt/lists/lock': No such file or directory

```

---

### Post by scxtt on 2007-07-01
do you even have a **/var/lib/apt/lists** directory?

---

### Post by Jem00 on 2007-07-01
......No i don't...why is that?????/

---

### Post by scxtt on 2007-07-01
no idea, never seen that before ... here's what i have:
```
scxtt@kubuntu [/var/lib/apt]
:> ls -l
total 24
-rw-r--r-- 1 root root  1216 2007-07-01 06:26 extended_states
drwxr-xr-x 3 root root 12288 2007-07-01 23:44 lists
drwxr-xr-x 3 root root  4096 2007-04-17 01:20 mirrors
drwxr-xr-x 2 root root  4096 2007-06-26 00:51 periodic
```

---

### Post by Jem00 on 2007-07-01
i have no apt directory in /var/lib

```

root@UBUNTU:/var/lib# ls -l
total 128
drwxrwsr-x   3 root src     4096 2007-04-21 09:29 cvs
drwxr-xr-x   2 root root    4096 2007-06-07 16:53 debtags
drwxr-xr-x   2 root root    4096 2007-04-21 09:29 dictd
drwxr-xr-x   6 root root    4096 2007-06-23 16:36 dpkg
drwxr-xr-x   2 root root    4096 2006-10-25 23:31 gcj-4.1
drwxr-xr-x   4 root root    4096 2006-10-25 23:28 gconf
drwxrwx--T   2 root gdm     4096 2007-07-02 12:45 gdm
drwxr-xr-x   3 root root    4096 2006-10-25 23:28 gstreamer
drwxr-xr-x   2 root root    4096 2007-04-21 10:24 initramfs-tools
drwxr-xr-x   2 root root    4096 2006-10-06 21:34 initscripts
drwxr-xr-x   3 root root    4096 2006-10-25 23:26 locales
drwxr-xr-x   2 root root    4096 2007-04-20 08:38 logrotate
drwxr-xr-x   2 root root    4096 2006-10-25 23:27 misc
drwxr-xr-x   3 root root    4096 2006-10-25 23:40 mozilla-firefox
drwxr-xr-x   3 root root    4096 2006-10-25 23:40 mozilla-thunderbird
drwxr-xr-x   2 root root    4096 2007-06-06 18:56 msttcorefonts
drwxr-xr-x   2 root root    4096 2006-10-25 23:28 pango
drwxr-xr-x   4 root root    4096 2007-04-21 10:35 python-support
drwxr-xr-x 108 root root    4096 2007-07-02 13:00 scrollkeeper
drwxr-xr-x   2 root root    4096 2006-10-25 23:28 sgml-base
drwxr-x---   2 root slocate 4096 2007-07-02 12:51 slocate
drwxr-xr-x   2 root root    4096 2006-09-19 05:02 snmp
drwxr-xr-x   2 root root    4096 2006-10-12 07:34 synaptic
drwxr-xr-x   5 root root    4096 2007-04-21 01:41 tex-common
drwxr-xr-x   3 root root    4096 2007-04-21 01:47 ucf
drwxr-xr-x   2 root root    4096 2006-10-12 08:33 update-manager
drwxr-xr-x   3 root root    4096 2006-10-25 23:39 update-notifier
drwxr-xr-x   2 root root    4096 2007-07-02 12:45 urandom
drwxr-xr-x   3 root root    4096 2006-10-25 23:27 vim
drwxr-xr-x   2 root root    4096 2006-10-25 23:37 x11
drwxr-xr-x   2 root root    4096 2007-07-02 12:45 xkb
drwxr-xr-x   2 root root    4096 2006-10-25 23:31 xml-core

```

---

### Post by Jem00 on 2007-07-01
What should I do??

Re-install Ubuntu or is there another option??

---

### Post by scxtt on 2007-07-01
seems like you would have to reinstall - since you can't really use apt* to reinstall any packages, esp. apt itself :p ... maybe a chroot environment, but i'm not sure i could walk you through that ... if it's not a huge pain, i'd reinstall if i was in your position ...

---

### Post by Jem00 on 2007-07-01
K Thanks for your help

---

### Post by scxtt on 2007-07-02
you could forcibly create those dirs and that file, can't hurt to try ...

mkdir -p /var/lib/apt/lists
touch /var/lib/apt/lists/lock
apt-get update

you've got nothing to lose @ this point

---

### Post by castoroil97 on 2007-07-02
might want to see if apt is installed in synaptic

---

### Post by jescis on 2007-07-08
I was having the same problem, until I reinstalled apt in synaptic Package Manager. :guitar:

---

