---
title: "Ubuntu 13.04 on 2010 MacBook Pro: Multiple problems, extremely sluggish"
date: 2013-05-04
forum: Apple Hardware Users
---

### Post by glaze on 2013-05-04
Live session worked fine, but when I began installing Ubuntu, problems began. The installation step that removes packages was very, very slow. After installing I must use "noapic" to even get into the desktop. I'd like to install Wi-Fi and NVIDIA driver, but running apt-get update and applying updates was extremely slow (unpacking linux-headers-xxx seemed to take forever so I just gave up after 45 minutes). Launching Firefox takes ages. The machine has Core 2 Duo, but only one core is shown in /proc/cpuinfo. My hard drive is an SSD and works fine on OS X (I dual-boot using rEFIT). Well, this was more a rant than a question, but if anyone else has had similar problems, feel free to share information.

**Edit: I reinstalled Ubuntu from normal image, not mac-version, and all my problems disappeared**.

---

### Post by bootlessxfly on 2013-05-04
Are you running it through the emulated bios or EFI? And have you run a apt-get upgrade. When i installed ubuntu 13.04 on my MBP 8.2 i udated everything during the install and almost everything is working. The wireless even worked with no fixes needed from me. The only problems i have now are poor battery, intel graphics not working, and a bit of a heat problem. I do remember when i first installed linux a few months back it seemed laggish... and that was on the emulated bios. So maybe try booting through EFI.

---

### Post by glaze on 2013-05-05
I guess I'm using emulated BIOS (rEFIT + Ubuntu mac .iso). Might give normal Ubuntu a try soon, or can I somehow select BIOS or EFI in boot menu?

---

