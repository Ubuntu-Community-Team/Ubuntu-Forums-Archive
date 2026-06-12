---
title: "amaroK hates me"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by MHlavsa on 2006-05-04
I've been trying to use amaroK for a while now, and can't get it to work.

The load screen comes up, then disappears.

To try to figure out why, I loaded it in terminal and this is what I got:
```

matt@ubuntu:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
terminate called after throwing an instance of 'std::bad_alloc'
  what():  St9bad_alloc
KCrash: Application 'amarok' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
```

Any ideas? :(

---

### Post by Bloch on 2006-05-04
I have no direct help for you, but I also had problems with amarok. It is built for the KDE desktop and known to be buggy on the default gnome desktop. I uninstalled and reinstalled several times.
I was advised to go to the homepage of the amarok project (I'm sure you can find it easily on google) and download and compile from source. They have an excellent script which automates the whole compilation process. Since then it has been very stable for me.

I am using breezy. I don't know how stable amarok from the repositories is in Dapper Drake. I presume you are using Breezy. Will you be updating at the end of the month?

---

### Post by chaumurky on 2006-05-04
[quote=MHlavsa]I've been trying to use amaroK for a while now, and can't get it to work.
 
The load screen comes up, then disappears.
 
To try to figure out why, I loaded it in terminal and this is what I got:
```

matt@ubuntu:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
terminate called after throwing an instance of 'std::bad_alloc'
  what():  St9bad_alloc
KCrash: Application 'amarok' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
```
 
Any ideas? :([/quote]
 
I'm getting something similar too.

---

### Post by testube_babies on 2006-05-05
I assume you are using the version of amarok from the repositories.  Perhaps building it yourself would solve the problem.  Here's an easy-to-follow tutorial:

[http://www.ubuntuforums.org/showthread.php?t=80492](http://www.ubuntuforums.org/showthread.php?t=80492)

If you want to steer yourself away from amarok, I recommend the GNOME-based music player Listen (although I think it is only offered for Dapper):

[http://www.ubuntuforums.org/showthread.php?t=156547](http://www.ubuntuforums.org/showthread.php?t=156547)

---

