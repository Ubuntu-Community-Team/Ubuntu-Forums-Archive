---
title: "Java Applet wont open!"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by BruceWayne on 2006-02-28
Ok, I installed Automatix and installed the Java plugins for Firefox. I work for BNSF Railway and in order to access our computer at work from home we have to log in what they call an "Emulator" When I used windows alls I had to do was install the latest Java Virtual Machine and it would come up no problem. Now all i get is a red X in the box where it is supposed to open. If anyone can help me out with this it would be great. The web address is BNSF.com/emu, then click start emulator, click ok, and then username=lineup, password=crew. Let me know if you guys can get it to come up.

---

### Post by BruceWayne on 2006-03-01
anyone?

---

### Post by mlind on 2006-03-01
hi,

I'm not expert on applets, but it throws an exception which says there's
problem in providers authentication information.

You can see the exception if you right click on the 'X' and select 
*Open Java Console*. Applets are very picky about their signing. It needs to be
done correctly.

Here's the exception. I guess you should review this with some of the developers.

```

java.lang.SecurityException: class "oc.wcGB.ez"'s signer information does not match signer information of other classes in the same package
	at java.lang.ClassLoader.checkCerts(ClassLoader.java:775)
	at java.lang.ClassLoader.preDefineClass(ClassLoader.java:487)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:614)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:163)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:119)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at oc.wcGB.c.<init>(DashoA8032)
	at oc.wcGB.WebConnect.q(DashoA8032)
	at oc.wcGB.WebConnect.run(DashoA8032)
	at oc.wcGB.WebConnect.p(DashoA8032)
	at oc.wcGB.WebConnect.init(DashoA8032)
	at sun.applet.AppletPanel.run(AppletPanel.java:378)
	at java.lang.Thread.run(Thread.java:595)

```

---

### Post by daredevil on 2006-03-01
I came across this article. Hope this is very useful

```
http://www.debian-administration.org/articles/142
```

---

### Post by daredevil on 2006-03-01
Looks like your system policy file does not have proper permission for applets

---

