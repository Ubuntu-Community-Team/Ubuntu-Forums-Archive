---
title: "Hyperthreading"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by meestayenkins on 2005-12-02
First off, I'm very new to the whole linux thing so explanations have to be incredibly simply ;) 

Ok, I have a p4 3.0Ghz with HT. I just downloaded and installed the newest ubuntu. Is there any way to enable HT? I went into the device manager and under processor then advance tab I see this...

Key                                    Type        Value
processor.number              int         0(0x0)

I have read about the security issues but as far as I can tell they have been fixed.

---

### Post by 23meg on 2005-12-02
To take advantage of HT, use the 686-smp kernel.

[http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

---

### Post by frodon on 2005-12-02
here are some details on howto change your kernel : [http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

---

### Post by meestayenkins on 2005-12-02
How do I go about getting that. I've already googled it alot and have found nothing do to with downloading it. 

Sorry I realize these are probably really dumb questions...

Oh sweet, you guys are fast

---

### Post by 23meg on 2005-12-02
```
sudo apt-get install linux-image-686-smp
``` will install the latest available 686-smp kernel in the repositories.

(Note: Give a priority to forum and wiki searches and guides over Google and you'll get to answers faster. See my signature for some good places to look at. )

---

### Post by meestayenkins on 2005-12-02
Ok, i just installed it and restarted to complete teh installation.

Now, the ubuntu wont start :confused: I get a blue screen that says "Would you like to view the detailed X server output as well?" I click Yes.

In the report I do see Linux 2.6.10 i686 [ELF] so the upgrade i presume was successful.

I hit ok in that and I get the message "The X server is now disabled. Restart GDM when it is configured correctly."

Any ideas what I should do?

---

### Post by 23meg on 2005-12-02
If you have Nvidia video hardware you need to recompile the Nvidia kernel module, which practically means reinstalling the Nvidia drivers.

---

### Post by meestayenkins on 2005-12-02
worked like a charm

---

### Post by 23meg on 2005-12-02
Cool, now type ```
cat /proc/cpuinfo
``` and you should see HT mentioned somewhere.

---

### Post by meestayenkins on 2005-12-02
yep i now have a processor 0 and processor 1! thanks guys you helped alot.

---

### Post by ekravche on 2005-12-04
[QUOTE=23meg]If you have Nvidia video hardware you need to recompile the Nvidia kernel module, which practically means reinstalling the Nvidia drivers.[/QUOTE]

I've seen a 686-smp-nvidia kernel package in Ubuntu 5.10 which I presume is for nvidia video cards. It may be worth installing 686-smp-nvidia kernel  instead of recompiling the nvidia drivers.

---

### Post by Glass Casket on 2005-12-04
Thanks, I have HT too!

---

