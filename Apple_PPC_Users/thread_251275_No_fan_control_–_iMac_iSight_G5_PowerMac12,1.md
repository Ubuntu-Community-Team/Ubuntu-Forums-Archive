---
title: "No fan control – iMac iSight G5 PowerMac12,1"
date: 2006-09-05
forum: Apple PPC Users
---

### Post by kulath on 2006-09-05
Has this been reported as a bug?
 
Where should it be reported? To [http://bugzilla.kernel.org/?](http://bugzilla.kernel.org/?) can mere mortals report bugs there. Although Ubuntu bug no #23445 mentions the fan problem, I think this particular fan problem should be reported separately.
 
(Please note that this is specifically about the iMac iSight G5, because I think that thermal control has been fixed in the latest code (though it may not have made its way into the various distributions)). I don’t think there is a fix for the thermal control for the iMac iSight G5, because when I asked Benjamin Herrenschmidt in one of the forums in March whether it was fixed, he said he needed a loan of a machine to investigate it, and Googling for a possible fix I haven’t found one. Does anyone know whether that is fixed? (I think it is fixed on other revisions, but not on Rev C).


 
Also please note that this is separate from the bugs with gdm (black screen after booting into linux) and sound (hangs when a sound should be output, this is what #23445 is really about) – both of which may also be fixed. 
 
 
[1.] One line summary of the problem:    No fan control – iMac iSight G5 PowerMac12,1
[2.] Full description of the problem/report: After a short time, the fans come on full, and stay on
[3.] Keywords (i.e., modules, networking, kernel): thermal control fans
[4.] Kernel version (from /proc/version): 2.6.15-26-powerpc

---

### Post by wagerrard on 2006-09-05
Can't answer your specific questions, but I will add my voice to calls for getting Linux to work on these machines.  

I've got a very late model iMac iSight G5.  None -- as in zero -- of the distributions I've tried can even boot their install disk, even though they all claim to run happily on this hardware. That includes Ubuntu, openSUSE, and Fedora.  In all cases, the kernel starts to load, the screen goes black, the fans rev up, and everything comes to a full stop.

---

### Post by stmiller on 2006-09-05
This has been discussed by me and others on the forum. Please use the search feature. There IS fan support, in the newer Linux kernel.

 The kernel on the current ubuntu discs does not have fan support for any G5 machines, powermac or imac. You must compile your own kernel from kernel.org, doing a g5_defconfig. Anything 2.6.17 and up will support the G5 machines.

See this thread:

[http://ubuntuforums.org/showthread.php?t=232908&highlight=fans+powermac](http://ubuntuforums.org/showthread.php?t=232908&highlight=fans+powermac)

---

### Post by kulath on 2006-09-05
stmiller,

I have searched, and I agree that there is fan support for some of the G5 machines, but I do not believe that there is fan support for the latest iMac (iSight G5 Powermac 12,1), which is why I was very specific about the machine.

As you yourself say, "I have no iMac; only a powermac G5". You have a PowerMac7,3 and the fact that there is fan support for that machine does not mean that there is fan support for the latest G5.

Etienne Bersac with the help of Benjamin Herrenschmidt at [https://wiki.ubuntu.com/iMacG5revC](https://wiki.ubuntu.com/iMacG5revC) says that the fans still run at maximum speed, so are you really sure that the fan issue has been fixed for the latest G5? I really don't want to go to all the trouble of dowloading and compiling a kernel just to find it doesn't work anyway.

---

### Post by Torrance on 2006-09-05
Please follow this How To: [http://ubuntuforums.org/showthread.php?t=248238](http://ubuntuforums.org/showthread.php?t=248238)

The thermal support options in the kernel have 7,1 ; 8,1 and 12,1 options enabled. I'm not completely sure this means revC will work, but the kernel at least *suggests* that it will. It'd be worthwhile finding out. :)

---

### Post by stmiller on 2006-09-05
Okay, sorry man. When you posted this line:

"[4.] Kernel version (from /proc/version): 2.6.15-26-powerpc"

it seemed that you haven't tried a more recent kernel. It is obvious there is no fan support with a pre 2.6.17 kernel. (Not built in, anyways)
 Try the latest kernel. And check out the gentoo ppc forums. Several iMac G5 users on there.

---

### Post by kulath on 2006-09-05
Torrence,

Can you tell me where the kernel has support options for 12,1 enabled? (Are you looking at a particular file that says this is supported?)

The latest patch information I could find was a message (in Gentoo and elsewhere) in May this year from Robin Hugh Johnson which said:
I'm working on the windfarm thermal drivers, trying to support:
- absolutely all of the sensors available
- write windfarm modules for as-yet unported or unwritten machines
  (Current list is PowerMac3,6 PowerMac7,2, PowerMac12,1)."

stmiller's Powermac7,3 was supported by a specific patch in Oct 04:
2004/10/22 07:31:28-07:00 benh
[PATCH] ppc64: Update G5 thermal control driver

This patch updates the G5 thermal control driver, the main change
is support for the new "PowerMac7,3" type desktops including the
dual 2.5Ghz with liquid cooling.

Signed-off-by: Benjamin Herrenschmidt <benh@kernel.crashing.org>
Signed-off-by: Linus Torvalds <torvalds@osdl.org>

---

### Post by Torrance on 2006-09-06
From the kernel config:
```
# Macintosh device drivers
#
CONFIG_ADB_PMU=y
# CONFIG_ADB_PMU_LED is not set
CONFIG_PMAC_SMU=y
CONFIG_THERM_PM72=y
CONFIG_WINDFARM=y
CONFIG_WINDFARM_PM81=y
CONFIG_WINDFARM_PM91=y
CONFIG_WINDFARM_PM112=y
```
So, unfortunately, there is no thermal support for PowerMac12,1 and therefore the iMacG5 Rev C (iSight).

---

### Post by kulath on 2006-09-08
I'm not quite sure how the list of kernel device drivers establishes that there is no support for the fans in Powermac12,1, but I will take your word for it.

So... that takes us back to my original quetsion, is this reported as a bug, and if not, should I do so?

It does rather mean that there is probably little point in building a new kernel on the machine, because I suspect that the gdm display issue may be resolved by a change to the ocnfig file, and I need to disable sound to stop the freeze, and there is not much point in enabling it when the fans are making so much noise.

---

### Post by Torrance on 2006-09-09
> I'm not quite sure how the list of kernel device drivers establishes that there is no support for the fans in Powermac12,1, but I will take your word for it.
I'm just going by what configurations the kernel allows to build for - I assume that is representative of what the kernel can support in actuality.

> It does rather mean that there is probably little point in building a new kernel on the machine, because I suspect that the gdm display issue may be resolved by a change to the ocnfig file, and I need to disable sound to stop the freeze, and there is not much point in enabling it when the fans are making so much noise.
The GDM issue is directly related to an improperly compiled kernel. Even without thermal control, the iMac G5 Rev C will still benefit from a new kernel in that it will load properly, and also have sound.

---

### Post by stmiller on 2006-09-09
What do you have to loose with trying a new kernel? It sounds like you already have Linux installed. Try the latest from kernel.org and let us know what you find out.

From that ubuntu iMacRevC page:

> The fans still run at the maximum speed, Airport Extreme support is not compiled, but this is a great step toward support those last PPC boxes from Apple.

He would have A.E. support if he enabled broadcom wireless in the kernel. And why use a kernel image from ppcimage.org? Just get the latest from the source! That kernel image he is using may be trying to load the thermal control with modules instead of built-in from the kernel. The g5_defconfig enables all the built-in thermal goodness.

***Also: I just noticed that wiki author is not even using the correct kernel image for a G5!! 

So you are better off compiling your own to enable what you need with a g5_defconfig.

---

### Post by kulath on 2006-09-10
I have never build a kernel myself before, and it looks rather difficult, as well as probably taking a long time to download all the necessary bits (even with 1Meg broadband)

I was trying to find out whether the fan issue had ever been solved - and I am still no clearer.

I thought the gdm issue in Dapper was due to incorrect xorg.conf information, and could be resolved just by correcting that - or am I wrong?

---

### Post by Torrance on 2006-09-11
No, the GDM issue is a conflicting sound module - it freezes when GDM makes a start up sound.

The kernel compile is quite easy, and a 40mb download (which is only 15 minutes with a 1mbit connection). Just go to the "How TO: iMac G5" thread which will guide you through the whole process. I learnt how to do it off the cuff from a newbie status, so I'm sure you'll be able to follow it. :D

With regards to the fan - I think the issue is probably not going to be fixed by a new kernel, but we'll only know if you test it.

---

### Post by stmiller on 2006-09-11
See post #5, I explained how to download and compile a new kernel from kernel.org:

[http://ubuntuforums.org/showthread.php?t=232908&highlight=fans+powermac](http://ubuntuforums.org/showthread.php?t=232908&highlight=fans+powermac)

I posted this link earlier in this very thread.

A new kernel compile is REQUIRED to get Linux working correctly on any G5 machine, at the moment. PPC support is being aggressively done on the current kernels. Any kernel in the ubuntu repositories WILL NOT WORK, as you need a specific kernel config (g5_defconfig).

And search the gentoo ppc forum. There might be help there. They know ppc linux better than anyone else out there.

---

