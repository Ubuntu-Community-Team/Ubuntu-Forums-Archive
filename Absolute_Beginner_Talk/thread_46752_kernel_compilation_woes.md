---
title: "kernel compilation woes"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by zue on 2005-07-06
Hi.  I've been using linux for all of 3 weeks or so now, so I figure that qualifies me as a newbie.  First off, I just wanna say that even with the pile of problems I've been having with getting linux functional, I haven't even been tempted to boot into my Windows partition.   O:) 

So here's my immediate problem.  A few days after I first installed ubuntu I decided to update the kernel (using the very helpful HOWTO in this forum), because I needed the 2.6.12 kernel to fix a system clock problem I was having (it was going 2x too fast).  My first couple compiles wouldn't boot at all (some kind of VFS kernel panic), so I got someone else's .config file, modified it a bit, and used it to compile a kernel that would boot.  It worked, but I noticed an error on startup that had something to do with IO-APIC and NMI Watchdog.  With the help of some people more knowledgeable than myself, we narrowed this down to APIC support not being turned on when I compiled my kernel.  I was told to look for this in "Processor Type and Features" > "Local APIC support on uniprocessors" (CONFIG_X86_UP_APIC).  It wasn't there.  I decided that I must've done something really weird so I started clean with the other person's .config file again.  That's when I noticed that when I ran make xconfig I got like fifty messages like this:

```
.config:104: trying to assign nonexistent symbol X86_POPAD_OK
.config:106: trying to assign nonexistent symbol X86_INTEL_USERCOPY
.config:107: trying to assign nonexistent symbol X86_USE_PPRO_CHECKSUM
.config:112: trying to assign nonexistent symbol X86_UP_APIC
.config:113: trying to assign nonexistent symbol X86_UP_IOAPIC
.config:118: trying to assign nonexistent symbol X86_MCE_NONFATAL
```

They all look like that but with different numbers and nonexistent symbols.  This might have been happening right from the start (I may not have been paying attention to the output whem I ran make xconfig before).  Anyway, this explains why I don't have a local APIC support option to turn on. 

The next thing I tried is starting over with the next kernel revision (first one was 2.6.12.1 and now I have 2.6.12.2).  Being a dumbass I thought whatever I broke might be overwritten and all would be good.  Not so.  Now not only do I get all that nonexistent symbol stuff I had before, but I also get this error when I run make xconfig:

```
/usr/bin/ld: cannot find -lqt
collect2: ld returned 1 exit status
make[1]: *** [scripts/kconfig/qconf] Error 1
make: *** [xconfig] Error 2
```

...so I'm stuck with menuconfig.  Can somebody help me fix this mess I made?  Please?  Or am I better off just reinstalling ubuntu?

Thanks in advance,
Zue

---

### Post by zue on 2005-07-06
Oh, I should've mentioned that I got my kernel from kernel.org, not apt-get.

---

### Post by zue on 2005-07-07
Sigh.  I guess I must've really mucked it up if no-one can help me.  Ah well.  I just have one more question:

After I reinstall I'm going to have to get the 2.6.12 kernel again.  What is the absolute easiest way to do this?  

I don't mind it compiling with all the defaults.  I'll probably play around with making custom kernels again later, but first I'd really like a 2.6.12 kernel that woks that I can revert to when I muck things up again.

Thanks,
Zue

---

### Post by Brad wilkinson on 2005-07-07
ok, well you're not the newb-est here, trust me on that.

why do you even compile the kernel? I've just been using the synaptic package manager to get whatever i'm after and it just installs and runs? (using PIII and dualPIII machines)?

see. I told you there were newbier people than you......

---

### Post by varunus on 2005-07-07
Ah, the kernel compile.  Considered the first trial to go from linux newbie to linux user.   :) 

A piece of advice:  Don't use other people's kernel .config's unless its designed for your computer.  Most .config's you'll find have been customized for a specific computer.  Its best to just use Ubuntu's standard .config.  The error's you're getting about being unable to assign nonexistant symbol, that means that the .config you were using is from an older kernel version that 2.6.12.  What you really should do is copy the config file that came with Ubuntu (you can find it in /boot) and run "make oldconfig" on it.  Now, I know its text-based, but it'll keep all of the old options and only ask you about new ones.

Another thing to try, if you're feeling daring:  Breezy (the development version of Ubuntu) comes with 2.6.12.  If you want, you could download it from here:
[http://packages.ubuntu.com/breezy/base/](http://packages.ubuntu.com/breezy/base/)

Look for linux-image-2.6.12 and linux-restricted-2.6.12 and try installing them if you want.  But be warned; doing this was not meant to be done, and you may have dependency issues that stop you (though I did get away with using a Hoary kernel in Warty).  You may have to switch some of your core packages to their breezy versions.

Good luck.

---

### Post by zue on 2005-07-11
[QUOTE=varunus] The error's you're getting about being unable to assign nonexistant symbol, that means that the .config you were using is from an older kernel version that 2.6.12.[/QUOTE]

Yea, I thought about that.  The problem is, I was told that I need X86_UP_APIC = y and probably also X86_UP_IOAPIC = y in order to get rid of a APIC error I'm getting at startup which looks like this in my /var/log/dmesg file:

```
[   14.538701] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   14.538712]  failed.
[   14.538714] timer doesn't work through the IO-APIC - disabling NMI Watchdog!
[   14.539434] Uhhuh. NMI received for unknown reason 3d.
[   14.539436] Dazed and confused, but trying to continue
[   14.539438] Do you have a strange power saving mode enabled?
[   14.548551]  works.
[   14.548553] Using local APIC timer interrupts.
[   14.604416] Detected 12.436 MHz APIC timer.
[   14.604430] testing NMI watchdog ... CPU#0: NMI appears to be stuck (1->1)! 
```

...and X86_UP_IOAPIC and  X86_UP_APIC are two of those nonexistent symbols.  Should I just disable APIC in the BIOS?  ...I read in a few places that I can pass noapic as a kernel parameter, but I'm not sure how to do this.
  
> What you really should do is copy the config file that came with Ubuntu (you can find it in /boot) and run "make oldconfig" on it.  Now, I know its text-based, but it'll keep all of the old options and only ask you about new ones.

This was a good piece of advice.  I actually wanted to do this, but I didn't realize that a copy of the original .config was kept in /boot.  Thanks!  It did get rid of a few problems, though the APIC thing still persists.  And I have sound issues, but I've had those from the start.  I actually thought that my soundcard problems might be connected to my APIC problems, but since I can't fix the APIC thing I don't know.   :-?  (I'm not even sure if that makes any sense).

---

