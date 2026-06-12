---
title: "[SOLVED] Epiphany problems"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-05-27
Is anyone able to help with a problem  starting epiphany

When I try and start it from a launcher it wants me to choose between recovering or not recovering lost sessions  - last use apparently ended unexpectedly.

Doesn't matter which I choose - same result - it appears to be starting then nothing happens

When i start from terminal  I get - 

```
Segmentation fault (core dumped)
```

I've uninstalled and reinstalled through synaptic - with no change 

I've done both 
```
sudo apt-get purge epiphany-browser 
```
and ```
sudo apt-get install epiphany-browser
``` - with no change

Don't know what I can do next to get it working.

Please help

---

### Post by forestpixie on 2007-05-28
'bump

---

### Post by bapoumba on 2007-05-28
Which flavor of Ubuntu are you using and which version of epiphany is installed?
There are bugs related to java, amd64... Is firefox crashing as well ?
Any particular extension installed ?

---

### Post by Kobalt on 2007-05-28
You can also try removing it and removing as well the *epiphany* folder in */home/.gnome2* before reinstalling and relaunching it.

---

### Post by forestpixie on 2007-05-28
Bapoumba - I'm using Feisty,

apt-get is installing this epiphany - /epiphany-browser_2.18.1-0ubuntu1_i386.deb . 
I have no problems with firefox, I have no extensions in epiphany and adblock plus and user switcher in firefox

Kobalt - I removed the epiphnay folder, reinstalled, relaunched and got the segmentation fault again.

And thanks to you both for the replies!
:)

---

### Post by forestpixie on 2007-05-28
'bump

---

### Post by bapoumba on 2007-05-28
Hum. I'm using the same version of epiphany, feisty, and its fine here. I did no find related bugs with epiphany seg faults after install that did not affect firefox too. 

Is there more to the terminal message when it crashes ?

---

### Post by forestpixie on 2007-05-28
no - nothing at all

kevin@kevin-desktop:~$ epiphany
Segmentation fault (core dumped)
kevin@kevin-desktop:~$ 

and it didn't even close unexpectedly the first time! - I just got the message about recovering sessions when i tried to get in.

---

### Post by bapoumba on 2007-05-28
I've looked around. I cannot see anything relevant.
What is the output to **aptitude show epiphany-browser**? Is it properly installed ?
```
~$ aptitude show epiphany-browser
Package: epiphany-browser
State: installed
Automatically installed: no
Version: 2.18.1-0ubuntu1
Priority: optional
Section: gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 13.6M
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.13.1), libbonobo2-0 (>=
         2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.5-0ubuntu1), libcairo2
         (>= 1.4.2), libdbus-1-3 (>= 0.94), libdbus-glib-1-2 (>= 0.73),
         libenchant1c2a, libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2),
         libgcc1 (>= 1:4.1.2), libgconf2-4 (>= 2.13.5), libglade2-0 (>=
         1:2.5.1), libglib2.0-0 (>= 2.12.9), libgnome-desktop-2 (>= 2.11.1),
         libgnome-keyring0 (>= 0.7.1), libgnome2-0 (>= 2.14.1),
         libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.17.1), libgnomevfs2-0
         (>= 1:2.17.90), libgtk2.0-0 (>= 2.10.3), libice6 (>= 1:1.0.0),
         liblaunchpad-integration0 (>= 0.0patch26), liborbit2 (>= 1:2.14.1),
         libpango1.0-0 (>= 1.16.1), libpng12-0 (>= 1.2.13-4), libpopt0 (>=
         1.10), libsm6, libstartup-notification0 (>= 0.8-1), libstdc++6 (>=
         4.1.2), libx11-6, libxcursor1 (> 1.1.2), libxext6, libxfixes3 (>=
         1:4.0.1), libxi6, libxinerama1, libxml2 (>= 2.6.27), libxrandr2 (>=
         2:1.2.0), libxrender1, libxslt1.1 (>= 1.1.20), python2.5 (>= 2.5),
         zlib1g (>= 1:1.2.1), gnome-icon-theme (>= 2.9.90), dbus, iso-codes,
         gconf2 (>= 2.12.1-4ubuntu1), firefox (>= 1.5)
Recommends: yelp, epiphany-extensions
Suggests: mozilla-bonobo
Conflicts: epiphany-extensions (< 2.18)
Provides: www-browser

```

Can you get a backtrace with gdb ?
[https://wiki.ubuntu.com/Backtrace]("https://wiki.ubuntu.com/Backtrace")

---

### Post by forestpixie on 2007-05-28
output is

```
kevin@kevin-desktop:~$ aptitude show epiphany-browser
Package: epiphany-browser
State: installed
Automatically installed: no
Version: 2.18.1-0ubuntu1
Priority: optional
Section: gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 13.6M
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.13.1), libbonobo2-0 (>=
         2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.5-0ubuntu1), libcairo2
         (>= 1.4.2), libdbus-1-3 (>= 0.94), libdbus-glib-1-2 (>= 0.73),
         libenchant1c2a, libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2),
         libgcc1 (>= 1:4.1.2), libgconf2-4 (>= 2.13.5), libglade2-0 (>=
         1:2.5.1), libglib2.0-0 (>= 2.12.9), libgnome-desktop-2 (>= 2.11.1),
         libgnome-keyring0 (>= 0.7.1), libgnome2-0 (>= 2.14.1),
         libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.17.1), libgnomevfs2-0
         (>= 1:2.17.90), libgtk2.0-0 (>= 2.10.3), libice6 (>= 1:1.0.0),
         liblaunchpad-integration0 (>= 0.0patch26), liborbit2 (>= 1:2.14.1),
         libpango1.0-0 (>= 1.16.1), libpng12-0 (>= 1.2.13-4), libpopt0 (>=
         1.10), libsm6, libstartup-notification0 (>= 0.8-1), libstdc++6 (>=
         4.1.2), libx11-6, libxcursor1 (> 1.1.2), libxext6, libxfixes3 (>=
         1:4.0.1), libxi6, libxinerama1, libxml2 (>= 2.6.27), libxrandr2 (>=
         2:1.2.0), libxrender1, libxslt1.1 (>= 1.1.20), python2.5 (>= 2.5),
         zlib1g (>= 1:1.2.1), gnome-icon-theme (>= 2.9.90), dbus, iso-codes,
         gconf2 (>= 2.12.1-4ubuntu1), firefox (>= 1.5)
Recommends: yelp, epiphany-extensions
Suggests: mozilla-bonobo
Conflicts: epiphany-extensions (< 2.18)
Provides: www-browser

```

to do the backtrace do i need to just follow the instructions at the wiki site?

never done that before!

---

### Post by forestpixie on 2007-05-28
so for instance i would 

gdb epiphany 2>&1 | tee gdb-epiphany.txt
(gdb) handle SIG33 pass nostop noprint
(gdb) set pagination 0
(gdb) run <arguments, if any>

yes?

---

### Post by bapoumba on 2007-05-28
And a backtrace is necessary to file a bug for ex.

---

### Post by forestpixie on 2007-05-28
ok i'll have a go at that then

---

### Post by forestpixie on 2007-05-28
well i ran the instructions - no idea what i've done though!!

don't know where the .txt file has gone, I assume there's a gdb directory somewhere

this is the output from the terminal

not sure of the next step 
```

kevin@kevin-desktop:~$ gdb epiphany 2>&1 | tee gdb-epiphany.txt
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(gdb) 
(gdb) [COLOR="Red"]epiphany
Undefined command: "epiphany".  Try "help".[/COLOR] [COLOR="Blue"]made a mistake here[/COLOR]
(gdb) handle SIG33 pass nostop noprint
Signal        Stop      Print   Pass to program Description
SIG33         No        No      Yes             Real-time event 33
(gdb) set pagination 0
(gdb) run
Starting program: /usr/bin/epiphany 
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1230276384 (LWP 10074)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread -1267582064 (LWP 10083)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1230276384 (LWP 10074)]
0xb7e85047 in ?? () from /usr/lib/firefox/libgtkembedmoz.so
(gdb) backtrace full
#0  0xb7e85047 in ?? () from /usr/lib/firefox/libgtkembedmoz.so
No symbol table info available.
#1  0x08417100 in ?? ()
No symbol table info available.
#2  0xbffb4d28 in ?? ()
No symbol table info available.
#3  0xb7e8f9c8 in ?? () from /usr/lib/firefox/libgtkembedmoz.so
No symbol table info available.
#4  0xb6e8110c in nsCOMPtr_base::assign_with_AddRef () from /usr/lib/firefox/libxpcom_core.so
No symbol table info available.
#5  0xb7e8391b in ?? () from /usr/lib/firefox/libgtkembedmoz.so
No symbol table info available.
#6  0x08416140 in ?? ()
No symbol table info available.
#7  0xbffb4da8 in ?? ()
No symbol table info available.
#8  0x00000000 in ?? ()
No symbol table info available.
(gdb) info registers
eax            0x0      0
ecx            0x8417100        138506496
edx            0x0      0
ebx            0xb7e90930       -1209464528
esp            0xbffb4ce0       0xbffb4ce0
ebp            0xbffb4d48       0xbffb4d48
esi            0x8417110        138506512
edi            0xb37ccf40       -1283666112
eip            0xb7e85047       0xb7e85047 <_fini+37107>
eflags         0x210246 [ PF ZF IF RF ID ]
cs             0x73     115
ss             0x7b     123
ds             0x7b     123
es             0x7b     123
fs             0x0      0
gs             0x33     51
(gdb) thread apply all backtrace

Thread 2 (Thread -1267582064 (LWP 10083)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7dc4893 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e62c29 in PR_Poll () from /usr/lib/libnspr4.so
#3  0xb47d56db in ?? () from /usr/lib/firefox/components/libnecko.so
#4  0x083b6160 in ?? ()
#5  0x00000001 in ?? ()
#6  0xffffffff in ?? ()
#7  0xb7e664b8 in PR_GetCurrentThread () from /usr/lib/libnspr4.so
#8  0xb47d5f15 in ?? () from /usr/lib/firefox/components/libnecko.so
#9  0x083b5c78 in ?? ()
#10 0xb4723368 in ?? ()
#11 0xb4723358 in ?? ()
#12 0xb7e5120f in PR_SetThreadPrivate () from /usr/lib/libnspr4.so
#13 0xb6ecf1cb in ?? () from /usr/lib/firefox/libxpcom_core.so
#14 0x083b5c78 in ?? ()
#15 0x00000001 in ?? ()
#16 0x00000001 in ?? ()
#17 0xb7e6f554 in ?? () from /usr/lib/libnspr4.so
#18 0x0837d758 in ?? ()
#19 0x00000000 in ?? ()

Thread 1 (Thread -1230276384 (LWP 10074)):
#0  0xb7e85047 in ?? () from /usr/lib/firefox/libgtkembedmoz.so
#1  0x08417100 in ?? ()
#2  0xbffb4d28 in ?? ()
#3  0xb7e8f9c8 in ?? () from /usr/lib/firefox/libgtkembedmoz.so
#4  0xb6e8110c in nsCOMPtr_base::assign_with_AddRef () from /usr/lib/firefox/libxpcom_core.so
#5  0xb7e8391b in ?? () from /usr/lib/firefox/libgtkembedmoz.so
#6  0x08416140 in ?? ()
#7  0xbffb4da8 in ?? ()
#8  0x00000000 in ?? ()
(gdb) quit
The program is running.  Exit anyway? (y or n) y
kevin@kevin-desktop:~$ 
```

---

### Post by forestpixie on 2007-05-28
okay found the file

---

### Post by bapoumba on 2007-05-28
The .txt file should be in the directory you started gdb epiphany from.
The info here should be included in a bug report.

Just out of curiosity, could you paste your sources.list ?

---

### Post by forestpixie on 2007-05-28
Okay here is sources list - how do I go about a bug report?

ANd many thanks for your help here - the only information I found on epiphany all sort of petered out

```
## Uncomment the following two lines to fetch updated software from the network
deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe

deb http://gb.archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-security restricted main universe #Added by software-properties

deb http://gb.archive.ubuntu.com/ubuntu/ feisty-security universe

deb http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse #Added by software-properties

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb http://archive.ubuntustudio.org/ubuntustudio feisty main

deb http://morgoth.free.fr/ubuntu feisty-backports main
deb-src http://morgoth.free.fr/ubuntu feisty-backports main
deb http://security.ubuntu.com/ubuntu/ feisty-security restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu/ feisty-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

---

### Post by forestpixie on 2007-05-28
I've been reading the 'filing bugs' sticky - and I've looked in /var/crash - there is an epiphany crash report in there - it wouldn't open in text editor - when opened in oo it's 521 pages long and I see it's 2.5Mb - do I need to attach that with the bug report! Or just the gdb-epiphany file (he hopes)

---

### Post by bapoumba on 2007-05-28
Okay, I am no expert on reading backtraces :/

However, from our sources.list, I see several third party repos, and from the backtraces several references to libs.

Could you please try to:
1- purge epiphany (not just remove, but purge)
2- edit your sources.list, and comment out the third party repos, the backports, commercial. Basically keep main restricteed universe multiverse.
3- **sudo aptitude update** then **sudo aptitude install epiphany-browser**.

This may lead to downgrading some libs, which could cause other problems to you. Paste the output to the install epiphany before you run it if not sure.

---

### Post by forestpixie on 2007-05-28
Okay did that - and got the same error - BUT I'm not sure if I've commented out the correct  repos. 

This is the edited sorces.list. have I missed any that I should've commented out. 

```
## Uncomment the following two lines to fetch updated software from the network
deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe

deb http://gb.archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-security restricted main universe #Added by software-properties

deb http://gb.archive.ubuntu.com/ubuntu/ feisty-security universe

deb http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse #Added by software-properties

#deb http://archive.canonical.com/ubuntu feisty-commercial main

#deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb http://archive.ubuntustudio.org/ubuntustudio feisty main

#deb http://morgoth.free.fr/ubuntu feisty-backports main
#deb-src http://morgoth.free.fr/ubuntu feisty-backports main
deb http://security.ubuntu.com/ubuntu/ feisty-security restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu/ feisty-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

---

### Post by bapoumba on 2007-05-28
Well, just the backports, but not sure this would be making any difference (I do not see anything related there, but I may be wrong).
You should open a bug on epiphany then, and include the backtrace. If the devs need more info, they will ask for it.

---

### Post by forestpixie on 2007-05-28
Ok thanks for your help, I'll do that now and we'll see what happens with it.

:D

---

### Post by bapoumba on 2007-05-28
Please paste in here the link to the bug report, so that we can follow.
Cheers.

---

### Post by forestpixie on 2007-05-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/117419](https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/117419) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				reported to launchpad -

---

### Post by forestpixie on 2007-06-02
after todays ff update , reinstalling epiphany got it to work

---

### Post by bapoumba on 2007-06-02
> **forestpixie said:**
> after todays ff update , reinstalling epiphany got it to work
Yes, I had subscribed to your bug, and saw that earlier today. Cool :)

---

### Post by forestpixie on 2007-06-03
Yep all a bit odd but never mind such is life for those of us willing to experiment!!

Still thanks for your help

:D

---

