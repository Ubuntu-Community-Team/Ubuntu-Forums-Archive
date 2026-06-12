---
title: "Dependencies on Ubuntu Packages"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by ProSlayer on 2008-01-18
Hey,

I am new with Ubuntu (just installed Gutsy today) and just got my wireless working thanks to a guide on here. Maybe I am completely off, but it seems like with any package I want to download, it involves so many dependencies. For example, if I want to install WiFi Radar, I see 4 dependencies, who each have their own dependencies, etc. At first I did not know what dependencies were, so I installed the WiFi radar without any dependencies and it still ran, what is that all about?

Another question I had was what is hppa, lpia, and i386? and what if there is a package on feitsy, but not on gutsy, can are they backwards compatible?

---

### Post by mikewhatever on 2008-01-19
> **ProSlayer said:**
> Hey,

I am new with Ubuntu (just installed Gutsy today) and just got my wireless working thanks to a guide on here. Maybe I am completely off, but it seems like with any package I want to download, it involves so many dependencies. For example, if I want to install WiFi Radar, I see 4 dependencies, who each have their own dependencies, etc. At first I did not know what dependencies were, so I installed the WiFi radar without any dependencies and it still ran, what is that all about?

Strange. I would not expect it to run without dependencies. The good point is that they are taken care of automatically. I suspect that when you installed wifi radar with add/remove or synaptic, its dependencies where pulled in and installed first. Those of us who have no internet need to manually download all packages including dependencies.

> Another question I had was what is hppa, lpia, and i386? 

Simply put, these are CPU architectures. I am no expert in that field, so guess Wikipedia should do a better job:
[http://en.wikipedia.org/wiki/PA-RISC](http://en.wikipedia.org/wiki/PA-RISC)
[http://en.wikipedia.org/wiki/I386](http://en.wikipedia.org/wiki/I386)

> and what if there is a package on feitsy, but not on gutsy, can are they backwards compatible?
 
Not sure what that means, but most PCs that successfully ran Feisty should also be able to run Gutsy. New packages may be added to provide new features and some may be removed, but the bulk should remain the same apart from package versions.

---

### Post by ProSlayer on 2008-01-19
Thanks for the help! 

Edit: I was able to find what I was looking for.

Edit2: I noticed that some packages are not available on the Add/Remove Application list, that are available online. For example, I wanted to download dsniff, but it is not on the add/remove application list, but it can be found here: [http://packages.ubuntu.com/dapper/net/dsniff](http://packages.ubuntu.com/dapper/net/dsniff). Is there are way to automatically download its dependencies?

---

### Post by mikewhatever on 2008-01-19
> **ProSlayer said:**
> Thanks for the help! Does that mean I can just download packages without installing their dependencies first, or do I need to install them in a special way?

If you install packages through add/remove, synaptic or apt-get, all dependencies should be taken care of automatically. All you have to do is select the actual package you want and install it. If that is an off-line installation, namely, you download on another computer, place packages onto removable storage, and then install, then all packages should be downloaded, dependencies, and those of dependencies, included. There is a project that aims to facilitate this [http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/).

---

### Post by sumguy231 on 2008-01-19
> **ProSlayer said:**
> Thanks for the help! 

Edit: I was able to find what I was looking for.

Edit2: I noticed that some packages are not available on the Add/Remove Application list, that are available online. For example, I wanted to download dsniff, but it is not on the add/remove application list, but it can be found here: [http://packages.ubuntu.com/dapper/net/dsniff](http://packages.ubuntu.com/dapper/net/dsniff). Is there are way to automatically download its dependencies?

Add/Remove doesn't carry all software packages, for that you'll want to use Synaptic which does. Also you can greatly increase the amount of software choices available to you by enabling extra repositories from Synaptic or the Software Sources configuration thingy.

---

### Post by mikewhatever on 2008-01-19
> **ProSlayer said:**
> 
Edit2: I noticed that some packages are not available on the Add/Remove Application list, that are available online. For example, I wanted to download dsniff, but it is not on the add/remove application list, but it can be found here: [http://packages.ubuntu.com/dapper/net/dsniff](http://packages.ubuntu.com/dapper/net/dsniff). Is there are way to automatically download its dependencies?

Check this out [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/). Since there is a version for Gutsy ([http://packages.ubuntu.com/gutsy/net/dsniff](http://packages.ubuntu.com/gutsy/net/dsniff)), whats the point of installing an older one?

---

