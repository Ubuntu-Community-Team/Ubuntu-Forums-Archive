---
title: "Wine problems"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by Moezzie on 2005-12-10
I allways getting this error when i try to start winecfg. I started it some days ago to make some settings, but after that it wont work. Dont know if it's stupid me or its some other things.

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  13
  Current serial number in output stream:  14

cant use wine eather. It just wont start. 
someone having the same problem or know how to fix it?

---

### Post by tay on 2005-12-10
sahai@sahaihost:~$ cd /home/sahai/.wine
[email]sahai@sahaihost:~/.wine[/email]$ locate winecfg
/usr/bin/winecfg
/usr/lib/wine/winecfg.exe.so
[email]sahai@sahaihost:~/.wine[/email]$ cd /usr/bin/winecfg
bash: cd: /usr/bin/winecfg: Not a directory
[email]sahai@sahaihost:~/.wine[/email]$ gedit /usr/bin/winecfg

but that would'nt help.  because wine is read only, just like windows. so once it breaks, you have to uninstall and reinstall.


what are you running in wine?

---

### Post by Moezzie on 2005-12-10
at this time im not running anything cuz it dont work...but i installed it to first of all see how it works and how well(just used linux for like a 2 months now) and cuz i wanted Photoshop to run.

Could uninstalling and reinstalling be a solution? How can i get rid of all wine files so that i get a fresh instalation?

The poit is, it doesent realy matter if i get this to work. I onely want to leran how to fix it. Just getting a little better understanding about linux and go a little deaper.

---

### Post by Qrk on 2005-12-10
Delete the .wine directory in your home folder. That will remove all the configuration you've done. Perhaps you won't even need to uninstall it, you can just run through the configuration again.

---

### Post by tay on 2005-12-11
and that is the exact reason i stopped using microsoft.  
wine is just an emulator, so like the wine team says themselves, they are bound to place the same bugs into the system..

wine is not linux.

and wine and windows are not easily repaired, and alot of times just not worth being repaired.  so try uninstall and install, just like you would do with windows.

---

### Post by Moezzie on 2005-12-11
thnx Qrk. It works now.

one more question thoe.(it may be way of the topic but...)
what's so spesiel about the directorys that have a "." or a "~/." at the beginning of the name?

---

### Post by Qrk on 2005-12-11
~/ in linux is just a shortcut for /home/username. ./ is just another shortcut, but it means in the current directory. So if you want to run an install script, ./install.sh, it will run the one in that directory.

---

