---
title: "Random Lock / Freeze"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by LibertyShadow on 2007-11-01
I have a Dell E1505 with Ubuntu Gutsy... Nvidia GeForce Go 7300 installed by binary driver

I will be checking my email, or doing facebook or something inconspicuous, when for no reason everything stops responding, applications, mouse, keyboard.  Within about five seconds, the screen blanks out but remains on.  Everything sounds like it is running (that is all I have to go on) but it won't respond to my ctrl+alt+f*'s or ctrl+alt+bksp or anything. The only action I can take is to press and hold the power button.  When I reboot, fsck does not run; even though my Ubuntu partition was uncleanly mounted.

This is the output leading up to the freeze.  Judging by this, I'd say the problem has to do with my NVIDIA card, but I want some second opinions and/or advice from you Linux gurus :D  I also ran Dell diagnostics about a week ago without any problems in the PCI department, but I can check again if requested.

-LibertyShadow

/var/log/kern.log

> 
Nov  1 12:41:29 vinny-laptop kernel: [ 9350.780000] usb 3-1: configuration #1 chosen from 1 choice
Nov  1 12:41:29 vinny-laptop kernel: [ 9350.800000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input7
Nov  1 12:41:29 vinny-laptop kernel: [ 9350.800000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.2-1
Nov  1 12:41:29 vinny-laptop kernel: [ 9350.960000] input: Lid Switch as /class/input/input8
Nov  1 12:41:29 vinny-laptop kernel: [ 9350.960000] ACPI: Lid Switch [LID]
Nov  1 12:41:29 vinny-laptop kernel: [ 9350.960000] input: Power Button (CM) as /class/input/input9
Nov  1 12:41:29 vinny-laptop kernel: [ 9350.960000] ACPI: Power Button (CM) [PBTN]
Nov  1 12:41:29 vinny-laptop kernel: [ 9350.960000] input: Sleep Button (CM) as /class/input/input10
Nov  1 12:41:29 vinny-laptop kernel: [ 9350.960000] ACPI: Sleep Button (CM) [SBTN]
Nov  1 12:41:29 vinny-laptop kernel: [ 9351.076000] ACPI: Thermal Zone [THM] (25 C)
Nov  1 12:41:29 vinny-laptop kernel: [ 9351.156000] ACPI: AC Adapter [AC] (on-line)
Nov  1 12:41:30 vinny-laptop kernel: [ 9351.196000] ACPI: Battery Slot [BAT0] (battery present)
Nov  1 12:41:30 vinny-laptop kernel: [ 9351.760000] b44: eth0: Link is up at 100 Mbps, full duplex.
Nov  1 12:41:30 vinny-laptop kernel: [ 9351.760000] b44: eth0: Flow control is off for TX and off for RX.
Nov  1 12:41:30 vinny-laptop kernel: [ 9351.764000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov  1 12:41:44 vinny-laptop kernel: [ 9365.604000] eth0: no IPv6 routers present
Nov  1 12:43:55 vinny-laptop kernel: [ 9496.784000] NVRM: Xid (0001:00): 6, PE0000 0198 beef0201 0000f550 00ede9e3 00000000
Nov  1 12:44:09 vinny-laptop kernel: [ 9496.804000] NVRM: Xid (0001:00): 30,  L1 -> L0
Nov  1 12:44:09 vinny-laptop kernel: [ 9496.804000] Uhhuh. NMI received for unknown reason 80 on CPU 0.
Nov  1 12:44:09 vinny-laptop kernel: [ 9496.868000] You have some hardware problem, likely on the PCI bus.
Nov  1 12:44:09 vinny-laptop kernel: [ 9496.868000] Dazed and confused, but trying to continue
Nov  1 12:44:12 vinny-laptop kernel: [ 9513.428000] NVRM: Xid (0001:00): 26, Ch 000001ff M 00001ffc D ffffffff intr ffffffff
Nov  1 12:44:13 vinny-laptop kernel: [ 9514.428000] NVRM: Xid (0001:00): 30,  L0 -> L0
Nov  1 12:44:16 vinny-laptop kernel: [ 9517.428000] NVRM: Xid (0001:00): 1, Ch 000001ff M 00001ffc D ffffffff intr ffffffff
Nov  1 12:44:21 vinny-laptop kernel: [ 9522.428000] NVRM: Xid (0001:00): 6, PE01ff 1ffc ffffffff 00000000 00000000 00010000
Nov  1 12:45:18 vinny-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic


I am thinking the last line is the book I just performed, meaning that everything above it was before the crash or during the crash.

---

### Post by Paqman on 2007-11-01
Has it just started doing this, or has it been happening since you installed Gutsy?

---

### Post by LibertyShadow on 2007-11-01
It has started in the last week + 1/2, and has happened four times, twice in the last two days.  It never happened in Ubuntu Feisty.

Thanks for the reply

---

### Post by LibertyShadow on 2007-11-08
It has happened three times since my last post.  Each time I am in firefox when it has happened.  The screen just flashes fast and everything freezes.  Each time I have been able to Ctrl + Alt +Bksp out of it though (by pressing repeatedly and praying).  It just happened and this is the corresponding time i my /var/log/kern.log file:

```
Nov  8 14:07:53 vinny-laptop kernel: [79668.872000] NVRM: Xid (0001:00): 6, PE0000 0198 beef0201 0000fdf0 00ffffff 00000000
Nov  8 14:07:53 vinny-laptop kernel: [79668.892000] NVRM: Xid (0001:00): 30,  L1 -> L0
```

Anybody with a suggestion?

---

### Post by LibertyShadow on 2007-11-08
I think my problem is here: [http://ubuntuforums.org/showthread.php?t=566422]("http://ubuntuforums.org/showthread.php?t=566422")

---

