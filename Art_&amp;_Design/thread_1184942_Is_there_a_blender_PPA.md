---
title: "Is there a blender PPA?"
date: 2009-06-11
forum: Art &amp; Design
---

### Post by xakh on 2009-06-11
I'm not a fan of extracting tar.gz's, and I love my .deb's.Is there a PPA I can just add to allow blender to update faster?

---

### Post by days_of_ruin on 2009-06-11
not really any help but looks like there used to be: [https://edge.launchpad.net/~ubuntu-bleedingedge/+archive/ppa]("https://edge.launchpad.net/~ubuntu-bleedingedge/+archive/ppa")

---

### Post by shredwheat on 2009-06-27
I didn't find a PPA, but the [http://blender.org](http://blender.org) download page has .deb files for Ubuntu 9.04. I just one click installed 2.49a from [http://video.blendertestbuilds.de/download.blender.org/release/Blender2.49a/blender_2.49a-ubuntu0904_i386.deb](http://video.blendertestbuilds.de/download.blender.org/release/Blender2.49a/blender_2.49a-ubuntu0904_i386.deb)

It looks like there are also 64 bit versions.

---

### Post by eshwar_andhavarapu on 2010-07-21
> **shredwheat said:**
> I didn't find a PPA, but the [http://blender.org](http://blender.org) download page has .deb files for Ubuntu 9.04. I just one click installed 2.49a from [http://video.blendertestbuilds.de/download.blender.org/release/Blender2.49a/blender_2.49a-ubuntu0904_i386.deb](http://video.blendertestbuilds.de/download.blender.org/release/Blender2.49a/blender_2.49a-ubuntu0904_i386.deb)

It looks like there are also 64 bit versions.

well there's an unstable ppa here:

```
ppa:cheleb/blender-svn
```

otherwise, the stable ones are in the repository.

---

### Post by mahmudinashar on 2011-04-18
Yes, here is :
[INDENT][FONT=&quot]sudo add-apt-repository ppa:cheleb/blender-svn[/FONT]
[FONT=&quot]sudo apt-get update[/FONT]
[FONT=&quot]sudo apt-get install blender[/FONT]
[/INDENT][check this out]("http://www.ubuntubuzz.com/2011/04/blender-257-ppa-repository-install.html")

---

### Post by aslam on 2011-08-22
cheleb/blender-svn's PPA a is development/unstable ppa

for latest stable version i found this

sudo add-apt-repository [B]ppa:irie/blender

for more details [http://ubuntu-tweak.com/source/irie-blender/](http://ubuntu-tweak.com/source/irie-blender/)
[/B]

---

### Post by masuch on 2011-10-16
thanks for stable and unstable ppa.

---

### Post by snowz on 2012-01-28
Thanks :)

---

