---
title: "Boot issues - Newb needs help"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by austinw on 2007-02-22
I've run the live cd i have on other computers with no problem, but on my own computer I get a message that "MP-Bios bug - 8254 timer not connected to IO-APIC"
From a search I found:[INDENT] At the grub boot screen, use arrow keys to highlight "kernel /boot/linuz-2.6.15-25-386 root=/dev/sda3 ro quiet splash". Then type 'e' to edit; you'll be taken to another screen. Append 'noapic' to end of boot options and enter.  Then 'b' to boot.
[/INDENT]

When I boot from the cd, a screen comes up with the Ubuntu logo and options for booting from cd, etc.  I tried hitting escape but a prompt comes up that does not "know" anything i type.  I am completely lost in this.  How do I get to the are where I can append the boot options?

Once I figure this out, I want to dual-boot Ubuntu and XP (XP is already installed)  If anyone knows a tutorial or help on that it would be much appreciated.
Thanks,
Austin
:confused:

---

### Post by louis_nichols on 2007-02-22
OK. On that initial screen, with the boot options of the CD, there is an option for "Advanced boot options", if I remember correctly. It asks you to press a certain F key. That will display at the bottom of the screen the actual grub command with the boot parameters, which you can edit.

Sorry I can't be more specific, but I haven't booted the liveCD for a looong time.

---

