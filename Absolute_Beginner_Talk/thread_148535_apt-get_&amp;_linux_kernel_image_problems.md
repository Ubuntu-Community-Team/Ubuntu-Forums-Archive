---
title: "apt-get &amp; linux kernel image problems"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by werebunny on 2006-03-22
hello ubuntu community!
complete noobie reporting in :)  !
just installed ubuntu breezy and it installed as a charm.
wanted to get gdesklets  (i have added the repositorys)

**sudo apt-get install gdesklets gdesklets-data**

after downloading the packages it asked me to remove the **linux kernel image**

since i didn't know if that is ok or not i said NO. know when i start synaptic it says that there is 1 broken package. with the broken filter i found it and it is 
the linux-image-2.6.12-9-386. 
how to fix this?
is it ok to remove the running kernel image if packages ask me to.

now when i try **sudo apt-get install gdesklets gdesklets-data** i get this (the first time it downloaded without a problem):

zekopeko@leviathan:~$ sudo apt-get install gdesklets gdesklets-data
Reading package lists... Done
Building dependency tree... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  gdesklets: Depends: libavahi-client3 (>= 0.6.5) but it is not going to be installed
             Depends: libavahi-common3 (>= 0.6.4) but it is not going to be installed
             Depends: libavahi-glib1 (>= 0.6.0) but it is not going to be installed
             Depends: libbonobo2-0 (>= 2.13.0) but 2.10.1-0ubuntu1 is to be installed
             Depends: libcairo2 (>= 1.0.2-2) but 1.0.2-0ubuntu1 is to be installed
             Depends: libdbus-1-2 (>= 0.60) but it is not going to be installed
             Depends: libgcrypt11 (>= 1.2.2) but 1.2.1-3 is to be installed
             Depends: libglib2.0-0 (>= 2.9.3) but 2.8.3-0ubuntu1 is to be installed
             Depends: libgnomeui-0 (>= 2.13.0) but 2.12.0-0ubuntu1 is to be installed
             Depends: libgnomevfs2-0 (>= 2.13.4) but 2.12.1-0ubuntu2 is to be installed
             Depends: libgpg-error0 (>= 1.1) but 1.0-1 is to be installed
             Depends: libgtop2-7 (>= 2.13.2) but it is not going to be installed             Depends: libpango1.0-0 (>= 1.11.3) but 1.10.1-0ubuntu1 is to be installed
             Depends: librsvg2-2 (>= 2.13.4) but 2.12.5-0ubuntu1 is to be installed
             Depends: libtasn1-2 (>= 0.2.13) but 0.2.10-4 is to be installed
             Depends: libxml2 (>= 2.6.23) but 2.6.21-0ubuntu1 is to be installed             Depends: gconf2 (>= 2.12.1-4ubuntu1) but 2.12.0-0ubuntu1 is to be installed
  linux-image-2.6.12-9-386: Depends: initramfs-tools (>= 0.17) but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).


what is the problem? and what are gdesklets? only thing i understood about them  
is that u need them to run mac os x theme

thanks for any help u can provide

---

### Post by az on 2006-03-22
What repositories did you add?  You seem to have a version of initramfs-tools that is not compatible with ubuntu?  What happened there?

---

