---
title: "Suspend/Resume freeze on MacBookAir4,1 Ubuntu 14.04 LTS"
date: 2014-05-16
forum: Apple Hardware Users
---

### Post by cloudane2 on 2014-05-16
Hi,
Sorry if this has been mentioned already, I have attempted a few searches.

I'm running Trusty on my MacBook Air Mid 2011 (4,1) and roughly 1 in 5 times that I put it to sleep, it won't wake up again.  If I then force a power off (holding the power button) and start it back up, it offers to send a crash report regarding a suspend/resume KernelOops error.

I have tried the latest Trusty mainline kernel (3.15rc2), no difference

However without X running (sudo service lightdm stop, log in from the text console) if I sleep it from there, which of course requires a command:
```
echo "mem" | tee /sys/power/state
```
It's fine.  I have done countless suspend/resume cycles with no problems in text mode, although once or twice it could only be woken up from a tap of the power button, while the rest of the time any key will wake it.  I'm not sure if it's related at all.

My instincts point me towards i915 / the xorg intel driver.  Just wondering if there's anything else I can try.  I have tried changing the AccelMode to UXA instead of SNA (as one would try in Arch [https://wiki.archlinux.org/index.php/Intel_Graphics](https://wiki.archlinux.org/index.php/Intel_Graphics)) but that didn't help either.


Edit: to be exact it hangs on sleep, not on resume.  The keyboard stays lit.
Edit 2: also tried setting NoAccel on the intel driver, and i915.semaphores=1 as a boot parameter.
Edit 3: tried this kernel here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2014-05-07-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2014-05-07-utopic/)  - interestingly, this one freezes with the screen on and showing the last frame before it froze.  But still freezes.
Edit 4: tried the latest graphics stack here [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
I'm completely out of ideas :(  Frustrating... I have Ubuntu set up 99% perfectly, if not for this massive showstopper that will probably end in me going back to OS X :(

---

### Post by cloudane2 on 2014-05-18
I suspect my problem lies within the  Intel graphics driver somewhere in the kernel.  But for the benefit of  anyone searching, I may have found a workaround for my version of the  problem...

 For me it only freezes on suspend if X is showing at the time.  If  it's on any of the virtual terminals, it's fine.  So I created /etc/pm/sleep.d/5_crashfix containing:
#! /bin/sh
case $1 in
  suspend|suspend_hybrid|hibernate)
    /bin/chvt 1
    ;;
  resume|thaw)
    /bin/chvt 7
    ;;
esac

 Then chmod +x to the 5_crashfix file.

 This changes to VT1 on suspend, and changes back to X on resume, which I think bypasses the bug.


 Unfortunately 
a) I don't know "what I'm doing" well enough to try and  report anything upstream, I think it's too vague for them to do anything  useful with.
              
b) As it's intermittent, it's hard to say for certain if this works.  So far so good based on maybe 40 or 50 suspend/resume cycles, but only a significant amount of time can tell for sure.

---

### Post by saviq2 on 2014-06-21
> **cloudane2 said:**
> 
 Unfortunately 
a) I don't know "what I'm doing" well enough to try and  report anything upstream, I think it's too vague for them to do anything  useful with.

I've the same here, have filed an ubuntu bug for now - [http://pad.lv/1332885](http://pad.lv/1332885)

> **cloudane2 said:**
> 
 This changes to VT1 on suspend, and changes back to X on resume, which I think bypasses the bug.

I've applied this workaround now, I'll report back whether it works or not.

---

### Post by ceres2 on 2015-02-23
Hi,

> **cloudane2 said:**
> I suspect my problem lies within the Intel graphics driver somewhere in the kernel. But for the benefit of anyone searching, I may have found a workaround for my version of the problem...

For me it only freezes on suspend if X is showing at the time. If it's on any of the virtual terminals, it's fine. So I created /etc/pm/sleep.d/5_crashfix containing:
tell for sure.

i tried this crashfix today on my 6,1 Macbook air w/ 14.04.2
For some reason it seems not to execute the 5_crashfix script, neither in suspend nor wake up.
it executes the other two scripts therein, but not this.

However i found a fix in a .deb package from this source:
[https://github.com/patjak/mba6x_bl](https://github.com/patjak/mba6x_bl)

This now strangly gives a black screen, when the system is booted, but closing the lid, waiting for the laptop to suspend and opening again. And from then on in the session it works!

Regards,
 CereS.

---

### Post by este.el.paz on 2015-02-28
Just chiming in here to say that "yes" there are problems with suspend/resume for a number of my computers, both PPC & MBPro '10 . . . UbuntuMATE PPC and LM17 on the MBPro.  I posted a bug report on Launchpad at one point . . . can't remember if that's the one that got "closed" after a month . . . nobody seemed too interested in a fix.  I added some swap space on my iBook to see if that alleviated the problem . . . didn't seem to make a difference . . . .  I have dual-boot or triple-boot set ups, if I need to "sleep" I reboot into OSX partition . . . seems to "solve" the problem.  A few incarnations of LM back I could suspend/resume without too much problem, then I would have to log out to do it, now LM17 MBPro if I suspend the apple logo stays lit and the fan keeps running . . . doesn't seem too "suspended" . . . .  If someone here wants to search through LP Bugs and see if there is one there, or try reviving mine, then post the bug number here and I'll add my items to it.

e.e.p.

---

### Post by krumm2 on 2015-04-13
The issue I have with my MBA 6,2 is when I close the lid to suspend, sometimes it wakes back up after the lid is closed and runs down the battery... Really annoying.

---

### Post by este.el.paz on 2015-04-13
> **krumm2 said:**
> The issue I have with my MBA 6,2 is when I close the lid to suspend, sometimes it wakes back up after the lid is closed and runs down the battery... Really annoying.

@krumm2:

Yes, it is annoying . . . although I believe in LM 17.1 if I log out, remove any peripherals like the mouse and then click "suspend" from the log in manager window . . . there is less tendency to "wake up" with the lid closed.  If I click suspend and then un-plug the mouse . . . certainly it will "wake" . . . .  Some of that "running down the battery" could possibly be handled in "power manager" to "spin down the HD" after a certain number of minutes . . . on battery.

e...

---

### Post by krumm2 on 2015-04-13
So... I had been messing about with kernels, and had updated to to a 3.16.0-31 kernel. Which I had forgotten I done. Duh... I switched back to 3.13.0-37 and this seems to have resolved the issue for me.

---

