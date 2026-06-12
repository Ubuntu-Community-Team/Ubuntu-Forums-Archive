---
title: "Pidgin install on Ubuntu 6.06"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by OmnificienT on 2007-05-31
I've been looking for tutorials on this, but all I've found is tutorials on how to install Pidgin on Feisty. Am I supposed to download the sourcecode and then compile it? If yes, how do I do such a thing?

---

### Post by Dougie187 on 2007-05-31
After you download the source (in a tarball) You need to first untar it, and then you need to get the dependancies met, configure, make and install it.Here are the commands.

To untar:
*tar xvzf tarball.tar.gz*

To get dependancies:
*sudo apt-get build-dep gaim*

To Configure:
You need to cd into the pidgin directory, and then type the following
*./configure*

To Make:
*make*

To install:
*sudo make install*

Let me know if you need anything else.

---

### Post by OmnificienT on 2007-06-01
Well I believe that it is not a tarrball:

pim@Celeron:~/Desktop$ tar xvzf pidgin-2.0.1.tar.bz2

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
pim@Celeron:~/Desktop$

This is the output I get, so what should I do?

Well, I got it to work, I used:
```

 tar xvjf pidgin-2.0.1.tar.bz2

```

Anyway, could someone explain to me what all of these steps do to my system?

---

### Post by zvacet on 2007-06-01
```
tar jxvf pidgin-2.0.1.tar.bz2
```

---

### Post by OmnificienT on 2007-06-01
The apt get is not really working:
Err [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/main x11proto-core-dev 7.0.4-0ubuntu2
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21:1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]

This is what I get. How can I make it work? Are there different servers?

---

### Post by Dougie187 on 2007-06-01
Well i guess you only really need the build-dep command if you need to use msn or googletalk. Otherwise just skip that step. Though you might have to come back to it if your configure fails because you might not have all the libraries installed. Ive seen alot of people with a similar problem lately. You could try going into your sources.list file and commenting out that repo to see if it works then. but that doesnt really solve your problem.

---

### Post by OmnificienT on 2007-06-02
Ah, but I'd like to use msn messenger. You're telling me there is no fix for this?

---

### Post by zvacet on 2007-06-02
You can get deb file from there

[http://www.getdeb.net/search.php?keywords=pidgin]("http://www.getdeb.net/search.php?keywords=pidgin")

---

### Post by OmnificienT on 2007-06-02
Well thanks, but what am I supposed to do with the .deb file?

---

### Post by OmnificienT on 2007-06-02
So now I tried skipping the second step:
And this is what it got me:
```

pim@Celeron:/usr/pidgin$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for sed... /bin/sed
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

---

### Post by vrven1985 on 2007-10-24
@zvacet

thanx :), for the procedure....finally got pidgin working in dapper...

---

