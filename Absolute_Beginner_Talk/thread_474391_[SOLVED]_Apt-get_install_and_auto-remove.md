---
title: "[SOLVED] Apt-get install and auto-remove"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-06-15
Can anyone help with this? When I 'apt-get install' I get a long list of packages which it says are no longer required - luckily I read things.

Is there a way to tell the system which packages are actually wanted - in this case I have removed the Ubuntu openoffice and installed the one from openoffice. I assume there are packages in the 'these are rubbish' list that are needed by openoffice - as are obviously the open office packages.

What I'm getting at is how can I tell which are REALLY not needed.

Any help would be gratefully received.

:D

---

### Post by Gannin on 2007-06-15
You can lock packages with Synaptic.  But if you installed OpenOffice from the OpenOffice website, then it comes with everything it needs.  You don't need any of the OpenOffice packages that come with Ubuntu.  It should be safe to remove whatever apt-get suggests you should remove.

---

### Post by forestpixie on 2007-06-15
Well not sure about that - what I'm trying to say is that if I did apt-get autoremove it'd get rid of this - 


```
kevin@kevin-desktop:~$ sudo apt-get install exaile
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
exaile is already the newest version.
The following packages were automatically installed and are no longer required:
  libfaad2-0 libgsf-gnome-1-114 python-musicbrainz2 libalgorithm-diff-perl
  libgstreamer0.8-0 apache2-utils [COLOR="Red"]openoffice.org-writer[/COLOR] libgoffice-0-common
  [COLOR="Red"]openoffice.org-impress openoffice.org-draw[/COLOR] libstlport5.1 apache-common
  gstreamer0.8-misc libdiscid0 libgstreamer-gconf0.8-0 libtext-diff-perl
  libtagc0 libapr1 liberror-perl libmdbtools [COLOR="Red"]openoffice.org-math[/COLOR] python-ctypes
  [COLOR="Red"]openclipart-png[/COLOR] rcs libgoffice-0-3 libwps-0.1-1 libxalan2-java
  python-wxversion liblo0 python-tunepimp libgstreamer-plugins0.8-0
  liblocale-maketext-lexicon-perl libhsqldb-java libraptor1 liblrdf0
  [COLOR="Red"]openoffice.org-base[/COLOR] libcgi-session-perl python-wxgtk2.6 [COLOR="Red"]openoffice.org-calc[/COLOR]
  libaprutil1 libxalan2-java-gcj libdigest-sha1-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kevin@kevin-desktop:~$ 
```


Some I know about (red) -  - I know they're needed, a couple of the others I know about and want to keep. What I have a problem with is if (for instance) apt-get is saying get rid of openoffice.org-calc and I know I want it - how can I find out whether some of the other packages are needed by openoffice progs?



Or is it just not worth worrying about until I have to do anything major? In which case I'll just ignore the suggestion!

:-k

---

### Post by forestpixie on 2007-06-15
bump

---

### Post by forestpixie on 2007-06-16
bump

---

