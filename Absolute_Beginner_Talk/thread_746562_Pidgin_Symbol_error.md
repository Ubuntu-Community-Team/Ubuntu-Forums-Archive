---
title: "Pidgin Symbol error"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by emuellner on 2008-04-05
I am running Gutsy, and I recently tried to update to the newest version of Pidgin because I was having problems with the other one. I first went to the synaptic package manager and completely removed pidgin from there, and restarted.

I then followed the instructions in the install text file that I downloaded with Pidgin 2.4.1 and it all went fine.

Now, when I try to run it, nothing happens. So I tried running it from the terminal and I go this error message, ```
pidgin: symbol lookup error: pidgin: undefined symbol: purple_account_get_current_error
```

Any suggestions will be greatly appreciated. I'm still somewhat new to all of this, but I have a general understanding as to how it works.

---

### Post by Oldsoldier2003 on 2008-04-05
> **emuellner said:**
> I am running Gutsy, and I recently tried to update to the newest version of Pidgin because I was having problems with the other one. I first went to the synaptic package manager and completely removed pidgin from there, and restarted.

I then followed the instructions in the install text file that I downloaded with Pidgin 2.4.1 and it all went fine.

Now, when I try to run it, nothing happens. So I tried running it from the terminal and I go this error message, ```
pidgin: symbol lookup error: pidgin: undefined symbol: purple_account_get_current_error
```

Any suggestions will be greatly appreciated. I'm still somewhat new to all of this, but I have a general understanding as to how it works.

if you downloaded pidgin from getdeb you need to install 3 packages, libpurple0 pidgin-data and pidgin. all three of these packages need to be installed and after you install them you need to pin the version in synaptic so that the dont get downgraded by a software "update"

---

### Post by finer recliner on 2008-04-05
try removing (or renaming) your ~/.purple directory. this is the directory that holds all of your personal settings for pidgin. personal setting directories are generally NOT removed when you uninstall an application. 

by removing (or renaming) the directory, a new one will be created for you next time you run pidgin.

---

### Post by emuellner on 2008-04-05
Thanks, I got it fixed. I removed the .purple directory and that solved my issues.

I am always impressed with this forum whenever I ask questions here. I appreciate it very much.

---

### Post by ruicovelo on 2008-04-24
the pidgin version in synaptic kept crashing so I tried the newest version from source and I also got this error. Solved it by removing ~/.purple. But now I wonder if the crashes could be solved with this simple solution...

PS:

Argh! The newest version also crashes:
Pidgin 2.4.1 has segfaulted and attempted to dump a core file.
This is a bug in the software and has happened through
no fault of your own.

If you can reproduce the crash, please notify the developers
by reporting a bug at:
[http://developer.pidgin.im/simpleticket/](http://developer.pidgin.im/simpleticket/)

Please make sure to specify what you were doing at the time
and post the backtrace from the core file.  If you do not know
how to get the backtrace, please read the instructions at
[http://developer.pidgin.im/wiki/GetABacktrace](http://developer.pidgin.im/wiki/GetABacktrace)

If you need further assistance, please IM either SeanEgn or 
LSchiere (via AIM).  Contact information for Sean and Luke 
on other protocols is at
[http://developer.pidgin.im/wiki/DeveloperPages](http://developer.pidgin.im/wiki/DeveloperPages)
Aborted (core dumped)

---

### Post by jnylen on 2008-06-18
I was able to fix this problem in a very simple way.  For some reason I had some incorrect/old libpurple.* libraries in /usr/local/lib, and pidgin was loading those libraries before looking in /usr/lib.  Check and see if you have any of these with the following command:```
find /usr/local/lib -name *purple*.so*
```If that command shows any files, then you can run the following command which should fix the problem:```
for f in /usr/local/lib/*purple*.so*; do sudo mv "$f" "$f.old"; done
```Worked for me, at least!  No need to lose your settings or reinstall packages either.  (But you should probably not do this if you have installed Pidgin from source in /usr/local).

---

