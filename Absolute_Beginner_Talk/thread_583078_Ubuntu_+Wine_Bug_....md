---
title: "Ubuntu +Wine Bug ..."
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by termi on 2007-10-20
Now an another annoying bug has struck me.. 

Running Utorent under Wine, worked great, downloaded loads of files, then now when i try to reopen the window,  It wont Open!. Its stuck in the Tray icon stage, still downloading every time i restart the PC, or close/restart the program. 

Anyone can unlock this mystery for me?

thanks in advance, 

termi.

---

### Post by termi on 2007-10-20
bump...

---

### Post by termi on 2007-10-20
Finally found the problem, thought id post the solution incase someone elese might get the bug aswell...
----
uTorrent starts but goes completely blank.  Delete Settings.dat and Settings.dat.old in ~/.wine/drive_c/windows/profiles/<username>/Application\ Data/uTorrent

-utorrent.com
------

-termi..

---

### Post by Mr Green on 2007-10-31
Thanks mate. Worked for me.

:guitar:

---

