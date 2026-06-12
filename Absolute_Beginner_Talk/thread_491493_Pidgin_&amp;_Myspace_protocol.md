---
title: "Pidgin &amp; Myspace protocol"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by FlyinRedneck on 2007-07-03
I have sort of a newbie question here. I recently successfully installed pidgin. So, i decided to download the myspace protocol source. I untared it into /home/me/pidgin-2.0.2/libpurple/protocols/.
I then changed my directory to the myspace file. But when i Make the file I get an error,

cd ../../.. && /bin/bash ./config.status libpurple/protocols/myspace/Makefile depfiles
config.status: error: invalid argument: libpurple/protocols/myspace/Makefile
make: *** [Makefile] Error 1

Since i am a newbie i have no idea what this means.

A little help will be much appreciated.

---

### Post by Happy_Man on 2007-07-03
Where did you get those lines from?

---

### Post by FlyinRedneck on 2007-07-03
I copied them straight from the terminal.

---

### Post by FlyinRedneck on 2007-07-03
Bump will somebody help me!

---

### Post by FlyinRedneck on 2007-07-03
Bump Bump Bump

How many times will i have to bump this post to get help?

---

### Post by Happy_Man on 2007-07-04
No, sorry, I mean, what did you type that produced those results? Sorry that I couldn't help, I was sleeping.

---

### Post by ghostdog on 2007-07-08
I was getting the same error, what I did was edit the Makefile inside the "myspace" folder.

and chaged this line

```

cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@ $(am__depfiles_maybe)

```

to this (i copied it from the msn makefile)

```

echo ' cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@ $(am__depfiles_maybe)'; \
    cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@ $(am__depfiles_maybe);; \
esac;
```

also make sure that the pigdin path &  prefix line in Makefile is changed from

```
pidginpath = /usr/local/bin/pidgin
prefix = /usr/local
```

to

```
pidginpath = /usr/bin/pidgin
prefix = /usr
```l

There is no need to compile pidgin, just do the following:

- Download the sources

- Place myspace folder inside the protocol folder of the pidgin sources

- run ./configure --prefix=/usr at the "root" level of the pidgin sources

- cd to the myspace folder and compile

You can download the pidgin binary and install it

[http://www.getdeb.net/release.php?id=955](http://www.getdeb.net/release.php?id=955)

---

