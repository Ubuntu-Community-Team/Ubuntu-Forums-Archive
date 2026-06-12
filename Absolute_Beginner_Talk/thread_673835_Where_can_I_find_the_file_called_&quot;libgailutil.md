---
title: "Where can I find the file called &quot;libgailutil.so.17&quot;?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-01-21
I guess the title pretty much says it all. I'm trying to install Mono (a HUGE pain in its own right!!), and it tells me it can't finish the installation because I'm missing something called "libgailutil.so.17". I've searched high and low, and I can't find such a file.

Any help is appreciated! Thank you!

---

### Post by forestpixie on 2008-01-21
you can find rpm's on the net - but mono is in synaptic

---

### Post by pjkoczan on 2008-01-21
It's likely there's a version mismatch. The default libgailutil on my system is libgailutil.so.18. Can you paste the output of the following?

```
ls -l /usr/lib/libgail*
```

One question, are you trying to compile mono by hand, install it via synaptic, or install a 3rd party package?

---

### Post by doctorbighands on 2008-01-21
I'm trying to install Mono by hand. What a pain!!

Here is the output of "ls -l /usr/lib/libgail*":
```
-rw-r--r-- 1 root root   828 2007-09-17 09:12 /usr/lib/libgailutil.la
lrwxrwxrwx 1 root root    21 2008-01-20 23:41 /usr/lib/libgailutil.so -> libgailutil.so.18.0.1
lrwxrwxrwx 1 root root    21 2008-01-18 17:24 /usr/lib/libgailutil.so.18 -> libgailutil.so.18.0.1
-rw-r--r-- 1 root root 26816 2007-09-17 09:12 /usr/lib/libgailutil.so.18.0.1
```

I hope that helps.

While you're all here, the thing that seems to be stopping me from installing mono is something called "libc6". I have v2.6-1 installed, but the terminal is demanding v2.7-1, and I don't know how to find that.
**EDIT: I've found the latest version of libc6 and installed it successfully. It's the "Hardy" version, but it installed fine.

I still need a copy of libgailutil.so.17 in order to get Mono to agree with me...

---

### Post by doctorbighands on 2008-01-21
*bump*

---

### Post by pjkoczan on 2008-01-21
Well, there's your version mismatch. It might be an old version of the package (requiring libgailutil.so.17) or a bad configure script.

You might be able fix this yourself somehow (an option to configure, manually editing the configure script itself) if you're comfortable doing that. Either way, you should contact the mono people to inform them of this.

If all else fails, installing mono via synaptic might work.

---

### Post by doctorbighands on 2008-01-21
I tried to install mono via synaptic. I'm told I have the following unresolvable dependencies:
```
mono:
  Depends: mono-common (=1.2.5-1~pre2) but 1.2.6+dfsg-2 is to be installed
  Depends: mono-jit (=1.2.5-1~pre2) but 1.2.6+dfsg-2 is to be installed
```

Am I to understand this message to mean that my dependency versions are too...*new*?? How is that possible?

If I'm misunderstanding, then what is the terminal trying to tell me?

Either way, I'm in slightly over my head here, and I'm not sure how to get this fixed.

---

### Post by doctorbighands on 2008-01-22
*bump*

---

### Post by pjkoczan on 2008-01-23
Yep, apparently they're too new. I've seen this with a few other Why mono's configure script or package isn't smart enough to work around this I do not know. Open a case with the mono people (or at least lurk their forums a bit), hopefully it's just easily-overcome laziness and not some sort of incompatibility with newer versions of this library.

---

### Post by gn2 on 2008-01-23
Does the download links at the bottom of [ this]("http://packages.debian.org/etch/libgail17") page help?

"libgailutil.so.17" is listed in the package contents.

---

### Post by doctorbighands on 2008-01-23
> **gn2 said:**
> Does the download links at the bottom of [ this]("http://packages.debian.org/etch/libgail17") page help?

"libgailutil.so.17" is listed in the package contents.

This seems to have done the trick...sort of. Now, when I run the binary Mono installer, instead of prompting me for files I don't have, it tells me I "should have no trouble running gtk# files". That much is good.

When I go to run MonoDevelop, I double-click the icon, and nothing happens.

I went into the terminal and, just to see what happens, I ran "sudo apt-get install mono". It replied by telling me that the "mono-common" and "mono-jit" dependencies were unmet, because THE VERSIONS I HAVE ARE TOO NEW.

Good lord!

Anyway, thank you for the help. I guess I'll just wait for the Mono people to come around on this one!

---

### Post by gn2 on 2008-01-23
I also found this similar site: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by HDave on 2008-03-24
doctorbighands -- Any update on this?  I am in the EXACT same situation as you...

---

### Post by lpsmith on 2008-06-09
I also had this exact same problem, and eventually worked out that if I had libgailutil.so.17 installed, the manual mono installer would work fine.  Fairly helpful was the page [http://blog.baelemans.com/post/2008/04/Installing-Mono-19-and-MonoDevelop-10-on-Ubuntu-Linux.aspx](http://blog.baelemans.com/post/2008/04/Installing-Mono-19-and-MonoDevelop-10-on-Ubuntu-Linux.aspx)

(He talks there about getting monodevelop to work; I didn't need that bit, so can't comment, but it might be helpful.)

I downloaded the file "libgail17_1.8.11-4_i386.deb" from [http://packages.debian.org/etch/i386/libgail17/download](http://packages.debian.org/etch/i386/libgail17/download) and then installed it by running

sudo dpkg -i libgail17_1.8.11-4_i386.deb 

At that point, running mono-1.9.1_2-installer.bin worked fine!

---

