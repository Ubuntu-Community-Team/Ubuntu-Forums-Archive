---
title: "I downloaded firefox-2.0.tar.gz... now how do i install it?"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Comrade42 on 2006-10-29
Um, I downloaded Firefox 2.0 for Linux and I got a whole bunch of files in some folders and I have no idea how to turn it all into a running Firefox 2.0. I would greatly appreciate some simple help.

---

### Post by DOD1951 on 2006-10-29
try this [http://www.ubuntuforums.org/showthread.php?t=248158&highlight=firefox+2]("http://www.ubuntuforums.org/showthread.php?t=248158&highlight=firefox+2")

Think you can miss out step 1 because you have already extracted the files.

---

### Post by Comrade42 on 2006-10-29
It has installed Firefox Beta 2... this isn't the newly-released version, is it?

---

### Post by taurus on 2006-10-29
If you have installed Edgy or upgraded to Edgy, then you have the final version of firefox 2.  Otherwise, you can download the latest version, 2, from here...

[http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/)

---

### Post by Comrade42 on 2006-10-29
Which leaves me with my original problem - I downloaded the file from there and now i have a "firefox-2.0.tar.gz" and I don't know how to install firefox 2 with it!

---

### Post by taurus on 2006-10-29
Move that somewhere in your home directory where you want to extract it.  For now, I assume you want to extract it in your ~/bin.

```

mkdir ~/bin
cd ~/Desktop
mv firefox-2.tar.gz ~/bin
cd ~/bin
tar xvzf firefox-2.tar.gz
ls -la
```
At this point, there will be a new directory called firefox-2 so change to that directory and show me the output of the last command below!

```

cd firefox-2
ls -la

```

---

### Post by Comrade42 on 2006-10-29
For the "ls -la" in the first code block, I get this:
(*Note: I replaced all "firefox-2" to "firefox-2.0" because that's that name of the file)
```
tom@tom-laptop:~/bin$ ls -la
total 9428
drwxr-xr-x  3 tom tom    4096 2006-10-28 22:28 .
drwxr-xr-x 41 tom tom    4096 2006-10-28 22:27 ..
drwxr-xr-x 12 tom tom    4096 2006-10-10 23:58 firefox
-rw-r--r--  1 tom tom 9622508 2006-10-28 22:15 firefox-2.0.tar.gz

```

I got that far, but then I tried the next step, here's what I see:

```
tom@tom-laptop:~/bin$ cd firefox-2.0
bash: cd: firefox-2.0: No such file or directory

```

---

### Post by Comrade42 on 2006-10-29
Actually, I went back and tried using "cd firefox", and it worked, so here's what I got for that:

```
tom@tom-laptop:~/bin$ cd firefox
tom@tom-laptop:~/bin/firefox$ ls -la
total 13632
drwxr-xr-x 12 tom tom     4096 2006-10-10 23:58 .
drwxr-xr-x  3 tom tom     4096 2006-10-28 22:28 ..
-rw-r--r--  1 tom tom        0 2006-10-10 23:57 .autoreg
-rw-r--r--  1 tom tom      230 2006-10-10 23:57 browserconfig.properties
drwxr-xr-x  3 tom tom     4096 2006-10-10 23:57 chrome
drwxr-xr-x  2 tom tom     4096 2006-10-10 23:57 components
drwxr-xr-x  5 tom tom     4096 2006-10-10 23:57 defaults
drwxr-xr-x  2 tom tom     4096 2006-10-10 23:57 dictionaries
drwxr-xr-x  5 tom tom     4096 2006-10-10 23:57 extensions
-rwxr-xr-x  1 tom tom     5239 2006-10-10 23:57 firefox
-rwxr-xr-x  1 tom tom 10501396 2006-10-10 23:57 firefox-bin
drwxr-xr-x  2 tom tom     4096 2006-10-10 23:57 greprefs
drwxr-xr-x  2 tom tom     4096 2006-10-10 23:57 icons
-rw-r--r--  1 tom tom      476 2006-10-10 23:58 libfreebl3.chk
-rwxr-xr-x  1 tom tom   231468 2006-10-10 23:57 libfreebl3.so
-rwxr-xr-x  1 tom tom   627932 2006-10-10 23:57 libmozjs.so
-rwxr-xr-x  1 tom tom   176236 2006-10-10 23:57 libnspr4.so
-rwxr-xr-x  1 tom tom   430608 2006-10-10 23:57 libnss3.so
-rwxr-xr-x  1 tom tom   260832 2006-10-10 23:57 libnssckbi.so
-rwxr-xr-x  1 tom tom    15304 2006-10-10 23:57 libplc4.so
-rwxr-xr-x  1 tom tom     8240 2006-10-10 23:57 libplds4.so
-rwxr-xr-x  1 tom tom   138316 2006-10-10 23:57 libsmime3.so
-rw-r--r--  1 tom tom      476 2006-10-10 23:57 libsoftokn3.chk
-rwxr-xr-x  1 tom tom   304292 2006-10-10 23:57 libsoftokn3.so
-rwxr-xr-x  1 tom tom   152456 2006-10-10 23:57 libssl3.so
-rwxr-xr-x  1 tom tom    94892 2006-10-10 23:57 libxpcom_compat.so
-rwxr-xr-x  1 tom tom   698512 2006-10-10 23:57 libxpcom_core.so
-rwxr-xr-x  1 tom tom     9240 2006-10-10 23:57 libxpcom.so
-rwxr-xr-x  1 tom tom     8284 2006-10-10 23:57 libxpistub.so
-rwxr-xr-x  1 tom tom    10336 2006-10-10 23:57 mozilla-xremote-client
drwxr-xr-x  2 tom tom     4096 2006-10-10 23:57 plugins
-rw-r--r--  1 tom tom      177 2006-10-10 23:57 readme.txt
-rwxr-xr-x  1 tom tom     2148 2006-10-10 23:57 removed-files
drwxr-xr-x  6 tom tom     4096 2006-10-10 23:57 res
-rwxr-xr-x  1 tom tom    10492 2006-10-10 23:57 run-mozilla.sh
drwxr-xr-x  2 tom tom     4096 2006-10-10 23:57 searchplugins
-rwxr-xr-x  1 tom tom    67496 2006-10-10 23:57 updater
-rw-r--r--  1 tom tom      145 2006-10-10 23:57 updater.ini
-rwxr-xr-x  1 tom tom    21368 2006-10-10 23:57 xpicleanup

```

---

### Post by taurus on 2006-10-29
> **Comrade42 said:**
> Actually, I went back and tried using "cd firefox", and it worked, so here's what I got for that:

```
tom@tom-laptop:~/bin$ cd firefox
tom@tom-laptop:~/bin/firefox$ ls -la
total 13632
drwxr-xr-x 12 tom tom     4096 2006-10-10 23:58 .
drwxr-xr-x  3 tom tom     4096 2006-10-28 22:28 ..
-rw-r--r--  1 tom tom        0 2006-10-10 23:57 .autoreg
-rw-r--r--  1 tom tom      230 2006-10-10 23:57 browserconfig.properties
drwxr-xr-x  3 tom tom     4096 2006-10-10 23:57 chrome
drwxr-xr-x  2 tom tom     4096 2006-10-10 23:57 components
drwxr-xr-x  5 tom tom     4096 2006-10-10 23:57 defaults
drwxr-xr-x  2 tom tom     4096 2006-10-10 23:57 dictionaries
drwxr-xr-x  5 tom tom     4096 2006-10-10 23:57 extensions
-rwxr-xr-x  1 tom tom     5239 2006-10-10 23:57 firefox
-rwxr-xr-x  1 tom tom 10501396 2006-10-10 23:57 firefox-bin
drwxr-xr-x  2 tom tom     4096 2006-10-10 23:57 greprefs
drwxr-xr-x  2 tom tom     4096 2006-10-10 23:57 icons
-rw-r--r--  1 tom tom      476 2006-10-10 23:58 libfreebl3.chk
-rwxr-xr-x  1 tom tom   231468 2006-10-10 23:57 libfreebl3.so
-rwxr-xr-x  1 tom tom   627932 2006-10-10 23:57 libmozjs.so
-rwxr-xr-x  1 tom tom   176236 2006-10-10 23:57 libnspr4.so
-rwxr-xr-x  1 tom tom   430608 2006-10-10 23:57 libnss3.so
-rwxr-xr-x  1 tom tom   260832 2006-10-10 23:57 libnssckbi.so
-rwxr-xr-x  1 tom tom    15304 2006-10-10 23:57 libplc4.so
-rwxr-xr-x  1 tom tom     8240 2006-10-10 23:57 libplds4.so
-rwxr-xr-x  1 tom tom   138316 2006-10-10 23:57 libsmime3.so
-rw-r--r--  1 tom tom      476 2006-10-10 23:57 libsoftokn3.chk
-rwxr-xr-x  1 tom tom   304292 2006-10-10 23:57 libsoftokn3.so
-rwxr-xr-x  1 tom tom   152456 2006-10-10 23:57 libssl3.so
-rwxr-xr-x  1 tom tom    94892 2006-10-10 23:57 libxpcom_compat.so
-rwxr-xr-x  1 tom tom   698512 2006-10-10 23:57 libxpcom_core.so
-rwxr-xr-x  1 tom tom     9240 2006-10-10 23:57 libxpcom.so
-rwxr-xr-x  1 tom tom     8284 2006-10-10 23:57 libxpistub.so
-rwxr-xr-x  1 tom tom    10336 2006-10-10 23:57 mozilla-xremote-client
drwxr-xr-x  2 tom tom     4096 2006-10-10 23:57 plugins
-rw-r--r--  1 tom tom      177 2006-10-10 23:57 readme.txt
-rwxr-xr-x  1 tom tom     2148 2006-10-10 23:57 removed-files
drwxr-xr-x  6 tom tom     4096 2006-10-10 23:57 res
-rwxr-xr-x  1 tom tom    10492 2006-10-10 23:57 run-mozilla.sh
drwxr-xr-x  2 tom tom     4096 2006-10-10 23:57 searchplugins
-rwxr-xr-x  1 tom tom    67496 2006-10-10 23:57 updater
-rw-r--r--  1 tom tom      145 2006-10-10 23:57 updater.ini
-rwxr-xr-x  1 tom tom    21368 2006-10-10 23:57 xpicleanup

```
Okay, so it creates a directory called firefox instead of firefox.  Looks like you have three options to run it!!!  

```
./run-mozzila.sh
-or-
./firefox
-or-
./firefox-bin
```

---

### Post by Comrade42 on 2006-10-29
Haha, yes, alright it finally worked after I did some weird stuffs and stuff. I had to close firefox and reopen it before it would work right (actually, that step should have been obvious to me, but whatever.)

Thanks for the help!

---

### Post by taurus on 2006-10-29
> **Comrade42 said:**
> Haha, yes, alright it finally worked after I did some weird stuffs and stuff. I had to close firefox and reopen it before it would work right (actually, that step should have been obvious to me, but whatever.)

Thanks for the help!
So you did some weird stuff and stuff, eh!  I assume the first command, ./run-mozilla.sh, is the one!

---

### Post by comfortablynumb on 2006-10-29
I'm having the same problems, I followed the steps mentioned on page 1, the only command that will work is ./firefox

If I type ./run-mozilla.sh it returns an error run-mozilla.sh:cannot execute.

If I close the firefox 2.0 window and try to relaunch it from the system menu it launches 1.5 ](*,) 

Is there anyway to officially install it?

---

### Post by taurus on 2006-10-29
> **comfortablynumb said:**
> I'm having the same problems, I followed the steps mentioned on page 1, the only command that will work is ./firefox

If I type ./run-mozilla.sh it returns an error run-mozilla.sh:cannot execute.

Check to make sure you have an executable permission for it!

```
chmod 755 run-mozilla.sh
```

> If I close the firefox 2.0 window and try to relaunch it from the system menu it launches 1.5 ](*,) 

Is there anyway to officially install it?

You can create a short cut in the panel to point to your firefox 2.0.  Place a cursor on the panel and click the right button.  Pick the first option in that window (add apps to panel or something similar to that) and create a new launch.  Then, browse to where your firefox 2.0 is for the "command" field...

---

### Post by aysiu on 2006-10-29
You could use this script to install Firefox 2.0...
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

It may save you copying and pasting a few commands...

---

### Post by comfortablynumb on 2006-10-29
I changed the permissions on the file and it returns the same error, I changed the permissions on bin to 755 also and it returned the same error. :confused:

---

### Post by taurus on 2006-10-29
Then don't worry about run-mozilla.sh.  Just run firefox in that directory if you want to use version 2.0.

---

### Post by comfortablynumb on 2006-10-29
> **aysiu said:**
> You could use this script to install Firefox 2.0...
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

It may save you copying and pasting a few commands...

Cool thanks the script worked :)

---

