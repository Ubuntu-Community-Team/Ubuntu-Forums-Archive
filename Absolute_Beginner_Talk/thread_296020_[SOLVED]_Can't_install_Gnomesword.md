---
title: "[SOLVED] Can't install Gnomesword"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by shaft350x on 2006-11-09
I would like to install the Gnomesword program and I can't.  I tried through the add/remove and it says that I cannot install Gnomesword because it conflicts with other software.  (I don't know what because I don't have much on as I just got into Ubuntu)  It tells me to switch to advanced mode to resolve the conflicts.  I didn't know there was an advanced mode, so I don't know how to do that.

So then I tried to do this via Synaptics Package manager.  And I get this ```

gnomesword:
 Depends: libsword5c2a (>=1.5.8-7) but it is not installable

```

I looked at the Gnomesword site, but not sure what I should download.  Any suggestions as to going about this?  I'm a seminary student and would really like to have a decent bible program handy.

---

### Post by linuxhacker on 2006-11-09
You'll find a resolution on this page :
> [http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html](http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html)

---

### Post by aysiu on 2006-11-09
> **linuxhacker said:**
> You'll find a resolution on this page :
Here's the relevant passage: > Gnomesword libsword5c2a dependency error

gnomesword Depends: libsword5c2a (>=1.5.8-7) but it is not installable

Solution

Install libsword5c2a version 1.5.8-8+bg2 from [here](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fs%2Fsword%2Flibsword5c2a_1.5.8-8%2Bb1_i386.deb&md5sum=f5d3d7aa584860d23ed69055af815236&arch=i386&type=main)

If You came across any other problems when you upgrade ubuntu edgy you can post here with your error messages and their solutions. 

---

### Post by LLRNR on 2006-11-09
Hi shaft350x. Well I tried it myself out of curiosity and it's a LOT easier to do the followig: in a terminal, type
```
sudo aptitude install gnomesword
```
If it doesn't come up in your menu, then issue
```
killall gnome-panel
```

HTH

LLRNR

EDIT: In fact, it even resolves the dependency problem automatically, you don't even have to bother about that.

---

### Post by shaft350x on 2006-11-09
The package download says it is for Intel x86 machines (and has the i386 signifier in the package download).  I'm running an AMD 64 system (my signature contains the info on my system, not bragging rights, just so people know what I'm running).  Will loading i386 packages on my kernel/system work?

---

### Post by shaft350x on 2006-11-09
Update: tried both methods neither worked.

---

### Post by shaft350x on 2006-11-27
Is this something that just won't work on an AMD 64 machine?

Is it possible to "compile" a version that would work?  (Never done that so I don't have the slightest clue where to start with that)

---

### Post by apalacheno on 2006-12-06
Hi there!
I followed the advice in [this thread]("http://www.ubuntuforums.org/showpost.php?p=1682605&postcount=4") and it worked.

Cheers,
apalacheno

---

### Post by shaft350x on 2006-12-06
Great, that worked for me too!  Thanks.

Now I just have to find some English versions of the bible.

---

### Post by apalacheno on 2006-12-07
To get more bible modules, open the Module Manger:
**Edit -> Module Manager**

In the Module Manager, enable Remote sources:
**SWORD -> Configure**
Change 'Install Source' to 'Remote'

Now select the bible modules which you want to install. In the Module Manager:
**Modules -> Install**
And tick the modules that should be downloaded and installed.

Hope that was clear.

Cheers,
apalacheno

---

### Post by shaft350x on 2006-12-07
very clear thanks!

---

