---
title: "vgaswitcheroo on macbook 8,2: blank screen while switching from DIS to IGD"
date: 2013-05-31
forum: Apple Hardware Users
---

### Post by miguelnegrao on 2013-05-31
Hi

I'm booting in EFI stub mode directly from rEFInd in a macbookpro8,2. This means I have the radeon card working and active. I would like now to get vgaswitcheroo working. It reports both cards are present:

```

0:IGD: :Pwr:0000:00:02.0
1:DIS:+:Pwr:0000:01:00.0
2:DIS-Audio: :Pwr:0000:01:00.1

```

However switching to the integrated intel graphics card i915 results in a black screen. Switching back to the discrete card the display goes back to working normally (except with the fans blowing at full speed). I do ctrl-alt-F1 and 
```

sudo -s
stop lightdm
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch

```

I think it is this bug : [https://bugzilla.kernel.org/show_bug.cgi?id=56911](https://bugzilla.kernel.org/show_bug.cgi?id=56911) . 
Is there any way around this ? Has anyone gotten vgaswitcheroo working when booting via EFI stub mode ?

thanks,
Miguel Negrão

ps: It's not possible to get the properietary fglrx driver working with EFI stub mode, is it ? I tried and it doesn't work, it can't access the BIOS.

---

