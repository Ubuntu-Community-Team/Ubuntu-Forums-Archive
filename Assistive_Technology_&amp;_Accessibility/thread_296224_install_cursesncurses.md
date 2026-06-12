---
title: "install curses/ncurses"
date: 2006-11-09
forum: Assistive Technology &amp; Accessibility
---

### Post by yolloms on 2006-11-09
i want to install curses/ncurses.h file to my ubuntu.

iv gotten the file off the web using 'wget'

then untared it
then was instructed by the website to use the following commands
       cd ncurses-5.5
       ./configure
       make
   **  su root
       make install

** -> this is where my problem is. i do the su root command and im promted for a password. since i am the only user & administrator on my laptop i entered my password. however it wont accept it.

any ideas what this password could be or is there any way around it.

iv tried my password, 0, root, rootroot but to no avail.:-k

---

### Post by qamelian on 2006-11-09
> **yolloms said:**
> i want to install curses/ncurses.h file to my ubuntu.

iv gotten the file off the web using 'wget'

then untared it
then was instructed by the website to use the following commands
       cd ncurses-5.5
       ./configure
       make
   **  su root
       make install

** -> this is where my problem is. i do the su root command and im promted for a password. since i am the only user & administrator on my laptop i entered my password. however it wont accept it.

any ideas what this password could be or is there any way around it.

iv tried my password, 0, root, rootroot but to no avail.:-k
Don't use su. Instead use ```
sudo make install
``` and enter your own password. This gives you the equivalent of root privleges temporarily.

---

### Post by yolloms on 2006-11-09
so simple

thanks

---

### Post by qamelian on 2006-11-09
I also should have mentioned that Ubuntu by default doesn't use a root account. Using sudo, you should never need one. I've been using Ubuntu since Warty and haven't needed a root account yet.

---

### Post by ktuulos on 2007-02-24
> **yolloms said:**
> i want to install curses/ncurses.h file to my ubuntu.

iv gotten the file off the web using 'wget'

then untared it
then was instructed by the website to use the following commands
       cd ncurses-5.5
       ./configure
       make
   **  su root
       make install

** -> this is where my problem is. i do the su root command and im promted for a password. since i am the only user & administrator on my laptop i entered my password. however it wont accept it.

any ideas what this password could be or is there any way around it.

iv tried my password, 0, root, rootroot but to no avail.:-k
Hello

Maybe I'm just stupid, but why Ubuntu/Kubuntu does not contain the ncurses.h file by default?

[EDIT] ---> stupid me. The file (or symlink to curses.h) comes with libncurses5-dev package. But still, it again took a while before I found this.... in fact I found this from Cygwin documentation.

Thanks,

   - Kalle

---

### Post by city-17 on 2007-10-01
> **ktuulos said:**
> Hello

Maybe I'm just stupid, but why Ubuntu/Kubuntu does not contain the ncurses.h file by default?

[EDIT] ---> stupid me. The file (or symlink to curses.h) comes with libncurses5-dev package. But still, it again took a while before I found this.... in fact I found this from Cygwin documentation.

Thanks,

   - Kalle

Thank you Kalle, that information was very useful. Without it, I also would have attempted to recompiled myself. Thanks for the tip

---

### Post by cg2112 on 2007-10-30
ubuntu, and all linux distribs, has a root account.  Ubuntu chooses by default not to give this account a password.  Personally, I think it's a bad idea for a number of reasons, but that's they way they have chosen to distribute the OS.

---

### Post by Avalanche21 on 2007-12-12
Im noob to linux and I am trying to install ncurses lib to ubuntu but I am not sure how. All the info I get on the web expects me to know something about what I am doing...but I do not:confused:. 

First I downloaded Ncurses 5.6 to my desktop so I could find it. Now i need to install it and I am not sure how. If I navigate to the ncurses file  and type ./configure I get an error
```

checking for C compiler default output... 
configure: error: C compiler cannot create executables

```

I need to write an application using the curses library so I need this to work badly

any help?

Thank you!

Av

---

### Post by driedfruit on 2008-02-23
sudo apt-get install build-essentials
sudo apt-get install libncurses5-dev

---

### Post by seren6ipity on 2008-12-06
I was compiling my cobol program using openCOBOL and was getting error :
/usr/bin/ld: cannot find -lncurses
collect2: ld returned 1 exit status

Following the discussion above I installed libncurses5-dev and it works!

Thanks all!
):P

---

### Post by pehden on 2012-03-31
-bash: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory
Connection to 127.0.0.1 closed.
root@:~# ls -l /usr/lib |grep libncurses
lrwxrwxrwx  1 root root          12 2012-03-25 11:25 libcurses.a -> libncurses.a
lrwxrwxrwx  1 root root          13 2012-03-25 11:25 libcurses.so -> libncurses.so
-rw-r--r--  1 root root      552854 2010-03-06 22:25 libncurses.a
-rw-r--r--  1 root root      188744 2010-03-06 22:25 libncurses++.a
-rw-r--r--  1 root root     3468952 2010-03-06 22:25 libncurses_g.a
-rw-r--r--  1 root root      711312 2010-03-06 22:25 libncurses++_g.a
lrwxrwxrwx  1 root root          20 2012-03-25 11:25 libncurses.so -> /lib/libncurses.so.5
lrwxrwxrwx  1 root root          13 2012-03-31 16:48 libncurses.so.5 -> libtermcap.so
-rw-r--r--  1 root root      188744 2010-03-06 22:25 libncurses++w.a
-rw-r--r--  1 root root      648370 2010-03-06 22:25 libncursesw.a
-rw-r--r--  1 root root      711368 2010-03-06 22:25 libncurses++w_g.a
-rw-r--r--  1 root root     3975578 2010-03-06 22:25 libncursesw_g.a
lrwxrwxrwx  1 root root          21 2012-03-31 16:48 libncursesw.so -> /lib/libncursesw.so.5
lrwxrwxrwx  1 root root          12 2012-03-25 11:25 libtermcap.a -> libncurses.a
lrwxrwxrwx  1 root root          13 2012-03-25 11:25 libtermcap.so -> libncurses.so

---

### Post by overdrank on 2012-03-31
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

