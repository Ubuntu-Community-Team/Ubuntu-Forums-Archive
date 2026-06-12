---
title: "Suspend Laptop"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by natman on 2007-04-22
Hi i have KDE running and in the system tray i have "KLaptop" and i have the button switch to give suspend the laptop when the lid is closed. When i close the lid the computer and fan stop and its seems to be asleep, then when i open the lid it seems to wake but the screen stays blank. 

Is there any way for me to recover the screen when i open the lip or is there something wrong with my laptop, is there a key bord shortcut to restart ( until now im holding the power button for 5 sec )

Thanks:
Patrick

---

### Post by nsleiman on 2007-04-23
I have same problem (Edgy), i can put the laptop on a suspend but i can never have it back running without shutting it down and restarting :(.
So i decided to act like the suspend does not even exist :)

---

### Post by Taigrr on 2007-04-23
For the record, i'm running Feisty now, and suspend works perfectly on my e1505. =D Maybe yours will work after an upgrade, should you decide to do so.:popcorn:

---

### Post by jmagsho on 2007-04-23
I'm using Feisty with a Compaq Armada E500 and suspend is now broken.   It had been working with Dapper (for whatever reason I never tried it with Edgy).   The machine will go into suspend mode and cannot be brought back despite numerous and different attempts at recussitation. :)    After getting it going, I found it would not power down until I did a hard reset (pulled the battery).

---

### Post by madmetal on 2007-05-16
> **jmagsho said:**
> I'm using Feisty with a Compaq Armada E500 and suspend is now broken.   It had been working with Dapper (for whatever reason I never tried it with Edgy).   The machine will go into suspend mode and cannot be brought back despite numerous and different attempts at recussitation. :)    After getting it going, I found it would not power down until I did a hard reset (pulled the battery).

i just installed feisty on a compaq armada E500 and suspend works fine out of box.. (celeron 600Mhz 512ram )
i did a clean install... the only thing i cant make work till now its irda.

---

### Post by yexin218 on 2007-10-19
I couldn't suspend my laptop, and i should press the power button for 5s to get it shutdown.
Is it something woring with my system(7.10). before upgrading, 7.04, suspend could work perfectly.
I don't know why?
do me a favor.

---

### Post by Mr.Beast on 2007-10-19
> **natman said:**
> Hi i have KDE running and in the system tray i have "KLaptop" and i have the button switch to give suspend the laptop when the lid is closed. When i close the lid the computer and fan stop and its seems to be asleep, then when i open the lid it seems to wake but the screen stays blank. 

Is there any way for me to recover the screen when i open the lip or is there something wrong with my laptop, is there a key bord shortcut to restart ( until now im holding the power button for 5 sec )

Thanks:
Patrick

I don't think you are alone, IMHO the sheer number of powersaving features on so many laptops causes many potential problems (not just a *nix issue, I have seen similar issues with Vista as well when hibernate / suspend functions are called.)
I would also state that not everything comes back properly out of suspend (if anything) and hibernate features.  Audio seems to be my biggest bugbear on this.
I would suggest ignoring suspend, but perhaps using hibernate instead, it does come back.
Also, do check for latest BIOS etc etc.. yada yada yada..  :-)

---

### Post by jmagsho on 2007-11-06
> **madmetal said:**
> i just installed feisty on a compaq armada E500 and suspend works fine out of box.. (celeron 600Mhz 512ram )
i did a clean install... the only thing i cant make work till now its irda.

Madmetal - maybe that is what I need to do - I've done distro upgrades on this machine since Breezy I think.  Maybe it's time for a fresh install.

Thanks.

---

### Post by Bigbird999 on 2007-11-06
E500 here, as well.  If I have any drives mounted when it suspends, it won't resume properly and it hangs on shutdown.  If I unmount any drives, before I shut down or suspend both work properly..

BB

---

### Post by bongkin123 on 2007-11-24
After I upgrade my laptop from the Fesity to 7.10, I coundn't get the suspend/hibernate functions work. I've just realized when I turn off the printing services (cupsys/hplip), that works like a charm.
Do you have any idea how these printing services affect the acpi/apm ones?

---

### Post by jmagsho on 2007-12-11
Bongkin,

Are you using a network printer?   Perhaps HPLIP is trying to keep the network connection alive and causing issues once you resume?

I have a similar setup and have not rooted it down to the printing functions.   My issue has been with Wi-fi not working after resuming from suspend or hibernate.   I simply go to the network connection setup and disable and then re-enable the Wireless card which works every time.

It is time consuming, but seems to do the trick.  I generally try to actually shut the thing down most of the time though.

Just my $.02.

---

### Post by khurrum1990 on 2007-12-11
Hi, please post in detail what ur system specs r, also whether u use beryl, compiz, compiz fusion, ur vga card, whether its agp, pci, or pci express. Whether u have any on board vgs card etc.

---

### Post by khurrum1990 on 2007-12-11
do u want us to help u or is it working now?

---

