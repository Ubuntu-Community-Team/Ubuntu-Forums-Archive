---
title: "Hard Wine"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-10-28
I tried to install wine from their website, but they don't really provide us 64bit people with an easy way to install it. Can somebody tell me how to install it on a 64bit computer?

---

### Post by AlReece45 on 2006-10-28
Compiling didn't work for me, at first I forced archetecture on the .deb package; but now I created a chroot environment and run it from there. Its easier for me to keep it up to date that way.

---

### Post by OptimusPrime on 2006-10-28
Even after I add the repo's, I get this:

wesley@wesley-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

---

### Post by OptimusPrime on 2006-10-28
I even did apt update:

Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
99% [Connecting to packages.freecontrib.org]
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Temporary failure resolving 'packages.freecontrib.org'
Fetched 5B in 45s (0B/s)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Temporary failure resolving 'packages.freecontrib.org'
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/non-free/binary-amd64/Packages.gz](http://dl.google.com/linux/deb/dists/stable/non-free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by OptimusPrime on 2006-10-28
Is there a different repository?  It looks like these don't even exist.

---

### Post by OptimusPrime on 2006-10-28
> **AlReece45 said:**
> Compiling didn't work for me, at first I forced archetecture on the .deb package; but now I created a chroot environment and run it from there. Its easier for me to keep it up to date that way.

I'm not really sure what chroot even is.  I just want wine to work!  I think I got something, but I can't really figure out how to use it:

wesley@wesley-laptop:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
wesley@wesley-laptop:~$ wine PROGRAM
wine: could not load L"c:\\windows\\system32\\PROGRAM.exe": Module not found

---

### Post by OptimusPrime on 2006-10-28
If it can't be done, just say so.  I don't want to waste hours of my life on my threads that no more than one person ever visits](*,)

---

### Post by Gaute65 on 2006-10-28
You can use automatix to install wine. [http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

### Post by AlReece45 on 2006-10-28
> **OptimusPrime said:**
> I'm not really sure what chroot even is.  I just want wine to work!  I think I got something, but I can't really figure out how to use it:

wesley@wesley-laptop:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
wesley@wesley-laptop:~$ wine PROGRAM
wine: could not load L"c:\\windows\\system32\\PROGRAM.exe": Module not found

Well, it looks like you got most of it done. Try running winecfg and see if it loads up.

---

### Post by OptimusPrime on 2006-10-28
wesley@wesley-laptop:~$ winecfg
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
wesley@wesley-laptop:~$

---

### Post by AlReece45 on 2006-10-28
That looks like another problem entirely (with X). I've encountered it a few times when playing DVDs. I believe its something with memory available for windows or something. Try closing some graphical things (windows) and try (or if you want, google the problem and see if you can find out more about it than me)

---

### Post by claydoh on 2006-10-28
Wine is and probably will be a bit of a pain on 64 bit systems, so don't expect too much untill the wine developers can tackle that.

I did find a few links searching the forums, here is one:
[http://ubuntuforums.org/showthread.php?t=185557](http://ubuntuforums.org/showthread.php?t=185557)

---

