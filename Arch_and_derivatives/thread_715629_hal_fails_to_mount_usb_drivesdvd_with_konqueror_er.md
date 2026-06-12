---
title: "hal fails to mount usb drives/dvd with konqueror erred as Feature  available wit hal"
date: 2008-03-05
forum: Arch and derivatives
---

### Post by deepclutch on 2008-03-05
Hi,
Just finished installing archlinux with kdemod.whenever I put a dvd/cd ,konqueror pops up with "want to open?" question,if I select,below error pops out :(

```
Feature only available with HAL
```
I can see that my dvd(/dev/sr0) is shown in konqueror,but if I press it is not mounted.

although I can manually mount cd or usb pendrive etc .

I tried removing /etc/fstab entry for /dev/sr0(dvd drive),but then not at all detected by hal.
here is my /etc/fstab:
```
/dev/dvd  /media/cdrom0  udf,iso9660 ro,user,noauto,unhide   0     0
```
I have tried arch forums and arch wiki for a solution,have below lines in a newly made file /etc/hal/fdi/policy/preferences.fdi :
```
<?xml version="1.0" encoding="UTF-8"?>
 <deviceinfo version="0.2">



<device>
   <match key="storage.hotpluggable" bool="false">
   <match key="storage.removable" bool="false">
   <merge key="storage.automount_enabled_hint" type="bool">false</merge>
   <merge key="volume.ignore" type="bool">false</merge>
   </match>
   </match>
</device>

 <device>
   <match key="block.is_volume" bool="true">
   <match key="volume.size" compare_lt="8000000000">
   <match key="@block.storage_device:storage.hotpluggable" bool="true">
   <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
   <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
   </match>
   <match key="@block.storage_device:storage.removable" bool="true">
   <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
   <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
   </match>
   </match>
   <match key="volume.size" compare_ge="8000000000">
   <match key="@block.storage_device:storage.hotpluggable" bool="true">
   <merge key="volume.policy.mount_option.sync" type="bool">false</merge>
   <merge key="volume.policy.mount_option.noatime" type="bool">false</merge>
   </match>
   <match key="@block.storage_device:storage.removable" bool="true">
   <merge key="volume.policy.mount_option.sync" type="bool">false</merge>
   <merge key="volume.policy.mount_option.noatime" type="bool">false</merge>
   </match>
   </match>
   </match>
</device>


</deviceinfo>
```
Is this a problem with HAL ,dbus?
I can very well restart these services.
below is my /etc/rc.conf:
```
# Scan hardware and load required modules at bootup
MOD_AUTOLOAD="yes"
# Module Blacklist - modules in this list will never be loaded by udev
MOD_BLACKLIST=(intel_agp)
#
# Modules to load at boot-up (in this order)
#   - prefix a module with a ! to blacklist it
#
MODULES=(8139cp 8139too mii slhc ppp_generic ac97_bus snd-mixer-oss snd-pcm-oss snd-page-alloc snd-pcm snd-timer snd snd-ac97-codec snd-intel8x0 soundcore)
# Scan for LVM volume groups at startup, required if you use LVM
USELVM="no"

#
# -----------------------------------------------------------------------
# NETWORKING
# -----------------------------------------------------------------------
#
HOSTNAME="myhost"
#
# Use 'ifconfig -a' or 'ls /sys/class/net/' to see all available
# interfaces.
#
# Interfaces to start at boot-up (in this order)
# Declare each interface then list in INTERFACES
#   - prefix an entry in INTERFACES with a ! to disable it
#   - no hyphens in your interface names - Bash doesn't like it
#
# Note: to use DHCP, set your interface to be "dhcp" (eth0="dhcp")
#
# Don't use this for wireless interfaces, see network profiles below
#
eth0="eth0 192.168.1.2 netmask 255.255.255.0 broadcast 192.168.1.255"
INTERFACES=(eth0)
#
# Routes to start at boot-up (in this order)
# Declare each route then list in ROUTES
#   - prefix an entry in ROUTES with a ! to disable it
#
#gateway="default gw 192.168.1.1"
#ROUTES=(gateway)
#
# Enable these network profiles at boot-up.  These are only useful
# if you happen to need multiple network configurations (ie, laptop users)
#   - set to 'menu' to present a menu during boot-up (dialog package required)
#   - prefix an entry with a ! to disable it
#
# Network profiles are found in /etc/network-profiles
#
#NET_PROFILES=(main)

#
# -----------------------------------------------------------------------
# DAEMONS
# -----------------------------------------------------------------------
#
# Daemons to start at boot-up (in this order)
#   - prefix a daemon with a ! to disable it
#   - prefix a daemon with a @ to start it up in the background
#
DAEMONS=(syslog-ng hal network ppp netfs crond)
```
Is there some custom hal build available for kdemod?Thank You All!waiting....

---

### Post by finferflu on 2008-03-05
Did you check out the wiki for HAL? [Here](http://wiki.archlinux.org/index.php/HAL).

Good luck ;)

---

### Post by deepclutch on 2008-03-05
after a reboot,thinks works normally,a popup dialog comes with a progress bar mounting cd/dvd and usb drives.some "kio_xx" thing :p
Thank you.
yeah,already tried wiki .

---

### Post by kpkeerthi on 2008-03-05
Is it OK to use /etc/hal/fdi/policy/preferences.fdi file. Arch [WIKI ]("http://wiki.archlinux.org/index.php/HAL")says it is deprecated from hal >= 0.5.10

[quote="http://wiki.archlinux.org/index.php/HAL"]
Policies

**NOTE: this is deprecated from hal => 0.5.10**

Create the "/etc/hal/fdi/policy/preferences.fdi" file and open it with a text editor. Insert

 <?xml version="1.0" encoding="UTF-8"?> 
 <deviceinfo version="0.2">
 
   [RULE_1]
 
   [RULE_2]
 
 </deviceinfo>

and instead of [RULE_X] add the rules below (the ones you need). 
[/quote]

---

### Post by deepclutch on 2008-03-05
yeah,currently I am using preferences.fdi with contents as in #1 post.
I am a satisfied Arch kde(mod) user :cool:
this kdemod thing is awesome!u wont need to install full kde bloat!just what u needed!kudos to the devels and community :)

---

### Post by deepclutch on 2008-03-12
I have filed a bug report in arch BTS:
** 	 FS#9821 - HAL does not automount CD/DVD drives,USB drives in kde(kdemod)  **


[http://bugs.archlinux.org/task/9821](http://bugs.archlinux.org/task/9821)

---

### Post by aeto on 2008-03-12
If you think it's more of a kdemod issue, there is a kdemod bugtracker.

---

### Post by deepclutch on 2008-03-13
^Thx.already kdemod maintainer "@funkyou" noted the bug report.

---

### Post by deepclutch on 2008-03-13
the problem is "automagically" solved after a kdemod-*** update!now no policy file in /etc/hal/ dir.thank you :)

---

