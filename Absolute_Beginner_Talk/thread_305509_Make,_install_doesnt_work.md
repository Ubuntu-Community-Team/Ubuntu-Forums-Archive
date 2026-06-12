---
title: "Make, install doesnt work"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by baysl on 2006-11-23
Im trying to install a program in linux.

File type is *.tar.gz.

First I extract it to XXX directory.

Then I go to XXX directory and write:

./configure
make
make install

but its not working. Whats wrong?
What do I have to do?

---

### Post by Bachstelze on 2006-11-23
Please be more precise. "It's not working" doesn't help us much to find out what the problem is...

---

### Post by taurus on 2006-11-23
Maybe you need the build-essential package first!

```
sudo aptitude update
sudo aptitude install build-essential
./configure
make
sudo make checkinstall
```

---

### Post by baysl on 2006-11-23
This is the error

roko@linux:~/Downloads/bnc2.9.4$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
roko@linux:~/Downloads/bnc2.9.4$

---

### Post by taurus on 2006-11-23
Check out my post above!!!

---

### Post by baysl on 2006-11-23
I did try what you wrote in your post but its not working:

roko@linux:~$ sudo aptitude update
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by taurus on 2006-11-23
Not sure what you did to your system but run that command to fix it!  Otherwise, paste the content of /etc/apt/sources.list here then.

```
sudo dpkg --configure -a
cat /etc/apt/sources.list
```

---

### Post by baysl on 2006-11-23
Its still not working...
Here is the list:

deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by taurus on 2006-11-23
Try to put a # in front of the last line, "deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main", and see if you can update it again.

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by baysl on 2006-11-23
Now everything works fine:

./configure  #works ok
make         #works ok
make install   #error (make: *** No rule to make target `install'.  Stop.)

Whats wrong??

---

### Post by baysl on 2006-11-23
help please...

---

### Post by taurus on 2006-11-23
> **baysl said:**
> Now everything works fine:

./configure  #works ok
make         #works ok
make install   #error (make: *** No rule to make target `install'.  Stop.)

Whats wrong??
Try running 

```
sudo make install 
-or-
sudo checkinstall
```

---

### Post by baysl on 2006-11-23
Still not working...

roko@linux:~/Downloads/bnc2.9.4$ sudo checkinstall
sudo: checkinstall: command not found
roko@linux:~/Downloads/bnc2.9.4$ sudo make install
make: *** No rule to make target `install'.  Stop.

??

---

### Post by taurus on 2006-11-23
What's the output of this command then?

```
ls -la ~/Downloads/bnc2.9.4
```
Are you sure both ./configure && make ran fine?

---

### Post by baysl on 2006-11-23
**Output:**

roko@linux:~/Downloads/bnc2.9.4$ ls -la ~/Downloads/bnc2.9.4
total 588
drwxr-xr-x 2 roko roko   4096 2006-11-23 21:57 .
drwxr-xr-x 6 roko roko   4096 2006-11-23 21:53 ..
-rwxr-xr-x 1 roko roko  57242 2006-11-23 21:57 bnc
-rw-r--r-- 1 roko roko   5059 2005-02-06 19:12 bnc.c
-rwxr-xr-x 1 roko roko    544 2000-12-31 09:19 bncchk
-rw-r--r-- 1 roko roko   5672 2006-11-23 21:57 bnc.o
-rwxr-xr-x 1 roko roko   9082 2005-02-07 02:51 bncsetup
-rw-r--r-- 1 roko roko   7812 2005-02-07 02:17 Changelog
-rw-r--r-- 1 roko roko  30363 2005-02-07 02:27 cmds.c
-rw-r--r-- 1 roko roko  19444 2006-11-23 21:57 cmds.o
-rw-r--r-- 1 roko roko  12573 2005-02-06 19:02 conf.c
-rw-r--r-- 1 roko roko   1282 2006-11-23 20:05 config.h
-rw-r--r-- 1 roko roko   1189 2004-11-10 03:28 config.h.in
-rw-r--r-- 1 roko roko  23118 2006-11-23 21:57 config.log
-rwxr-xr-x 1 roko roko  28306 2006-11-23 21:57 config.status
-rwxr-xr-x 1 roko roko 155520 2004-11-10 03:29 configure
-rw-r--r-- 1 roko roko   1578 2004-11-10 03:28 configure.in
-rw-r--r-- 1 roko roko   7892 2006-11-23 21:57 conf.o
-rw-r--r-- 1 roko roko  17982 2000-12-31 09:19 COPYING
-rw-r--r-- 1 roko roko   5853 2005-01-26 05:17 ctcp.c
-rw-r--r-- 1 roko roko    289 2002-08-05 21:14 ctcp.h
-rw-r--r-- 1 roko roko   4564 2006-11-23 21:57 ctcp.o
-rw-r--r-- 1 roko roko   1121 2005-02-07 02:16 example.conf
-rw-r--r-- 1 roko roko    933 2006-11-23 21:57 Makefile
-rw-r--r-- 1 roko roko    917 2005-01-26 05:15 Makefile.in
-rw-r--r-- 1 roko roko     44 2000-12-31 09:19 Makefile.out
-rwxr-xr-x 1 roko roko   8364 2006-11-23 20:05 mkpasswd
-rw-r--r-- 1 roko roko   1424 2000-12-31 09:19 mkpasswd.c
-rw-r--r-- 1 roko roko    461 2005-02-06 15:44 motd
-rw-r--r-- 1 roko roko  12309 2005-02-06 15:44 README
-rw-r--r-- 1 roko roko   4775 2004-11-11 06:38 sbuf.c
-rw-r--r-- 1 roko roko   1021 2004-09-19 01:06 sbuf.h
-rw-r--r-- 1 roko roko   2536 2006-11-23 20:05 sbuf.o
-rw-r--r-- 1 roko roko   7484 2005-01-26 05:18 send.c
-rw-r--r-- 1 roko roko    124 2002-07-11 17:09 send.h
-rw-r--r-- 1 roko roko   5540 2006-11-23 21:57 send.o
-rw-r--r-- 1 roko roko  32292 2005-02-07 02:29 server.c
-rw-r--r-- 1 roko roko  18192 2006-11-23 21:57 server.o
-rw-r--r-- 1 roko roko   2927 2005-02-07 02:02 struct.h

[B]
This is the output of ./configure and make:[/B]

roko@linux:~/Downloads/bnc2.9.4$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for library containing strerror... none required
checking for egrep... grep -E
checking for AIX... no
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking whether time.h and sys/time.h may both be included... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking return type of signal handlers... void
checking for select in -lsocket... no
checking for select in -lnsl... yes
checking for gethostbyname in -lresolv... yes
checking for malloc in -lgnumalloc... no
checking for malloc in -lbsdmalloc... no
checking for select in -linet... no
checking for select in -lcposix... no
checking for select in -lnet... no
checking for crypt in -lcrypt... yes
checking whether to enable SSL support... no
checking for snprintf... yes
checking for vsnprintf... yes
checking for gethostbyname2... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
roko@linux:~/Downloads/bnc2.9.4$ make
gcc -O3 -Wall -include config.h -c bnc.c
gcc -O3 -Wall -include config.h -c conf.c
conf.c: In function ‘loadconf’:
conf.c:597: warning: pointer targets in passing argument 1 of ‘fgets’ differ in signedness
conf.c:603: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
conf.c:609: warning: pointer targets in passing argument 1 of ‘strtok’ differ in signedness
conf.c:634: warning: pointer targets in passing argument 1 of ‘strtok’ differ in signedness
gcc -O3 -Wall -include config.h -c server.c
server.c: In function ‘send_queued’:
server.c:406: warning: pointer targets in passing argument 2 of ‘sbuf_pagemap’ differ in signedness
server.c: In function ‘identwd_unlock’:
server.c:570: warning: pointer targets in passing argument 3 of ‘getsockname’ differ in signedness
server.c: In function ‘dccsend’:
server.c:1123: warning: pointer targets in passing argument 2 of ‘sbuf_pagemap’ differ in signedness
server.c: In function ‘addon_client’:
server.c:1546: warning: pointer targets in passing argument 3 of ‘getpeername’ differ in signedness
gcc -O3 -Wall -include config.h -c cmds.c
cmds.c: In function ‘handlepclient’:
cmds.c:404: warning: pointer targets in passing argument 1 of ‘fgets’ differ in signedness
cmds.c:406: warning: pointer targets in passing argument 1 of ‘remnl’ differ in signedness
gcc -O3 -Wall -include config.h -c ctcp.c
ctcp.c: In function ‘ctdcc_send’:
ctcp.c:333: warning: dereferencing type-punned pointer will break strict-aliasing rules
gcc -O3 -Wall -include config.h -c send.c
gcc -o bnc bnc.o conf.o server.o cmds.o ctcp.o sbuf.o send.o -lnsl -lresolv -lcrypt

---

### Post by Perfect Storm on 2006-11-23
I don't know what you are compiling but:
> checking whether to enable SSL support... no

You might get the -dev package of it and recompile it. Just make sure to run make clean first.


By thet way, have you checked the readme.txt for more information. Usually it tells how, what and when.

---

### Post by baysl on 2006-11-23
Tell me what to do?

Ive just started to use linux, i dont know what dev package is...

---

### Post by Perfect Storm on 2006-11-23
ah sorry.

```
sudo aptitude install libssl-dev
```
-dev packages are used to compiling and stuff.

Then clean the make you made (remember to be in the right place to do it)
```
make clean
./configure
make

```

---

### Post by HydroDiOxide on 2006-11-28
I'm trying to install a [gtk-theme-switcher](http://plasmasturm.org/code/gtk-chtheme/). Sadly the package is not available through synaptic, so I have to use the makefile. Good to say that I an absolute beginner when it comes to linux/ubuntu.

I followed the instructions found [here](http://monkeyblog.org/ubuntu/installing/#source) on how to install using make. I installed the build-essentials which seemed to go okeh except for an error about the gtk-engines-eazel

```
(Reading database ... 68734 files and directories currently installed.)
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up gtk-engines-eazel (0.3-5.1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing gtk-engines-eazel (--configure):
 subprocess post-installation script returned error exit status 2
Setting up build-essential (11.3) ...
Errors were encountered while processing:
 gtk-engines-eazel
E: Sub-process /usr/bin/dpkg returned an error code (1)
hensen@Dog:~$ 
```

However, when I try to run the ./configure command or the make or make install command, I get a bunch of errors and nothing happens.

error ./configure: ```
bash: ./configure: No such file or directory
```

error make:

```
hensen@Dog:~/Desktop/gtk-chtheme-0.3.1$ make
make: pkg-config: Command not found
cc   -Wall  -DGTK_DISABLE_BROKEN -DGTK_DISABLE_DEPRECATED -DPROJNAME='"Gtk+ 2.0 Change Theme"' -DVERSION='"0.3.1"'   -c -o util.o util.c
util.c:17:21: error: gtk/gtk.h: No such file or directory
In file included from util.c:18:
util.h:20: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
util.h:21: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
util.h:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
util.c:20: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
util.c:26: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
util.c:33: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
make: *** [util.o] Error 1
hensen@Dog:~/Desktop/gtk-chtheme-0.3.1$
```

error make install:

```
hensen@Dog:~/Desktop/gtk-chtheme-0.3.1$ make install
make: pkg-config: Command not found
cc   -Wall  -DGTK_DISABLE_BROKEN -DGTK_DISABLE_DEPRECATED -DPROJNAME='"Gtk+ 2.0 Change Theme"' -DVERSION='"0.3.1"'   -c -o util.o util.c
util.c:17:21: error: gtk/gtk.h: No such file or directory
In file included from util.c:18:
util.h:20: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
util.h:21: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
util.h:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
util.c:20: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
util.c:26: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
util.c:33: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
make: *** [util.o] Error 1
hensen@Dog:~/Desktop/gtk-chtheme-0.3.1$ 
```

Any idea how to fix this? I really new to this so if you can give an explanation on the different steps towards a solution, great. Best way to learn I think.

---

### Post by HydroDiOxide on 2006-12-07
bump

---

### Post by Perfect Storm on 2006-12-07
Do you have libgtk2-dev installed?


Why don't you use the theme changer that are already installed with ubuntu?

---

### Post by ]Nbx*cmD[ on 2006-12-07
first of all, when you install you should do it as superuser, so:

> sudo make install

If it's not working it might be an issue of the software you're trying to install, which one is it? Did you read its README or INSTALL file?

---

### Post by ]Nbx*cmD[ on 2006-12-07
oops sorry x'D
i didn't read the second page of this thread :p

---

### Post by HydroDiOxide on 2006-12-08
The main problem is that I can't install make files. I haven't got the libgtk2-dev package installed, but when I run ```
sudo apt-get install libgtk2-dev
``` the package can't be found.

I've got an xubuntu base with fluxbox here and I'm using the xfce-setting-show command to switch my themes. So that problem is solved.

However, installing makefiles is something I can't get done. If you could help me out, great!

---

### Post by Arndt on 2006-12-08
> **HydroDiOxide said:**
> The main problem is that I can't install make files. I haven't got the libgtk2-dev package installed, but when I run ```
sudo apt-get install libgtk2-dev
``` the package can't be found.

I've got an xubuntu base with fluxbox here and I'm using the xfce-setting-show command to switch my themes. So that problem is solved.

However, installing makefiles is something I can't get done. If you could help me out, great!

```
sudo apt-get install libgtk2.0-dev
```

should work better.

---

