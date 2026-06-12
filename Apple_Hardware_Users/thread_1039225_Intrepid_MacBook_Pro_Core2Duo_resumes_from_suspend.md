---
title: "Intrepid MacBook Pro Core2Duo resumes from suspend with quirks"
date: 2009-01-14
forum: Apple Hardware Users
---

### Post by tp42 on 2009-01-14
I work on a 15" MacBook Pro Core2Duo with an up to date patched Ubuntu 8.10 installation. Suspend worked out of the box but resume from suspend is not working fine yet.

After resuming from suspend, I notice regularly some graphic quirks on the top border of my desktop (see turquoise line in the screenshot quirks.png) and on the edge of the open windrows on my desktop. When I log out/log in the quirks disappear.

uname -a reveils:  2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

dmesg.txt in the attachment reveils the output of the dmesg command.

Is there some more information necessary to detect possible reasons for the quirks? I would be happy to try out some hints.  
Best regards,
tp42

---

### Post by cyberdork33 on 2009-01-14
Please see the "Before you Post" link in my signature to properly identify your Mac. There are several hardware versions of the same system.

What video driver are you using?

---

### Post by tp42 on 2009-01-14
thanks for the quick reply.
My model/hardware revision is: MacBookPro2,2
My video card: 01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
My video driver is the "out of the box" ATI/Radeon driver Version 1:6.9.0
I have not installed the  'fglrx' driver on this system yet.
I hope this spec might be helpful in determining the cause of the quirks.
Best regards,
tp42

---

### Post by tp42 on 2009-01-15
Just a short note: todays official Ubuntu update of the ACPI-scripts did not change the situation on my MacBook Pro. The quirks are still present after resuming from suspend.

---

### Post by cyberdork33 on 2009-01-15
That looks similar to what I see on another ATI laptop I have that uses the open ATI driver. It may be a bug in that. You might try enabling the propritary driver and see if you get the same results.

---

### Post by tp42 on 2009-01-16
Thanks for the hint which lead at least to a temporary but not stable solution:

The good news: I installed the proprietary fglrx ATI driver on my macbook pro and the quirks vanished :-)

The bad news: Besides that the dual monitor handling git rather cumbersome with the ATI catalyst software, I faced a further issue:
Title bar distortion as described in this bug report which I was not able to fix, even not with an reconfiguration of xorg.conf and a reset.
So I decided to get back to the open source radeon driver according  to [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver") section "Removing the proprietary fglrx driver".

And the happy end - at least for a little while - after re-installation of the open source radeon driver: 
[LIST]
[*]the quirks did not reappear anymore
[*]during shut down of the macbook, the Ubuntu splash screen appears (before, it was just a red screen with some white rectangles, I thought that should look this way...)
[/LIST]

However, after some hours , some shut downs and starts, some suspends and resumes the quirks are suddenly back again and I lost again my Ubuntu splash screen during shut down.  The red cloured screen with the white rectangles is back again.

So I think that some setting might get lost somehow? Is there a way to reset my video driver? 

Best regards,
tp42

---

