---
title: "dpkg error question"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by kystorms on 2007-04-26
hopefully someone can tell me what to do, as i get this error when i try to use my synaptic -

E: dpkg was interrupted: you must manually run dpkg --configure -a to correct the problem"

now when i try to to do that, i get the code I list below:




lisac@lisac-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
lisac@lisac-desktop:~$ help superuser
bash: help: no help topics match `superuser'.  Try `help help' or `man -k superuser' or `info superuser'.
lisac@lisac-desktop:~$ sudo dpkg --configure -a
Setting up msttcorefonts (1.2ubuntu3) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--11:41:42--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--11:41:52--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--11:42:02--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--11:42:12--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--11:42:22--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--11:42:32--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
lisac@lisac-desktop:~$

thanks for any help :confused:

---

### Post by benfindlay on 2007-04-26
sorry, misread the post, please ignore!

---

### Post by benfindlay on 2007-04-26
have tried to install the fonts myself recently and received the same error, wondering if perhaps they have been discontinued?

---

### Post by rillip on 2007-04-26
Yeah, it looks like it's trying to use the true type fonts, and cannot connect to where it's trying to get the file at sourceforge.  You may be able to manually locate and install these, then give it a go. If it still asks you for a configure -a try it, with the fonts installed it may just go through without needing to do anything or it may reveal another error.

---

