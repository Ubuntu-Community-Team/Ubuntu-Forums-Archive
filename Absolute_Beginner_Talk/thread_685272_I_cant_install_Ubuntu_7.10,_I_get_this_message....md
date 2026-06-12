---
title: "I cant install Ubuntu 7.10, I get this message..."
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by pacoramirez on 2008-02-02
I just built a PC and I cant install ubuntu 7.10. I burned the ISO image to a CD and put it in the PC. I get the first screen which is the Ubuntu setup options. Then I select "install ubuntu" and then I get this message:

"MP-BIOS bug: 8254 timer not connected to IO-APIC
 Kernel Panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and
 send a report. Then try rebooting with the 'noapic' option"

Does any one know what this means? Thanks for any help.

---

### Post by spiderbatdad on 2008-02-02
press f6 at the install screen and delete --quiet splash and add noapic.  There may also be a config setting in your system bios to set pci.

---

### Post by r4ik on 2008-02-02
Seems to be a bug see,

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/76989](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/76989)

Try to boot with the noapic option.

Good luck !

---

### Post by MikeCheck on 2008-02-02
> **spiderbatdad said:**
> press f6 at the install screen and delete --quiet splash and add noapic.  There may also be a config setting in your system bios to set pci.

How do I change it so that I don't have to type that in every time I reboot?

Edit:  Nevermind.  I think I found it [here]("http://ubuntuforums.org/showthread.php?t=684815")

---

### Post by spiderbatdad on 2008-02-02
> **MikeCheck said:**
> How do I change it so that I don't have to type that in every time I reboot?

Edit:  Nevermind.  I think I found it [here]("http://ubuntuforums.org/showthread.php?t=684815")
```
gksudo gedit /boot/grub/menu.lst
```add it to the end of the kernel line below the first entry after ####END DEFAULT OPTIONS##### (or something like that.:S)  Save after editing and close. Reboot.

EDIT: OOPS! :S

---

