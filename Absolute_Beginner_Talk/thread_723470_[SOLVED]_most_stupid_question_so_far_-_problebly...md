---
title: "[SOLVED] most stupid question so far - problebly.."
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by lover_of_sc on 2008-03-13
I have installed a 32bit version of ubuntu, I downloaded a 64bit version but when I tried to install it - the screen became all black. Is that because I have not got a 64bit processor? I have a HP pavilion DV9500 with a dual 2ghz processor - I would have thought they are 64bit processor? Or have I managed to find a non-working 64bit version of ubuntu? /stupid anders

---

### Post by jan quark on 2008-03-13
check the processor with and post the result of:
```
sudo lshw -C cpu
```

did you also try to install via the alternate installation ?

---

### Post by jseiser on 2008-03-13
64bit should work on a core 2 duo.  you might have burned the iso to fast, or ended up with a corrupt download, be sure to check the md5 on your downloads before you burn.  Also, sticking your model number + ubuntu into google reveals problems with your HP and ubuntu.  Some of these might be old problems, so i would first google your model number, and do a search here for it, you will find a lot of threads on this.

this looks like a good thread.

[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by Duck2006 on 2008-03-13
The only stupid question is the question that is never asked.

---

### Post by lover_of_sc on 2008-03-13
*-cpu                   
       description: CPU
       product: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.15.10
       serial: 0000-06FA-0000-0000-0000-0000
       slot: U2E1
       size: 2001MHz
       capacity: 2001MHz
       width: 64 bits
       clock: 800MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 64 bits
          capabilities: logical

---

### Post by lover_of_sc on 2008-03-13
So it looks like I have a 64bit version for sure, what is the MD5 mate? Have you got a link to  a version of the 64bit ubuntu? Thanks

---

### Post by jan quark on 2008-03-13
ubuntu releases:

[http://releases.ubuntu.com/gutsy/](http://releases.ubuntu.com/gutsy/)

burn the cd on low speed (2,4 x) and check the cd for defects. also I prefer the text based installation (alternate CD) it is more stable

---

### Post by jseiser on 2008-03-13
i imagine the problem isnt the iso, but his hardware. check the thread i posted, people have to work to get that model to work.

[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by 1875 on 2008-03-13
Boot off 64 bit Live cd press F6 at the menu screen and remove quiet and splash from the boot options.

---

