---
title: "A beginner's Ubuntu hurdles"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by narvitopia on 2007-03-05
Hello all.

So I installed Ubuntu on my laptop, and while I really like the experience of using it so far, there are three things that are preventing me from totally switching over from XP:
[LIST=1]
[*]Fonts: I'm so used to Windows that I really just want my fonts to look like Windows in all programs. Probably an easy one to fix, but I've gone through steps listed in messages on this board, and can't seem to get this fixed.
[*]Syncing with Treo 700w (Windows Mobile 5): It seems that while there are a lot of posts about syncing Windows Mobile devices (and how hard it is), there's almost nothing on the Treo 700w. 
[*]Suspend to Ram/Hibernate not working: I have an HP ze4200 AMD laptop and it will go into standby, but when I try to bring it back up, it comes on for a second and then totally shuts down. Again, I've looked around on these boards for a similar problem with similar computers, but with no luck.
[/LIST]

Being an old laptop with 512MB of RAM, I REALLY want to get Ubuntu working on it - it's just SO much snappier and nicer than trying to continue with XP at this point. 

Help?

---

### Post by Paerez on 2007-03-05
1) install "msttcorefonts" then open System->Preferences->Fonts and change the Sans fonts to Verdana and the mono font to Andale, and the serif fonts to Times New Roman.

2) dunno

3) Probably your video card.

---

### Post by narvitopia on 2007-03-05
Thanks Paerez!

Well, one down, two to go. 

If I can get these three things working, how happy I will be.

-=N=-

---

### Post by Paerez on 2007-03-05
what is the output of these programs:

lspci
grep Driver /etc/X11/xorg.conf

---

### Post by narvitopia on 2007-03-05
Take into account here that I'm a total beginner. How do I check the output of those programs?

I'm at work now, so I'll do it when I get home and post the results.

Thanks again.

-=N=-

---

### Post by oilchangeguy on 2007-03-05
in version 6.06, go to applications, accessories, terminal. open the terminal and type the requested command.

---

### Post by narvitopia on 2007-03-05
Ah, so just type:
lspci
and then type:
grep Driver /etc/X11/xorg.conf

Excellent. Thanks. Will give results tonight.

Anyone have any hints on Treo 700w syncing?

---

### Post by lamalex on 2007-03-05
> **narvitopia said:**
> Ah, so just type:
lspci
and then type:
grep Driver /etc/X11/xorg.conf

Excellent. Thanks. Will give results tonight.

Anyone have any hints on Treo 700w syncing?

no youll want to do ```
cat /etc/X11/xorg.conf |grep Driver
```
what that means is print any line in the xorg.conf file that has Driver in it. Thats a very simplified way of explaining it but, it works :) you'll want to maybe pick up a book or something, command line is very useful when you learn it well.

EDIT: actually both commands output identical output, so pick your favourite

---

### Post by Paerez on 2007-03-05
lol lamalex:

grep Driver /etc/X11/xorg.conf

is the same as:
cat /etc/X11/xorg.conf | grep Driver

except my way is more efficient.

---

### Post by narvitopia on 2007-03-06
Alright, here are the results.

After typing "lspci" I get:
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface


And after typing "cat /etc/X11/xorg.conf |grep Driver" I get:
Driver          "kbd"
        Driver          "mouse"
        Driver          "synaptics"
  Driver        "wacom"
  Driver        "wacom"
  Driver        "wacom"
        Driver          "ati"


Any thoughts?

Thanks!

-=N=-

---

### Post by Paerez on 2007-03-06
That looks like a pretty good graphics set up for hibernating and suspending, lets check your suspending configuration file. Can you post the contents of:
cat /etc/default/acpi-support

---

### Post by narvitopia on 2007-03-06
Sounds good - I will check that tonight and post my results.

Thanks again for the font tip - I did it and it looks pretty much like my windows fonts. However, I think I messed something up. I changed everything except the mono font to "Verdana." Which one should I change to "Times New Roman?"

Also, is there a way to get the fonts to be a little bigger overall? They are pretty small it seems.

Thanks!

-=N=-

---

### Post by Paerez on 2007-03-06
Hey if they are small, just raise them.

Here is a shot of mine, showing what you should change

You may want to set Document Font to Times New Roman. Your call.

---

### Post by narvitopia on 2007-03-06
Got it. Thanks again, mucho.

I'll get back to you tonight with that other stuff.

Good weather in San Francisco today. Hoorah.

-=N=-

---

### Post by Paerez on 2007-03-06
great weather today in.... baltimore .... ;(

ahh who am I kidding its 30, cold, and windy.

---

### Post by narvitopia on 2007-03-07
> **Paerez said:**
> That looks like a pretty good graphics set up for hibernating and suspending, lets check your suspending configuration file. Can you post the contents of:
cat /etc/default/acpi-support

Alright, here's my suspending config file:
-------------
# Comment the next line to disable ACPI suspend to RAM
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
POST_VIDEO=false

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
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false
-------------

Thoughts?

-=N=-

---

### Post by Paerez on 2007-03-07
OK change:

SAVE_VBE_STATE=false
DOUBLE_CONSOLE_SWITCH=true

then reboot and try suspend and hibernate.

---

### Post by narvitopia on 2007-03-07
Paerez,

Made those changes (after a bit of research on how to do so! Learning and learning.), rebooted, and tried to suspend. No luck :(

Other ideas?

---

### Post by narvitopia on 2007-03-07
To be more specific, I tried SUSPEND, and the laptop seemed to go into suspend mode, but when I tried to bring it out of SUSPEND, it flashed for a second and then just shut off completely.

I then tried Hibernate, in which case it seemed to turn off completely, but then when I rebooted it brought me to a different login screen than usual and then put me back exactly where I was before the hibernation. But the bootup sequence still took a good while. Still, I guess it was faster than a total reboot, but it seems hibernate should be much faster - more like a slightly longer Suspend.

Thoughts?

---

### Post by Paerez on 2007-03-07
I can get suspend to work, but not hibernate. Here is my whole acpi-support file:

```
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Comment the next line to disable the use of the hibernate script for
# driving the suspend-to-disk process.
ACPI_USE_HIBERNATE_SCRIPT=true

# Arguments to pass to the hibernate script if ACPI_USE_HIBERNATE_SCRIPT is set
#ACPI_HIBERNATE_ARGS="--config-file=/etc/hibernate/suspend2.conf"

# Enable the following to use the hibernate script for suspend to RAM also.
# Enabling this means that most of the rest of this file is irrelevant.
# Add your tweaks to /etc/hibernate/ram.conf instead.
#ACPI_USE_HIBERNATE_FOR_STR=true

# Arguments to pass to the hibernate script for suspend to RAM if
# ACPI_USE_HIBERNATE_FOR_STR is enabled, above.
#ACPI_HIBERNATE_STR_ARGS="--config-file=/etc/hibernate/ram.conf"

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
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

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
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false
```

---

### Post by narvitopia on 2007-03-08
Damn - that didn't work. I copied your text and pasted it into my file, and no go. Same result - computer comes on for a second, then turns off completely. Argh.

Thoughts?

-=N=-

---

### Post by Paerez on 2007-03-08
beyond this point suspending and hibernation is voodoo magic to me. I am still trying to get my comp to hibernate.

Though I think my problem is that I installed dapper and have since upgraded to edgy and feisty, so I think many of my conf files are confused.

---

### Post by narvitopia on 2007-03-08
Thanks Paerez. Maybe I'll update from Edgy to Feisty and see if that changes anything. 

I'm surprised no one else has chimed in with expertise. :( So sad.

Thanks again! Enjoy that east coast winter - spring is a'comin'.

-=N=-

---

### Post by CadetD on 2008-03-12
*** Bump  *** 

Someone has the answer to the last question, I am sure. 

There has to be someone out there who managed to configure sync with the Treo 700w/wx.

---

### Post by A$h X on 2008-03-12
This link may help you:

[http://discussion.treocentral.com/showthread.php?p=1416935](http://discussion.treocentral.com/showthread.php?p=1416935)

---

### Post by CadetD on 2008-03-13
> **A$h X said:**
> This link may help you:

[http://discussion.treocentral.com/showthread.php?p=1416935](http://discussion.treocentral.com/showthread.php?p=1416935)

Thanks but as all oher links, describes the 700p or 650. Neither run Windows Mobile. 

Problem is with 700w or 700wx.

---

