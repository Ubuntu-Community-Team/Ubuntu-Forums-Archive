---
title: "CUPS problem"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by lemmy999 on 2006-01-27
I'm trying to install my Canon ip1000 printer. I have found what appear to be good drivers and instructions at

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus25.html](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus25.html).

Part of the howto says "Before installation of my packages, make sure that cupsys on your system works fine" How do i do that?

---

### Post by bscbrit on 2006-01-27
There is probably a much simpler way of doing this, but here is one solution:

Confirm that cupsys is installed.  You can use Synaptic or whatever other method that you usually use to install software.  If in doubt 'sudo apt-get install cupsys' will either install it or tell you that it is already installed.

Make sure that cupsys is running:

sudo /etc/init.d/cupsys start

Thats it!

---

### Post by lemmy999 on 2006-01-27
OK
Think I've done that and CUPS is working. Proceeded with install but get the following output

chris@ubuntuchris:~$ sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
Reading package lists... Done
Building dependency tree... Done
Package libcnbj-2.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libcnbj-2.5 has no installation candidate


Any thoughts? Do I need to find another source for the missing file? I assume its not in any of the Ubuntu repositories. 

Chris

---

### Post by bscbrit on 2006-01-27
I cannot find it in any of the usual repos.  You may be faced with quite a long search to find all of the necessary dependancies required to get the printer working.  On the other hand, once you have installed  libcnbj-2.5 you might simply find that everything works as expected.

There is not a lot of assistance that I can offer - this is a Canon-specific problem and not really related to Ubuntu - but if you give it a shot and return to this forum when (if?) you have specific problems then I'm sure that I or someone else will be able to help.

Good Luck

---

### Post by bscbrit on 2006-01-27
Try these links:

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus25.html](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus25.html)

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian/libcnbj-2.5-0/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian/libcnbj-2.5-0/)

---

### Post by lemmy999 on 2006-01-27
Aha

Sorted first problem- hadn't edited repo listing to include this one. Have corrected that, updated and tried again. Now the output is

Preconfiguring packages ...
(Reading database ... 76436 files and directories currently installed.)
Unpacking libcnbj-2.5 (from .../libcnbj-2.5_0-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libcnbj-2.5_0-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libcnbpess214.so.2.0.5', which is also in package bjfilter-pixmaip1500
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking pstocanonbj (from .../pstocanonbj_3.0-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/pstocanonbj_3.0-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/cups/filter/pstocanonbj', which is also in package bjfilter-common
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
Errors were encountered while processing:
 /var/cache/apt/archives/libcnbj-2.5_0-1_i386.deb
 /var/cache/apt/archives/pstocanonbj_3.0-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Is it a case of starting again from scratch or can i retrieve this?

---

### Post by bscbrit on 2006-01-27
It might be retrievable - but I haven't a clue how to do it!

My suggestion - which might not be worth very much - would be to open Synaptic, do a 'reload' and then "Edit -> fix broken packages".  It might work, there again.....:(

---

