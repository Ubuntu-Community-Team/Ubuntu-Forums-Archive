---
title: "It wants me to update--but then says it will break something??"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by wilberfan on 2007-01-18
Check out the attached capture.   The adept manager seems to be saying that there are updates available for K3b?   But when I request the update it says it will "break" the package (or something!)...

Any idea what's going on??

---

### Post by towsonu2003 on 2007-01-18
> **wilberfan said:**
> Check out the attached capture.   The adept manager seems to be saying that there are updates available for K3b?   But when I request the update it says it will "break" the package (or something!)...

Any idea what's going on??
I don't use adept (but if I would report that as a usability bug)

anyway, from the command line, what's the output of 
```

sudo apt-get update
sudo apt-get -s upgrade
```
-s means "simulate but don't update"...

---

### Post by jbus on 2007-01-19
Are you using any unofficial repositories?

---

### Post by wilberfan on 2007-01-19
> **towsonu2003 said:**
> I don't use adept (but if I would report that as a usability bug)

anyway, from the command line, what's the output of 
```

sudo apt-get update
sudo apt-get -s upgrade
```
-s means "simulate but don't update"...
> 
wilberfan@AMD64:~$ sudo apt-get -s upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  k3b libk3b2
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

That echoes what happens in the adept updater...

---

### Post by wilberfan on 2007-01-19
> **jbus said:**
> Are you using any unofficial repositories?

That's affirmative!

---

### Post by jbus on 2007-01-19
If k3b is the only application that is threatening to break you might just want to lock in the version you are using right now. Though, that would just be a temporary fix. This could mean that one or more of your unofficial repositories are supplying conflicting packages for some of k3b's dependencies or k3b itself. This could create problems with other applications as well.

---

### Post by towsonu2003 on 2007-01-19
I forgot which one, but try
```

sudo apt-get -s install k3b
```
or ```
sudo apt-get -s upgrade k3b
``` and paste the output? and probably the output of ```
apt-cache policy k3b
``` maybe it's coming from an unofficial repo (what are your repos?).

---

### Post by wilberfan on 2007-01-19
> **towsonu2003 said:**
> I forgot which one, but try ```
sudo apt-get -s install  k3b
``` and paste the output? and probably the output of ```
apt-cache policy k3b
``` maybe it's coming from an unofficial repo (what are your repos?).

> wilberfan@AMD64:~$ sudo apt-get -s install k3b
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  k3b: Depends: kdelibs4c2a (>= 4:3.5.5-1) but 4:3.5.5-0ubuntu3 is to be installed
       Depends: libdbus-1-3 (>= 0.94) but 0.93-0ubuntu3.1 is to be installed
       Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is to be installed
       Depends: libmusicbrainz4c2a (>= 2.1.4) but 2.1.2-6ubuntu2 is to be installed
       Depends: libpng12-0 (>= 1.2.15~beta5) but 1.2.8rel-5.1ubuntu0.1 is to be installed
       Depends: libqt3-mt (>= 3:3.3.7) but 3:3.3.6-3ubuntu3 is to be installed
       Depends: wodim but it is not installable
E: Broken packages

Hmmm....    Here's the next one:

> wilberfan@AMD64:~$ apt-cache policy k3b
k3b:
  Installed: 0.12.17-1ubuntu3
  Candidate: 1.0~pre2+svn20061211.2010+r612636-0rarewares1
  Version table:
     1.0~pre2+svn20061211.2010+r612636-0rarewares1 0
        500 [http://www.rarewares.org](http://www.rarewares.org) ./ Packages
 *** 0.12.17-1ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
        100 /var/lib/dpkg/status

I've got LOTS of unofficial repos...  :???:   (Thanks for your ongoing help with this...!)

---

### Post by Duppy on 2007-01-19
Just carry on with the installation. It means BREAK in a different way, it doesnt mean it will BREAK your PC.

---

### Post by wilberfan on 2007-01-19
> **Duppy said:**
> Just carry on with the installation. It means BREAK in a different way, it doesnt mean it will BREAK your PC.

Actually, I don't think it will ALLOW me to proceed...

---

### Post by towsonu2003 on 2007-01-19
Comment out the following repo:
```

http://www.rarewares.org ./

```
so it would rather look like this
```

**#**http://www.rarewares.org ./

```
and try again with update & **-s** upgrade (so it will simulate and spit out any errors it finds, without breaking anything)

I suggest you also contact the maintainer of that repo :)

PS. never install packages with unmet dependencies, as they will probably break synaptic / apt-get / dpkg... (which means until you spend time and effort to fix the unmet dependencies, you won't be able to update your packages)

---

### Post by wilberfan on 2007-01-19
> **towsonu2003 said:**
> Comment out the following repo:
```

http://www.rarewares.org ./

```
so it would rather look like this
```

**#**http://www.rarewares.org ./

```
and try again with update & **-s** upgrade (so it will simulate and spit out any errors it finds, without breaking anything)

I suggest you also contact the maintainer of that repo :)

PS. never install packages with unmet dependencies, as they will probably break synaptic / apt-get / dpkg... (which means until you spend time and effort to fix the unmet dependencies, you won't be able to update your packages)

Here's the result of an -s upgrade:
> 
wilberfan@AMD64:~$ sudo apt-get -s upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I guess that means all is well now?  (Except for whatever it was that I added the rarewares.org repo for! [I need more comments in my sources file!])  What, exactly, should I tell the rarewares maintainer?

While I wasn't inclined to "force" anything to install, it's good to know why it's a bad idea!

---

### Post by towsonu2003 on 2007-01-19
> **wilberfan said:**
> 
I guess that means all is well now?  (Except for whatever it was that I added the rarewares.org repo for!
yes, I believe everything is fine. You won't loose any installed packages by commenting out repos, but you'll not get updates. You can check what you installed probably by launching synaptic and checking the "Status > Installed (Local or obsolete)" section thre.

> What, exactly, should I tell the rarewares maintainer?
I think you can just give him/her the link to this thread and s/he can use the info here to fix his/her k3b package if s/he'd like to.

---

