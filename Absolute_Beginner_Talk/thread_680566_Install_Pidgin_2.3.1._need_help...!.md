---
title: "Install Pidgin 2.3.1. need help...!"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by yogatta on 2008-01-28
im tryin to install pidgin. i've dowloaded the pidgin-2.3.1.tar.bz2 file and done some following code.
> 
tar xvfj pidgin-2.3.1.tar.bz2

cd pidgin-2.3.1

./configure

then...

this is the output

> checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


i cannot run **make**

fyi, i'm running gutsy gibbon.. plz help me.

---

### Post by jan quark on 2008-01-28
you need build-essentials package to compile applications

why not use synaptic to install the package without compiling

just open synaptic package manager and search for pidgin
there select pidgin mark to install and apply

---

### Post by jan quark on 2008-01-28
here is a good guide dealing with installing anything in ubuntu 
some reading for your free time
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
:)

---

### Post by Perfect Storm on 2008-01-28
Compiling pidgin requires alot of headers and devs. Best option for newbies is to install the one in the synaptic.

Otherwise, I wrote a guide - [http://ubuntuforums.org/showthread.php?t=658244](http://ubuntuforums.org/showthread.php?t=658244)

---

### Post by LeAstrale on 2008-01-28
[http://ubuntudanmark.dk/forum/viewtopic.php?t=1838](http://ubuntudanmark.dk/forum/viewtopic.php?t=1838)

that should do the trick for you. just follow it even though its in danish (some of it.)

---

### Post by btlee on 2008-01-28
Instead of building it, you can get a binary one at getdeb.net.

---

### Post by yogatta on 2008-01-28
> **Artificial Intelligence said:**
> Compiling pidgin requires alot of headers and devs. Best option for newbies is to install the one in the synaptic.

Otherwise, I wrote a guide - [http://ubuntuforums.org/showthread.php?t=658244](http://ubuntuforums.org/showthread.php?t=658244)

i've done step by step like in your post guide until the step that asking to do **make**

i cannot proceed to **sudo checkinstall** because there was failure notice.

this is the output from the **make** i've done:

> make  all-recursive
make[1]: Entering directory `/home/yogatta/Desktop/pidgin-2.3.1'
Making all in libpurple
make[2]: Entering directory `/home/yogatta/Desktop/pidgin-2.3.1/libpurple'
make  all-recursive
make[3]: Entering directory `/home/yogatta/Desktop/pidgin-2.3.1/libpurple'
Making all in gconf
make[4]: Entering directory `/home/yogatta/Desktop/pidgin-2.3.1/libpurple/gconf'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/yogatta/Desktop/pidgin-2.3.1/libpurple/gconf'
Making all in plugins
make[4]: Entering directory `/home/yogatta/Desktop/pidgin-2.3.1/libpurple/plugins'
Making all in mono
make[5]: Entering directory `/home/yogatta/Desktop/pidgin-2.3.1/libpurple/plugins/mono'
Making all in api
make[6]: Entering directory `/home/yogatta/Desktop/pidgin-2.3.1/libpurple/plugins/mono/api'
mcs -t:library -out:PurpleAPI.dll ./BlistNode.cs ./BuddyList.cs ./Buddy.cs ./Contact.cs ./Debug.cs ./Event.cs ./PurplePlugin.cs ./Group.cs ./Signal.cs ./Status.cs
/bin/bash: mcs: command not found
make[6]: *** [PurpleAPI.dll] Error 127
make[6]: Leaving directory `/home/yogatta/Desktop/pidgin-2.3.1/libpurple/plugins/mono/api'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/yogatta/Desktop/pidgin-2.3.1/libpurple/plugins/mono'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/yogatta/Desktop/pidgin-2.3.1/libpurple/plugins'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/yogatta/Desktop/pidgin-2.3.1/libpurple'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/yogatta/Desktop/pidgin-2.3.1/libpurple'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/yogatta/Desktop/pidgin-2.3.1'
make: *** [all] Error 2



---

### Post by Perfect Storm on 2008-01-28
Try disable mono (remove it from configure), then 
make clean
<the configure command>
make
etc.

---

### Post by nowshining on 2008-01-28
go to my website in my sig for a howtwo on getting pidgin 2.3.1 or later - also u can get a newer version of rhythmbox :)

---

