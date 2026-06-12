---
title: "Broke my libc6 library"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by zasdarq on 2006-08-25
Hello!

I was attempting to install python-gpod which has a series of dependencies.  This includes libc6 (>= 2.3.6-6)....

zasdarq@natalie:~/Desktop$ sudo dpkg -i libgpod0*
(Reading database ... 134090 files and directories currently installed.)
Preparing to replace libgpod0 0.3.2-1.1 (using libgpod0_0.3.2-1.1_i386.deb) ...
Unpacking replacement libgpod0 ...
dpkg: dependency problems prevent configuration of libgpod0:
 libgpod0 depends on libc6 (>= 2.3.6-6); however:
  Package libc6 is not configured yet.
dpkg: error processing libgpod0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgpod0


So I attempted to download the library from a link given on the same site ([http://packages.debian.org/)](http://packages.debian.org/)).  When installing it however...

zasdarq@natalie:~/Desktop$ sudo dpkg -i libc6*
(Reading database ... 134090 files and directories currently installed.)
Preparing to replace libc6 2.3.6.ds1-3 (using libc6_2.3.6.ds1-3_i386.deb) ...
Unpacking replacement libc6 ...
Replaced by files in installed package belocs-locales-bin ...
dpkg: dependency problems prevent configuration of libc6:
 libc6 depends on tzdata; however:
  Package tzdata is not installed.
dpkg: error processing libc6 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6

So I downloaded tzdata from the same site, but that gave me this error:

(Reading database ... 134090 files and directories currently installed.)
Unpacking tzdata (from tzdata_2006g-2_all.deb) ...
dpkg: error processing tzdata_2006g-2_all.deb (--install):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package locales
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 tzdata_2006g-2_all.deb

But after attempting and failing to install the libc6 package it broke the current one, which is a fairly important library I believe (though I'm still pretty new so I could be just thoroughly confused).  So now I'm stuck with a broken libc6, no way to install the package I have, and python-gpod is still not on my computer.  ](*,)  Please help!

Thanks in advance,
-Matthew

---

### Post by zasdarq on 2006-08-25
Nevermind, was able to fix it via many of the other posts on the subject.  I didn't realize it was such a common problem!  If you're having the same problem, just run a search for libc6 or tzdata and a hundred will pop up, I lost the direct link to the one that fixed it for me.  I just ended up downloading and reinstalling the previous version of libc6.

-Matthew

---

### Post by Anduu on 2006-08-25
> **zasdarq said:**
> Nevermind, was able to fix it via many of the other posts on the subject.  I didn't realize it was such a common problem!  If you're having the same problem, just run a search for libc6 or tzdata and a hundred will pop up, I lost the direct link to the one that fixed it for me.  I just ended up downloading and reinstalling the previous version of libc6.

-Matthew

It isn't a problem at all...Ubuntu uses a certain version of libc6 for a reason...from the description of libc6:

```
GNU C Library: Shared libraries and Timezone data
[B][I][COLOR="Red"]Contains the standard libraries that are used by nearly all programs on
the system[/COLOR][/I][/B]. This package includes shared versions of the standard C library
and the standard math library, as well as many others.
Timezone data is also included.
```

Messing with important system files is bad news...you are lucky you recovered...

---

