---
title: "Several errors during Gutsy Gibbon install"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by mohnkern on 2007-10-18
[resolved]
So I ran through the Gutsy Gibbon upgrade today (I'd previously been running Feisty Fawn), and during the Distribution upgrade, I got the following error several (at least 6) times.

subprocess new post-removal script returned error exit status 127

Should I

1) Worry about this,

2) It suggest submitting a bug report, but I don't know what log file information to include, and where to submit it.

---

### Post by mohnkern on 2007-10-18
Interesting, I got a couple of others that are "status 2"

---

### Post by mohnkern on 2007-10-18
Wow, the distribution upgrade errors clearly caused a lot of problems:

Now I'm getting the following when running update-manager:

Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk.glade
ImportError: /usr/lib/libxml2.so.2: undefined symbol: gzopen64

---

### Post by mohnkern on 2007-10-18
Well, here's what I've done so far:

apt-get -f install

(Generates dependency and package  errors)

apt-get -f clean

apt-get -f install

It's downloading now, we'll see what happens.

---

### Post by mohnkern on 2007-10-18
Well, that doesn't work.  Now it wants me to run dpkg --configure -a

However when I do that, I get a whole bunch of error 127's.


I'm pretty sure that this is a libxml2 problem, but I can't remove or reinstall libxml2 until I clear the current errors with apt and dpkg.

---

### Post by mohnkern on 2007-10-19
Building the dependency table from "the ground up" one application at a time resolved my issues.

---

### Post by telex4 on 2007-10-20
Can you explain how you did that? I'm getting the same errors from java, caused by libxml2:

```

Preparing to replace sun-java6-jre 6-00-2ubuntu2 (using .../sun-java6-jre_6-03-0ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-jre ...
update-mime-database: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
update-mime-database: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6-03-0ubuntu2_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
sun-dlj-v1-1 license has already been accepted
update-mime-database: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Selecting previously deselected package gcc-4.2-base.
Unpacking gcc-4.2-base (from .../gcc-4.2-base_4.2.1-5ubuntu4_i386.deb) ...
Preparing to replace libgcc1 1:4.1.2-0ubuntu4 (using .../libgcc1_1%3a4.2.1-5ubuntu4_i386.deb) ...
Unpacking replacement libgcc1 ...
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-jre_6-03-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by oberoc on 2007-10-31
Try this from the command line:

sudo ldconfig
sudo update-manager

see what happens. I was experiencing the same problem as you, and the ldconfig seem to have cleared it up.

-Tino

---

