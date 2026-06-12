---
title: "Security"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-03-13
Does Ubuntu need anti-virus, firewall or anti-spyware? I have a friend who uses Linux and doesn't use anything, but I am a Windows user just converted and am terrified of having my system online without the usual security. Do other people use those sort of programmes or go online with just Ubuntu as it is??

---

### Post by mozkaynak on 2007-03-13
No anti-virus needed. clamav is a product available for linux environment but no one writes viruses for linux for using

firewall: this may be needed. do you have any server service in your box? If so, you better set up a firewall. firestarter a common tool for this purpose.

anti-spyware: I dont use but I am not sure that it is unnecessary.

---

### Post by orkim on 2007-03-13
Typically virus/malware/spyware/etc are written for Windows.  This does not make you invulnerable by default, but it means that there is a lot less threat towards Linux boxes online.  There still does exist remote/local exploits and root kits that are (dare I say rarely?) found in the wild.

Your best bet is to adopt good administration techniques.  If you give out accounts on your box be sure that they have correct permissions.  Don't run more services (daemons) than you actually use; the more you run the higher a chance that one might be exploitable somewhere.  Apply the updates early and often.  Make sure to keep a secure root password (on Ubuntu the first user can use sudo, so make sure thats a secure password as well).

You can install and use a firewall.  There are many to choose from.  If this is just one system on a cable/dsl/modem connection to the internet you shouldn't really need a firewall.  Most home users who use Linux are OK without using one.  If this computer is a gateway for a corporate environment you might prefer a firewall.

Most of these suggestions will hinder the use of the system.  You will need to weigh which are important for security and which are important for usability.  I typically don't do much tweaking form the default Ubuntu setup when I install it for friends/family as it is pretty secure.

I hope this has helped shed a little light on the subject for you.

-orkim

---

### Post by mrbungle on 2007-03-13
doesn't ubuntu come with a firewall already installed?  just doesn't have the gui to it.

---

### Post by Wake Rider on 2007-03-13
Your information is really good thank you. I am not running a server, just a home PC on a 56k dialup connection. Sadly the modem won't work yet but I have sent an email to the winmodem organisation for help.

---

### Post by aysiu on 2007-03-14
Read this:
[http://psychocats.net/ubuntu/security#firewallantivirus](http://psychocats.net/ubuntu/security#firewallantivirus)

---

