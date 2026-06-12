---
title: "no power management utility :("
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by skohari on 2007-08-29
I have installed 7.04 using the 'noapic acpi=off' option. Now i do not have power mangement utility. My 'Power Remaining' is always shown as 0.00 and it shuts down abruptly due to loss of power when it actually hits 0.00. Can anyone please tell me how to have a power utility? All help appreciated.

---

### Post by viciouslime on 2007-08-29
I don't think this is possible if you can't get your computer to boot without those options, however, if you want to try removing those options, press esc when the computer is booting. You will see a message telling you when to press it. This will give you the grub boot menu, press 'e' to edit the current line (the one highlighted by default will be the right one so just press e straight away) then delete those options from the line.

Press enter and see if the computer boots and everything works. If so, to remove those options permanently you need to delete them from the same line in the file /boot/grub/menu.lst

Use the command "gksudo gedit /boot/grub/menu.lst" in the terminal (Applications/Accessories/Terminal) :)

If you get stuck, post back here.

---

### Post by skohari on 2007-08-31
I did that. I permanently changed the options in grub; so now it loads fine, but i do not have the power monitoring point. Where should I be looking to see "remaining battery"? Thanks

---

### Post by skohari on 2007-08-31
and if i remove those options, it does not boot. I got the idea from the forums to use those options to boot. Is there a one to one connection between noapic acpi=off and power management?

---

