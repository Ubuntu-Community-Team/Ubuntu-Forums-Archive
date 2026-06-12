---
title: "Swiftweasel beta for core 2 duo: which build?"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by SomeGuyDude on 2007-12-08
Bit of a problem here.

Swiftweasel's project page ([http://swiftweasel.wiki.sourceforge.net/Which+Build%3F](http://swiftweasel.wiki.sourceforge.net/Which+Build%3F)) says to get the nocona build. However, when I download that version (from [http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=231607](http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=231607)), the only one there is listed as AMD64 and when I attempt to install it, figuring it's just labeled wrong or something, I'm obviously told it's the wrong architecture.

Is there any build of this thing I can use?

---

### Post by fineas on 2007-12-08
I don't know for sure which version you 're running (32bit or 64bit). Check here:
[http://sourceforge.net/project/showfiles.php?group_id=195473](http://sourceforge.net/project/showfiles.php?group_id=195473)
there is a stable version for you

---

### Post by Yellow Pasque on 2007-12-08
There doesn't appear to be a 2.0.11 i386 build at the moment. However, there is a 2.0.10 build:
[Nocona 32-bit](http://downloads.sourceforge.net/swiftweasel/swiftweasel-2.0.0.10_nocona-32bit_ubuntu-i386.deb?modtime=1196321829&big_mirror=0)

---

### Post by SomeGuyDude on 2007-12-09
> **Temüjin said:**
> There doesn't appear to be a 2.0.11 i386 build at the moment. However, there is a 2.0.10 build:
[Nocona 32-bit](http://downloads.sourceforge.net/swiftweasel/swiftweasel-2.0.0.10_nocona-32bit_ubuntu-i386.deb?modtime=1196321829&big_mirror=0)

I have 2.0.11. What I'm looking for, however, is the 3.0b1.

fineas, I have a core 2 duo, so what I've been doing is downloading the version of things for the core 2 duo. In this case, the Nocona build for a 64-bit processor. I've not run into any issues doing such.

I am, however, running 32-bit Ubuntu, so if I should avoid 64-bit software despite the .deb made for my proc because I don't have a 64-bit OS, then which dang version should I get in THAT case? Prescott? Pentium 4?

Of course, if I could figure out how to install from the tar.gz then that'd probably fix things, but without a configure file I don't know what I'm doing.

---

### Post by fineas on 2007-12-09
Swiftweasel is optimized for 1) processor type (nocona is the recommended build for Intel 64bit chips) and 2) target operating system and version, which is ubuntu i386 (see [http://swiftweasel.wiki.sourceforge.net/Installation?token=20a40a9844134663ca8a5c54391daf8b](http://swiftweasel.wiki.sourceforge.net/Installation?token=20a40a9844134663ca8a5c54391daf8b)). So, the most suitable package for you should be a swiftweasel-3.0b1_nocona-32bit_ubuntu-i386.deb, but it seems that there is not such a build for 3.01b version. So, if I were you, I would go for the platform independent tar.gz package


> **SomeGuyDude said:**
> 

Of course, if I could figure out how to install from the tar.gz then that'd probably fix things, but without a configure file I don't know what I'm doing.

The link above describes how to install from the tar.gz

---

