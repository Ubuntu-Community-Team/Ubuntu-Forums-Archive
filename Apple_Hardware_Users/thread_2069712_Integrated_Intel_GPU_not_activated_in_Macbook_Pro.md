---
title: "Integrated Intel GPU not activated in Macbook Pro"
date: 2012-10-11
forum: Apple Hardware Users
---

### Post by Splooshie123 on 2012-10-11
The macbook pro I have has 2 GPUs, a dedicated NVidia card (GeForce GT 330M) and an integrated intel gpu (intel HD graphics).

For some reason, I can only access the nvidia card, which is an unnecessary power drain if all I'm doing is browsing the internet. However, the intel gpu doesn't seem to get powered on at all.

Only the nvidia card appears:
```
$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 330M] (rev a2)
```

dmesg:
```
$ dmesg | grep intel
[    0.717130] intel_idle: MWAIT substates: 0x1120
[    0.717131] intel_idle: v0.4 model 0x25
[    0.717132] intel_idle: lapic_timer_reliable_states 0xffffffff
[   23.758574] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   23.758629] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   23.758636] intel ips 0000:00:1f.6: request irq failed, aborting
[   23.758647] intel ips: probe of 0000:00:1f.6 failed with error -16
[   23.903191] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   23.903264] snd_hda_intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[   23.903296] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   23.966323] snd_hda_intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.966327] hda_intel: Disabling MSI
[   23.966407] snd_hda_intel 0000:01:00.1: setting latency timer to 64
```

I don't mind if I have to reboot to switch between cards, I just want to get the intel gpu working in the first place.

---

