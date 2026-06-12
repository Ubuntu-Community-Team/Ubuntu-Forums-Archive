---
title: "Suspend/Hibernate issues; ACPI workaround"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by brommage on 2007-11-24
Long time reader, first time caller.

I've been playing with Ubuntu on a dual-boot HP ZE4610US laptop for few months now.  It's an upgraded copy to Gusty.  But, under both Edgy (fresh install) and Feisty (upgrade) I have not been able to configure the hibernate/suspend settings correctly.

1.  I've tried a few workarounds on the net to try to get things working smoothly.  Now it will hibernate (but not suspend) and I've never been able to get the system to hibernate/suspend when closing the laptop lid.

2. My wireless card (bcm43xx) does not reinitialize on restart.  I know I need to put something in the whitelist under acpi-settings to get it to work, but I'm not sure what.  Alternatively, is there a good tutorial on what the cryptic lines on the ACPI config file mean?  I've been toying with the settings, but nothing quite has given me the correct settings.

3. I'm now getting an error on restart that Ubuntu did not hibernate correctly, but there is no info besides this. Is there a way I can view exactly what the conflict is, so that I can amend it?  Where are system error messages written to?  I imagine I need to cat or grep something, but no idea what. 

4.  I fear that I've employed so many different workarounds such that I believe my system is fracking up due to conflicts.  I know a lot of errors can be corrected by going with a fresh install rather than an upgraded version, so I'm thinking about re-installing a fresh copy of Gusty to fix this.  However, when I re-install does it overwrite all of my files (specifically in my $HOME directory)?  I know backing up is good practice--but I spent a lot of time trying to get my desktop settings right, and don't want to lose them all and have to re-install all of my files.

Any help would be appreciated.  Having to re-boot every time I take a break from writing is getting old.

---

### Post by brommage on 2007-11-24
bump.

---

### Post by Bigbird999 on 2007-11-24
You are not alone.  There are a coup;e of 30 page threads on this issue.  Some have total successm some partial success and some no sucess with getting susoend/hibernate to work.  search acpi in the hardware section   and you should find them.

BB

---

