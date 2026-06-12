---
title: "sun java 6 web start"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by bluemanjacob on 2008-04-04
Hello to all. I installed Xubuntu 7.10 and have it working perfectly. The only question I have  is what is Sun Java 6 Web Start and do I need it? And would uninstalling it interfere with Firefox?

Thanks in advance, Jake:guitar:

---

### Post by Thelasko on 2008-04-04
You need it to run Java applets like [Yahoo Stock Screener]("http://screener.finance.yahoo.com/fscr/us/launch.html").  Most websites don't use Java, so you should be ok if you uninstall it.  Beware that some programs like, Azureus and OpenOffice also use Java.  Synaptic will let you know if any programs depend on Java 6 web start when you try to uninstall it.

---

### Post by alexsabree on 2008-04-04
I think he wants to know what web start even is.. I already had java but not "java webstart." I choose to download it anyway, not had a prob yet. :)

---

### Post by bluemanjacob on 2008-04-04
Thanks Alex and Telasko. Actually, it was a 2 part question and I think I am going to keep it on my  computer. It sounds like I may need it at some point. I was just wondering if it was necessary.

Jake

---

### Post by orclev on 2008-04-18
webstart is a technology that sun created to make it easier to deploy java applications from the internet. Essentially it allows you to download a file (a jnlp file) that gets read by the webstart program, which then goes and downloads all the java files specified in the jnlp file and runs the program. It's a simpler way to distribute java programs, and as a bonus if the developer puts out a new copy of one of the jars that make up the program, webstart will automatically fetch the new version next time the program is run.

---

