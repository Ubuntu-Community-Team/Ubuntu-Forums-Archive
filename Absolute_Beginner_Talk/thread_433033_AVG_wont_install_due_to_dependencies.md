---
title: "AVG wont install due to dependencies"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by hayward room on 2007-05-04
Hi there - I'm trying to install AVGfree anitvirus for linux and gave me this error message: 

[I][B]error: Failed dependencies:
        pygtk2.0 >= 2.0.0 is needed by avg75flm-r45-a0973.i386
        pygtk2.0-libglade >= 2.0.0 is needed by avg75flm-r45-a0973.i386
        python >= 2.2.2 is needed by avg75flm-r45-a0973.i386
        /bin/sh is needed by avg75flm-r45-a0973.i386[/B][/I]

I have tried to update these needed dependencies but stated I already have these installed or they are in te newest version? 

Please advise on any help. Thnx! :confused:

---

### Post by davidgarcin on 2007-05-04
are you using the Synaptic Package manager to install the python/gtk updates?  If you aren't, give that a try.  Go to System -> Administration -> Synaptic Package Manager and search for the dependencies using the toolbar search button.  In my experience, SPM does a fine job of resolving dependencies etc.

---

### Post by hayward room on 2007-05-04
> **davidgarcin said:**
> are you using the Synaptic Package manager to install the python/gtk updates?  If you aren't, give that a try.  Go to System -> Administration -> Synaptic Package Manager and search for the dependencies using the toolbar search button.  In my experience, SPM does a fine job of resolving dependencies etc.

Yes I tried SPM but still gave me failed dependencies error: 
error: Failed dependencies:
        pygtk2.0 >= 2.0.0 is needed by avg75flm-r45-a0973.i386
        pygtk2.0-libglade >= 2.0.0 is needed by avg75flm-r45-a0973.i386
        python >= 2.2.2 is needed by avg75flm-r45-a0973.i386
        /bin/sh is needed by avg75flm-r45-a0973.i386

It stated that i have the latest version of python. 

Any other ideas? Thnx! :confused:

---

### Post by davidgarcin on 2007-05-04
uhhh.....  download and install them manually?  That's all I've really got.  And having tried that myself, it can be quite the arduous/unsuccessful operation.....  sorry!

---

### Post by Delkster on 2007-05-04
I don't know what version of Ubuntu you're running but at least on my Feisty install it seems that the packages have different names, such as python-gtk2 and python-glade2 rather than pygtk2.0 and pygtk2.0-libglade.

Where did you get the package? If it's been converted from rpm with the "alien" tool, for example, the dependencies may be off because the packages may have different names on rpm-based distros.

---

### Post by gpilkay on 2007-05-04
I had some troubles with AVG too.  I wound up with Avast, it actually worked better for me, I downloaded the .deb file, double clicked it, and entered the code they e-mailed me.  It installed itself, and now shows up in Synaptic

---

### Post by mojo123 on 2007-05-04
whats the point of having windows antivirus for linux?

---

### Post by davidgarcin on 2007-05-07
yeah, I don't see much of a point to it either... although it is a Linux version, not a Windows.

if you guys are still struggling, check out avast!, they have a linux version packaged as a .deb which is easy to install.  and in my experience, avast! can take on AVG anyday.

EDIT: yeah, looks like someone already suggested that.  I second it.

---

### Post by orb9220 on 2007-05-07
For New person's that do not know.

You do not need to install Firewall or Antivirus since iptables firewall is installed and setup by default.

You only need Antivirius if you are running a Mail/File server that windows user's access. You need to then be able to scan their mail and windows files on the server.

If you have a windows partition then windows antivirius programs like nod32 and others generally do a much better job.

---

