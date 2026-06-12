---
title: "problem installing microsoft core fonts."
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by dougmwpsu on 2006-07-04
i'm trying to install the microsoft core fonts.  this is what my terminal outputs.

> doug@doug-desktop:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  msttcorefonts
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/22.5kB of archives.
After unpacking 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package msttcorefonts.
(Reading database ... 82619 files and directories currently installed.)
Unpacking msttcorefonts (from .../msttcorefonts_1.2ubuntu3_all.deb) ...
Setting up msttcorefonts (1.2ubuntu3) ...
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--14:41:19--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.ex](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.ex) e
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--14:41:29--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32). exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--14:41:39--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--14:41:49--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--14:41:59--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--14:42:09--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

anyone have any ideas? i found this tutorial on another thread, but i don't know how to run it.

> 1. Get the following files from a friend, another pc or download manually from the internet by some means (like in my earlier post above):-
andale32.exe comic32.exe impact32.exe verdan32.exe
arial32.exe courie32.exe times32.exe webdin32.exe
arialb32.exe georgi32.exe trebuc32.exe
2. Create the following directory and put them into it: /tmp/mstt/
3. Manually launch the postinstall script, telling it to use your local copy:
/usr/sbin/update-ms-fonts /tmp/mstt
4. Remove your temp directory
rm -rf /tmp/mstt/
5. To ensure apt/dpkg is happy rerun
apt-get install msttcorefonts


i'm really not sure how to manually launch a postinstall script:p

---

