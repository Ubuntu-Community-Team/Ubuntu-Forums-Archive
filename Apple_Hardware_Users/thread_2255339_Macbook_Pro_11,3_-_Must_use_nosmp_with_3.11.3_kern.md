---
title: "Macbook Pro 11,3 - Must use nosmp with 3.11.3 kernel"
date: 2014-12-04
forum: Apple Hardware Users
---

### Post by karypid on 2014-12-04
Hi,

I have a mid-2014 Haswell Macbook Pro (15" retina display) and I installed Ubuntu 14.04 LTS on it, using this guide:
[https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)

I am using Apple's EFI to boot (hold down Alt key, installation shows up as "Windows" and when I select it grub takes over).

My problem is that when I start ubuntu it hangs on a blank screen and if you wait the laptop gets hot, as if it is busy-waiting or something with 100% CPU usage.

I held shift after selecting windows and went into grub, then edited the command line to remove quiet and use nosplash. When loading I saw in the kernel logs that it gets stuck while initializing SMP. I added "nosmp" and was able to start ubuntu.

So, my question is, how can I enable SMP? I have updated to the latest kernel as of yesterday, but I still get the "freeze" during startup. I'd appreciate any pointers on what to try. I googled around a bit and found conflicting information, mostly due to the several factors involved. It seems that this may or may not work based on kernel version. whether you are using legacy bios mode or EFI, whether you are using grub or grub-efi, etc.

As far as I could tell, my combination should work.

- Use Apple's EFI (not refit)
- Use normal grub (not grub-efi as Apple EFI no understands common grub)

Any help on what else to try will be appreciated. Thanks in advance!

P.S. I have added "[COLOR=#333333][FONT=UbuntuMono]libata.force=noncq[/FONT][/COLOR]" to my kernel params as per the instructions and ran update-grub; my hang is not intermittent it is permanent and prevents booting with SMP.

---

### Post by karypid on 2014-12-04
It seems like I misinterpreted the situation. There is a kernel bug report for this, but the decision is NOT to fix it: [https://bugzilla.kernel.org/show_bug.cgi?id=60635#c19](https://bugzilla.kernel.org/show_bug.cgi?id=60635#c19)

Apparently one _does_ need grub-efi anyway; when simple grub is used, it switches again back to compatibility mode which seems to trigger the bug. I guess the other option is to use rEFInd

---

