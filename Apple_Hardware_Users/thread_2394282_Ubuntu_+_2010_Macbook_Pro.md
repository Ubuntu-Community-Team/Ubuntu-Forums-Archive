---
title: "Ubuntu + 2010 Macbook Pro"
date: 2018-06-15
forum: Apple Hardware Users
---

### Post by andrew80 on 2018-06-15
Hi all, 

apologies if this is the wrong section, been a Linux user for years, my last laptop Lenovo broke a while ago and got offered a 2010 Macbook Pro 13" for cheap so been using that for a while. Found out the other day that this device won't receive the newest MacOS update so decided this was an excuse to install Ubuntu 18.0LTS on it. 

I followed a number of guides, firstly creating a partition for Ubuntu, then booting from Ubuntu bootable USB, I added nomodeset to the boot options or else the display won't work. I then did the install from the live USB. 

Once installed it would reboot but then go to a black screen, I eventually managed to get at the options during boot by holding shift or esc (cant remember which) while allowed me to put nomodeset into it again.

Once booted again then I could select the driver for the display and also driver for the wifi, it asks me to reboot then but when I do black screen again, only this time I couldn't get esc or shift to work. Shift brings up a screen but there's nothing to edit. I was expecting to take out nomodeset. Wifi also appears not to work even with the driver. I did all this on Ethernet. 

Anybody who has installed on a 2010 MBP (intel duo core 2) that can assist? I knew it wasn't going to be straight forward but the guides make it look fairly.

---

### Post by slickymaster on 2018-06-15
*Thread moved to **Apple Hardware Users**.*

---

### Post by andrew80 on 2018-06-15
Cheers didn't see that forum!

---

### Post by andrew80 on 2018-06-16
anybody?

---

### Post by slickymaster on 2018-06-19
bumping this one for OP's benefit

---

### Post by andrew80 on 2018-06-19
Haha thanks, had a quick play again last night. Doesn't matter what driver I use for screen, every time reboot I have to reboot with either nomodeset or nouveau.nomodeset=0. 

Also selecting the wifi driver doesn't make the wifi work.

---

### Post by mrreid on 2018-07-04
Same sort of issues here but up and running (sort of).

My hardware is a mid 2010 13" Macbook Pro (model is MacbookPro7,1) with inbuilt nVidia GeForce 320M 256MB.

Was running like a 3 legged dog after upgrade to High Sierra so my girlfriend bought a new computer and handed her MacBook off to me (rsync is a Godsend).  She's happily working with 18.04 an an Acer Aspire.

Due to needing OS X for a particular application, I installed Ubuntu Linux 18.04 in a dual boot configuration.  First time worked like a charm except for display.  You MUST install/use the nVidia driver.  Everything else beautiful...until...

...an OS X update was notified and I installed it.  Ubuntu gone.  Apparently OS X is no respecter of other things in the EFI partition.

So, reinstall just like the first time?  Yeah, right...NOT!

I have literally spent weeks trying to, and researching, dual boot reinstall.

So, blew everything away and installed OS X (+ the needed applications).

Made sure OS X was up to date (never again will I update OS X without backups).

Obtained tools (gdisk == GPT fdisk) to shrink the OS X partitiion

Installed Ubuntu 18.04 via the DVD (NOT USB) using the option key at power on (select the "Windows" disk).

You must use nomodeset for the install and it will install as a legacy BIOS boot with completely stuffed display (1/4 of a screen, so you can't easily get to things outside of that upper left window).

Once (sort of) up and running obtain/install the nVidia driver, this will give you a usable system, even the wifi works.

However, and this isn't Apple hardware specific as same problem on another machine, I'm currently only able to login as the first defined (installation) user.  Users defined later can't login, it just comes back to the login screen.

---

