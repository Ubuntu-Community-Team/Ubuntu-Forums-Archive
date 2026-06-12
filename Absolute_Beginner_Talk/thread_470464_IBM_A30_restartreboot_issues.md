---
title: "IBM A30 restart/reboot issues"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ageilers on 2007-06-11
I am having a problem with Ubuntu/Kubuntu/Xubuntu feisty with restart on an IBM Thinkpad A30.  It seems to shutdown fine, but has no video once the shutdown splash screen goes away.  It seems to be rebooting due to the sounds that it makes and the hard drive activity. I have the issue with all three versions. I have tried the reboot=b and other options in the /boot/grub/menu.lst file to no avail.  The only time it worked is after booting from hibernation.?.  

I have Kubuntu installed on an IBM T23 and a Athalon XP 2500 with relatively no issues. I wanted to set this system up for my mom, but having to many issues. I would hate to have to reinstall XP.

---

### Post by HackingYodel on 2007-06-11
I think there were some problems with ACPI and some Thinkpads.  

Try booting with the noacpi option.  Here is how it's done for the IBM A31 and other IBM laptops, it may work for you.  [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM)

Hope that helps.

---

### Post by ageilers on 2007-06-13
Thanks, I will have to try some of those options when I get home.

---

