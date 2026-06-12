---
title: "Gutsy Kernel video problems with Macbook Pro (ATI X1600 card)"
date: 2007-08-29
forum: Apple Intel Users
---

### Post by E Gardner on 2007-08-29
Hello-

I understand that some of the Macbook (Pro) hardware problems are at least potentially fixed in the new Gutsy kernel, especially some power management issues (heat, battery life, sleep). Fixing these problems would make Ubuntu a lot more usable for me, so I decided to try upgrading to the new kernel (as it seemed a lot easier than compiling my own).

I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)
and used the script provided.

After upgrading, the machine booted fine and there were no problems as far as the x login manager. If I logged into an XGL session, however, all video output was horribly skewed and garbled so that the contours of the desktop could only vaguely be made out. Everything was working, but the display was so distorted as to make the system unusable.

Logging into a standard GNOME session without XGL caused no problems, but I'd rather not do this as I use things like the AWN dock that depend on it. I had to reboot and enter grub to revert to the Feisty kernel.

I am using a first-generation Macbook Pro (2Ghz, ATI X1600 with FGLRX driver installed). Does anyone have any idea what the problem could be, or whether it could be easily fixed?

Or, for that matter, is the new kernel even worth the trouble right now? Have other laptop-users noticed significant power-management improvements, enough to merit trying to make this work?

Thanks for reading-

---

### Post by cyberdork33 on 2007-08-29
> **E Gardner said:**
> Hello-

I understand that some of the Macbook (Pro) hardware problems are at least potentially fixed in the new Gutsy kernel, especially some power management issues (heat, battery life, sleep). Fixing these problems would make Ubuntu a lot more usable for me, so I decided to try upgrading to the new kernel (as it seemed a lot easier than compiling my own).

I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)
and used the script provided.

After upgrading, the machine booted fine and there were no problems as far as the x login manager. If I logged into an XGL session, however, all video output was horribly skewed and garbled so that the contours of the desktop could only vaguely be made out. Everything was working, but the display was so distorted as to make the system unusable.

Logging into a standard GNOME session without XGL caused no problems, but I'd rather not do this as I use things like the AWN dock that depend on it. I had to reboot and enter grub to revert to the Feisty kernel.

I am using a first-generation Macbook Pro (2Ghz, ATI X1600 with FGLRX driver installed). Does anyone have any idea what the problem could be, or whether it could be easily fixed?

Or, for that matter, is the new kernel even worth the trouble right now? Have other laptop-users noticed significant power-management improvements, enough to merit trying to make this work?

Thanks for reading-
Likely, you need to 'compile' the fglrx module for your new kernel. (just download the official driver from ATI). Boot from the newer kernel, and compile the driver.  fglrx links against the kernel headers, and in the normal repository the module is linked against ubuntu's kernel.

You can check that stuff in ok in your regular gnome session, do fglrxinfo and see if ATI is listed as the provider.

---

