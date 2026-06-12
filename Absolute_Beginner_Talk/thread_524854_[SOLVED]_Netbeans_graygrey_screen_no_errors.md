---
title: "[SOLVED] Netbeans gray/grey screen no errors"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by purdticker on 2007-08-13
After I start netbeans, it has nothing but a title bar and a gray screen.  No errors are produced in terminal.

Anyone know what the issue may be?

> 
$ java -version
java version "1.5.0_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Client VM (build 1.5.0_11-b03, mixed mode, sharing)


---

### Post by Zalbor on 2007-08-13
It's compiz (or beryl). It has trouble with Java applications.
If it's the latest version, switching back to the normal window manager (metacity for gnome, kwin for kde) and back to compiz will fix it.

---

### Post by purdticker on 2007-08-13
Woohoo!  Thanks a lot that fixed it!

---

### Post by genxian on 2007-08-27
How can I switch back and forth from Compiz to Metacity.  I had been starting Compiz with a Session addition: compiz --replace --indirect-rendering

However, I disabled this session addition, so I figure it is just metacity running, yet Netbeans still won't run.

Thanks,

Brandon

---

### Post by purdticker on 2007-08-27
Not sure with compiz...

---

### Post by SomethingUniqueHere on 2007-09-12
I came across a much less elegant solution: [http://hip2b2.yutivo.org/2007/03/28/netbeans-55-blank-screen-under-fedora-core-6/](http://hip2b2.yutivo.org/2007/03/28/netbeans-55-blank-screen-under-fedora-core-6/)

---

### Post by revchris on 2008-01-30
found the answer.  enter "export AWT_TOOLKIT=MToolkit"  without the quotes in your /etc/profile

---

