---
title: "Open Office Quickstart"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-09-11
How do I get the open office quickstart applet working properly? I have installed it and put it on my panel, however if I right click on it and say New Text Document or any of the other options it does nothing, also if I go into Open Office Writer and go to tools > options > memory the quickstarter has a check box (which I have checked) but it doesn't have the text next to it that I think it should, i.e. its just a check box instead of a check box saying something about it being the quick starter.'

I'd say Open Office is loading quite fast anyway although it seems its faster for others (I have a 3Gb processor, 512Mb RAM) and it loads in about 10seconds for writer, i've heard of people talking about 3 seconds but i'm more worried about the not being able to right click and not thinking i've got it set up right!

As an update, going to a terminal and typing ooffice (since the preferences of the quickstarter is pointing to usr/bin/ooffice, I get this message:

fopen() of /etc/openoffice/sofficerc failed: No such file or directory



Calv

---

### Post by Rui Pais on 2006-10-04
hi, 
thats a very annoying problem that happens sometimes when installing openoffice.org-common package.
That package is the one that contains, among others, the files:
> /etc/openoffice/psprint.conf
/etc/openoffice/sofficerc
but, apparently, it won't install those specific 2 if either there is some old files from previous OOffice (use purge option or synaptic in 'Not installed (residual config)' to clean it) or if openoffice.org-l10n-en-us isn't installed. 
Usually is installed as a dependency of openoffice.org, but i don't know why,  i found myself without that. 
Don't remember remove it... did it fails to been adding to dependencies list? Don't know, but seems that without openoffice.org-l10n-en-us openoffice.org-common installs but don't copy nothing to /etc/openoffice. 


At least for me, purging and ensured that package was installed and then reinstall the openoffice.org-common, solved the issue.


If file on /etc/openoffice/ continues missing after that i suppose that open can always extract from the deb file and move it manually to that folder. A bad hack that with above should be necessary.

---

