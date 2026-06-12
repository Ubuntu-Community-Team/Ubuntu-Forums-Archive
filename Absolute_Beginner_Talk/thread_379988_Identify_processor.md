---
title: "Identify processor"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by xyz on 2007-03-09
Hi,
I'm currently trying to compile kernel according to this howto:
[Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel")
I'm at the point where, in the terminal, I'm asked to chose which is my processor and, for the life of me, I'm confused as to which it is:
> Processor family
  1. 386 (M386)
> 2. 486 (M486)
  3. 586/K5/5x86/6x86/6x86MX (M586)
  4. Pentium-Classic (M586TSC)
  5. Pentium-MMX (M586MMX)
  6. Pentium-Pro (M686)
  7. Pentium-II/Celeron(pre-Coppermine) (MPENTIUMII)
  8. Pentium-III/Celeron(Coppermine)/Pentium-III Xeon (MPENTIUMIII)
  9. Pentium M (MPENTIUMM)
  10. Core 2/newer Xeon (MCORE2) (NEW)
  11. Pentium-4/Celeron(P4-based)/Pentium-4 M/older Xeon (MPENTIUM4)
  12. K6/K6-II/K6-III (MK6)
  13. Athlon/Duron/K7 (MK7)
  14. Opteron/Athlon64/Hammer/K8 (MK8)
  15. Crusoe (MCRUSOE)
  16. Efficeon (MEFFICEON)
  17. Winchip-C6 (MWINCHIPC6)
  18. Winchip-2 (MWINCHIP2)
  19. Winchip-2A/Winchip-3 (MWINCHIP3D)
  20. GeodeGX1 (MGEODEGX1)
  21. Geode GX/LX (MGEODE_LX)
  22. CyrixIII/VIA-C3 (MCYRIXIII)
  23. VIA C3-2 (Nehemiah) (MVIAC3_2)
choice[1-23]: 


Processor Information:
> Socket Designation: uFC-PGA Socket
        Type: Central Processor
        Family: Celeron
        Manufacturer: Intel Corporation
        ID: 29 0F 00 00 00 00 00 00
        Signature: Type 0, Family 15, Model 2, Stepping 9
        Flags: None
        Version:
        Voltage: 1.5 V
        External Clock: 100 MHz
        Max Speed: 2700 MHz
        Current Speed: 2700 MHz
        Status: Populated, Enabled
        Upgrade: ZIF Socket
        L1 Cache Handle: 0x0012
        L2 Cache Handle: 0x0013
        L3 Cache Handle: Not Provided

Handle 0x0009, DMI type 5, 20 bytes.

 *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.70GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: uFC-PGA Socket
          size: 2700MHz
          capacity: 2700MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 8KB
             capacity: 8KB
             clock: 1GHz (1ns)
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 128KB
             capacity: 128KB
             clock: 1GHz (1ns)
             capabilities: internal write-back


Thanks for your help.

---

### Post by igknighted on 2007-03-09
P4 based celeron at that clock speed. (11)  G/L w/ the compile, it took me a few times to get it right, buts a great feeling when you do.  Be ready for this to keep you system occupied for 3hrs or so on a system like that.

---

### Post by xyz on 2007-03-09
> **igknighted said:**
> P4 based celeron at that clock speed. (11)  G/L w/ the compile, it took me a few times to get it right, buts a great feeling when you do.  Be ready for this to keep you system occupied for 3hrs or so on a system like that.
Thanks I'll go for 11 and see what happens!
Can you please explain a bit more what exactly (based on my processor info) told you it's 11?...just so I understand!

---

### Post by igknighted on 2007-03-09
> **xyz said:**
> Thanks I'll go for 11 and see what happens!
Can you please explain a bit more what exactly (based on my processor info) told you it's 11?...just so I understand!

Mainly process of elimination.  It's def a Celeron, so it must be 7, 8, or 11.  No PIII or PII chip can clock as high as 2.7ghz without massive overclocking, and if you knew enough to do that you probably don't ask this question ;-).  Hence we eliminate 7 and 8, and 11 is our choice.  Mine was nice and easy, theres only one Athlon64 choice ;-)

---

### Post by xyz on 2007-03-09
Yes you're right! I'm realizing -from questions it's asking me now- I got into something I really don't know enough about. I should've studied the question lots more!!

Tell me...would it be a good idea, at this point, to stop this and use my backup.tgz to restore?

---

### Post by igknighted on 2007-03-09
> **xyz said:**
> Yes you're right! I'm realizing -from questions it's asking me now- I got into something I really don't know enough about. I should've studied the question lots more!!

Tell me...would it be a good idea, at this point, to stop this and use my backup.tgz to restore?

I'd go for it.  Following those instructions the absolute worst thing that will happen is you'll have a no-good kernel installed, but the old working ones will still be there if it fails.  Even in this case you still learn something.  That is a good guide, I used it too.  Worked perfectly when I had failed several times before.

EDIT: PS, i love your avatar

---

### Post by xyz on 2007-03-09
Ok I'll try...but...
These are the last lines of my terminal:
> Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

and then "qconf" opened all by itself  which is logical since it's not 'confed' right.
Oh boy...when I take a look at the number of questions I'll need to answer right...well...I don't really feel confident! But we'll see!

PS: Thnx for the avatar! First time I saw I just kept lauging for about 1 hout!!
You up quite early over there in NY?

---

### Post by igknighted on 2007-03-09
Done with classes for the week and next week is our spring break... so im pulling the obligatory all nighter.  Most questions click help if you don't know and they will say "if you don't know, say blank".  Make sure you select ext2/ext3 file system support built into the kernel, not as a module.  Otherwise it wont boot.

The session reject thing is kde's debug output.  It's normal, ignore it.  qconf is a qt (KDE) app.

---

### Post by xyz on 2007-03-09
OK Thanks again and Happy Spring break! Those were good 'ol times for me back when I was at UCB in California.

---

### Post by xyz on 2007-03-09
Well it took 4 hours but it works. I don't yet know if 'eveything' works but I rebooted fine!
So far so good! I can't believe it; first time I do this.
Now this process increased my disk usage by about 10%! Seems a lot to me, isn't it?
I know it's a good idea to keep at least 2 kernels but I need to make some space.
so...my menu.lst:
> title           Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=d2f96cdc-6a84-4bc2-98a4-442b70eeb7bf ro single
initrd          /boot/initrd.img-2.6.17-11-386
boot

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=d2f96cdc-6a84-4bc2-98a4-442b70eeb7bf ro ro quiet splash elevator=cfq
initrd          /boot/initrd.img-2.6.17-11-generic
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=d2f96cdc-6a84-4bc2-98a4-442b70eeb7bf ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

But Synaptic reports this:
> linux-image-2.6.17-11-386
linux-image-2.6.17-11-generic
linux-image-2.6.20.1   
linux-image-386
linux-image-686
linux-image-generic 2.6.17.11

Which would you advise me to delete?

PS: so far it is much faster...is what I can say as of now!

---

### Post by Hatrist on 2007-03-09
I am currently following that Master Kernel guide.
Have an Athlon XP 2500+ processor, so I have to choose **13. Athlon/Duron/K7 (MK7)**, right?

---

### Post by xyz on 2007-03-09
Hi,
It would seem that you are right since there is only one Athlon in the list.
Hope it works for you, too.

---

### Post by igknighted on 2007-03-09
Glad to hear it worked!  The kernel source is a big disk hog, but it you can get away with it I would leave it.  If you need to install any modules (like for 3rd party drivers) it needs the source to build against.  You can purge the apt's cache to delete all the leftovers from packages you have downloaded, although I'm not positive how to do that.

---

### Post by xyz on 2007-03-10
> If you need to install any modules (like for 3rd party drivers) **it needs the source to build against.**
Yes..obviously! Thnx for reminding me!
*So far I can only report that "brightness" has disappeared.*

I like to delete stuff this way:
```
root@luser:/var/cache/apt/archives#
```
```
root@luser:/var/cache/apt/archives# shred -fuzv vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb

```
and this is what will happen then in the terminal:

> shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 1/26 (random)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 2/26 (db6db6)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 3/26 (249249)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 4/26 (111111)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 5/26 (666666)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 6/26 (777777)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 7/26 (222222)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 8/26 (dddddd)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 9/26 (444444)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 10/26 (aaaaaa)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 11/26 (b6db6d)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 12/26 (888888)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 13/26 (random)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 14/26 (000000)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 15/26 (ffffff)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 16/26 (cccccc)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 17/26 (333333)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 18/26 (eeeeee)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 19/26 (6db6db)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 20/26 (492492)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 21/26 (999999)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 22/26 (924924)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 23/26 (555555)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 24/26 (bbbbbb)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 25/26 (random)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: pass 26/26 (000000)...
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: removing
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: renamed to 0000000000000000000000000000000000000000000000
shred: 0000000000000000000000000000000000000000000000: renamed to 000000000000000000000000000000000000000000000
shred: 000000000000000000000000000000000000000000000: renamed to 00000000000000000000000000000000000000000000
shred: 00000000000000000000000000000000000000000000: renamed to 0000000000000000000000000000000000000000000
shred: 0000000000000000000000000000000000000000000: renamed to 000000000000000000000000000000000000000000
shred: 000000000000000000000000000000000000000000: renamed to 00000000000000000000000000000000000000000
shred: 00000000000000000000000000000000000000000: renamed to 0000000000000000000000000000000000000000
shred: 0000000000000000000000000000000000000000: renamed to 000000000000000000000000000000000000000
shred: 000000000000000000000000000000000000000: renamed to 00000000000000000000000000000000000000
shred: 00000000000000000000000000000000000000: renamed to 0000000000000000000000000000000000000
shred: 0000000000000000000000000000000000000: renamed to 000000000000000000000000000000000000
shred: 000000000000000000000000000000000000: renamed to 00000000000000000000000000000000000
shred: 00000000000000000000000000000000000: renamed to 0000000000000000000000000000000000
shred: 0000000000000000000000000000000000: renamed to 000000000000000000000000000000000
shred: 000000000000000000000000000000000: renamed to 00000000000000000000000000000000
shred: 00000000000000000000000000000000: renamed to 0000000000000000000000000000000
shred: 0000000000000000000000000000000: renamed to 000000000000000000000000000000
shred: 000000000000000000000000000000: renamed to 00000000000000000000000000000
shred: 00000000000000000000000000000: renamed to 0000000000000000000000000000
shred: 0000000000000000000000000000: renamed to 000000000000000000000000000
shred: 000000000000000000000000000: renamed to 00000000000000000000000000
shred: 00000000000000000000000000: renamed to 0000000000000000000000000
shred: 0000000000000000000000000: renamed to 000000000000000000000000
shred: 000000000000000000000000: renamed to 00000000000000000000000
shred: 00000000000000000000000: renamed to 0000000000000000000000
shred: 0000000000000000000000: renamed to 000000000000000000000
shred: 000000000000000000000: renamed to 00000000000000000000
shred: 00000000000000000000: renamed to 0000000000000000000
shred: 0000000000000000000: renamed to 000000000000000000
shred: 000000000000000000: renamed to 00000000000000000
shred: 00000000000000000: renamed to 0000000000000000
shred: 0000000000000000: renamed to 000000000000000
shred: 000000000000000: renamed to 00000000000000
shred: 00000000000000: renamed to 0000000000000
shred: 0000000000000: renamed to 000000000000
shred: 000000000000: renamed to 00000000000
shred: 00000000000: renamed to 0000000000
shred: 0000000000: renamed to 000000000
shred: 000000000: renamed to 00000000
shred: 00000000: renamed to 0000000
shred: 0000000: renamed to 000000
shred: 000000: renamed to 00000
shred: 00000: renamed to 0000
shred: 0000: renamed to 000
shred: 000: renamed to 00
shred: 00: renamed to 0
shred: vim-runtime_1%3a7.0-164+1ubuntu6~edgy1_all.deb: removed


Of course you can also open "Computer" as root, go to :/var/cache/apt/archives and delete by hand.

---

### Post by Crooksey on 2007-03-10
Just remember to keep the generic kernel, because when you have to run a dist-upgrade, I don't think It will run that great on a custom kernel.

---

### Post by matthekc on 2007-03-10
i was wondering could he just burn the source to cd then use it later?

---

### Post by xyz on 2007-03-10
> Just remember to keep the generic kernel, because when you have to run a dist-upgrade, I don't think It will run that great on a custom kernel.
Thanks.
> i was wondering could he just burn the source to cd then use it later?
Reply With Quote
No idea!!

---

### Post by igknighted on 2007-03-10
> **matthekc said:**
> i was wondering could he just burn the source to cd then use it later?

Should work, but remember it has to be symlinked to /usr/src/linux.  Also, don't try to build modules with the source on the CD as it may need to edit some of the files.

---

