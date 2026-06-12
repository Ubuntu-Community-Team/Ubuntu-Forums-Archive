---
title: "Kernel panic, can't boot after update"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by zemadz on 2008-03-18
Hello,

I ran into troubles after installing updates via Synaptic Package Manager. When rebooting the kernel now panics.

```
Starting up ...
[ 0.4920001 ] .. MP-BIOS bug: 8254 timer not connected to IO-APIC
[ 0.4960001 ] Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the 'noapic' option
```

When I edit the boot parameters at the startup, adding noapic causes the computer to just reboot instead of booting up. However I can use the recovery mode to boot Ubuntu up. What should I do to solve this problem? Install the previous version of kernel back from the Ubuntu CD or are there any better solutions?

Thanks

---

### Post by forrestcupp on 2008-03-18
What updates were you installing and exactly how were you installing them?  

You're not using Hardy Heron testing version of Ubuntu, are you?  If so, is there more than one kernel option in your grub menu?  If so, select an older one.

Also, did you ever install video drivers either with Envy or with the proprietary drivers downloaded from your video card manufacturer's web site?  I'm sure that's not the problem, but it might be useful to know.

---

### Post by zemadz on 2008-03-18
I was using Ubuntu 7.10 that is available for download at the moment (I downloaded it yesterday). Today I wanted to update things so I checked some things in the Software Sources program under the "Updates" tab and opened Synaptic Package Manager. Selected all updates that were available and started the progress.

There are two kernel options in my Grub menu. First has only the kernel name, the second has the same kernel name with "(recovery mode)" after it. That one works, but I doubt that it is meant for everyday use why else the "recovery mode" name.

I have installed some video drivers, but I didn't use Envy and neither the drivers from Nvidia website. I believe it was the Synaptic Package Manager where I selected the "nvidia" and installed them that way.

---

### Post by zemadz on 2008-03-18
The only difference between the "recovery mode" and usual one is that one has "single" parameter, the other has "splash quiet". Visually the "recovery mode" isn't different from the usual one I used, I can play 3D games there and Compiz works too.

---

### Post by forrestcupp on 2008-03-18
Try doing the noapic thing like [this](http://ubuntuforums.org/showpost.php?p=4385355&postcount=4)

Edit:
I guess you can't boot, so you can't do it like that.  Do it from the recovery mode and use nano instead of gedit.  Also, you don't have to use sudo in recovery mode because you're already root.

Nano is a CLI text editor.  When you're done, ctrl+x exits and gives you the option to save.

---

### Post by zemadz on 2008-03-18
Tried it, but now it hangs at "Waiting for root file system".

---

