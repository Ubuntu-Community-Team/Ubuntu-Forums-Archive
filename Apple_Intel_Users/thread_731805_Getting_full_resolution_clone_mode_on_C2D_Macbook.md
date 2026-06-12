---
title: "Getting full resolution clone mode on C2D Macbook"
date: 2008-03-22
forum: Apple Intel Users
---

### Post by veiho on 2008-03-22
I have C2D macbook and external Philips 220WS, connected to DVI (TMDS-1), running Ubuntu 7.10 x86_64.
> Mar 22 08:38:06 macbook kernel: Linux version 2.6.24.3 (root@macbook) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Thu Mar 20 01:26:17 EET 2008
> Mar 22 13:04:42 macbook kernel: ACPI: EC: EC description table is found, configuring boot EC
Mar 22 13:04:42 macbook kernel: ACPI: EC: non-query interrupt received, switching to interrupt mode
Mar 22 13:04:42 macbook kernel: ACPI: BIOS _OSI(Linux) query ignored
Mar 22 13:04:42 macbook kernel: ACPI: DMI System Vendor: Apple Inc.
Mar 22 13:04:42 macbook kernel: ACPI: DMI Product Name: MacBook2,1
Mar 22 13:04:42 macbook kernel: ACPI: DMI Product Version: 1.0
Mar 22 13:04:42 macbook kernel: ACPI: DMI Board Name: Mac-F4208CA9
Mar 22 13:04:42 macbook kernel: ACPI: DMI BIOS Vendor: Apple Inc.
Mar 22 13:04:42 macbook kernel: ACPI: DMI BIOS Date: 06/27/07

I want to create a clone mode configuration (both monitors show same information, only resolution would be different and to turn off LVDS (internal display) when external monitor is connected on TMDS-1. For that purpose, I have searched google and tried several examples with no luck at all for innumerable hours. Yes, I could get it working with "i810" driver, but not with "intel" driver. X.org seems to have no documentation at all and Intel's driver documentation is incomplete and works only for i810 driver, but i810 causes whining noise which is not acceptable at all.

With default Gutsy installation X.org configuration, I am able to switch TMDS-1 to full resolution with xrandr.
> xrandr --output TMDS-1 --auto
xrandr --output LVDS --off

Turning off LVDS causes TMDS-1 display corruption, but doing --auto and --off several times, it is possible to shut the LVDS off without corrupting TMDS-1. Thought, sometimes there are little artifacts (horizontal lines) and some applications, when using xvideo, can corrupt TMDS-1 again, but for the most of the time everything works.

But I don't want to do it manually every time! I want X.org to correctly detect TMDS-1 resolution and switch to it automatically.
I have tried virtually everything with no improvements in results.

From Xorg.0.log i can read:

> (II) intel(0): Output LVDS connected
(II) intel(0): Output TMDS-1 connected
(II) intel(0): Output TV disconnected
(II) intel(0): Output LVDS using initial mode 1280x800
(II) intel(0): Output TMDS-1 using initial mode 1280x800

Ho to to configure X so that last line would end with 1680x1050?

---

### Post by pexi on 2008-03-26
Hi, I have the same problem with my macbook. I get the full resolution of my external monitor with:   

     $ xrandr --output TMDS-1 --mode 1680x1050

But I can't disable the macbook's lcd panel.

if I execute this command:

     $ xrandr --output LVDS --off

I can't use the external screen because is corrupt.

Best regards.

---

### Post by pexi on 2008-03-26
Ok, I have found a way to disable the lcd panel without problems, if I'm playing a video I can execute 

    $ xrandr --output LVDS --off

And everything is ok.

Best regards

---

### Post by veiho on 2008-06-11
Now using Hardy with current updates and still the same error exists.

---

