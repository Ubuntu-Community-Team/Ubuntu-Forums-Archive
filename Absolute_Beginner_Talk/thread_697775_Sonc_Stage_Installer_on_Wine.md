---
title: "Sonc Stage Installer on Wine"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by slymi2005 on 2008-02-15
I downloaded wine version 0.9.54 and I typed in winecfg after it installed and then I download SonicStageInstaller.exe and when I click it it starts up for a bit but then says "Insufficient hard disk space Drive C." I tried using the terminal by using wine SonicStageInstaller.exe but that did the same thing. Anyone know the problem? It's version 4.3 by the way, should I try an older version?

---

### Post by stevejesus on 2008-02-15
I found this on Wine's Application DB, and it gets only a bronze.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6911&iTestingId=20249]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6911&iTestingId=20249")
Meaning that it might not work well without some hacking.

If you do end up getting it to work well, you should report this to the WineDB.  Also, if you do get it working, I foresee that you will probably have alot of issues regarding audio performance that you MAY not be able to circumvent.  That is unless Wine can be made to become JACK-aware.  

Also, have you tried Ardour?  It's in the repos, and works much the same way as pro-tools.  You should give it a whirl.:)

---

