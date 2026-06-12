---
title: "Re-instlling firefox32 on a 64 bit platform"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2007-12-04
Hey all,

Was having problems with firefox the other day suddenly stopped playing all media.  If it was something I did, I couldn't figure it out, so I decided to un/reinstall firefox and start over.

I remember from the first time I did it, I had to force install the 32 bit version of firefox to play all the java and flash stuff properly, so I found the same tutorial I used back then and went to it.  Unfortunately, when it comes time to test my 32bit install, I get a permission denied message and for the life of me can't figure out where it is coming from:

```
brian@brian-desktop:~$ sudo chmod +x /usr/local/bin/firefox32 
brian@brian-desktop:~$ firefox32 &
[2] 1715
brian@brian-desktop:~$ linux32: /usr/local/firefox32/firefox: Permission denied

[2]-  Exit 1                  firefox32
brian@brian-desktop:~$ 
```

Can anybody tell me why I am getting a permission denied?

Thanks!

-B

---

### Post by bollix47 on 2007-12-04
Try it without the "&" sign after firefox32.

---

### Post by Paqman on 2007-12-04
What version of Ubuntu are you using? Recent versions no longer require you to run 32-bit firefox to get flash. Simply install flashplugin-nonfree and it'll install the wrapper automatically. Couldn't be easier!

---

### Post by marmaladejackson on 2007-12-04
No joy for not using th "&" after the command:

```
brian@brian-desktop:~$ firefox32 
linux32: /usr/local/firefox32/firefox: Permission denied
brian@brian-desktop:~$ 
```

As for flash, just installed the non-free plugin, haven't noticed much of a change.  The controls or the video on most of the embeded medial sites comes out all funky and/or doesn't work alt all.  See the attached youtube screen-shot.  Also, if I open more than 2 windows on the 64 bit version of firefox, the whole thing crashes.

Thanks for the help so far, any other advice?

-B

---

### Post by bollix47 on 2007-12-04
Could you please provide the link to the tutorial that you used to install firefox32?

FYI - Using "&" after a command/program puts same in the background.  It would not be used when running an interactive program like Firefox.

---

### Post by marmaladejackson on 2007-12-04
Sure here is the link:

[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

I am pretty sure I used the same tutorial about a year ago when I first switched to Linux.  I'm using 7.10 now and my experience level is obviously much greater than it was after first install.  I remember having some problems getting firefox32 to work, but I solved it within an evening and for the life of me can't figure out why I'm having so much trouble now.

Thanks again!

---

### Post by bollix47 on 2007-12-04
Please paste the output of

```
ls -l /usr/local/bin/firefox32
```

---

### Post by ptn107 on 2007-12-04
Just get Ubuntu 64-bit and install *ubuntu-restricted-extras*.  You don't need Firefox 32 bit on 64-bit Ubuntu.  Problem solved.

---

### Post by marmaladejackson on 2007-12-04
Those restricted driver were already installed.  I re-installed them.

```
brian@brian-desktop:/usr/local/firefox32$ ls -l /usr/local/bin/firefox32
-rwxr-xr-x 1 root root 192 2007-12-04 09:47 /usr/local/bin/firefox32
brian@brian-desktop:/usr/local/firefox32$ 
```

---

### Post by bollix47 on 2007-12-04
Sorry ... one more

```
ls -l /usr/local/firefox32
```

BTW I did see where the & was being used to start firefox32 and can only assume  they did it that way to free up the terminal after starting.  It works okay.  I always use a launcher so don't have that problem.

---

### Post by marmaladejackson on 2007-12-04
```
brian@brian-desktop:/usr/local/firefox32$ ls -l /usr/local/firefox32
total 44
-rw-r--r--  1 brian brian    57 2007-12-01 18:42 active-update.xml
drwxr-xr-x  2 brian brian  4096 2007-12-03 19:06 components
drwxr-xr-x 13 brian brian  4096 2007-12-03 22:18 firefox
-rw-r--r--  1 brian brian 10659 2007-11-29 22:34 install.log
-rw-r--r--  1 brian brian   112 2007-10-14 11:01 old-homepage-default.properties
drwxr-xr-x  2 brian brian  4096 2007-12-03 20:57 plugins
drwxr-xr-x  3 brian brian  4096 2007-12-01 18:42 updates
-rw-r--r--  1 brian brian  5894 2007-12-01 18:42 updates.xml
brian@brian-desktop:/usr/local/firefox32$ 

```

---

### Post by marmaladejackson on 2007-12-06
OK, I think I almost got it licked, but I can't seem to get permission to run the script that allows me to run firefox32.  I've used the chmod command in every way I can imagine, but can't get it to go.  Observe:

```
brian@brian-desktop:/usr/local/bin$ firefox32
linux32: /usr/local/firefox32/firefox: Permission denied
brian@brian-desktop:/usr/local/bin$ sudo chmod +x firefox32
brian@brian-desktop:/usr/local/bin$ firefox32
linux32: /usr/local/firefox32/firefox: Permission denied
brian@brian-desktop:/usr/local/bin$ sudo chmod +X firefox32
brian@brian-desktop:/usr/local/bin$ firefox32
linux32: /usr/local/firefox32/firefox: Permission denied
brian@brian-desktop:/usr/local/bin$ sudo chmod u+xrw firefox32 
brian@brian-desktop:/usr/local/bin$ ls -ld firefox32
-rwxr-xr-x 1 root root 192 2007-12-04 09:47 firefox32
brian@brian-desktop:/usr/local/bin$ sudo chmod ug+xrw firefox32 
brian@brian-desktop:/usr/local/bin$ ls -ld firefox32
-rwxrwxr-x 1 root root 192 2007-12-04 09:47 firefox32
brian@brian-desktop:/usr/local/bin$ chmod +x firefox32
chmod: changing permissions of `firefox32': Operation not permitted
brian@brian-desktop:/usr/local/bin$ sudo chmod +x firefox32
brian@brian-desktop:/usr/local/bin$ ls -ld firefox32
-rwxrwxr-x 1 root root 192 2007-12-04 09:47 firefox32
brian@brian-desktop:/usr/local/bin$ firefox32
linux32: /usr/local/firefox32/firefox: Permission denied
brian@brian-desktop:/usr/local/bin$ 

```

What am I doing wrong?  I am baffled!

---

### Post by bollix47 on 2007-12-06
That is saying you have a permission problem with firefox not firefox32.

Have a look at /usr/local/firefox32/firefox

---

### Post by marmaladejackson on 2007-12-06
Not sure if I know what I am doing but I changed the permissions and this is what I got:

```
brian@brian-desktop:~$ ls -ln /usr/local/firefox32/
total 44
-rw-r--r--  1 1000 1000    57 2007-12-01 18:42 active-update.xml
drwxr-xr-x  2 1000 1000  4096 2007-12-03 19:06 components
drwxrwxr-x 13 1000 1000  4096 2007-12-06 19:21 firefox
-rw-r--r--  1 1000 1000 10659 2007-11-29 22:34 install.log
-rw-r--r--  1 1000 1000   112 2007-10-14 11:01 old-homepage-default.properties
drwxr-xr-x  2 1000 1000  4096 2007-12-04 21:44 plugins
drwxr-xr-x  3 1000 1000  4096 2007-12-01 18:42 updates
-rw-r--r--  1 1000 1000  5894 2007-12-01 18:42 updates.xml
brian@brian-desktop:~$ firefox32
linux32: /usr/local/firefox32/firefox: Permission denied
brian@brian-desktop:~$ linux32
$ /usr/local/firefox32/firefox
-sh: /usr/local/firefox32/firefox: Permission denied

```

---

### Post by bollix47 on 2007-12-06
What's the output of:

```
ls -ln /usr/local/firefox32/firefox
```

---

### Post by marmaladejackson on 2007-12-06
```
brian@brian-desktop:~$ ls -ln /usr/local/firefox32/firefox
total 13732
-rw-r--r-- 1 1000 1000      232 2007-11-27 18:57 browserconfig.properties
drwxrwxr-x 3 1000 1000     4096 2007-11-27 18:57 chrome
drwxrwxr-x 2 1000 1000     4096 2007-12-06 18:20 components
drwxrwxr-x 5 1000 1000     4096 2007-11-27 18:57 defaults
drwxrwxr-x 2 1000 1000     4096 2007-11-27 18:57 dictionaries
drwxrwxr-x 5 1000 1000     4096 2007-12-06 18:22 extensions
-rwxrwxrwx 1 1000 1000     5286 2007-11-27 18:57 firefox
-rwxr-xr-x 1 1000 1000 10562084 2007-11-27 18:57 firefox-bin
drwxrwxr-x 2 1000 1000     4096 2007-11-27 18:57 greprefs
drwxrwxr-x 2 1000 1000     4096 2007-11-27 18:57 icons
-rw-r--r-- 1 1000 1000     3375 2007-12-04 23:05 install.log
-rw-r--r-- 1 1000 1000      476 2007-11-27 18:57 libfreebl3.chk
-rwxr-xr-x 1 1000 1000   231468 2007-11-27 18:57 libfreebl3.so
-rwxr-xr-x 1 1000 1000   628924 2007-11-27 18:57 libmozjs.so
-rwxr-xr-x 1 1000 1000   176716 2007-11-27 18:57 libnspr4.so
-rwxr-xr-x 1 1000 1000   430608 2007-11-27 18:57 libnss3.so
-rwxr-xr-x 1 1000 1000   276064 2007-11-27 18:57 libnssckbi.so
-rwxr-xr-x 1 1000 1000    15304 2007-11-27 18:57 libplc4.so
-rwxr-xr-x 1 1000 1000     8240 2007-11-27 18:57 libplds4.so
-rwxr-xr-x 1 1000 1000   138316 2007-11-27 18:57 libsmime3.so
-rw-r--r-- 1 1000 1000      476 2007-11-27 18:57 libsoftokn3.chk
-rwxr-xr-x 1 1000 1000   309624 2007-11-27 18:57 libsoftokn3.so
-rwxr-xr-x 1 1000 1000   155560 2007-11-27 18:57 libssl3.so
-rwxr-xr-x 1 1000 1000    94924 2007-11-27 18:57 libxpcom_compat.so
-rwxr-xr-x 1 1000 1000   699056 2007-11-27 18:57 libxpcom_core.so
-rwxr-xr-x 1 1000 1000     9240 2007-11-27 18:57 libxpcom.so
-rwxr-xr-x 1 1000 1000     8284 2007-11-27 18:57 libxpistub.so
-rwxr-xr-x 1 1000 1000    10336 2007-11-27 18:57 mozilla-xremote-client
-rw-r--r-- 1 1000 1000      112 2007-11-27 18:57 old-homepage-default.properties
drwxrwxr-x 2 1000 1000     4096 2007-12-06 19:05 plugins
-rw-r--r-- 1 1000 1000      177 2007-11-27 18:57 readme.txt
-rw-r--r-- 1 1000 1000      335 2007-12-03 22:11 registry
-rwxr-xr-x 1 1000 1000    13062 2007-11-27 18:57 removed-files
drwxrwxr-x 6 1000 1000     4096 2007-11-27 18:57 res
-rwxr-xr-x 1 1000 1000    10492 2007-11-27 18:57 run-mozilla.sh
drwxrwxr-x 2 1000 1000     4096 2007-11-27 18:57 searchplugins
-rwxr-xr-x 1 1000 1000    67496 2007-11-27 18:57 updater
-rw-r--r-- 1 1000 1000      145 2007-11-27 18:57 updater.ini
drwxrwxr-x 3 1000 1000     4096 2007-12-03 19:50 updates
-rwxr-xr-x 1 1000 1000    21368 2007-11-27 18:57 xpicleanup
brian@brian-desktop:~$ 
```

---

### Post by bollix47 on 2007-12-06
It appears to be trying to execute a folder/directory.

Post the output of

```
cat /usr/local/bin/firefox32

```


With all the chmod's it may be that you will have to re-install Ubuntu.  If your home folder is on a separate partition or you have it backed up then that may be your best course.

First let's look at the above output.

---

### Post by misfitpierce on 2007-12-06
> **marmaladejackson said:**
> No joy for not using th "&" after the command:

```
brian@brian-desktop:~$ firefox32 
linux32: /usr/local/firefox32/firefox: Permission denied
brian@brian-desktop:~$ 
```As for flash, just installed the non-free plugin, haven't noticed much of a change.  The controls or the video on most of the embeded medial sites comes out all funky and/or doesn't work alt all.  See the attached youtube screen-shot.  Also, if I open more than 2 windows on the 64 bit version of firefox, the whole thing crashes.

Thanks for the help so far, any other advice?

-B

Controls should not be jumbled like that unless you are using Gnash. It's still being tested and has issues. Try Adobe only without Gnash on pc.

---

### Post by marmaladejackson on 2007-12-06
```
brian@brian-desktop:~$ cat /usr/local/bin/firefox32
#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
export GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders.32
linux32 /usr/local/firefox32/firefox $@
brian@brian-desktop:~$ 
```


I will uninstall gnash and see what happens on the 64bit version.  I don't think I'll have to re-install Ubuntu, even with all the chmods I've only been screwing with that directory and and associated files.  Everything else on the system works great.

---

### Post by bollix47 on 2007-12-06
Okay the following line appears to be trying to execute a folder which would explain the permission denied.

linux32 /usr/local/firefox32/firefox $@

Try changing it to 

linux32 /usr/local/firefox32/firefox/firefox $@

```
gksudo gedit /usr/local/bin/firefox32

```

---

### Post by marmaladejackson on 2007-12-06
Ha!  Clever!  I feel sooooo stupid, it is so obvious now that I look at it!  Looks like I am 90% back on track and only my quicktime plugin seems to be giving me trouble (see the attached screen shot).  Any suggestions on a plugin or something that will take care of it.  When I go to edit=>preferences=>content=>manage I can change settings for QT streams, but there isn't any .mov option.


Thanks everyone for your help.

---

### Post by bollix47 on 2007-12-07
Glad to hear it's working again.

As far as tikibartv I went there and the video did play using the mplayer plugin but I had to click on the play button a couple times before it started.  That site appears to have a flash problem which overlaps the mplayer but it did play.  Also,  I have no entry for mov type files under manage either but it didn't stop it from playing.

You may want to start a new thread if it doesn't work for you so that you get people with more expertise on that subject.

Good luck, I'm off for some much needed sleep. :)

---

### Post by marmaladejackson on 2007-12-07
Will do!  Thanks again!

---

