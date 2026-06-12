---
title: "SNMP Logger/ Monitor"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Hopworks on 2007-08-30
I found a pretty good free application that does a really good job of recording and archiving SNMP messages sent from my Linksys BEFSX41, but it is for windows only, and that doesn't fit into my plans to migrate to Linux as my primary OS. Could someone recommend a Linux app that does the same thing (for Ubuntu 7.04 Feisty)? I'm not too concerned about a GUI and command line is fine. I just need it to record network logging activity from the router 24/7. Thank you

---

### Post by dwhitney67 on 2007-08-31
You can obtain an SNMP client using apt-get:

[FONT="Courier New"]$ sudo apt-get install snmp[/FONT]

Then read the man-pages concerning **snmpcmd** and **snmpwalk**.  The command line options that are applicable to snmpcmd can be used with snmpwalk.  It appears that you will be "walking" the MIB to perform GetRequests so it should be pretty straightforward.

If you would like to install an SNMP manager (server) on your system, the command for this is:

[FONT="Courier New"]$ sudo apt-get install snmpd[/FONT]

This install will automatically start the service after the install is complete, and similarly each and every time to start your system. 

Here's the [site]("http://www.debianhelp.co.uk/snmp.htm") where I got this info.

---

### Post by Hopworks on 2007-08-31
Thank you! I knew it was probably something easy like that. I just didn't think of it. =\
Now I have one less reason to use Windows :)

---

