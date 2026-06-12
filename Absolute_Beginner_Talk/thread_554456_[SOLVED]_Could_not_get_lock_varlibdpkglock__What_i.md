---
title: "[SOLVED] Could not get lock /var/lib/dpkg/lock  What is this?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by curiousnoob on 2007-09-19
I was installing Compiz Fusion and afterword I was unable to open the Add/Remove program.  It says I have a broken link and I get this error in the console:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Anybody know what this is or how to fix it?

---

### Post by aquavitae on 2007-09-19
It usually means you have a package manager running.  Either you still have add/remove open, or you have synaptic open, or you are manually running the apt-get command.  If you're sure you don't have any of those running, then log out and log back in - hopefully it will kill whatever process is using the lock file.

---

### Post by curiousnoob on 2007-09-19
> **aquavitae said:**
> It usually means you have a package manager running.  Either you still have add/remove open, or you have synaptic open, or you are manually running the apt-get command.  If you're sure you don't have any of those running, then log out and log back in - hopefully it will kill whatever process is using the lock file.
I tried restarting my computer and when I tried again I got this message:
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Compiz Fusion also seems to have to be disabled now as well.

---

### Post by aquavitae on 2007-09-19
Hmm, sounds serious! Did you actually manage to restart then? 

Ok, try this. Open a terminal and type the following:
```
sudo apt-get update
```
If you get any sort of error, post the output of the command and the contents of the file /etc/apt/sources.list.  If it works then type the command```
sudo apt-get install -f
```

---

### Post by curiousnoob on 2007-09-19
The first line went through fine.  After the second line was put in I got this message at the end:

After unpacking 999kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  compiz-plugins
Install these packages without verification [y/N]? y
(Reading database ... 120970 files and directories currently installed.)
Unpacking compiz-plugins (from .../compiz-plugins_1%3a0.5.2+git20070829-0ubuntu1amaranth1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-plugins_1%3a0.5.2+git20070829-0ubuntu1amaranth1_i386.deb (--unpack):
 trying to overwrite `/usr/share/compiz/gconf.xml', which is also in package compiz-gnome
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-plugins_1%3a0.5.2+git20070829-0ubuntu1amaranth1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by splintercellguy on 2007-09-19
Try removing the compiz-plugins package, then reinstalling.

---

### Post by curiousnoob on 2007-09-19
> **splintercellguy said:**
> Try removing the compiz-plugins package, then reinstalling.
For some reason that seemed to work this time.  As far as I can tell everything works correctly.  There is one more thing though. It says I have one update and everytime I go through it all the messages say it updated but it keeps showing the same update that needs to be applied: 

compiz-core (version 1:0.5.2+git20070829-0ubuntu1amaranth1) will be upgraded to version                                          1:0.5.2+git20070829-0ubuntu1amaranth1

---

### Post by splintercellguy on 2007-09-19
It's an issue with the Amaranth repo I think, though I could be wrong.

---

### Post by curiousnoob on 2007-09-19
Just noticed something else odd.  When Compiz Fusion is enabled I can't resize or move any windows.

---

