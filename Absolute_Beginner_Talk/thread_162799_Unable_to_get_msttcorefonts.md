---
title: "Unable to get msttcorefonts"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Danny Boy on 2006-04-19
I just installed Dapper 6.06,  I'm trying to update and add all the programs I had in Breezy. 

Whenever I try and download the msttcorefonts, here is what I get:

```

dan@puppy:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  cabextract
The following NEW packages will be installed
  cabextract msttcorefonts
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 66.8kB of archives.
After unpacking 315kB of additional disk space will be used.
Do you want to continue [Y/n]?
Get: 1 http://archive.ubuntu.com dapper/universe cabextract 1.1-1 [44.7kB]
Get: 2 http://archive.ubuntu.com dapper/multiverse msttcorefonts 1.2ubuntu2 [22.1kB]
Fetched 66.8kB in 15s (4247B/s)
Preconfiguring packages ...
Selecting previously deselected package cabextract.
(Reading database ... 66440 files and directories currently installed.)
Unpacking cabextract (from .../cabextract_1.1-1_i386.deb) ...
Selecting previously deselected package msttcorefonts.
Unpacking msttcorefonts (from .../msttcorefonts_1.2ubuntu2_all.deb) ...
Setting up cabextract (1.1-1) ...
Setting up msttcorefonts (1.2ubuntu2) ...
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
--17:29:09--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--17:29:20--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--17:29:30--  http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--17:29:40--  http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--17:29:50--  http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--17:30:00--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It seems to me the sourceforge serveres are timing out. Is this a problem because I'm using dapper? Workaround? IPv6 is disabled by the way if that would have anything to do with it.

---

### Post by angkor on 2006-04-19
I get no response when pinging cesnet.dl.sourceforge.net. The server is probably down or something or there's some other problem.

Read this thread if you want to install the fonts manually:

[http://ubuntuforums.org/showthread.php?t=76655&page=2](http://ubuntuforums.org/showthread.php?t=76655&page=2)

---

### Post by ComplexNumber on 2006-04-19
alternatively, grab them from [here]("http://www.gnome-look.org/content/show.php?content=19259"), open up the gnome control centre (type 'gnome-control-center' on the command line if they're not in the menu. note the strange american spelling of 'center' ;)), click on 'fonts', and install them there after extracting the fonts from the tarball.

---

### Post by flyingsolo on 2006-04-19
I'm having same problem with msttcorefonts under Breezy.  If sourceforge servers are down, how long would this typically be?

---

