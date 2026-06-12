---
title: "Gnucash 2.0.5 in Feisty?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by 4seasons on 2007-05-09
Hello!
I read posts and tried various methods to install Gnucash 2.0.5 on Feisty but to no avail.  I have Gnucash 2.0.2 installed but would have liked to upgrade.  Is there a sure-fire method to install the upgrade?
Thank you

---

### Post by mazirian on 2007-05-12
Grab the source package from debian sid and build it.

---

### Post by MrKlean on 2007-05-12
I d/l the source to my desktop.  I then went into terminal and did cd Desktop/Gnu*  then did ./configure, then make, then  sudo make install.  It will tell you if it needs nore files..

---

### Post by 4seasons on 2007-05-13
I found this weblink for compiling gnucash 2.0.5 in Ubuntu.

[http://www.linuxmint.com/forum/viewtopic.php?t=1283&sid=8bcfd33fc9ff8564d51127f8e548451a](http://www.linuxmint.com/forum/viewtopic.php?t=1283&sid=8bcfd33fc9ff8564d51127f8e548451a)

Everything went beautifully until the very end.

This is what the log file contained in Terminal:

"Selecting previously deselected package gnucash.
(Reading database ... 96899 files and directories currently installed.)
Unpacking gnucash (from .../gnucash_2.0.5-1_i386.deb) ...
dpkg: error processing /home/cathy/gnucash1/gnucash-2.0.5/gnucash_2.0.5-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is also 
in package libgconf2-4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/cathy/gnucash1/gnucash-2.0.5/gnucash_2.0.5-1_i386.deb"

I'm new to linux and the Terminal so I don't know where to go from here.
Any suggestions?
Thanks!

---

### Post by mazirian on 2007-05-14
There is really no reason to go through this unless you want the learning experience, since the earlier version of gnucash in feisty is perfectly good. I use and rely on it every day.  I have also used the 2.0.5 version and I can't say there was any noticeable difference.  Is there a specific bug that is driving this need?  If so, here is how I used to maintain the currnet version of gnucash befroe ubuntu tracked gnucash2.

I grab the source package from debian (not ubuntu) sid using apt-get source gnucash and then cd into the resulting directory that apt creates.

```

debuild -us -uc

```

debuild will attempt to build the package from source, and will note any missing dependencies.  It may complain about one or two things.  I generally check the dependencies it is complaining about against hard dependancies that the gnucash developers say you need by visiting gnucash.org.  I upgrade anything that needs upgrading.  If I am satisfied that the dependancies are met, I force debuild to build the package using:

```

debuild -d -us -uc

```

If you install all the dependancies of the current version of gnucash2 in feisty, I am pretty confident that you will have satisfied all the dependenies needed.

debuild will create several .deb files.  Install them with "sudo dpkg -i whateverthebnamesare.deb"

This process is documented elsewhere on the forums in relation to building gnucash from source when gnucash2 first came out.

Again, if this isn't your thing and it isn't necesary, I really wouldn't bother with it.

---

### Post by 4seasons on 2007-05-14
Thank you for replying to my query mazirian!  I think at this point my curiousity has been replaced by reality.  I'll stay with version 2.0.2 until the time a package of a later(earlier) version is available.  I really appreciate you letting me know that there really is not that much of a difference between the upgrade.  That seals the deal for me!  I appreciate the time and effort you took to getting back to me on this one!

---

### Post by mazirian on 2007-05-14
No problem!  I find this is the one package I just really need to work and don't want to waste anytime tinkering with, so now that gnucash2 is in the repos, I don't bother with compiling it from source any longer.

---

### Post by Tommy on 2007-06-14
I found this thread because I was looking for gnucash info...

> **mazirian said:**
> I find this is the one package I just really need to work and don't want to waste anytime tinkering with, so now that gnucash2 is in the repos, I don't bother with compiling it from source any longer.

Be extra careful -- I had trouble with the version of Gnucash in Edgy and folks at the gnucash-users mailing list said 2.0.5 was highly recommended because all previous 2.0.x releases had important bugs (I ran into several myself including some frustrating problems with the registers). I was disappointed to see that the latest stable version 2.0.5 did NOT make it into Feisty. 

In my spare time I've been learning how to get it backported. Fortunately that process has already begun (see [https://bugs.launchpad.net/feisty-backports/+bug/113712](https://bugs.launchpad.net/feisty-backports/+bug/113712) for the official request and [http://ubuntuforums.org/showthread.php?t=293988](http://ubuntuforums.org/showthread.php?t=293988) for information about joining the backports team yourself).

FORTUNATELY version 2.0.5 made it into Gutsy (the next release of Ubuntu). Eventually it should get backported to Feisty and maybe Edgy (it compiles fine in both). I'm encouraging folks to learn to backport it and add their OK to the bug report (above) so it makes it through the process quickly.

---

### Post by mazirian on 2007-06-14
it should be very easy to build using the gutsy source package and debuild.  I'll give it a try.  I haven't run across any bugs with it yet and I use it at least once a week.  I must not be using some feature that's troublesome in the current stable build.

---

### Post by bvucinic on 2007-06-15
Just updated my system from the repositories, and it is 2.0.5 :)

---

### Post by Medieval_Creations on 2007-06-15
I don't know if you want to install unstable, but I was able to compile and install gnucash 2.1.3 no problems.  I had to get a few dependencies, but other than that it was smooth sailing.

---

### Post by Tommy on 2007-06-17
> **Medieval_Creations said:**
> I don't know if you want to install unstable, but I was able to compile and install gnucash 2.1.3 no problems.  I had to get a few dependencies, but other than that it was smooth sailing.

I'm glad to see the endorsement, and look forward to continued releases! However I was put off by the official gnucash.org warnings that one shouldn't use the "unstable" 2.1.x versions for actual important data... 

I don't sit around and enter made-up unimportant financial data onto my computer just for fun, so I guess I would make a really bad beta tester...! ;)

(I think the real message is to be sure to keep VERY good backups when running unstable software.)

---

### Post by Medieval_Creations on 2007-06-18
I really don't import anything.  I'm old fashioned, I just input all my entries manually.  I just dabble with it here and there so nothing mission critical.

Also, I frequently back up specific files in my home folder.  I've lost data one to many times, I learned that lesson.  :)

---

