---
title: "package in Hardy not in Gutsy. Can I not get it then?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Dodelijk on 2008-01-21
Hello, 

I'm running Gutsy and want to install Abinit. I searched google and this page came up: 
[http://packages.ubuntu.com/hardy/science/abinit](http://packages.ubuntu.com/hardy/science/abinit)
But there is no equivalent for Gutsy. Does this mean that there isn't a version of this package which is compatible with Gutsy? or is there a work around so that I can install this? 

Thanks 

p.s. i'd prefer to do it through synaptic if possible

---

### Post by nikoPSK on 2008-01-21
It is usually recommended to use the ubuntu version's complying package, but I am more than certain you can install packages from fiesty or older. :)

---

### Post by Dodelijk on 2008-01-21
Do you know how I'd go about installing it? When I search in Synaptic it returns no results...

---

### Post by houstonbofh on 2008-01-21
Yes, you can but....  And there is a big "but."

Let me start with an example.  I use Qemu a lot.  In gutsy it is broken because the BOCHS VGA BIOS is broken.  It is fixed in hardy...  There was some political reason it could not be fixed in Gutsy. (This may have changed) So I grabbed the Hardy version and installed it.  All was good, and QEMU worked.

However, a package may have dependencies that are also only in hardy.  At this point, thing can get ugly fast as you chase packages that require packages, and than break other packages...  This is a lot of what the bug fix process is in the alpha testing.

So, go to the download portion of the page you showed, and click on your architecture.  This will take you to mirrors of the download.  Grab it, and click it.  It will tell you if it is easy, or dependency hell.

---

