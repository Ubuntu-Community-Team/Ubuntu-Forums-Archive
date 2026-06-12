---
title: "Upgrading OpenOffice to 2.1?"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by fontosaurus on 2006-12-14
This is going to sound awfully lame, but has anyone made the upgrade to OpenOffice 2.1?  If so, what's the method you used to get there?

---

### Post by Bachstelze on 2006-12-14
It has not been packaged yet, the only way is to use the installer from openoffice.org.

---

### Post by oliviacond on 2006-12-17
can i update from synaptic?

---

### Post by Littleweseth on 2006-12-17
oliviacond : not until it's packaged for debian/ubuntu.

---

### Post by testube_babies on 2006-12-18
It IS possible to upgrade to 2.1 (I have done it on my Edgy install) but it requires basic command-line skills and a few sneaky maneuvers in Synaptic/apt-get.  If you want to try this is a good place to start:

[http://www.ubuntuforums.org/showpost.php?p=1892050&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1892050&postcount=4)

---

### Post by macogw on 2006-12-18
Nevermind.  OOo takes WAY too long to build from source

---

### Post by steve.horsley on 2006-12-18
I installed it by downloading direct from OOo, then using alien to convert the RPM files to tar files, then extracting them to /opt. Then I created a 2-line script to launch the new version and put it in /usr/local/bin/ooo. Script contents were:
> #!/bin/sh
/opt/openoffice.org2.1/program/soffice $*


javac is the java compiler that comes with the java development kit (JDK). Javac is not in the java runtime (JRE). Version 5 of the JDK in the repos, or version 6 is available from java.sun.com.

---

