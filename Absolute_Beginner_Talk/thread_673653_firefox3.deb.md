---
title: "firefox3.deb"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by exneo002 on 2008-01-20
I want a firefox3 beta 2 debian package is it possible will anybody compile one for me?

---

### Post by GavinZac on 2008-01-20
there's one floating about it think, and there is one in the Hardy Heron repositories. You have another option though:

[http://www.topicalmatt.com/23-12-2007/firefox-3-beta-2-in-ubuntu-710](http://www.topicalmatt.com/23-12-2007/firefox-3-beta-2-in-ubuntu-710)

---

### Post by exneo002 on 2008-01-20
you don't have to be a teacher just run it for children you know and thanx I use fiesty

---

### Post by sumguy231 on 2008-01-20
Firefox is typically distributed precompiled so it's really just a matter of copying it to the right place, fixing permissions, and running it:
[http://kb.mozillazine.org/Installing_Firefox#Linux](http://kb.mozillazine.org/Installing_Firefox#Linux)
It's not as clean as installing a .deb package but it should do you for now.

---

### Post by GavinZac on 2008-01-20
> **exneo002 said:**
> you don't have to be a teacher just run it for children you know and thanx I use fiesty

I'm just letting you know, its not that difficult to do what was on the link.

Alternatively, download a .deb from one of the mirrors here:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Ff%2Ffirefox-3.0%2Ffirefox-3.0_3.0~b3~cvs20080101t1000%2Bnobinonly-0ubuntu1_i386.deb&md5sum=d74f4a9774062a29e0a0fe077e574058&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Ff%2Ffirefox-3.0%2Ffirefox-3.0_3.0~b3~cvs20080101t1000%2Bnobinonly-0ubuntu1_i386.deb&md5sum=d74f4a9774062a29e0a0fe077e574058&arch=i386&type=main)

which is the Hardy Heron repository.

heres a link at random from that list if the mirrors link didnt work right:
[http://ubuntu.cs.utah.edu/ubuntu/pool/universe/f/firefox-3.0/firefox-3.0_3.0~b3~cvs20080101t1000+nobinonly-0ubuntu1_i386.deb](http://ubuntu.cs.utah.edu/ubuntu/pool/universe/f/firefox-3.0/firefox-3.0_3.0~b3~cvs20080101t1000+nobinonly-0ubuntu1_i386.deb)

---

### Post by syxbit on 2008-01-20
i tried installing the hardy x64 firefox3, and i get an error saying that i'm missing dependency libc6
but i installed that! and shouldn't apt just download any missing dependencies anyway?

---

### Post by GavinZac on 2008-01-20
> **syxbit said:**
> i tried installing the hardy x64 firefox3, and i get an error saying that i'm missing dependency libc6
but i installed that! and shouldn't apt just download any missing dependencies anyway?

Have you got build-essentials installed?

---

### Post by FuturePilot on 2008-01-20
It's not going to work on any earlier version of Ubuntu. It will only work on Hardy. It's built against a newer version of libc6 than what is in Gutsy and Feisty.

---

### Post by GavinZac on 2008-01-20
> **FuturePilot said:**
> It's not going to work on any earlier version of Ubuntu. It will only work on Hardy. It's built against a newer version of libc6 than what is in Gutsy and Feisty.

I guess he could install Hardy's build-essentials, if he's feeling brave?

---

### Post by FuturePilot on 2008-01-20
That probably won't work. You don't need build-essential for this.

---

### Post by syxbit on 2008-01-20
i tried the manual install, like some sites mention, but plugins (like flash) didn't work.
oh well

---

### Post by Kilz on 2008-01-20
[You could try Swiftweasel, ]("http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=231607")its an optimized build of firefox. It has deb's of the 3.0 beta 2 that was released a few weeks ago.

---

### Post by syxbit on 2008-01-21
nice!
thanks. trying it now

EDIT- works great!

---

