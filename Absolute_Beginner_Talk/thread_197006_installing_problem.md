---
title: "installing problem"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-06-15
Ive installed collectd and at the end despite having all the libraries installed it gave me these warnings. Do they matter?

[COLOR="Red"]cc1: warnings being treated as errors
mysql.c: In function 'mysql_read':
mysql.c:369: warning: implicit declaration of function 'mysql_get_server_version '
make[3]: *** [mysql.lo] Error 1
make[3]: Leaving directory `/tmp/collectd/collectd-3.9.3/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/tmp/collectd/collectd-3.9.3/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/tmp/collectd/collectd-3.9.3/src'
make: *** [all-recursive] Error 1
root@ubuntu:/tmp/collectd/collectd-3.9.3# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
[/COLOR]

Im trying to make collectd a command. Ive read that to do this you must place the collectd excecutable file into 1 of the "PATH directories". Doers any1 know what this means? Where do i find this "excecutable" and "path directory"

---

### Post by hajk on 2006-06-15
Your post worries me a lot! You seem to be compiling some software source outside the Ubuntu/Debian repositories, that's not really an "installing problem", is it? And you seem to be doing this as root user: this is not necessary, and also circumvents the Ubuntu safeguards that promote use of sudo. Of course, it's your system to do as you wish.

Now, specific to your problem: in order to compile you need some additional packages installed, like build-essential and (possibly) the kernel-headers for your 
installed kernel. You may also give some thought to which gcc-version you should use, the documentation with the source should be able to tell you.

---

### Post by meniscus on 2006-06-15
Why? is it bad practice to be logged in installing stuff as root? Should i log in as user and try it again?
Ive installed all essential development tools with these commands.

[COLOR="Red"]sudo apt-get install build-essential
sudo apt-get install manpages-dev autoconf automake libtool
sudo apt-get install flex bison gcc-doc g++[/COLOR]

Is there more that should be installed?

---

