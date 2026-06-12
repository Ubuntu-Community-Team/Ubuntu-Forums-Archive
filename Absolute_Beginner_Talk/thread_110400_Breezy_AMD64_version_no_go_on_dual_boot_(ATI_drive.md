---
title: "Breezy AMD64 version no go on dual boot (ATI driver problem????)"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by nbhaskar on 2005-12-30
Hi, Although I have been working in the IT field for over 18 years including unix, I'm still new to Linux especially Breezy. I installed the OS (AMD64 version), x server failed due to my ATI driver problem, all I was getting was the command line nothing else. Then I read from a forum that I should change the config file and replace "ati" with "vesa". I did that and now I get a blank screen when the OS starts x server, I could not do any thing after this but push the power button to shutdown the pc.

My set up is AMD Athlon 64 X2 3800+ on ECS nForce4 mobo with 2 GB Kingston DDR400 PC3200 ram. Mobo has sound processor built in, then the problem part ATI X700 256MB DDR3 PCIe card.

I have Windows XP pro already running on my machine, I installed GRUB loader for dual boot.

When I tried the live cd too I had the same problem.

Can any body help me out solve this problem and boot Breezy?

thanks.
a noob.:confused:

---

### Post by nbhaskar on 2006-01-07
[QUOTE=nbhaskar]Hi, Although I have been working in the IT field for over 18 years including unix, I'm still new to Linux especially Breezy. I installed the OS (AMD64 version), x server failed due to my ATI driver problem, all I was getting was the command line nothing else. Then I read from a forum that I should change the config file and replace "ati" with "vesa". I did that and now I get a blank screen when the OS starts x server, I could not do any thing after this but push the power button to shutdown the pc.

My set up is AMD Athlon 64 X2 3800+ on ECS nForce4 mobo with 2 GB Kingston DDR400 PC3200 ram. Mobo has sound processor built in, then the problem part ATI X700 256MB DDR3 PCIe card.

I have Windows XP pro already running on my machine, I installed GRUB loader for dual boot.

When I tried the live cd too I had the same problem.

Can any body help me out solve this problem and boot Breezy?

thanks.
a noob.:confused:[/QUOTE]

This worked finally when I changed my xorg.conf file to have "radeon" instead of "ati".

Cheers.

---

