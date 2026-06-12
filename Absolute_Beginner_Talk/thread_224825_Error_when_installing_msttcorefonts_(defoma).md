---
title: "Error when installing msttcorefonts (defoma?)"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by whein on 2006-07-28
Sorry for posting twice, the old thread seems to have passed into dormancy.

I went to go install the msttcorefonts deb package from [http://packages.ubuntu.com/dapper/x11/msttcorefonts](http://packages.ubuntu.com/dapper/x11/msttcorefonts) and it gave me the the following output:

> whein@HappyDrive1:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
msttcorefonts
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/22.5kB of archives.
After unpacking 168kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
msttcorefonts
Install these packages without verification [y/N]? y
Preconfiguring packages ...
Selecting previously deselected package msttcorefonts.
(Reading database ... 126811 files and directories currently installed.)
Unpacking msttcorefonts (from .../msttcorefonts_1.2ubuntu3_all.deb) ...
Setting up msttcorefonts (1.2ubuntu3) ...
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility". This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--20:39:24-- [http://belnet.dl.sourceforge.net/sou...s/andale32.exe](http://belnet.dl.sourceforge.net/sou...s/andale32.exe)
=> `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
--20:39:24-- [http://easynews.dl.sourceforge.net/s...s/andale32.exe](http://easynews.dl.sourceforge.net/s...s/andale32.exe)
=> `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Temporary failure in name resolution.
--20:39:24-- [http://twtelecom.dl.sourceforge.net/...s/andale32.exe](http://twtelecom.dl.sourceforge.net/...s/andale32.exe)
=> `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Temporary failure in name resolution.
--20:39:24-- [http://aleron.dl.sourceforge.net/sou...s/andale32.exe](http://aleron.dl.sourceforge.net/sou...s/andale32.exe)
=> `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Temporary failure in name resolution.
--20:39:24-- [http://cesnet.dl.sourceforge.net/sou...s/andale32.exe](http://cesnet.dl.sourceforge.net/sou...s/andale32.exe)
=> `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
--20:39:24-- [http://switch.dl.sourceforge.net/sou...s/andale32.exe](http://switch.dl.sourceforge.net/sou...s/andale32.exe)
=> `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Temporary failure in name resolution.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

I understand the problems connecting to the various servers since this machine does not have an internet connection yet. But what the heck do I do about the "uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108" and the rest? I'm 99% sure I have defoma installed and happy, but was I supposed to configure it?  Also, for the download requests, can I just download those files manually from another computer, copy them over and execute them? They look like Windows files since they have .exe extensions. How do I use them on Ubuntu?

---

### Post by ovimunt on 2006-07-28
You cannot install the fonts without an internet connection.

These are not part of the Ubuntu package so they won't be anywhere on your drive or on the installation disc.

---

### Post by whein on 2006-07-28
ovimunt:
I have so far been able to download all the .deb files and other stuff I need to a USB drive, copy them over to the Ubuntu machine and get them listed into Synaptic/apt.  I've installed a bunch of games and utilities that are not on the original install CD.  Does this particular .deb package require an internet connection or can I put the above mentioned .exe files somewhere on the machine and redirect it?  I already have the files downloaded on the USB drive.

Beyond that, does anyone know what the > Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108. errors mean and what I need to do to fix that?  Thanks in advance for the help.
-Will

---

### Post by ovimunt on 2006-07-28
I don't really know...

I've had an internet connection from the very begining of my linux aventure and all I've learned so far is dependent on it. I'd be totaly stuck if I din't have internet.

---

