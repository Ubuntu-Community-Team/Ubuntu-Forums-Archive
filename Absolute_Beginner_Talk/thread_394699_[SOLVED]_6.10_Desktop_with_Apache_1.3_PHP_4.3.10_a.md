---
title: "[SOLVED] 6.10 Desktop with Apache 1.3 PHP 4.3.10 and mysql 4.0.24"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by da_g_bomb on 2007-03-27
Hi all, hope some one can help,

I have managed to install Ubuntu 6.10 Desktop without any unsolvable problems, but I have run aground in my attempt to create my perfect desktop.

I use my computer for some website design, amongst other things and I have managed to get all the programs I need to replace my windows setup, but now only one thing remains.

What I really wanted was to be able to install Apache 1.3.33, PHP 4.3.10 and mysql 4.0.24, so that I had the same setup as my ISP, that way I could test my websites locally before uploading them to their final resting place.

From a bit of searching I have deduced that my ISP must be using debian Sarge as these are the package versions listed in distrowatch.

My question is can I install these debian packages onto Ubuntu 6.10? I have looked through the installable programs and its only later versions available from the Ubuntu repositories.

Would I be better just sticking debian 3.1 on my own machine. I have installed debian before and I much prefer Ubuntu, so if its possible I would rather keep ubuntu.

Secondly, if it is possible, does any body know of a howto to help me through the process?

Thanks in advance

G

---

### Post by az on 2007-03-27
No, you cannot install debian packages onto Ubuntu.  They are not binary-compatible.

The current versions of php4, apache1.3 and mysql 4 in universe should work exactly the same as the ones on Sarge. 

If you really want to use Sarge, then use Sarge.  I sugges you find an old computer with a 1 gig hard drive and use it as a headless LAMP server for your development and pleasure.

Or, you can create a virtual machine on your desktop machine using Zen, virtualbox or (ugh!) VmWare.

---

### Post by mpokrywka on 2007-03-27
You can install sarge in chroot:
```

sudo bash
mkdir sarge-dir
debootstrap sarge sarge-dir [http://ftp.pl.debian.org/debian](http://ftp.pl.debian.org/debian)

```
...and wait as it downloads (100MB?) and installs base sarge system

after that:
```

mount -o bind /proc sarge-dir/proc

```
(to make proc filesystem available in chroot)

now how to use it? it is simple:
```

chroot sarge-dir

```
...now you are inside chroot and you modify files inside chroot dir
...so first step should be:
```

echo deb [http://ftp.pl.debian.org/debian/](http://ftp.pl.debian.org/debian/) sarge main > /etc/apt/sources.list
echo deb [http://security.debian.org/](http://security.debian.org/) sarge/updates main  >> /etc/apt/sources.list
apt-get update
...and install desired packages:
apt-get install apache php4 mysql-server

```

Make sure that there are no apache or mysql running under your ubuntu: because sarge's apache will fail to "bind to port 80", similar problem will be with mysql if same listen ports are configured

to simplify file editing you can add sarge user identical to your current ubuntu:
in other terminal window check your user UID:
```

id -u

```

in sarge chroot:
adduser -u uid_as_shown_above  your_user_name

and now you have access to sarge-dir/home/your_user_name directory where you can create "public_html", edit files and test them with browser at [http://localhost/~your_user_name](http://localhost/~your_user_name)

---

### Post by da_g_bomb on 2007-03-27
Thanks, I will see if I can get the current versions working.

Though I may just try and get a headless LAMP Server running, that sounds a lot more fun.

What about hoary packages? Can they be made to run on edgy?

---

### Post by da_g_bomb on 2007-03-27
Woah mpokrywka,

That looks complicated. Would that mean sarge is running at the same time as edgy? I think I will keep my installation discs handy and have a play at trying that, before I do anything else.

Thanks guys

---

### Post by mpokrywka on 2007-03-27
> **da_g_bomb said:**
> 
That looks complicated. Would that mean sarge is running at the same time as edgy?

Heh, I thought 10 lines in terminal isn't that hard to type :) 
Seriously,
this "sarge chroot" is separate, complete system stored in some directory.
It is not "running" like rest of your system, but you can manually run some of its programs.
Key thing is that "chroot sarge-dir" command - it means that from now next commands will see root filesystem as "sarge-dir". If you browse this dir you will see that it is very similar to your / (root) directory. Every command run after that "chroot" command is in fact run from that sarge installation. You will for example see that there is no "firefox" command - exactly because it was not installed in this chroot.

You can also use this technique to run some programs from hoary, but I'm not sure if it is what you want - this technique is useful for running programs that work in text mode or they are network services (like your apache/php/mysql setup). I have no experience in running gui (gnome/kde) apps from chroot - it is doable but may require setting some environment variables like DISPLAY or something...

---

### Post by az on 2007-03-27
> **da_g_bomb said:**
> What about hoary packages? Can they be made to run on edgy?

No.  No debian distro is binary-compatible with another, or another release.  You can't install Edgy packages on Feisty, for example.

You *can* install the packages from source.  You can try to add the deb-src from Hoary (Or even debian sarge) and compile and build them with an Edgy toolchain.  Provided the dependencies are all still there, the packages you would make would be binary-compatible.  That's what a backport is, but this would be a "frontport" (since you are using older software - usually a backposrt is new software made to run on an old system)?

---

### Post by da_g_bomb on 2007-03-27
> **mpokrywka said:**
> You can install sarge in chroot:
```

sudo bash
mkdir sarge-dir
debootstrap sarge sarge-dir [http://ftp.pl.debian.org/debian](http://ftp.pl.debian.org/debian)

```
...and wait as it downloads (100MB?) and installs base sarge system


This is kicking up an error

```

bash: debootstrap: command not found

```

is the mkdir sarge-dir on the same line as the debootstrap?

---

### Post by da_g_bomb on 2007-03-28
Sorted that last problerm,

I used Synaptic Package Manager and installed debootstrap, then the download worked. I will let you know how I get on.

---

### Post by da_g_bomb on 2007-03-28
Hey guys this is a quick update.

From firefox with Ubuntu 6.10 (Edgy) I have just pulled up a localhost/phpinfo() test page that says I'm running

Apache 1.3.33 (Debian GNU/Linux) PHP/4.3.10-19 with mysql 4.0.24. I also have phpmyadmin running without any problems.

Thanks guys for all your help, looks like the chroot install of sarge was the way to go, I'll monitor this for performance, but it looks ideal at the moment.

---

