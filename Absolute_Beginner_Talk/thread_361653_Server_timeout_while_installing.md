---
title: "Server timeout while installing"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Pai on 2007-02-14
I recently installed Dapper for the first time, and am just starting to get acquainted with the OS.

One of the first things I wanted to do was get Windows fonts, so I went to my terminal.  Here's what I did, and what happened:

I don't know if I'm going about it wrong, or maybe the servers are down? The latter case seems very unlikely.  The fourth line, "msttcorefonts is already the newest version" made me think that maybe I already installed the fonts, but they don't seem to be available for use on my system.

> karl@karl-desktop:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (1.2ubuntu3) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--18:47:17--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.ex](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.ex) e
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--18:47:27--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32). exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--18:47:37--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32) .exe
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--18:47:47--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.ex](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.ex) e
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--18:47:57--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.ex](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.ex) e
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--18:48:07--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.ex](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.ex) e
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks.

---

