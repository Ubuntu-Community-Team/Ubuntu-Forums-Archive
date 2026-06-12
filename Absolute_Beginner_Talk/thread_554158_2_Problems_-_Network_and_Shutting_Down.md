---
title: "2 Problems - Network and Shutting Down"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Majorix on 2007-09-18
1. Unbuntu doesn't shutdown. Its stuck at the screen where the bar gets black. I have to hold down the power button to shutdown and it damages the computer. This is a common problem with Unbuntu.

2. My wireless won't connect all of a sudden. The network icon disappeared. When I opened the network-admin I saw that the wireless was disabled although I am 100% sure I didn't do that. When I re-enabled it and let it connect to my own AP using static IP it was stuck at loading the page in the web browser. Another common problem with Unbuntu. When I set it to DHCP, the icon disappeared again and I had no connection. I reset the computer several times but to no avail.

Anybody knows a solution?

---

### Post by alienexplorers on 2007-09-18
Do you have ACPI (Advanced Configuration and Power Interface) turned on in your BIOS.

---

### Post by Harpoon on 2007-09-18
You may be having some of the same symptoms preople  have been posting under "feisty freeze" and similar headings.  I also had similar problems.  My fix was to uninstall network manager, and install wifi-radar (or you could use wicd) as a substitute.

The reason for this:  network manager also installs (depends on) something called "dhcdbd" that is totally broken.  Inside that little gem are calls to directories and services that do not exist (a borrwed piece of code from redhat).  So far, no one seems to want to take responsibility for that, so the answer is to just avoid it.

Give that a try.  If it solves your problem that is terrific.  If it does not, then it will at least eliminate one branch of the debug tree.

I don't recall now if the fix was only complete after a reboot, so if it appears to be buggy try rebooting first.  If you are not satisfied, it's easy to go back to the package manager and try the other option, or reinstall network manager.  Doing this will not create boot problems.

Good luck.

---

### Post by Majorix on 2007-09-19
> **alienexplorers said:**
> Do you have ACPI (Advanced Configuration and Power Interface) turned on in your BIOS.

Yes I do. Thanks for thinking along though. I forgot to say everything was fine until yesterday when all hell broke loose.

> **Harpoon said:**
> You may be having some of the same symptoms preople  have been posting under "feisty freeze" and similar headings.  I also had similar problems.  My fix was to uninstall network manager, and install wifi-radar (or you could use wicd) as a substitute.

The reason for this:  network manager also installs (depends on) something called "dhcdbd" that is totally broken.  Inside that little gem are calls to directories and services that do not exist (a borrwed piece of code from redhat).  So far, no one seems to want to take responsibility for that, so the answer is to just avoid it.

Give that a try.  If it solves your problem that is terrific.  If it does not, then it will at least eliminate one branch of the debug tree.

I don't recall now if the fix was only complete after a reboot, so if it appears to be buggy try rebooting first.  If you are not satisfied, it's easy to go back to the package manager and try the other option, or reinstall network manager.  Doing this will not create boot problems.

Good luck.

I too guess the problem is with network-manager. So yes I will try to replace it. I will look at the alternatives you suggested.

Thanks a lot.

---

### Post by Majorix on 2007-09-23
Ok I fixed it.

I opened the pc thinking about removing the troublesome program, but then I decided to give it a last chance. I ran the network-admin, disabled wired connection, enabled wireless connection and set it to roaming mode (also DHCP of course) and then it worked. Donno why it did that to me in the first place though.

Thanks for the tries to help :)

---

