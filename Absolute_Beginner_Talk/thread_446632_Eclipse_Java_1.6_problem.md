---
title: "Eclipse Java 1.6 problem"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Julian Lewis on 2007-05-17
Hi all,
   I seem to get a problem in Eclipse when I use the Help menu item "Help Contents". See below. As far as I can tell apart from that; all is working OK. I am actually using Eclipse with C/C++ perspective. When I first used it with  the Ubuntu default VM, the help would not work at all, so I went to 1.6. If did all the usual things but was forced to specify the new version using the -vm (Vtirtual Machine) option to point to the 1.6 jre on the eclipse launch command line. In the eclipse preferences installed JREs I see ...

java-6-sun 1.6.00 /usr/lib/jvm/java-6-sun-1.6.0.00 Standard VM

The version of eclipse I am using is ...

Version: 3.2.2
Build id: M20070212-1330 (Ubuntu version: 3.2.2-0ubuntu3)


----------------------------------------------------- This is the error window contents I get ........


HTTP Status 503 - Servlet org.eclipse.help.internal.webapp.jsp.index_jsp is currently unavailable
type Status report

message Servlet org.eclipse.help.internal.webapp.jsp.index_jsp is currently unavailable

description The requested service (Servlet org.eclipse.help.internal.webapp.jsp.index_jsp is currently unavailable) is not currently available

---

### Post by mahy on 2007-05-19
Can you run 'java -version'? Can you select different JVMs in the Eclipse preferences? Can you wipe out the entire Eclipse profile and start over?

If everything else fails, installed the stock version of Eclipse from their site (not the one from Ubuntu repos). That's what i use and it works.

---

### Post by Julian Lewis on 2007-05-24
That was good advice, thanks. Conclusion wipe it out, go to the orrig and start over. There has to be a better way, but .... it worked. This topic has been mentioned on google ...

---

