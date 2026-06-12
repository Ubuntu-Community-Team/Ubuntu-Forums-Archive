---
title: "LD_LIBRARY_PATH getting unset from .bash_profile"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by padhia on 2007-05-25
Hello,

I have DB2 running under kubuntu 7.04. As part of DB2 environment initialization, I have a line in my .bash_profile that sources a DB2 script (db2profile) that seems to be setting LD_LIBRARY_PATH environment variable (along with many other). After I have logged into my KDE session, everything except LD_LIBRARY_PATH survives, but I can't use DB2 since it fails to find one of the load library. If I open a terminal window and start another bash login session with **bash -li** command, the LD_LIBRARY_PATH variable is then set correctly, so nothing wrong with my .bash_profile - I think. Only conclusion I can draw from this is, some process after the initial session is started is unsetting LD_LIBRARY_PATH, but can't figure out how to fix that. Does anyone have a clue where should I look?

TIA 

P Adhia

---

### Post by moma on 2007-05-25
An alternative solution: 
You can add the path (or paths) that you have in LD_LIBRARY_PATH into /etc/ld.so.conf file.   
/etc/ld.so.conf contains paths to dynamic libraries. Ldconfig tool reads it and generates a cache [binary file] of dynamic libs.

$ [COLOR="SeaGreen"]sudo gedit /etc/ld.so.conf[/COLOR]

Update the library cache after changes. Run 
$ [COLOR="SeaGreen"]sudo ldconfig [/COLOR]

You can verify it by running
$ sudo ldconfig -vv

---

### Post by padhia on 2007-08-10
Thanks for the suggestion. I learned something new. But, in my particular case this doesn't help. These libraries are installed by DB2 and each user accesses a different library based on the database they use. Hence, the db2 initialization procedure sets LD_LIBRARY_PATH based on user's configuration. For now, I have written some code in .bashrc that seems to work for command line, but not for KDE.

Frustratingly, I found out that I need following env. variable to make some python extension modules work correctly, but again .bash_profile will not retain the variable after I am logged in. 

export MALLOC_CHECK_=0

Is/Are this/these known bug(s)? If not, how can I report this? I really hope they get fixed in Gusty.

Thanks

---

