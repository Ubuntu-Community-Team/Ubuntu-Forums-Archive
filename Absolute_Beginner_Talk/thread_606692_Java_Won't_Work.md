---
title: "Java Won't Work"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-11-08
Following some advice in another thread, I just ran
```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin

```
I've restarted firefox, but java won't work. It just shows a white box where the applet is meant to be. I don't even get that message at the top of the browser saying I'm missing a plugin. I've also tried using appletviewer to run the applets, but I get this message:
> appletviewer: xcb_xlib.c:50: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
Aborted (core dumped)

I really need to get java up and running (again). Any help would be greatly appreciated.

---

### Post by Seisen on 2007-11-08
Enter this in the terminal ```
update-java-alternatives -l
``` and post what it says.

---

### Post by nhandler on 2007-11-08
> **Seisen said:**
> Enter this in the terminal ```
update-java-alternatives -l
``` and post what it says.

It says
> java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-6-sun 63 /usr/lib/jvm/java-6-sun


---

### Post by ankur_gupta10 on 2007-11-08
I installed using the Synaptic package manager and it worked fine.

---

### Post by DaveRM on 2007-11-08
Cheater-
I had this problem.
It is a known bug.
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6532373]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6532373")

None of the workarounds mentioned, worked for me.
I had to remove libx11-xcb1 downgrade libx11-6.

Java then worked.

If you had upgraded these packages, to use the git version of Compiz Fusion, git can still be installed and used with the no xcb patch.

[http://gitweb.compiz-fusion.org/?p=users/3v1n0/compiz-patches;a=summary]("http://gitweb.compiz-fusion.org/?p=users/3v1n0/compiz-patches;a=summary")

I found an excellent script that uses the patch for Compiz Fusion git at:
[http://telperion.wordpress.com/2007/10/27/fusion-nuovo-script-per-compilazione/]("http://telperion.wordpress.com/2007/10/27/fusion-nuovo-script-per-compilazione/")

But it's in Italian. ;)

Good Luck.

---

### Post by VHans on 2007-11-08
I had java problems recently and solved them by cleaning up my /etc/hosts file.

---

### Post by alienexplorers on 2007-11-08
Did you setup a symbolic link to the java plugin in the .mozilla plugin folder.  You will need that for Firefox to run java.

---

### Post by VHans on 2007-11-08
I had java problems recently and solved them by cleaning up my /etc/hosts file.

---

### Post by nhandler on 2007-11-09
Well, none of the suggestions posted here worked. I recently tried running a java applet in eclipse, and that failed as well. This is driving me nuts.

---

### Post by alienexplorers on 2007-11-09
Try in terminal:
> sudo apt-get update
sudo apt-get install sun-java6-jdk

Then create a symbolic link into your .mozilla plugin folder as shown below:
> ln -s  /usr/lib/jvm/JAVA_VERSION/jre/plugin/i386/ns7/libjavaplugin_oji.so

Reboot and try firefox again.

---

