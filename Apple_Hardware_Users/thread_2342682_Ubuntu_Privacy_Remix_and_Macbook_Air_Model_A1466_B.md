---
title: "Ubuntu Privacy Remix and Macbook Air Model A1466 Booting Issues"
date: 2016-11-08
forum: Apple Hardware Users
---

### Post by codestaxx on 2016-11-08
I've completely exhausted myself trying different boot parameters to get UPR to boot on my Macbook Air Model A1466.  It has the Broadwell 1.6ghz Intel HD 6000 chipset.  I created a UPR drive with Rufus and I can get UPR to load to the selection screen, I would Start UPR, however, it would fault out with the error:


**hda_intel: azx_get_response timeout, switching to single cmd mode:  last cmd=0x000f0001**

Obviously I tried the safe mode to see if that would fix it.  Nope!  I've tried editing the boot/grub/grub.cfg file to no avail.  As you can see from my current desperation (to include possible Skylake parameters) in my config attempts - I've failed miserably.

```
--class=upr $"Start"" Ubuntu Privacy Remix" { 
    linux    /casper/vmlinuz2 boot=casper quiet splash noprompt nopersistent ibata.force=noncq i915.preliminary_hw_support=1 nouveau.blacklist=1 edd=on nolapic pcie_aspm=force tpm_tis.interrupts=0 i915.modeset=0 i915.i915_enable_rc6=1 video=VGA-1:1440x900-24@60 video=1440x900-24@60 video.use_bios_initial_backlight=0 -- 
```

I've tried:

nomodeset
vga=868
nolapic
acpi=off
acpi="linux"
 

And many others I can't think of right now.

I would really appreciate a suggestion.  TIA

---

### Post by QIII on 2016-11-09
Moved to Apple Hardware Users.

You may get better help here, but since you are not using a recognized Ubuntu flavor (you are using an OS ***BASED*** on Ubuntu, not Ubuntu, and there is no guarantee that they developers have not done something unique) that is not certain.

---

### Post by codestaxx on 2016-11-09
Thank you for the move!


Bumpies!

---

