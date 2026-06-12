---
title: "Wireless Roaming Mode"
date: 2008-10-31
forum: Arch and derivatives
---

### Post by zephyrus17 on 2008-10-31
I have a T61p with the Intel 4965 and with Gnome. How do I enable roaming mode for my wireless?

And, along the same line, how do I enable my ethernet to roam as well?

---

### Post by kpkeerthi on 2008-10-31
[Wicd]("http://wicd.sourceforge.net/")?

---

### Post by SomeGuyDude on 2008-10-31
At the risk of sounding like an idiot, what is "roaming mode" and how could that possibly apply to a wired ethernet connection?

---

### Post by zephyrus17 on 2008-10-31
You mean ethernet is already roaming?

I'm having a slight problem. I'm having trouble getting my wireless connected. Here's my rc.conf ```
#
# /etc/rc.conf - Main Configuration for Arch Linux
#

# -----------------------------------------------------------------------
# LOCALIZATION
# -----------------------------------------------------------------------
#
# LOCALE: available languages can be listed with the 'locale -a' command
# HARDWARECLOCK: set to "UTC" or "localtime"
# USEDIRECTISA: use direct I/O requests instead of /dev/rtc for hwclock
# TIMEZONE: timezones are found in /usr/share/zoneinfo
# KEYMAP: keymaps are found in /usr/share/kbd/keymaps
# CONSOLEFONT: found in /usr/share/kbd/consolefonts (only needed for non-US)
# CONSOLEMAP: found in /usr/share/kbd/consoletrans
# USECOLOR: use ANSI color sequences in startup messages
#
LOCALE="en_AU.utf8"
HARDWARECLOCK="UTC"
USEDIRECTISA="no"
TIMEZONE="Australia/Adelaide"
KEYMAP="dvorak"
CONSOLEFONT=
CONSOLEMAP=
USECOLOR="yes"

# -----------------------------------------------------------------------
# HARDWARE
# -----------------------------------------------------------------------
#
# MOD_AUTOLOAD: Allow autoloading of modules at boot and when needed
# MOD_BLACKLIST: Prevent udev from loading these modules
# MODULES: Modules to load at boot-up. Prefix with a ! to blacklist.
#
# NOTE: Use of 'MOD_BLACKLIST' is deprecated. Please use ! in the MODULES array.
#
MOD_AUTOLOAD="yes"
#MOD_BLACKLIST=() #deprecated
MODULES=(ac battery button dock processor thermal video wmi cdrom intel-agp nvram hid usbhid i2c-i801 i2c-core evdev ff-memless joydev pcspkr psmouse serio_raw led-class thinkpad_acpi mmc_core ricoh_mmc sdhci-pci sdhci pci_hotplug shpchp rtc-cmos rtc-core rtc-lib nvidia output iTCO_vendor_support iTCO_wdt snd-mixer-oss snd-pcm-oss snd-hwdep snd-page-alloc snd-pcm snd-timer snd snd-pcsp snd-hda-intel soundcore pata_acpi ata_generic scsi_mod ahci ata_piix e1000e mac80211 rfkill iwlagn iwlcore cfg80211 pcmcia_core rsrc_nonstatic yenta_socket usbhid usbcore ehci-hcd uhci-hcd ieee1394 ohci1394 sd_mod sr_mod)

# Scan for LVM volume groups at startup, required if you use LVM
USELVM="no"

# -----------------------------------------------------------------------
# NETWORKING
# -----------------------------------------------------------------------
#
# HOSTNAME: Hostname of machine. Should also be put in /etc/hosts
#
HOSTNAME="Arkainia_Prime"

# Use 'ifconfig -a' or 'ls /sys/class/net/' to see all available interfaces.
#
# Interfaces to start at boot-up (in this order)
# Declare each interface then list in INTERFACES
#   - prefix an entry in INTERFACES with a ! to disable it
#   - no hyphens in your interface names - Bash doesn't like it
# 
# DHCP:     Set your interface to "dhcp" (eth0="dhcp")
# Wireless: See network profiles below
#

#eth0="eth0 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255"
eth0="dhcp"
INTERFACES=(eth0 wlan0)

# Routes to start at boot-up (in this order)
# Declare each route then list in ROUTES
#   - prefix an entry in ROUTES with a ! to disable it
#
gateway="default gw 192.168.0.1"
ROUTES=(!gateway)
 
# Enable these network profiles at boot-up.  These are only useful
# if you happen to need multiple network configurations (ie, laptop users)
#   - set to 'menu' to present a menu during boot-up (dialog package required)
#   - prefix an entry with a ! to disable it
#
# Network profiles are found in /etc/network.d
#
# This now requires the netcfg package
#
#NETWORKS=(main)

# -----------------------------------------------------------------------
# DAEMONS
# -----------------------------------------------------------------------
#
# Daemons to start at boot-up (in this order)
#   - prefix a daemon with a ! to disable it
#   - prefix a daemon with a @ to start it up in the background
#
DAEMONS=(syslog-ng @laptop-mode !network @dbus @wicd @netfs crond @adsl @acpid @hal @fam @alsa @transmissiond @mpd @gdm)
```

What seems to be the problem? wicd won't start.

I want to either use wicd or nm-applet. I'm ok with either.

---

### Post by Rumor on 2008-10-31
I use wicd on my eee 901 running Arch. The thing I see in your rc.conf file is that you have not disabled your interfaces that you wish wicd to control. The [wiki]("http://wiki.archlinux.org/index.php/Wicd") article on wicd is a good source for getting wicd up and running.

> Disable (!) any devices in the INTERFACES array that you wish to manage with Wicd. For example: 
```
INTERFACES=(!eth0 !wlan0)
``` 

You might also want to un-background dbus in your daemons array so that it starts before you start the wicd daemon.

---

### Post by zephyrus17 on 2008-10-31
Well, the thing is, the wireless is fine now. I didn't want wicd to control my ppp connection, because it's working fine as it is, but now my Sonata/mpd won't connect. Here's my updated rc.conf ```
#
# /etc/rc.conf - Main Configuration for Arch Linux
#

# -----------------------------------------------------------------------
# LOCALIZATION
# -----------------------------------------------------------------------
#
# LOCALE: available languages can be listed with the 'locale -a' command
# HARDWARECLOCK: set to "UTC" or "localtime"
# USEDIRECTISA: use direct I/O requests instead of /dev/rtc for hwclock
# TIMEZONE: timezones are found in /usr/share/zoneinfo
# KEYMAP: keymaps are found in /usr/share/kbd/keymaps
# CONSOLEFONT: found in /usr/share/kbd/consolefonts (only needed for non-US)
# CONSOLEMAP: found in /usr/share/kbd/consoletrans
# USECOLOR: use ANSI color sequences in startup messages
#
LOCALE="en_AU.utf8"
HARDWARECLOCK="UTC"
USEDIRECTISA="no"
TIMEZONE="Australia/Adelaide"
KEYMAP="dvorak"
CONSOLEFONT=
CONSOLEMAP=
USECOLOR="yes"

# -----------------------------------------------------------------------
# HARDWARE
# -----------------------------------------------------------------------
#
# MOD_AUTOLOAD: Allow autoloading of modules at boot and when needed
# MOD_BLACKLIST: Prevent udev from loading these modules
# MODULES: Modules to load at boot-up. Prefix with a ! to blacklist.
#
# NOTE: Use of 'MOD_BLACKLIST' is deprecated. Please use ! in the MODULES array.
#
MOD_AUTOLOAD="yes"
#MOD_BLACKLIST=() #deprecated
MODULES=(ac battery button dock processor thermal video wmi cdrom intel-agp nvram hid usbhid i2c-i801 i2c-core evdev ff-memless joydev pcspkr psmouse serio_raw led-class thinkpad_acpi mmc_core ricoh_mmc sdhci-pci sdhci pci_hotplug shpchp rtc-cmos rtc-core rtc-lib nvidia output iTCO_vendor_support iTCO_wdt !snd-mixer-oss !snd-pcm-oss !snd-hwdep !snd-page-alloc !snd-pcm !snd-timer !snd !snd-pcsp snd-hda-intel !soundcore pata_acpi ata_generic scsi_mod ahci ata_piix e1000e mac80211 rfkill iwlagn iwlcore iwl4965 cfg80211 pcmcia_core rsrc_nonstatic yenta_socket usbhid usbcore ehci-hcd uhci-hcd ieee1394 ohci1394 sd_mod sr_mod)

# Scan for LVM volume groups at startup, required if you use LVM
USELVM="no"

# -----------------------------------------------------------------------
# NETWORKING
# -----------------------------------------------------------------------
#
# HOSTNAME: Hostname of machine. Should also be put in /etc/hosts
#
HOSTNAME="Arkainia_Prime"

# Use 'ifconfig -a' or 'ls /sys/class/net/' to see all available interfaces.
#
# Interfaces to start at boot-up (in this order)
# Declare each interface then list in INTERFACES
#   - prefix an entry in INTERFACES with a ! to disable it
#   - no hyphens in your interface names - Bash doesn't like it
# 
# DHCP:     Set your interface to "dhcp" (eth0="dhcp")
# Wireless: See network profiles below
#

#eth0="eth0 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255"
eth0="dhcp"
INTERFACES=(lo eth0 !wlan0)

# Routes to start at boot-up (in this order)
# Declare each route then list in ROUTES
#   - prefix an entry in ROUTES with a ! to disable it
#
gateway="default gw 192.168.0.1"
ROUTES=(!gateway)
 
# Enable these network profiles at boot-up.  These are only useful
# if you happen to need multiple network configurations (ie, laptop users)
#   - set to 'menu' to present a menu during boot-up (dialog package required)
#   - prefix an entry with a ! to disable it
#
# Network profiles are found in /etc/network.d
#
# This now requires the netcfg package
#
#NETWORKS=(main)

# -----------------------------------------------------------------------
# DAEMONS
# -----------------------------------------------------------------------
#
# Daemons to start at boot-up (in this order)
#   - prefix a daemon with a ! to disable it
#   - prefix a daemon with a @ to start it up in the background
#
DAEMONS=(syslog-ng @laptop-mode @acpid !network @netfs crond hal @fam @adsl @wicd @alsa @transmissiond @mpd @gdm)
```
I didn't add dbus because I read that starting hal automatically starts dbus

What does "lo" do? Should it even be in "INTERFACES=("?

---

### Post by Rumor on 2008-10-31
No, you don't need lo in your interfaces.

Try starting mpd from a root terminal (/etc/rc.d/mpd restart). If it starts fine, then maybe you need to un-background it in your array.

My array has mpd before wicd, but I don't know if that makes any difference:
```
DAEMONS=(syslog-ng !network netfs crond mpd hal fam acpid wicd slim)
```
My eth0 is also disabled, but if you didn't make any changes to that and your mpd+sonata was working before, then it shouldn't make any difference.

---

### Post by zephyrus17 on 2008-10-31
Right, I'll give it a shot. Does it matter if all the daemons are backgrounded? Or should have be background and half active? Because if all daemons are background, then none of them are background..

MPD won't connect by itself. I need to run ```
# /etc/rc.d/mpd restart
``` to get it to get my music. Even after taking out the "@".

---

