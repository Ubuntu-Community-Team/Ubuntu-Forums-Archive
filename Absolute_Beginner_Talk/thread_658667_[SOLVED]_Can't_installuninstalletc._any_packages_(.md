---
title: "[SOLVED] Can't install/uninstall/etc. any packages (Gutsy)"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by ihatetomarnold on 2008-01-04
I've been having a real headache of an issue the past few days, being unable to install or uninstall anything.  I can't use the terminal or update manager or Synaptic.  

If I use update manager I receive this error
> Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.


I open Synaptic and and receive a broken package error.  "exim4-base" is broken.  I mark it for reinstallation and get the error
> E: tzdata: subprocess post-installation script returned error exit status 2


I click ok and then "details".  It tells me (see screenshots... couldn't copy-paste):
[http://picasaweb.google.com/ihatetomarnold/Screenshots/photo#5151825283236142658](http://picasaweb.google.com/ihatetomarnold/Screenshots/photo#5151825283236142658)
[http://picasaweb.google.com/ihatetomarnold/Screenshots/photo#5151825287531109970](http://picasaweb.google.com/ihatetomarnold/Screenshots/photo#5151825287531109970)

I run sudo apt-get install -f in the terminal and am told
> richard@computah:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  exim4-config
The following NEW packages will be installed:
  exim4-config
0 upgraded, 1 newly installed, 0 to remove and 30 not upgraded.
4 not fully installed or removed.
Need to get 0B/258kB of archives.
After unpacking 889kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: Perl may be unconfigured (Can't locate Debconf/Config.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
Setting up tzdata (2007k-0ubuntu0.7.10) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)


From this point, I have no idea what to do.  I've only been using Ubuntu for about 3 or 4 months now, and its my introduction to Linux, as well.  

If I've forgotten any information please let me know and I'll gather it.  Thanks in advance to anyone who helps!

---

### Post by Sef on 2008-01-04
Have you tried this command:

```
sudo dpkg-reconfigure exim4-config
```

---

### Post by bwtranch on 2008-01-04
Try this run sudo gedit /var/lib/dpkg/status and see if there are any packages that failed to install. Delete those entries and save. If you have any problems, post the output and I will try to help.

---

### Post by Xavieran on 2008-01-04
Try running sudo dpkg --configure -a
That has fixed a few broken package issues for me in the past

---

### Post by perlluver on 2008-01-04
Also check your time zone.  If your time zone is messed up it will not let you update.  That tzdata stands for Time Zone Data.  Another person had almost the same time and his time zone was set to Eastern and he was in Europe.

---

### Post by ihatetomarnold on 2008-01-05
Thanks to all of you for your input.  Unfortunately, I'm still stuck.  Here's what happened when I tried your suggestions:

Sef -  this is the output I got
> 
richard@computah:~$ sudo dpkg-reconfigure exim4-config

[sudo] password for richard:

Can't locate Debconf/Db.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/dpkg-reconfigure line 9.

BEGIN failed--compilation aborted at /usr/sbin/dpkg-reconfigure line 9.


bwtranch -  I couldn't find the word "failed" anywhere in the file, but here is what I have in it:  [http://ihatetomarnold.googlepages.com/status.txt](http://ihatetomarnold.googlepages.com/status.txt)


Xaverian - I got this output
> richard@computah:~$ sudo dpkg --configure -a

dpkg: dependency problems prevent configuration of exim4-base:

 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however:

  Package exim4-config is not installed.

  Package exim4-config-2 is not installed.

dpkg: error processing exim4-base (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of exim4-daemon-light:

 exim4-daemon-light depends on exim4-base (>= 4.67); however:

  Package exim4-base is not configured yet.

dpkg: error processing exim4-daemon-light (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of mailx:

 mailx depends on exim4 | mail-transport-agent; however:

  Package exim4 is not installed.

  Package mail-transport-agent is not installed.

  Package exim4-daemon-light which provides mail-transport-agent is not configured yet.

dpkg: error processing mailx (--configure):

 dependency problems - leaving unconfigured

Errors were encountered while processing:

 exim4-base

 exim4-daemon-light

 mailx


perlluver - I am located in West Virginia, USA.  I have my time zone set to America/New_York.  

Hopefully this information will lead someone to understand what the issue is.  Thanks again for your help, I look forward to your ideas.

---

### Post by geirha on 2008-01-05
Does this show any errors? ```
sudo aptitude update
```

Also it complains that perl might be unconfigured, try ```
sudo dpkg-reconfigure perl
```

---

### Post by ihatetomarnold on 2008-01-05
> **geirha said:**
> Does this show any errors? ```
sudo aptitude update
```

Also it complains that perl might be unconfigured, try ```
sudo dpkg-reconfigure perl
```

"Sudo aptitude update"  simply updated and said "done".

The perl command gave me
> richard@computah:~$ sudo dpkg-reconfigure perl
Can't locate Debconf/Db.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/dpkg-reconfigure line 9.
BEGIN failed--compilation aborted at /usr/sbin/dpkg-reconfigure line 9.


Thanks for your help, though.  Any other ideas?

---

### Post by geirha on 2008-01-05
> Can't locate Debconf/Db.pm
That file should be located at  /usr/share/perl5/Debconf/Db.pm. Does it exist?
```
ls -l /usr/share/perl5/Debconf/Db.pm
```

---

### Post by ihatetomarnold on 2008-01-05
> **geirha said:**
> That file should be located at  /usr/share/perl5/Debconf/Db.pm. Does it exist?
```
ls -l /usr/share/perl5/Debconf/Db.pm
```

No, it does not.  How do I correct this?

> ls: /usr/share/perl5/Debconf/Db.pm: No such file or directory


---

### Post by geirha on 2008-01-05
A better question is, how did it disappear? Have you run any delete (rm) commands as root (with sudo) lately? or uninstalled any packages you can remember? Has there been any errors on the filesystem lately?

The file is part of the debconf package, and obviously, without it, you can't install any packages, so I'm thinking the best way might be booting the ubuntu CD, mount your partition(s), and try to install the package using the dpkg on the CD.

If the /usr dir is on the / partition (a common setup if you haven't partitioned manually), and you mount that partition as /media/disk, then the following command will hopefully reinstall the package:
```
sudo aptitude download debconf
sudo dpkg --root=/media/disk -i debconf*.deb
```

I haven't tested this myself, this is based on reading the man-pages for aptitude and dpkg, so I can't guarantee it will work. If it doesn't, paste the output here, and we might be able to tweak the commands to work.

Oh and to mount the partition, open nautilus (the file browser) by going to the home-folder or wherever from the places menu, then in the left margin, you should see all your partitions listed by size. Double clicking an entry there will mount it.

---

### Post by ihatetomarnold on 2008-01-06
This is what the terminal output was

> ubuntu@ubuntu:~$ sudo dpkg --root=/media/disk -i debconf*.deb
(Reading database ... 104613 files and directories currently installed.)
Preparing to replace debconf 1.5.14ubuntu1 (using debconf_1.5.14ubuntu1_all.deb) ...
xargs: /dev/null: Permission denied
Unpacking replacement debconf ...
Setting up debconf (1.5.14ubuntu1) ...
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied


What now?  Thank you all again for your help, I really mean it.

---

### Post by geirha on 2008-01-06
Those /dev/null permission denied messages are puzzling, but, if you're still on the ubuntu cd, see if the file exist with ```
ls -l /media/disk/usr/share/perl5/Debconf/Db.pm
```

If you've booted back to your regular system, do the same with ```
ls -l /usr/share/perl5/Debconf/Db.pm
```

If it's there, try installing a package again ...

---

### Post by ihatetomarnold on 2008-01-06
I just logged back into my normal Ubuntu and was able to run the update manager successfully and Synaptic no longer gives me a broken message!  Thank you so much for all your help!  I still have no idea what caused this issue, but I'm glad you guys all offered your expertise.  I think this is why I love Ubuntu. :)

---

### Post by geirha on 2008-01-06
Happy to hear it worked! I was actually expecting there to be more problems like other broken packages or something, but now that dpkg is working again, such problems will most likely be fixed by reinstalling/reconfiguring such a package if it manifests itself. 

Anyway, could you mark the thread as solved? Thread Tools -> Mark as solved or something like that near the top of this page.

---

### Post by ihatetomarnold on 2008-01-06
> **geirha said:**
> Anyway, could you mark the thread as solved? Thread Tools -> Mark as solved or something like that near the top of this page.

Done and done.  Thanks again!

---

