---
title: "Java 5 can't run .awt"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by greymaus on 2005-12-04
I have Java 5 installed from Sun. It compiles and executes applet and application (text-only) programs perfectly. However, it will not run graphics programs at all, in spite of the fact that these compile ok and give me the required .class file. 

Apparently the Java compiler can't find the gtk toolkit files.  They may be there (since the same download from Sun runs well in all functions on my other Linux distros), but there must be a link or pointer that I haven't enabled in Ubuntu. 

Here is the error message I get:
   "Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit"

This message points to: "java.awt.Toolkit.getDefaultToolkit()"
                    with a reference to: "/usr/lib/libgcj.so.6.0.0"

The problem stems from the fact that there isn't a libgcj file in /usr/lib/.   Is this file available from Ubuntu as an upgrade?

TIA for your help  ...

---

### Post by hod139 on 2005-12-04
> This message points to: "java.awt.Toolkit.getDefaultToolkit()"
with a reference to: "/usr/lib/libgcj.so.6.0.0"
Too me, this looks like you are using the gnu version of java for runtime execution, not Sun's version.  If you type 
```
  java -version 
```
of if you do 
```
 ls -al /usr/bin/java 
```
that can verify if you are using Sun's java runtime or GNU's runtime.

If you are using Sun's version, then I don't know what is wrong.

---

### Post by greymaus on 2005-12-04
Yes, thanks, Hod. I think you've uncovered the problem.

The system here IS running the GNU version of JRE...and that's because I haven't installed the Sun version yet.  I imagine the required file is in there someplace.  Will be doing that immediately.

---

### Post by greymaus on 2005-12-04
Nope.  Sorry, Hod--that DIDN'T do it.  I spoke too soon.  Still got the same problem...

---

### Post by greymaus on 2005-12-04
Hod --

Thought you might like to know, the problem is solved.  In my usual cowardly fashion [[gg]] I wiped the Java 5 install and downloaded the full Java 5/Netbeans 4.1 package from Sun.  Using the Netbeans IDE presents Ubuntu with no problems--graphics programs running fine.

---

