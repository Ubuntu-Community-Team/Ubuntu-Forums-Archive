---
title: "Left speaker sounds off in MacBook Air 2017/Early 2015"
date: 2018-02-19
forum: Apple Hardware Users
---

### Post by newhacker1746 on 2018-02-19
Have a MacBookAir7,2, the 2017 model, which is really just a cpu upgrade of the 13 inch Early 2015 one. Identical except the cpu. When booting macOS (which I do not want to use, I want to single boot ubuntu efi only) the speakers sound great. When booting ubuntu, the right speaker sounds the same, while the left speaker loses a lot of fidelity. 

Overall it seems like the left speaker has much increased bass and low-mids, and loses a lot of the fidelity of the high frequencies. The CS4208 audio codec used is driven by snd_hda_intel, which appears as "[FONT=courier new]00:03.0 Audio device [0403]: Intel Corporation Broadwell-U Audio Controller [8086:160c] (rev 09)[/FONT]" with subsystem "[FONT=courier new]Apple Inc. Broadwell-U Audio Controller [106b:011b][/FONT]" and this exposes the internal speakers left/right and the headphone/line-out left/right. Is there a reason for this discrepancy? 

I tried [FONT=courier new]apple_set_os.efi[/FONT] to trick EFI into thinking macOS is booting, and all that accomplished was it eliminated the internal keyboard and trackpad, they just disappeared from all lspci/lsusb outputs, and were non-functional (but the keyboard backlight stayed on and was controllable.) The speakers stayed the same. This really ruins the experience for me. Is there a solution, or perhaps just a system-wide equalizer that allows me toi equalize just one speaker, not both at the same time? Thank you. This also doesn't happen with my 2012 MacBookAir 11', booted EFI it sounds exactly the same...

---

