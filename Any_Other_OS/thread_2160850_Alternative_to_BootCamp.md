---
title: "Alternative to BootCamp?"
date: 2013-07-08
forum: Any Other OS
---

### Post by Jamie_Edwards on 2013-07-08
Hi guys,

This is a bit of a weird question I know and I didn't know where it was supposed to go in terms of the forum, so I put it here.

Not so long ago ( don't know if it's still going ) Apple release some software called "Bootcamp" which enabled their computers to boot into Windows without having to restart the PC, and I think it's vice versa too.

How does it work? I mean, is it some sort of VM wizardry? and more importantly, is there a Linux alternative? If there isn't, then is it possible to make something that mimicks it?

The reason I'm asking this is because I want to get a PC that I could just boot into Windows to have a gaming session, and then without having to restart the PC, just boot back into Ubuntu and do what I normally do on that ( and continue gaming with the games I have on the Steam for Linux platform ).

Thanks.

---

### Post by buzzingrobot on 2013-07-08
Pretty sure you *do* need to reboot to run Windows via Bootcamp. 

Macs do not have a BIOS. They are EFI machines.  Windows wants a BIOS.  Apple's Bootcamp emulates a BIOS, so Windows will boot.  It also provides the necessary drivers for the specific hardware it's running on. 

No VM trickery is involved.  Bootcamp is not a VM.  When you run Windows via Bootcamp, Windows is the only OS that's running. 

BTW, you can't reboot with restarting.  It's the same thing.

More here:  [http://www.apple.com/support/bootcamp/](http://www.apple.com/support/bootcamp/)

---

### Post by Jamie_Edwards on 2013-07-09
OK, well if that's the case then how would I configure GRUB for example to boot into Ubuntu upon pressing the on button, and while in Ubuntu I have an icon that I press that asks if I'm sure I want to go into Windows ( or any other Linux distro I might have on my system ). Boot into Windows and while I'm in Windows, have the same sort of thing that allows me to get back into Ubuntu ( or the other distros ) or be able to just shut my pc down no matter which O/S I'm in?

Thanks.

---

### Post by buzzingrobot on 2013-07-09
If you actually want to *boot* into one OS and then *boot* into another OS, the only way I know of to do that is to install both in a dual-boot configuration. Then, when the machine boots up. you'd have the choice of which OS to use. When you wanted to run the other OS, you'd reboot thte machine and select it.

A more convenient approach would be to run a virtual machine on either, or both, Windows and Linux.  A virtual machine is a program that emulates in software the hardware an OS expects to see.  So, you could run Linux inside a virtual machine running on Windows; or run Windows in a virtual machine running on Linux.

---

### Post by gravitar on 2013-07-09
I've experienced your issue as well. Virtualisation works, but to an extent. On my MacBook, I run a handy tool called [rEFIt]("http://refit.sourceforge.net/") which replaces the boot manager on your Mac. I was able to install Ubuntu 12.10 from a DVD. In fact, there's a [specialised image]("http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-amd64+mac.iso") available specifically for Macs. Let me know if it works out.
Cheers,
Gravitar

---

