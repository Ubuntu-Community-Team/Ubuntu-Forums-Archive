---
title: "msttcorefonts error"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by bking on 2006-04-08
Every time I install anything I get serveral unsuccessful attempts to connect to sourceforge and then an error processing msttcorefonts message. It's looking for andale32.exe

I have searched the forum and tried some of the solutions including turning off pasive ftp, to no avail. Trying to get them with Automatix gives the same error message. Is there something I need to do to access the sourceforge servers?

Adept shows msttcorefonts as being installed. I get this when I do:
sudo apt-get install msttcorefonts.

Thanks for any help.

Becki


Reading package lists... Done
Building dependency tree... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 77 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (1.2ubuntu2) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--09:10:14--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--09:10:24--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--09:10:34--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--09:10:44--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--09:10:54--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--09:11:05--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dcstar on 2006-04-08
[QUOTE=bking]Every time I install anything I get serveral unsuccessful attempts to connect to sourceforge and then an error processing msttcorefonts message. It's looking for andale32.exe

I have searched the forum and tried some of the solutions including turning off pasive ftp, to no avail. Trying to get them with Automatix gives the same error message. Is there something I need to do to access the sourceforge servers?
......[/QUOTE]
I just tried the last link and it worked for me, perhaps there was a problem when you tried, give it another go.

---

### Post by bking on 2006-04-09
[QUOTE=dcstar]I just tried the last link and it worked for me, perhaps there was a problem when you tried, give it another go.[/QUOTE]

After reading a number of posts on this topic I was finally able to get the fonts installed by following the instructions here:

**[http://ubuntuforums.org/showthread.php?t=76655&page=2](http://ubuntuforums.org/showthread.php?t=76655&page=2)**

Basically downloading the fonts from sourceforge manually and installing them.

I was quite happy to finally get this to work!

Becki

---

### Post by trent dillman on 2006-04-09
You might want to 

```
sudo apt-get -f install
```

just in case....

---

