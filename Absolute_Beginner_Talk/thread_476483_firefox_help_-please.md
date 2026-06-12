---
title: "firefox help -please"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by natman on 2007-06-17
Hi, I am running firefox 32 bit in a 64 bit machine, and for the last few weeks ( i have no idea why or how this started ) but firefox will just crash when i click to view a youtube video. I ran firefox from the terminal and got this.
[HTML]natman@natman-laptop:~$ firefox32
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
esd: no process killed
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(firefox-bin:7163): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
Warning: locale not supported by C library, locale unchanged
Segmentation fault (core dumped)
natman@natman-laptop:~$ ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
natman@natman-laptop:~$ 
[/HTML]
Any Ideas?

---

### Post by sailor2001 on 2007-06-17
[http://ubuntuforums.org/showthread.php?t=202537&page=11](http://ubuntuforums.org/showthread.php?t=202537&page=11)     Sorry can't stick with you on this, have to go...
also after you get that fixed, do click grease monkey as an add-on

---

### Post by Myglaren on 2007-06-17
I'm sorry that I can't be of any actual help for your problem but just want to say that I've used 32 bit Firefox on a 64 bit machine for the past four iterations of Ubuntu and never had a problem with it crashing and I use YouTube incessantly.
The only problem I have ever had was of my own making when I somehow stupidly installed the Esperanto version of Firefox, ordered Edgy from a Dutch site and couldn't remember my paypal password after navigating trying to guess what the combination of Dutch and Esperanto meant.

---

### Post by Andrax on 2007-06-17
I think it is a problem that every Ubuntu user has, given the fact that YouTube uses flash to play its videos, and flash is a commercial program, whos developers have not given the Ubuntu developers the actual codes for it run perfectly.

So do expect crashing and failures sometimes, but at least in my situation it's just a matter of force quiting firefox and reopening it again.

---

### Post by irish_flu on 2007-06-17
I can honestly say I've never had a crash using Firefox to view Youtube vids.  If I were you, I'd try uninstalling and reinstalling Flash.

---

### Post by natman on 2007-06-18
Im still having firerfox crash when i visit youtube ( for some reason, sometimes it works fine - i have no idea ). Anyway here's the terminal output, can someone please advise?
[HTML]natman@natman-laptop:~$ firefox32
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
esd: no process killed
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(firefox-bin:8274): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
Warning: locale not supported by C library, locale unchanged
Segmentation fault (core dumped)
natman@natman-laptop:~$ ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
natman@natman-laptop:~$ 

[/HTML]

Is part of the reason that im using 64, and forcing a 32 broswer on it? should i forget it and reinstall a 32bit OS?

---

### Post by Pragmatist on 2007-06-24
Please post the output of these:

```
ls -ld /usr/lib32
```
```
sudo updatedb
```
wait, as updatedb takes a few minutes. After it finishes, run this:

```
locate libpango
```

---

### Post by natman on 2007-06-24
Here is the terminal output

[HTML]natman@natman-laptop:~$ ls -ld /usr/lib32
drwxr-xr-x 21 root root 12288 2007-06-19 00:01 /usr/lib32
natman@natman-laptop:~$ sudo updatedb
Password:
natman@natman-laptop:~$ locate libpango
/var/lib/dpkg/info/libpango1.0-dev.md5sums
/var/lib/dpkg/info/libpango1.0-dev.list
/var/lib/dpkg/info/libpango1.0-0.list
/var/lib/dpkg/info/libpango1.0-0.md5sums
/var/lib/dpkg/info/libpango1.0-0.postinst
/var/lib/dpkg/info/libpango1.0-0.postrm
/var/lib/dpkg/info/libpango1.0-0.shlibs
/var/lib/dpkg/info/libpango1.0-common.conffiles
/var/lib/dpkg/info/libpango1.0-common.list
/var/lib/dpkg/info/libpango1.0-common.md5sums
/var/lib/dpkg/info/libpango1.0-common.postinst
/var/lib/dpkg/info/libpango1.0-common.postrm
/var/lib/dpkg/info/libpango1.0-common.prerm
/usr/lib/mono/gtk-sharp-2.0/libpangosharpglue-2.so
/usr/lib/pango/1.6.0/module-files.d/libpango1.0-0.modules
/usr/lib/libpango-1.0.so.0.1600.2
/usr/lib/libpango-1.0.so.0
/usr/lib/libpangocairo-1.0.so.0
/usr/lib/libpangoft2-1.0.so.0
/usr/lib/libpangox-1.0.so.0
/usr/lib/libpangoxft-1.0.so.0
/usr/lib/libpangocairo-1.0.so.0.1600.2
/usr/lib/libpangocairo-1.0.la
/usr/lib/libpango-1.0.la
/usr/lib/libpangocairo-1.0.so
/usr/lib/libpangoft2-1.0.la
/usr/lib/libpangox-1.0.la
/usr/lib/libpangoxft-1.0.la
/usr/lib/libpango-1.0.a
/usr/lib/libpangocairo-1.0.a
/usr/lib/libpangoft2-1.0.a
/usr/lib/libpangox-1.0.a
/usr/lib/libpangoxft-1.0.a
/usr/lib/libpango-1.0.so
/usr/lib/libpangoft2-1.0.so
/usr/lib/libpangox-1.0.so
/usr/lib/libpangoxft-1.0.so
/usr/lib/libpangoft2-1.0.so.0.1600.2
/usr/lib/libpangox-1.0.so.0.1600.2
/usr/lib/libpangoxft-1.0.so.0.1600.2
/usr/share/doc/libpango1.0-dev
/usr/share/doc/libpango1.0-0
/usr/share/doc/libpango1.0-0/NEWS.gz
/usr/share/doc/libpango1.0-0/README.Debian
/usr/share/doc/libpango1.0-0/README.Defoma
/usr/share/doc/libpango1.0-0/changelog.Debian.gz
/usr/share/doc/libpango1.0-0/changelog.gz
/usr/share/doc/libpango1.0-0/copyright
/usr/share/doc/libpango1.0-0/README
/usr/share/doc/libpango1.0-common
/usr/share/doc/ia32-libs-gtk-libpangohack
/usr/share/doc/ia32-libs-gtk-libpangohack/README.Debian
/usr/share/doc/ia32-libs-gtk-libpangohack/Manifest
/usr/share/doc/ia32-libs-gtk-libpangohack/changelog.gz
/usr/share/doc/ia32-libs-gtk-libpangohack/copyright
/usr/lib32/libpango-1.0.so.0.1504.1
/usr/lib32/pango/1.6.0/module-files.d/libpango1.0-0.modules
/usr/lib32/libpango-1.0.so.0
/usr/lib32/libpangox-1.0.so.0
/usr/lib32/libpangoft2-1.0.so.0
/usr/lib32/libpangoxft-1.0.so.0
/usr/lib32/libpangocairo-1.0.so.0
/usr/lib32/libpangohack.so.0.0
/usr/lib32/libpangohack.so.0
/usr/lib32/libpangoft2-1.0.so.0.1504.1
/usr/lib32/libpangox-1.0.so.0.1504.1
/usr/lib32/libpangocairo-1.0.so.0.1504.1
/usr/lib32/libpangoxft-1.0.so.0.1504.1
natman@natman-laptop:~$ 

[/HTML]

---

### Post by Pragmatist on 2007-06-24
Now these:

```
ls -l  /usr/lib32/libpango*
```

```
ls -l  /usr/lib/libpango*
```

---

### Post by natman on 2007-06-24
And here
[HTML]natman@natman-laptop:~$ ls -l  /usr/lib32/libpango*
lrwxrwxrwx 1 root   root       24 2007-04-22 14:31 /usr/lib32/libpango-1.0.so.0 -> libpango-1.0.so.0.1504.1
-rw-r--r-- 1 root   root   249788 2007-01-23 11:35 /usr/lib32/libpango-1.0.so.0.1504.1
lrwxrwxrwx 1 root   root       29 2007-04-22 14:31 /usr/lib32/libpangocairo-1.0.so.0 -> libpangocairo-1.0.so.0.1504.1
-rw-r--r-- 1 root   root    30848 2007-01-23 11:35 /usr/lib32/libpangocairo-1.0.so.0.1504.1
lrwxrwxrwx 1 root   root       27 2007-04-22 14:31 /usr/lib32/libpangoft2-1.0.so.0 -> libpangoft2-1.0.so.0.1504.1
-rw-r--r-- 1 root   root   175192 2007-01-23 11:35 /usr/lib32/libpangoft2-1.0.so.0.1504.1
lrwxrwxrwx 1 natman natman     19 2007-06-19 00:00 /usr/lib32/libpangohack.so.0 -> libpangohack.so.0.0
-rw-r--r-- 1 natman natman   2994 2005-08-30 13:38 /usr/lib32/libpangohack.so.0.0
lrwxrwxrwx 1 root   root       25 2007-04-22 14:31 /usr/lib32/libpangox-1.0.so.0 -> libpangox-1.0.so.0.1504.1
-rw-r--r-- 1 root   root    43552 2007-01-23 11:35 /usr/lib32/libpangox-1.0.so.0.1504.1
lrwxrwxrwx 1 root   root       27 2007-04-22 14:31 /usr/lib32/libpangoxft-1.0.so.0 -> libpangoxft-1.0.so.0.1504.1
-rw-r--r-- 1 root   root    24900 2007-01-23 11:35 /usr/lib32/libpangoxft-1.0.so.0.1504.1
natman@natman-laptop:~$ ls -l  /usr/lib/libpango*
-rw-r--r-- 1 root root 478292 2007-04-10 14:14 /usr/lib/libpango-1.0.a
-rw-r--r-- 1 root root    816 2007-04-10 14:14 /usr/lib/libpango-1.0.la
lrwxrwxrwx 1 root root     24 2007-04-22 14:14 /usr/lib/libpango-1.0.so -> libpango-1.0.so.0.1600.2
lrwxrwxrwx 1 root root     24 2007-04-22 14:14 /usr/lib/libpango-1.0.so.0 -> libpango-1.0.so.0.1600.2
-rw-r--r-- 1 root root 282336 2007-04-10 14:14 /usr/lib/libpango-1.0.so.0.1600.2
-rw-r--r-- 1 root root  58786 2007-04-10 14:14 /usr/lib/libpangocairo-1.0.a
-rw-r--r-- 1 root root    846 2007-04-10 14:14 /usr/lib/libpangocairo-1.0.la
lrwxrwxrwx 1 root root     29 2007-04-22 14:14 /usr/lib/libpangocairo-1.0.so -> libpangocairo-1.0.so.0.1600.2
lrwxrwxrwx 1 root root     29 2007-04-22 14:14 /usr/lib/libpangocairo-1.0.so.0 -> libpangocairo-1.0.so.0.1600.2
-rw-r--r-- 1 root root  37328 2007-04-10 14:14 /usr/lib/libpangocairo-1.0.so.0.1600.2
-rw-r--r-- 1 root root 453982 2007-04-10 14:14 /usr/lib/libpangoft2-1.0.a
-rw-r--r-- 1 root root    834 2007-04-10 14:14 /usr/lib/libpangoft2-1.0.la
lrwxrwxrwx 1 root root     27 2007-04-22 14:14 /usr/lib/libpangoft2-1.0.so -> libpangoft2-1.0.so.0.1600.2
lrwxrwxrwx 1 root root     27 2007-04-22 14:14 /usr/lib/libpangoft2-1.0.so.0 -> libpangoft2-1.0.so.0.1600.2
-rw-r--r-- 1 root root 190136 2007-04-10 14:14 /usr/lib/libpangoft2-1.0.so.0.1600.2
-rw-r--r-- 1 root root 147968 2007-04-10 14:14 /usr/lib/libpangox-1.0.a
-rw-r--r-- 1 root root    822 2007-04-10 14:14 /usr/lib/libpangox-1.0.la
lrwxrwxrwx 1 root root     25 2007-04-22 14:14 /usr/lib/libpangox-1.0.so -> libpangox-1.0.so.0.1600.2
lrwxrwxrwx 1 root root     25 2007-04-22 14:14 /usr/lib/libpangox-1.0.so.0 -> libpangox-1.0.so.0.1600.2
-rw-r--r-- 1 root root  49552 2007-04-10 14:14 /usr/lib/libpangox-1.0.so.0.1600.2
-rw-r--r-- 1 root root  39062 2007-04-10 14:14 /usr/lib/libpangoxft-1.0.a
-rw-r--r-- 1 root root    834 2007-04-10 14:14 /usr/lib/libpangoxft-1.0.la
lrwxrwxrwx 1 root root     27 2007-04-22 14:14 /usr/lib/libpangoxft-1.0.so -> libpangoxft-1.0.so.0.1600.2
lrwxrwxrwx 1 root root     27 2007-04-22 14:14 /usr/lib/libpangoxft-1.0.so.0 -> libpangoxft-1.0.so.0.1600.2
-rw-r--r-- 1 root root  29336 2007-04-10 14:14 /usr/lib/libpangoxft-1.0.so.0.1600.2
natman@natman-laptop:~$ 

[/HTML]

---

### Post by Pragmatist on 2007-06-24
Did you follow these directions?
[http://ubuntuforums.org/showthread.php?t=202537&highlight=pango](http://ubuntuforums.org/showthread.php?t=202537&highlight=pango)

---

### Post by natman on 2007-06-24
Yes thats the install script that i used to get 32 firefox, actuall it seems to be working again now, but you have any other ideas please past them on.
Thanks For all the help:)

---

### Post by Pragmatist on 2007-06-24
> **natman said:**
> Yes thats the install script that i used...

O.K. If you read that thread then you must have seen this:
> **[SIZE=4][COLOR=Sienna]Common Problems[/COLOR][/SIZE]**
IF YOU HAVE ANY PROBLEMS CHECK THE SECTIONS FOR FIXES TO COMMON PROBLEMS. If you make a post requesting help please state if you followed the howto or installed the script, also list all steps you have made to try and correct the problem.

Error 1
     Code:
     ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored. 
[COLOR=Red]** Ignore this error.**[/COLOR]So this error you keep posting is not the cause of your problems.  The error about locale IS a problem and the solution is in the thread I linked in my last post:
> 
Another Feisty Error that I have seen a few times is this one.
     Code:
     Gtk-WARNING **: Locale not supported by C library.Using the fallback 'C' locale. 
To fix it, [Go Here:]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Funiverse%2Fi%2Fia32-libs-gtk%2Fia32-libs-gtk_25_amd64.deb&md5sum=e810a79e9dece355c4737998732b2de1&arch=amd64&type=main")  and download the ia32-libs-gtk package, double click on the .deb file and let gdebi install it. Afterwards please rerun the install script as half the packages did not install because this dependancy was not installed.
Did you do any of this??

---

