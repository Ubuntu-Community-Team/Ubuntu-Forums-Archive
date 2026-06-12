---
title: "MacBookPro5,3 &quot;Kernel panic - not syncing: Fatal machine check on current CPU&quot;"
date: 2013-04-11
forum: Apple Hardware Users
---

### Post by elparkiro on 2013-04-11
Hi, i've spent a few days downloading and trying to [install via USB]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick") (because my SuperDrive is broken), but I always get Kernel Panic message when I choose "[Try Ubuntu without installing]("http://i.stack.imgur.com/rL6Jh.jpg")" in the GRUB menú of the USB image. This is the complete message I have:

```

[     4.244110] [Hardware Error]: CPU 1: Machine Check Exception: 5 Bank 5: b200121020080400
[     4.244110] [Hardware Error]: RIP !INEXACT! 10:<ffffffff81031f8f> {mwait_idle_with_hint+0x5f/0x80}
[     4.244110] [Hardware Error]: TSC 2503279d43
[     4.244110] [Hardware Error]: PROCESSOR 0:1067a TIME 1365670341 SOCKET 0 APIC 1 microcode a07
[     4.244110] [Hardware Error]: Run the above throught 'mcelog --ascii'
[     4.244110] [Hardware Error]: CPU 1: Machine Check Exception: 5 Bank 5: b200121020080400
[     4.244110] [Hardware Error]: RIP !INEXACT! 10:<ffffffff81031f8f> {mwait_idle_with_hint+0x5f/0x80}
[     4.244110] [Hardware Error]: TSC 2503279d43
[     4.244110] [Hardware Error]: PROCESSOR 0:1067a TIME 1365670341 SOCKET 0 APIC 1 microcode a07
[     4.244110] [Hardware Error]: Run the above throught 'mcelog --ascii'
[     4.244110] [Hardware Error]: Some CPUs didn't answer in synchronization
[     4.244110] [Hardware Error]: Machine check: Processor context corrupt
[     4.244110] Kernel panic - not syncing: Fatal machine check on current CPU
[     4.244110] Shutting down cpus with NMI
_ 

```


MacBookPro5,3
2.8 GHz Core 2 Duo (T9600) 4GB RAM 500GB HDD (SuperDrive broken)
rEFIt boot manager

I've tried with the next 64bit ISOs:
Ubuntu 12.04
Xubuntu 12.04
Ubuntu 12.10


Please could I get some help!?

Thank You in advance, and sorry for my poor english u_u'

---

