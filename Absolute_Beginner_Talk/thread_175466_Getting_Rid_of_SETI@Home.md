---
title: "Getting Rid of SETI@Home"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by CybaCowboy on 2006-05-13
When trying to install SETI@Home, I was told that the program would automatically download additonal components (namely setiathome-3.08.i686-pc-linux-gnu.tar) during the installation, which it preceeded to do using Terminal...

However, after four attempts (which last up to 10 minutes each!) this file never actually downloads and I am left with time-out errors.

To make matters worse, whenever I add software now, Ubuntu picks-up where it left off, trying to download setiathome-3.08.i686-pc-linux-gnu.tar again; if I forcibly close Terminal, it spits the dummy the next time I go into a package manager!


Can someone either help me download the additional components needed for SETI@Home, or remove it completely so that it does not try to download these components everytime I open a package manager?

---

### Post by louis_nichols on 2006-05-13
Just use the command

sudo apt-get remove setiathome

Then things will back to normal. You won't have setiathome installed, tho. But, then again, it doesn't seem to be possible using the deb. Try visiting their home page and see what other way there is.

EDIT: typo

---

### Post by Resurrection on 2006-05-13
Could this be a repository problem since SETI's old software stopped being used in December 2005 and now they have that new software?  

Also have you looked into [Folding@home]("http://ubuntuforums.org/showthread.php?t=102313&highlight=folding")?

---

### Post by louis_nichols on 2006-05-13
I believe that, indeed, someone didn't get the chance to either update the package or simply remove it from the repos, if it's not needed anymore. You can file a bug report, i guess, but I don't think it's that important, since the issue is easily solved.

---

### Post by CybaCowboy on 2006-05-13
When I tried to remove SETI@Home:
*sudo apt-get remove setiathome*


I am told:
*E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.*


Of course *doing* this starts trying to download SETI@Home's missing components:
[i]Setting up setiathome (3.08-4) ...
setiathome-3.08.i686-pc-linux-gnu.tar not found in /tmp.
--01:36:09--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar)
           => `/tmp/filewIeLx2'
Resolving alien.ssl.berkeley.edu... 128.32.18.176
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21...[/i]


Which we *know* will never come:
[i]failed: Connection timed out.
Retrying.[/i]


Any ideas?

---

### Post by louis_nichols on 2006-05-13
Strange... I replicated the situation and it worked for me. Do this then:

sudo apt-get -f install

---

### Post by CybaCowboy on 2006-05-13
[i]cowboy@kubuntu:~$ sudo apt-get -f install
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.[/i]

---

### Post by louis_nichols on 2006-05-13
ok. Then run ```
sudo dpkg --configure -a
``` I've seen this before and, well, sorry for not paying more attention to your previous post, but the obvious does work.

---

### Post by CybaCowboy on 2006-05-13
[i]cowboy@kubuntu:~$ sudo dpkg --configure -a
Password:
Setting up setiathome (3.08-4) ...
setiathome-3.08.i686-pc-linux-gnu.tar not found in /tmp.
--02:24:15--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar)
           => `/tmp/file7WxyN4'
Resolving alien.ssl.berkeley.edu... 128.32.18.176
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21...[/i]


It just keeps timing out, then trying to download the file again, then timing out and so forth.

I'm going to bed now, so I'll leave it running while I'm asleep, check it in the morning, try *sudo apt-get remove setiathome* and then post my results...

---

### Post by Resurrection on 2006-05-13
I had a problem with a different package like this once, I know how to get rid of it, but its technical, and I have to find that thread again.  I should have the answer up soon.  There is a file for dpkg you must manually edit to remove it.

---

### Post by CybaCowboy on 2006-05-13
This is what I got:


[i]cowboy@kubuntu:~$ sudo dpkg --configure -a
Password:
Setting up setiathome (3.08-4) ...
setiathome-3.08.i686-pc-linux-gnu.tar not found in /tmp.
--02:24:15--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar)
           => `/tmp/file7WxyN4'
Resolving alien.ssl.berkeley.edu... 128.32.18.176
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Connection timed out.
Retrying.

--02:29:26--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar)
  (try: 2) => `/tmp/file7WxyN4'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Connection timed out.
Retrying.

--02:34:37--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar)
  (try: 3) => `/tmp/file7WxyN4'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Connection timed out.
Retrying.

--02:39:49--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar)
  (try: 4) => `/tmp/file7WxyN4'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Connection timed out.
Retrying.

--02:45:02--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar)
  (try: 5) => `/tmp/file7WxyN4'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Connection timed out.
Retrying.

--02:50:16--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar)
  (try: 6) => `/tmp/file7WxyN4'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Network is unreachable.
dpkg: error processing setiathome (--configure):
 subprocess post-installation script returned error exit status 1
Setting up mozilla-thunderbird (1.0.8-0ubuntu05.10.1) ...
Updating mozilla-thunderbird chrome registry...find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

done.

Errors were encountered while processing:
 setiathome
cowboy@kubuntu:~$ sudo apt-get remove setiathome
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  setiathome
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 73.7kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 67976 files and directories currently installed.)
Removing setiathome ...[/i]


Well it *appears* to have successfully removed SETI@Home...

---

### Post by louis_nichols on 2006-05-13
I assure you it has. :)

---

### Post by CybaCowboy on 2006-05-13
[QUOTE=louis_nichols]I assure you it has. :)[/QUOTE]

Thank God for that!

The amount of trouble SETI@Home caused me...](*,)

---

