---
title: "Trouble installing OoO 2.4"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by stalkier on 2008-03-28
Ok I have OpenOffice.org 2.3 installed and I want to upgrade to version 2.4 (don't ask me why). I got the JRe installer to come up and it goes through a few steps. When I get to the "Create Directory Yes/No" it comes up with an error saying it cannot perform the action. I know why this is. First off I am not logged into the root. I try but it will not let me log in as root. Not sure why but it will not. I have successfully logged in as root in the terminal using sudo command and have also brought up the GUI root. However I am unsure what to do in the terminal and the GUI version does not run the jar file. Any info would be helpful. 

As a separate note: I am not a newbie, I just have zero retention on any linux commands. Not sure why....can't remember. :D

---

### Post by Joeb454 on 2008-03-28
If you have the OOo 2.4 deb file saved on your desktop run the following code from a terminal (1 line at a time :)):

```
cd ~/Desktop
sudo dpkg i ./<install.deb>

```

Where <install.deb> is the name of the file OOo is packaged in :)

---

### Post by stalkier on 2008-03-28
Sorry it is RPM version.

---

### Post by Joeb454 on 2008-03-28
In that case you'll need to see if there is a .deb version, RPM is for Red Hat based distributions (Fedora etc.) :)

I'll have a look as well and post a link if I find one :)

EDIT: Here is a link to the US English version: [OpenOffice 2.4 Deb Download]("http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0")

---

### Post by stalkier on 2008-03-28
Sweet man. I looked and had no luck. I can take it from here. Thanks for the fast responses and the link.

---

### Post by Joeb454 on 2008-03-28
No worries :) Hope you enjoy it :p

---

### Post by Inxsible on 2008-03-28
As a side note you can install rpm files in Ubuntu by using alien.

It won't keep a track of the updates but that's just the same as installing from an external deb file which is not in the repos.

**alien** is a program that converts between Redhat rpm, Debian deb, Stampede slp, Slackware tgz, and Solaris pkg file formats. 
```
alien /path/to/filename
```

---

### Post by Joeb454 on 2008-03-28
I didn't really want to recommend alien, though it's been a while since I've looked at it, so it could've come on a long way since then :)

Either way, if a deb is available, might as well use that ;)

---

### Post by stalkier on 2008-03-29
I forgot about Alien. I installed it. The deb file I got wouldn't install, something about a newer version of openoffice was installed. Not sure how, isn't 2.4 newer than 2.3??? Who knows. :D Anyways I really don't need to upgrade I just though oh there is a newer verion let me upgrade. Version 2.3 is good though for now. I am sure the final release of Hardy will include the newer verion of OOo. Thanks for everything guys.

---

