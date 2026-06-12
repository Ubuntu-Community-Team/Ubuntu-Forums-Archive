---
title: "Can't run ubuntu 7.10 AMD Alt."
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by Bgeorge07 on 2007-11-17
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/3610](https://answers.launchpad.net/ubuntu/+question/3610) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/3610](https://answers.launchpad.net/ubuntu/+question/3610) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am not able to run ubuntu 7.10 on my Intel Core 2 Duo Pentium D 2.66.
after the boot process, Loading hardware drivers....
the machine scroll for ever and sits there..
I have also tried all the boot options. eg., pci=acpi,noapic that doesn't work.
sometimes the machines hangs up and restarts.



Please help...

Intel D945GCL

Processor
Intel PD 805 2.66 GHZ / 2.66GHZ
WD Caviar 80GB serial ATA HD 7200/8MB/S-ATA-150
(2)-- DDR 2 512 MB RAM PC2-4200-- 533mhz
NVIDIA GeForce FX 5200 (PCI) 256MB DDR

---

### Post by sirgogo on 2007-11-18
Ooh I see, I see.

Well, troubleshooting this can be somewhat of a problem, as we can't see whats going on over at your computer. Nevertheless, answer these questions:

1. Are you duel-booting with another OS?
2. Does the GRUB menu show up?
3. If the GRUB menu shows up, have you tried the memtest?
4. Have you tried doing fsck to make sure your installation has integrity.
5. Have you tried installing a different version of Ubuntu? I checked out the launchpad bug report, and though that guy said that amd64 is the correct version for you, I'm not convinced. I'm not a pro at this either, so its best you double-checked.

With those questions answered, I think I'll have a better idea as to what the exact problem is.

Good luck!:)

P.S.: It should be noted that the nVidia fx 5200 card is very buggy with Ubuntu. I installed it on a P4 machine, and could not get passed the installer. I had to take out the PCI card and use the on-board graphics. I believe it was a Dell DImension 2400, or similar. So you may want to try using a different graphics card, or try using on-board graphics (if you have any) to install, then you can get about fixing your graphics card.

---

### Post by Bgeorge07 on 2007-11-21
1. yes I am dual booting (win xp)
2. GRUB shows up fine. I am able to boot into windows. I can't boot into ubuntu
3. I don't know how to do a  fsck . 
4. I have tried Kubuntu.
Both Ubuntu and Kubuntu restart at loading drivers.....

I also tried the live cd of Ubuntu 7.10 that also restarts.

---

### Post by Bgeorge07 on 2007-11-21
I got it working today. Finally after six month I got my ubuntu working today.
thank you so much for you help.

My NVIDIA GeForce FX 5200 PCI card was the problem.  I took out the PCI card and set the bios to on board video. Wola... I am in ubuntu.

I just want to say thank you for your help...

---

