---
title: "Error installing kde 4 package synaptic"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by cawill on 2007-09-14
I am trying to install the KDE 4 test packages, but I can't even get them fully installed using synaptic:

Error Code while installing kde4libs:
```
(Reading database ... 138671 files and directories currently installed.)
Unpacking kde4libs-data (from .../kde4libs-data_3.80.3-0ubuntu4_all.deb) ...
Replaced by files in installed package kdelibs5-data ...
dpkg: error processing /var/cache/apt/archives/kde4libs-data_3.80.3-0ubuntu4_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/apps/kstyle/themes/plastik.themerc', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package kde4libs.
Unpacking kde4libs (from .../kde4libs_3.80.3-0ubuntu4_all.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/kde4libs-data_3.80.3-0ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How can I fix this? I have been trying to try out kde 4 beta 2 for a while now but at all my attempts have been unsuccessful.

Thanks in advance, Chris.

---

### Post by cawill on 2007-09-14
Bump, I have also tried 'sudo apt-get install -f' but I get the same problem and its really annoying.

---

### Post by kuja on 2007-09-14
It looks like a packaging mistake. Two packages have the same file. There's a variety of ways to get around that. The *best* way to get around it would probably be to  open up one of the two deb packages (You'll find them in /var/cache/apt/archives) like you would an tar or zip file (any archive software will do really), navigate to the file it mentioned in the error (/usr/lib/kde4/share/apps/kstyle/themes/plastik.themerc) (it will be in a subarchive called data.tar.gz) 

Anyhow, delete that file from the archive. Then install the package manually. Then re-run the install and see how things go, it should remove the conflict and things should work.

---

### Post by cawill on 2007-09-14
I have extracted it and deleted the file, how do I create a deb again?

---

### Post by kuja on 2007-09-14
Erm, I would have just transparently deleted it (I at least think Ark lets me do that), anyhow, If I do recall a .deb is actually just a regular .tar.gz file. 

I would do this: tar cfz nameof.deb file1 file2 file3 ...

---

### Post by cawill on 2007-09-14
I made it a tar.gz file then renamed it to .deb, and it say's it is corrupted, can I manually install these deb files? If I did this, how would I use kde 4 then?

---

### Post by kuja on 2007-09-14
Hmmmmmmm, it's not liking the tarring part. I guess it'll have to be rebuilt with dpkg-build ... I'll post back later when I get time to explain (or you can try to figure it out, either way is fine by me)

---

### Post by cawill on 2007-09-15
Ok, I would not know where to start, if this is a packaging error and it was reported, would the package maintainers fix this error or not?

---

### Post by stan.distortion on 2007-09-17
The kde4libs package isn't needed to install beta 2, instructions are here:

[http://kubuntu.org/announcements/kde4-beta2.php](http://kubuntu.org/announcements/kde4-beta2.php)

However, I have just installed it to give it a try and while its looking good its still very much beta. alt+f2 or rightclick and select run command and launch kicker when you get it working as plasma is a long way from usable with this build.

cheers

---

### Post by kuja on 2007-09-17
> **kuja said:**
> Hmmmmmmm, it's not liking the tarring part. I guess it'll have to be rebuilt with dpkg-build ... I'll post back later when I get time to explain (or you can try to figure it out, either way is fine by me)

Okay, it's later now, and there ends a weekend at work :popcorn:

Anyhow, on to the aforementioned explanation (if it's even necessary anymore ... even if it's not, you'll still have it around for education purposes :P) :

Extract the conrol.tar.gz and data.tar.gz files from the deb into a folder, how about ~/kde5libs-data

Create another folder inside it calling it "DEBIAN"

Extract control.tar.gz into the DEBIAN folder.
Extract data.tar.gz into the base folder (ie: ~/kde5libs, or whatever you decided to call it)

Now, remove the offending file (ie: rm ~/kde5libs/usr/lib/kde4/share/apps/kstyle/themes/plastik.themerc)

Next, go to DEBIAN/control and edit the version field, bumping it up to ubuntu5 (or whatever's next, I think it was 5)

Now, run "fakeroot dpkg-build kdelibs5-data kdelibs5-data_3.80.3-0ubuntu5_all.deb" and assuming no issues it will build the package.

Lastly, install the package :confused:

---

### Post by fish_b0oy on 2007-09-20
```
 # sudo apt-get build-dep kde4libs
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  kde4libs
The following NEW packages will be installed:
  cdbs cmake debhelper diffstat html2text libenchant-dev libkeyutils-dev
  libkeyutils1 libpq-dev libqimageblitz-dev libqimageblitz4 libqt4-dev
  libsoprano-dev libsqlite0-dev libstreamanalyzer-dev libstreams-dev
  libungif4-dev libxtst-dev quilt x11proto-record-dev xsltproc
0 upgraded, 21 newly installed, 1 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 11.3MB of archives.
After unpacking 41.4MB of additional disk space will be used.
Do you want to continue [Y/n]?


```

just continue responding with "y" and everything will be fine :)

---

