---
title: "installing question."
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-06-14
I want to install a program called [COLOR="Blue"]collectd[/COLOR]

Will this line of code do it for me
[COLOR="DarkOrange"]
sudo apt-get install collectd[/COLOR]

and does that method count for any program some1 wishes to install?

---

### Post by JanVH on 2006-06-14
[QUOTE=meniscus]I want to install a program called [COLOR="Blue"]collectd[/COLOR]

Will this line of code do it for me
[COLOR="DarkOrange"]
sudo apt-get install collectd[/COLOR]

and does that method count for any program some1 wishes to install?[/QUOTE]

If it's in the package list, you can install every programming this way. Collectd doesn't seem to be, though.

You can search for a package with:

$ apt-cache search package

---

### Post by arochester on 2006-06-14
See 

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

"-How to install ANYTHING in Ubuntu!"

---

### Post by dabang on 2006-06-14
If it's in one of your configured repositories (listed in /etc/apt/sources.list), then YES.

If you downloaded the package, then this command will install it:

dpkg -i /path/to/package.deb

---

### Post by taurus on 2006-06-14
If it's not in the repos, then download either the source and build it or grap one of the .rpm files and convert it to .deb...

[http://collectd.org/download.shtml](http://collectd.org/download.shtml)

Let me know which method you want to go since you need to install "build-essenstial" if you want to build from source or "alien" if you want to convert .rpm to .deb.

---

### Post by meniscus on 2006-06-14
Tanx all for replying, and im sure ye are all right! But ill answer taurus (sorry if im insultin ye others) Whats the difference in installing from source or that other rpm method? which is easier i suppose would be the best option!
Anyway I suppose ill go source since its the way ive been attempting to install stuff so far!
Ive downloaded [COLOR="Blue"]collectd-3.9.3.tar.bz2[/COLOR] to [COLOR="Red"]/tmp/collectd[/COLOR]

Im logged in as root and in that folder.....
Now do i just type what it says on the website?

[COLOR="Magenta"] tar jxf collectd-3.9.3.tar.bz2
cd collectd-3.9.3
./configure
make all install[/COLOR]

---

### Post by taurus on 2006-06-14
[QUOTE=meniscus]Tanx all for replying, and im sure ye are all right! But ill answer taurus (sorry if im insultin ye others) Whats the difference in installing from source or that other rpm method? which is easier i suppose would be the best option!
Anyway I suppose ill go source since its the way ive been attempting to install stuff so far!
Ive downloaded [COLOR="Blue"]collectd-3.9.3.tar.bz2[/COLOR] to [COLOR="Red"]/tmp/collectd[/COLOR]

Im logged in as root and in that folder.....
Now do i just type what it says on the website?

[COLOR="Magenta"] tar jxf collectd-3.9.3.tar.bz2
cd collectd-3.9.3
./configure
make all install[/COLOR][/QUOTE]
Actually, before you want to build it, you need to install make, gcc, and a few other apps.  You can do that with 
```

apt-get install build-essential

```
Then, run those two commands to build and install collectd.
```

./configure
make all install

```

---

### Post by meniscus on 2006-06-15
Hi again, sorry for taking so long to reply. Im trying to configure collectd with rddtool so im using the commands

[COLOR="Red"]./configure --with-rrdtool=/tmp/rrdbuild/rrdtool-1.2.13
 make all install[/COLOR]

Is this correct?

Im getting this as my output.
[COLOR="Green"]

cc1: warnings being treated as errors
mysql.c: In function 'mysql_read':
mysql.c:369: warning: implicit declaration of function 'mysql_get_server_version'
make[3]: *** [mysql.lo] Error 1
make[3]: Leaving directory `/tmp/collectd/collectd-3.9.3/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/tmp/collectd/collectd-3.9.3/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/tmp/collectd/collectd-3.9.3/src'
make: *** [all-recursive] Error 1
root@ubuntu:/tmp/collectd/collectd-3.9.3#







[/COLOR]

---

