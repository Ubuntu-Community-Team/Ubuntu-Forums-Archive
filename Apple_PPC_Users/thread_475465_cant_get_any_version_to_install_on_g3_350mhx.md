---
title: "cant get any version to install on g3 350mhx"
date: 2007-06-16
forum: Apple PPC Users
---

### Post by dannyk1 on 2007-06-16
Hi all.  I am trying to install any version of ubuntu desktop onto a g3 350mhz with 128mb ram with no luck.

I tried xubuntu 6.06.1 ppc which will boot up but x will be blank. A also can't ctrl-alt-f1 to a shell to try to fix up the x settings.

I have also tried ubuntu 6.06.1ppc Desktop which will also boot up with a blank X screen.
With this version I can  ctrl-alt-f1 to a shell and change the xorg.conf and get X working fine.
The system is then useable (but a bit slow), untill I try to do a install.

Every time at some point (different every time), the installer crashes wanting me to file a bug report.

Is there anyway I can get this to install from text mode??

I know this computer can run linux as it has Fedora Core 4 installed at the moment.

---

### Post by ajgreeny on 2007-06-16
I think you need more ram to install, particularly from a live CD.  You may be lucky with the alternate install version of xubuntu, but I still think 128 MB is too low for good performance; another 128 making 256 would be worthwhile considering if there is room in the machine.

---

### Post by pxwpxw on 2007-06-16
Not sure if I understand the problem but:

1. 128MB ram probably not enough for a live cd install.

2. To get a console when restarting, as a last resort, if you can get the boot: prompt

 Hit <tab> then:

 boot: Linux single

3. If you use the alternate install cd, and choose the "cli install" option,
that will restart in a text console (with 6.06 it may be the server install CD you need). Then before you install X and desktop, can get it to restart as default in text mode, before running X from the command line, until you get it sorted out. (i.e. dont get trapped in crashed X), been there.

---

### Post by dannyk1 on 2007-06-17
More Ram did the job..

Thanks guys.

Uses a hell of a lot less of the hd than osx which is handy on a machine with on 6 gig to play with!

---

