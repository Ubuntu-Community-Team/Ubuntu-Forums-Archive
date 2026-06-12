---
title: "Moving Ubuntu to another PC"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Prognatus on 2007-02-18
What do I have to remember if I want to move my Ubuntu 6.06 installation to another PC?
I already have backup of everything in a compressed tar ball. Can I then just restore the backup on the other PC and reinstall grub?
Since this other PC has different hardware, I wonder if Ubuntu will rediscover the new hardware automaticly or if I must do something else afterwards.

A link to a how-to or other post would be great, if this is already explained somewhere else.

Thanks.

---

### Post by moshuptrail on 2007-02-18
I suggest you just install Ub. on the other PC from the LiveCD.  Copying your current install would likely result in problems due to the hardware differences.   Once you get the new PC working then restore all your files.  One thing you CAN copy is all the .xxx directories from your home directory.  That will retain all your personal preference settings.

---

### Post by Prognatus on 2007-02-18
Ok, thanks. Then I will go that route and install from a Live-CD first.

So the installed programs, settings and everything will be Ok then, when I restore the backup (except the /boot directory)? Are there other directories I should skip restoring?

Or should I just restore my home directory and then reinstall all programs?

---

### Post by moshuptrail on 2007-02-18
Personally, I would only restore my home directory, and re-install everything else.  You can probably restore most installed programs, but anything that deals directly with hardware would be suspect - like fax programs, wireless, printers, etc.
You could spend more time troubleshooting a problem than just re-installing the application.

---

### Post by Prognatus on 2007-02-18
I see your point. Thanks for the advice, I will follow it. :)

---

