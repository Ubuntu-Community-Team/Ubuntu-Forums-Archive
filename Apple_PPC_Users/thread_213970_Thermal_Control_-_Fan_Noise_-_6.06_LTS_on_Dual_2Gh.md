---
title: "Thermal Control - Fan Noise - 6.06 LTS on Dual 2Ghz G5"
date: 2006-07-12
forum: Apple PPC Users
---

### Post by jamesbrandongooch on 2006-07-12
I've been hunting around on the web for a solution to the fan noise/thermal control issues with Ubuntu 6.06 LTS on my Dual 2Ghz G5. I've completed the install and it boots, but it's unusable in my office environment due to the noise. Who else is having or has had this problem? Has anyone found a proper solution? Perhaps we can get a patch and a How-To going...

Oh, I also tried out a couple of other distros - Fedora Core 5 and SuSE 10.1 - neither of which exhibit the symptoms (but they ain't Ubuntu!).

---

### Post by Gailid on 2006-10-13
ya i just installed Ubuntu last night and both on the boot CD and now when i boot to Ubuntu on a Sec internal HDD, i can go about 5 min then my fan starts up. slow at first and very slowly increasion until i think its about to blast off. :confused:

---

### Post by stmiller on 2006-10-13
[http://ubuntuforums.org/showthread.php?t=232908](http://ubuntuforums.org/showthread.php?t=232908)

See post #5. You need to recompile a more recent kernel with a g5_defconfig. The kernel image on the ubuntu CD does not have support for G5 thermal.


***Forum mods? Are you there? Can we make this a sticky, along with the other iMacG5 thread? We get asked G5 questions every week here.

---

