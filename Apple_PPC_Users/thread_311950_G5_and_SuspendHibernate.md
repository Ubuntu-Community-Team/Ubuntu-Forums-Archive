---
title: "G5 and Suspend/Hibernate"
date: 2006-12-03
forum: Apple PPC Users
---

### Post by Torrance on 2006-12-03
I've been talking to Ben H a bit and he says it may be possible to suspend-to-disk my iMac G5 (and presumably other G5's). He says Standby (suspend-to-ram) is a no-go since the machines are SMU based and there's no support for this, and also since Nvidia chips currently do not wake up very well.

So I've looked into it a bit. Currently, the power management functions in the Vanilla kernel don't do anything. However, suspend 2 ([http://www.suspend2.net/)](http://www.suspend2.net/)), which is not yet part of the vanilla kernel but can be applied as a patch, is rumoured to provide much better support for suspend/hibernation. Unfortunately, my attempts to compile a suspend2-patched kernel fail as a result of the suspend2 patch itself.

Are there any G5 users out there who have had success with suspend/hibernate, or anyone on other machines who are using suspend2 successfully?

---

### Post by Torrance on 2006-12-03
This is the error I get when trying compile both the Vanilla Kernel 2.6.19 anf the Debian Testing kernel 2.6.18, both with the suspend2 patch applied:

```
kernel/built-in.o: In function `.suspend_atomic_restore':
(.text+0x3cd48): undefined reference to `.save_processor_state'
kernel/built-in.o: In function `.suspend_atomic_restore':
(.text+0x3cd50): undefined reference to `.swsusp_arch_resume'
kernel/built-in.o: In function `.suspend2_suspend':
(.text+0x3cdac): undefined reference to `.arch_prepare_suspend'
kernel/built-in.o: In function `.suspend2_suspend':
(.text+0x3ce2c): undefined reference to `.save_processor_state'
kernel/built-in.o: In function `.suspend2_suspend':
(.text+0x3ce34): undefined reference to `.swsusp_arch_suspend'
kernel/built-in.o: In function `.suspend2_suspend':
(.text+0x3ce54): undefined reference to `.restore_processor_state'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.18'
make: *** [debian/stamp-build-kernel] Error 2
```

---

### Post by APU on 2006-12-03
I had swsusp (the in-Kernel suspend) working on my powerbook!

Take a look at this thread: [http://www.ubuntuforums.org/showthread.php?t=248889](http://www.ubuntuforums.org/showthread.php?t=248889)

---

### Post by Torrance on 2006-12-03
Where were you enabling swsusp? I can't see it in the kernel configuration options. Maybe its not available for G5 architectures?

I had previously tried enabling the Power Management features in the kernel (under Kernel Options) but Hibernate does not recognise these.

---

### Post by APU on 2006-12-04
> Maybe its not available for G5 architectures?

Well, that could be the case but I don´t know.

I´m not sure where the option to enable swsusp was. Since then I switched the PowerBook back to OS X (because I could not get everything to work flawlessly) and have not tried to enable swusp on my current Ubuntu machine (a Mac mini G4). I think it really was one of the Kernel Options but you could always look into the Kernels .config file and search for "SWSUSP" there.

---

