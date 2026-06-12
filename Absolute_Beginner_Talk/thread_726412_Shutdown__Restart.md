---
title: "Shutdown / Restart"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by arboldt on 2008-03-16
I'm an absolute beginner at ubuntu, but I've searched the forums and didn't find this issue...

I installed ubuntu 7.10 on a rather old IBM NetVista desktop PC. I figured I could get experience with it on that before I consider changing my other PCs. Even though I'm a linux newbie, I'm quite impressed with everything. I have not really tried a lot, just poked around and surfed a bit.

However, when I shutdown (I click Shutdown -- *not* restart -- the PC powers down, then automatically restarts. I have to physically pull the power cord for it to stay shutdown. (This did not happen when the PC originally had WindowsME). 

I'm sure it's something very simple, but I can't find it. I've gone through all the setup / preference screens, gone through pages of help, but I still have to pull the plug. Once it's really down, I can plug it back in and it won't start until I push the power button. 

Can anyone point me in the right direction?

Thanks.

---

### Post by lsmobrian on 2008-03-16
This is usually a BIOS problem.  Could be a motherboard problem.   Try looking through your BIOS menus for power management too see if anything pops out, (power loss, surge, short circuit, power on after power off.. etc, something along those lines)  If you dont see anything you could try resetting BIOS to default

---

### Post by Daveski on 2008-03-16
Could this be APM ACPI? You could try editing your /boot/grub/menu.lst (or /boot/grub/grub.cfg for Grub2)

Find the entry similar to this,  and add the part in bold to yours.

"title Ubuntu, kernel 2.6.20-15-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=3015a7a1-6e5d-42d6-934d-193459bed89b **acpi=force**
initrd /boot/initrd.img-2.6.20-15-generic
quiet

---

