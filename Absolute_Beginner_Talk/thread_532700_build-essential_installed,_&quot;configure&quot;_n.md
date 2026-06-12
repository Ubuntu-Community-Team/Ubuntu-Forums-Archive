---
title: "build-essential installed, &quot;configure&quot; not found"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Zilphanael on 2007-08-23
I have build-essential installed, apparently without a hitch.  However, when I try to use the command "configure" or even "./configure", all I receive is "command not found" for the former or "no such file or directory" for the latter.  Any thoughts on why this might be occuring and how it might be fixed?

I'm running Feisty 7.04, by the way.

---

### Post by ramjet_1953 on 2007-08-23
What is the file you are trying to configure?

Is it in a tar, or tar.gz format?

Perhaps it is a perl script?

Regards,
Roger 8)

---

### Post by aquavitae on 2007-08-23
the configre script is not directly dependant on build-essential - it is a bash script (usually) included in the source package you downloaded.  What are you trying to configure?  You should be in the top level directory of the source package, and there should be a file called configure.  I say "should", but really it depends on what you're compiling - different packages use different methods, so there might not even be a configure script.  It would help if you told us what the package is.

---

### Post by Bachstelze on 2007-08-23
Not all .tar.* archive contain source code, and not all source code has a configure script. Please read the installation instructions for whetever you are trying to install.

---

### Post by heimo on 2007-08-23
> **Zilphanael said:**
> I have build-essential installed, apparently without a hitch.  However, when I try to use the command "configure" or even "./configure", all I receive is "command not found" for the former or "no such file or directory" for the latter.  Any thoughts on why this might be occuring and how it might be fixed?

I'm running Feisty 7.04, by the way.

What others have already said is true. I just add that you should have a good reason to compile software and if you tell us what it is that you're doing, it's perfectly possible that there's already better way to do it, like installing straight from repositories using Synaptic Package Manager.

---

