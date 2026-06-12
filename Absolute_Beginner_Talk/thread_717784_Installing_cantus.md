---
title: "Installing cantus"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by fk4rp6 on 2008-03-07
I'm not quite sure how to install this program cantus.  I have ran ./configure as suggested in the INSTALL file but I get the error 

"configure: error: C++ compiler cannot create executables
See `config.log' for more details."

I have checked the config.log file but most of it's Greek to me.

---

### Post by taurus on 2008-03-07
Looks like you need to install the build-essential package first before you can compile anything from source.

```
sudo apt-get update
sudo apt-get install build-essential
```
Now, run ./configure again and see what happens.

---

### Post by fk4rp6 on 2008-03-07
That seemed to have worked....kinda...

When I run the ./configure here's what I get now.

checking for libgtkmm... configure: error: Package requirements (gtkmm-2.4 >= 1.2.10) were not met:

No package 'gtkmm-2.4' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libgtkmm_CFLAGS
and libgtkmm_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by taurus on 2008-03-07
You need the libgtkmm-2.4-dev package.

```
sudo apt-get install libgtkmm-2.4-dev
```

---

### Post by fk4rp6 on 2008-03-07
Yeah, I had to install that and another similar.  It seems to have compiled the code.  This is what a got at the end of the output

/bin/sh: -o: not found
make[1]: *** [de.gmo] Error 127
make[1]: Leaving directory `/home/carl/Desktop/cantus-3.0.2-testing/po'
make: *** [all-recursive] Error 1

Not sure if that means it didn't finish.  If I list the directories contents it looks as if there is more there than before.

What's next? :)

Quick question....while compiling the code is it a good idea to try and not do anything/much else?  

While the code was compiling I had to load up Windows XP in VMware so I could Dameware into a computer on the other side of the network where we were having issues.  So I was doing other various things to troubleshoot network issues while the code was compiling.

Could that have caused an issue?

---

### Post by taurus on 2008-03-07
1.  So ./configure ran successfully.

2.  Can you post a few more lines before those ones that you posted?

3.  You can do something else while the code is running.  Wouldn't matter at all.

---

### Post by fk4rp6 on 2008-03-07
Yes ./configure I believe ran fine.  After so it said to type "make", I did and that's when it appeared to be compiling the code.



make[2]: Leaving directory `/home/carl/Desktop/cantus-3.0.2-testing/include'
make[1]: Leaving directory `/home/carl/Desktop/cantus-3.0.2-testing/include'
Making all in po
make[1]: Entering directory `/home/carl/Desktop/cantus-3.0.2-testing/po'
cd .. \
          && CONFIG_FILES=po/Makefile.in CONFIG_HEADERS= CONFIG_LINKS= \
               /bin/sh ./config.status
config.status: creating po/Makefile.in
config.status: executing depfiles commands
config.status: executing default-1 commands
make[1]: Leaving directory `/home/carl/Desktop/cantus-3.0.2-testing/po'
make[1]: Entering directory `/home/carl/Desktop/cantus-3.0.2-testing/po'
cd .. \
          && CONFIG_FILES=po/Makefile.in CONFIG_HEADERS= CONFIG_LINKS= \
               /bin/sh ./config.status
config.status: creating po/Makefile.in
config.status: executing depfiles commands
config.status: executing default-1 commands
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[1]: *** [de.gmo] Error 127
make[1]: Leaving directory `/home/carl/Desktop/cantus-3.0.2-testing/po'
make: *** [all-recursive] Error 1

---

### Post by fk4rp6 on 2008-03-07
Thank you very much for your help.  Apparently the program is installed.  And it doesn't do what I had hoped it would.  So how do I go about removing it...?

I'm looking for a program to automatically arrange,name, rename, etc. a large music collection similar to the way Windows Media Player does.  Any suggestions?

I'm currently using Amorak as my media player.  If it has this feature I'm sure how to use it.

---

