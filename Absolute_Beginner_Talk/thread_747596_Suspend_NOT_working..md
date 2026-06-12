---
title: "Suspend NOT working."
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Alterac on 2008-04-06
When I suspend my laptop, it turns off fine.

However upon restarting the screen is dim and is constantly flickering. I can still make out the password dialog and I can still log in but the screen remains dim and continues to flicker.

Is there anything I can do about this?

Also, my laptop's hibernate does not work either. It hangs while trying to do so.

My main concern is with suspend since, I'd hate to have to shutdown all the time.

Thanks in advance.

*My laptop's a Fujitsu T4220.

---

### Post by zigx on 2008-04-06
this may be a known issue?

i have the exact same problem with a Latitude D531 laptop.

---

### Post by riven0 on 2008-04-06
Go to the terminal and try these commands: 

1. gksudo gedit /etc/default/acpi-support

2. Find this line: **POST_VIDEO=true** and change to: **POST_VIDEO=**


Reboot and see if that helps any. If XServer crashes and throws you to the terminal, just revert by:

1. Log in terminal

2. sudo nano -w /etc/default/acpi-support

3. Change POST_VIDEO back to true

4. Reboot if you have to.

---

### Post by Alterac on 2008-04-07
Hi, thanks for helping out.

I've tried to do as you've said. After removing "true" and rebooting, I suspended my laptop. It went into suspended mode fine. However, upon starting up, nothing appears. The screen remains black.

I've already reverted the file. Still the same problem as before - dim and flickering display.

---

### Post by riven0 on 2008-04-07
Okay, why don't you post the output of this file: **/etc/default/acpi-support**. Also, what graphics cards are you using?

---

### Post by Alterac on 2008-04-07
> # Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12

The graphic card I'm using is a Integrated Intel GMA X3100.

---

### Post by canthus13 on 2008-04-07
This is a bit obnoxious, but try the previous edit mentioned again, suspend, turn it back on, and when you get the black screen, hold down ctrl and alt, and then tap back and forth a few times between f6, f7, and f8.  I don't know why it works, but it does for mine.  I've read that the issue has to do with the fact that the ACPI BIOS code is proprietary.

--Me

---

### Post by riven0 on 2008-04-07
> **Alterac said:**
> The graphic card I'm using is a Integrated Intel GMA X3100.

:( That looks exactly like my configuration except for the POST_VIDEO part. Well, you may have already done so, but try install the **hibernate** and **suspend2-userui** packages from the repositories. That's what I did, and along with the POST_VIDEO tweak, my suspend issues were solved.

Also, take a look at this post, it may help some: [Problems with Restart/Suspend/Hibernation]("http://ubuntuforums.org/showpost.php?p=2835450&postcount=13")

---

### Post by Alterac on 2008-04-07
> **canthus13 said:**
> This is a bit obnoxious, but try the previous edit mentioned again, suspend, turn it back on, and when you get the black screen, hold down ctrl and alt, and then tap back and forth a few times between f6, f7, and f8.  I don't know why it works, but it does for mine.  I've read that the issue has to do with the fact that the ACPI BIOS code is proprietary.

--Me

I tried this. The black screen switched to the dim, flickering one.

Thanks anyways.

> **riven0 said:**
> :( That looks exactly like my configuration except for the POST_VIDEO part. Well, you may have already done so, but try install the **hibernate** and **suspend2-userui** packages from the repositories. That's what I did, and along with the POST_VIDEO tweak, my suspend issues were solved.

Also, take a look at this post, it may help some: [Problems with Restart/Suspend/Hibernation]("http://ubuntuforums.org/showpost.php?p=2835450&postcount=13")

Thanks again.
I haven't tried this method yet.
I could install uswsusp but could not run this line:
> sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi
It keeps saying "command not found". Any idea why?

---

### Post by riven0 on 2008-04-07
> **Alterac said:**
> 
Thanks again.
I haven't tried this method yet.
I could install uswsusp but could not run this line:

It keeps saying "command not found". Any idea why?

I checked on Debian's website and apparently you're supposed to use --add with it. So, does this work?: 

**sudo dpkg-divert --add --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi**

---

### Post by Alterac on 2008-04-07
> **riven0 said:**
> I checked on Debian's website and apparently you're supposed to use --add with it. So, does this work?: 

**sudo dpkg-divert --add --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi**

oops... i just realised that I'm suppose to add spaces before a "--" and also after "--divert". I didn't use the "--add" option.

Okay, so I've entered the above line (without --add), rebooted and tried to suspend.

Produced the same results: black screen and after repeatedly switching between ctrl alt-f6, -f7 and -f8 I get the dim flickering screen. ("true" is removed from POST_VIDEO=)

Once again, thanks for continuing to assist me :)

---

### Post by koba101 on 2008-04-07
This happens to my PC as well (Intel mobo --core 2 duo)

---

### Post by riven0 on 2008-04-07
The last tweak I can think of is to go to the gconf-editor, (**sudo gconf-editor**), and if you haven't already done so, go to: Apps > Gnome-Power-Manager and look for these three entries:

lock_on_blank_screen

lock_on_hibernate

lock_on_suspend


And uncheck all three of them. Then do the CTRL+ALT+Backspace, or reboot if you want and try suspending again. 


If that doesn't work, I'm out of options. Sorry I couldn't help more. :(

---

### Post by Alterac on 2008-04-08
Sorry for taking so long to reply.

I've tried that out as well. It didn't work even with all the other tweaks combined.

Thanks for helping out so far. :)

Anyone else has any idea on how to solve this problem? :confused:

---

### Post by Alterac on 2008-04-09
bring
up
my
post

Please help :(

---

### Post by Alterac on 2008-04-10
one last try....

please help :(

---

### Post by NullHead on 2008-04-10
I don't know about intel graphics, but do you have the proper driver installed?

---

### Post by NullHead on 2008-04-10
Well it's worth a try. These are the things I did to make my Dell Inspiron 8600 sleep:
```

gksudo gedit /etc/default/acpi-support
```

and make these changes:

[B]SAVE_VBE_STATE=false

POST_VIDEO=false

HIBERNATE_MODE=platform[/B]

---

### Post by Alterac on 2008-04-11
> **NullHead said:**
> Well it's worth a try. These are the things I did to make my Dell Inspiron 8600 sleep:
```

gksudo gedit /etc/default/acpi-support
```

and make these changes:

[B]SAVE_VBE_STATE=false

POST_VIDEO=false

HIBERNATE_MODE=platform[/B]

Thanks for helping out.

It didn't work either.

Sigh. I guess I'll wait till 8.04 releases and hope it works then.:(

---

### Post by Alterac on 2008-05-04
Suspend works fine in 8.04! :guitar:

---

