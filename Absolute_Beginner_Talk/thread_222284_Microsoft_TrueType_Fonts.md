---
title: "Microsoft TrueType Fonts?"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-07-24
Hi,

I know there is a package called something like ***ttf-core-microsoft*** or something similar which is supposed to install the core Microsoft TrueType Fonts but I don't seem to find it in Synaptic.

And yes, I do have ***universe*** and ***multiverse*** enabled in my ***sources.list*** but maybe I'm missing an entry all together, I don't know. Feel free to post your ***sources.list*** if you think this will help.

Yet, when I used to have KDE I think I had this package listed in Adept from the start. 

Anyone any ideas how I could get hold of this package?

Thanks

---

### Post by Jagot on 2006-07-24
```
sudo aptitude update && sudo aptitude install msttcorefonts
```

It is in the multiverse repo.

---

### Post by ovimunt on 2006-07-24
Got it, it's downloading now. ;) 

Thanks

---

### Post by Bicycle Repairman on 2006-07-25
tgrayz@ipaq2:~$ sudo aptitude update && sudo aptitude install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Fetched 5B in 16s (0B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up msttcorefonts (1.2ubuntu3) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--07:57:36--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--07:57:46--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--07:57:56--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--07:58:07--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--07:58:17--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--07:58:27--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up msttcorefonts (1.2ubuntu3) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--07:58:55--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--07:59:05--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--07:59:15--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--07:59:25--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--07:59:35--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--07:59:45--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
This is what I get whenever I try to install this package. Any ideas what I'm doing wrong? Thanks in advance.
Tim

---

### Post by jimmygoon on 2006-07-25
You're not doing anything wrong unless you're some how bringing down sourceforge ;):D

Just give it a while, sf.net will be back up and that should work

---

### Post by Bicycle Repairman on 2006-07-25
Gotcha... it's just been this way for a while now. Good to know that I've not blown something up.

---

### Post by finferflu on 2006-07-25
I think I've got universe and multiverse enabled in my sources.list, since I've enabled everything (but I'm not sure if there is anything extra to add in the list). 

this is my output:

```
mmanu@scatolina:~$ sudo aptitude update && sudo aptitude install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 http://gb.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://gb.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:3 http://gb.archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://gb.archive.ubuntu.com dapper Release
Get:4 http://gb.archive.ubuntu.com dapper-updates Release [30.9kB]
Get:5 http://gb.archive.ubuntu.com dapper-backports Release [14.9kB]
Hit http://gb.archive.ubuntu.com dapper/main Packages
Hit http://gb.archive.ubuntu.com dapper/restricted Packages
Hit http://gb.archive.ubuntu.com dapper/main Sources
Hit http://gb.archive.ubuntu.com dapper/restricted Sources
Hit http://gb.archive.ubuntu.com dapper/universe Packages
Hit http://gb.archive.ubuntu.com dapper/universe Sources
Get:6 http://gb.archive.ubuntu.com dapper-updates/main Packages [43.0kB]
Get:7 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:8 http://security.ubuntu.com dapper-security Release [30.9kB]
Get:9 http://gb.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:10 http://gb.archive.ubuntu.com dapper-updates/main Sources [25.0kB]
Get:11 http://security.ubuntu.com dapper-security/main Packages [40.4kB]
Get:12 http://security.ubuntu.com dapper-security/restricted Packages [4275B]
Get:13 http://security.ubuntu.com dapper-security/main Sources [9872B]
Get:14 http://security.ubuntu.com dapper-security/restricted Sources [974B]
Get:15 http://security.ubuntu.com dapper-security/universe Packages [6951B]
Get:16 http://security.ubuntu.com dapper-security/universe Sources [902B]
Get:17 http://gb.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Fetched 209kB in 4s (46.2kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No candidate version found for msttcorefonts
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

mmanu@scatolina:~$ apt-cache policy msttcorefonts
msttcorefonts:
  Installed: (none)
  Candidate: (none)
  Version table:
```

It doesn't seem to work for me...


----edit----

I found out the problem: I didn't have some lines into my sources.list to start with, so I had to add the following:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

And everything worked alright.

---

### Post by whein on 2006-07-28
So I went to go install the msttcorefonts deb package from [http://packages.ubuntu.com/dapper/x11/msttcorefonts](http://packages.ubuntu.com/dapper/x11/msttcorefonts) and it gave me the the following output:

> 	whein@HappyDrive1:~$ sudo apt-get install msttcorefonts
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
	platform compatibility".  This is no longer the case, but they are
	still available from third parties.
	
	You are free to download these fonts and use them for your own use,
	but you may not redistribute them in modified form, including changes
	to the file name or packaging format.
	--20:39:24--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
	           => `./andale32.exe'
	Resolving belnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
	--20:39:24--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
	           => `./andale32.exe'
	Resolving easynews.dl.sourceforge.net... failed: Temporary failure in name resolution.
	--20:39:24--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
	           => `./andale32.exe'
	Resolving twtelecom.dl.sourceforge.net... failed: Temporary failure in name resolution.
	--20:39:24--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
	           => `./andale32.exe'
	Resolving aleron.dl.sourceforge.net... failed: Temporary failure in name resolution.
	--20:39:24--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
	           => `./andale32.exe'
	Resolving cesnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
	--20:39:24--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
	           => `./andale32.exe'
	Resolving switch.dl.sourceforge.net... failed: Temporary failure in name resolution.
	andale32.exe: No such file or directory
	
	All done, errors in processing 1 file(s)
	dpkg: error processing msttcorefonts (--configure):
	 subprocess post-installation script returned error exit status 1
	Errors were encountered while processing:
	 msttcorefonts
	E: Sub-process /usr/bin/dpkg returned an error code (1)


I understand the problems connecting to the various servers since this machine does not have an internet connection yet.  But what the heck do I do about the "uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108" and the rest?  Also, for the internet connections, can I just download those files manually from another computer, copy them over and execute them?  They look like Windows files since they have .exe extensions.  How do I use them on Ubuntu?

---

### Post by A2A on 2006-07-28
> sudo aptitude update && sudo aptitude install msttcorefonts 
Thanks Jagot.  It worked well for me :p

A2A

---

### Post by whein on 2006-08-05
/bump

I'm still getting the ```
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
```error every time I try to install the msttfcore package, and if I leave it partially installed it retries every time I use apt-get install to install anything else until I uninstall it.  Once again, I have downloaded all the .exe files manually on another machine, but the target system does not have an internet connection.  Anyone know how I can proceed?
-Will

---

### Post by penquin on 2006-08-05
I know you need wine to use the fonts and if you goto the howto setup wine forum it explains how to download them, but I am trying to find out how to put the fonts to use in openoffice

---

### Post by ovimunt on 2006-08-05
Whoa??? You DON'T need wine to use the fonts!!!

If you install them properly they should just show up in OpenOffice or any other application.

---

