---
title: "[SOLVED] troubleshooting sleep and suspend"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by El_Matthews on 2007-12-20
All,

the sleep and suspend aren't working on my computer. I would like to start using them but as soon as I use one of them my pc resumes directly.

I have no problem to put some time in making it work but I have nu clue where to start.

example, which command puts the computer to sleep? Where can I see what's going wrong etc.

If I succeed I could try to document everything for other users to get a troubleshooting guide.

Regards,

Matthews

---

### Post by nick_h on 2007-12-20
As a starting point read the [HowTo: Debug Suspend, Resume, Hibernate issues](http://ubuntuforums.org/showthread.php?t=505890) thread.

---

### Post by El_Matthews on 2007-12-23
ok I followed the guide and now when I try to put my pc to sleep I get this output;
```
mg@wsubu:/etc/acpi$ sudo ./sleep.sh force
[sudo] password for mg:
ifdown: interface eth0 not configured
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5098
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:f8:a8:70:87
Sending on   LPF/wlan0/00:18:f8:a8:70:87
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
 * Shutting down ALSA...                                                 [ OK ] 
/etc/acpi/resume.d/17-video-restore.sh: line 5: /var/lib/acpi-support/vbestate: No such file or directory
Function not supported
ifup: interface wlan0 already configured
 * Setting up ALSA...                                                    [ OK ] 
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.

```
What next ?

---

### Post by El_Matthews on 2007-12-23
Sorry, small mistake.
with following options the pc goes to sleep correctly
```

+ . /etc/default/acpi-support
++ ACPI_SLEEP=true
++ ACPI_HIBERNATE=true
[COLOR="Red"]++ ACPI_SLEEP_MODE=standby[/COLOR]
++ MODULES=
++ MODULES_WHITELIST=
++ SAVE_VBE_STATE=true
++ VBESTATE=/var/lib/acpi-support/vbestate

```

with the option ACPI_SLEEP_MODE=mem it doesn't work and I get following output.
```
mg@wsubu:/etc/acpi$ sudo ./sleep.sh force
+ . /etc/default/acpi-support
++ ACPI_SLEEP=true
++ ACPI_HIBERNATE=true
++ ACPI_SLEEP_MODE=mem
++ MODULES=
++ MODULES_WHITELIST=
++ SAVE_VBE_STATE=true
++ VBESTATE=/var/lib/acpi-support/vbestate
++ POST_VIDEO=true
++ USE_DPMS=true
++ HIBERNATE_MODE=shutdown
++ LOCK_SCREEN=true
++ STOP_SERVICES=
++ RESTART_IRDA=false
++ ENABLE_LAPTOP_MODE=false
++ SPINDOWN_TIME=12
+ . /usr/share/acpi-support/power-funcs
++ umask 022
++ PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/usr/bin/X11
++ POWERSTATE=/var/lib/acpi-support/powerstate
++ LAPTOP_MODE=/usr/sbin/laptop_mode
++ HDPARM='/sbin/hdparm -q'
++ LIDSTATE=/var/lib/acpi-support/lidstate
+ . /usr/share/acpi-support/device-funcs
+ . /usr/share/acpi-support/policy-funcs
+ DeviceConfig
++ cat /var/lib/acpi-support/system-manufacturer
+ manufacturer='To Be Filled By O.E.M.'
++ cat /var/lib/acpi-support/system-product-name
+ model='To Be Filled By O.E.M.'
++ cat /var/lib/acpi-support/system-version
+ version='To Be Filled By O.E.M.'
++ cat /var/lib/acpi-support/bios-version
+ bios_version=1009.003
+ '[' -f '/usr/share/acpi-support/To Be Filled By O.E.M..config' ']'
+ '[' xtrue '!=' xtrue ']'
+ '[' xforce '!=' xforce ']'
+ '[' xtrue = xtrue ']'
+ pidof xscreensaver
+ . /etc/acpi/prepare.sh
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/05-acpi-lock.sh ']'
++ . /etc/acpi/suspend.d/05-acpi-lock.sh
+++ touch /var/lock/acpisleep
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/10-thinkpad-standby-led.sh ']'
++ . /etc/acpi/suspend.d/10-thinkpad-standby-led.sh
+++ . /usr/share/acpi-support/state-funcs
+++ setLEDThinkpadSuspending 1
++++ test 1 -ne 0
++++ echo blink
+++ action=blink
+++ test -w /proc/acpi/ibm/led
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/15-anacron.sh ']'
++ . /etc/acpi/suspend.d/15-anacron.sh
+++ /usr/sbin/invoke-rc.d anacron stop
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/30-proc-sysfs-save-state.sh ']'
++ . /etc/acpi/suspend.d/30-proc-sysfs-save-state.sh
+++ '[' -d /var/run -a -w /var/run ']'
+++ for i in '/sys/class/net/*/device/rf_kill' '/sys/devices/system/cpu/cpu*/cpufreq/scaling_governor'
+++ '[' -r '/sys/class/net/*/device/rf_kill' ']'
+++ for i in '/sys/class/net/*/device/rf_kill' '/sys/devices/system/cpu/cpu*/cpufreq/scaling_governor'
+++ '[' -r '/sys/devices/system/cpu/cpu*/cpufreq/scaling_governor' ']'
+++ i=/proc/acpi/ibm/bluetooth
+++ '[' -r /proc/acpi/ibm/bluetooth ']'
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/50-irda-stop.sh ']'
++ . /etc/acpi/suspend.d/50-irda-stop.sh
+++ '[' -f /var/run/irattach.pid ']'
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/50-tosh-save-brightness.sh ']'
++ . /etc/acpi/suspend.d/50-tosh-save-brightness.sh
+++ TOSH_LCD=/proc/acpi/toshiba/lcd
+++ '[' -e /proc/acpi/toshiba/lcd ']'
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/55-down-interfaces.sh ']'
++ . /etc/acpi/suspend.d/55-down-interfaces.sh
+++ pccardctl eject
+++ killall dhclient dhclient3
++++ /sbin/ifconfig
++++ awk '/^[^ ]+/ {print $1}'
+++ INTERFACES='lo
wlan0'
+++ for x in '$INTERFACES'
+++ ifdown lo
+++ ifconfig lo down
+++ for x in '$INTERFACES'
+++ ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 9556
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:f8:a8:70:87
Sending on   LPF/wlan0/00:18:f8:a8:70:87
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
+++ ifconfig wlan0 down
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/60-generate-modules-list.sh ']'
++ . /etc/acpi/suspend.d/60-generate-modules-list.sh
+++ for x in '/sys/module/*_ircc' '/sys/module/*_ircc2'
++++ basename '/sys/module/*_ircc'
+++ x='*_ircc'
+++ '[' '*_ircc' '!=' nsc_ircc ']'
+++ modprobe -r '*_ircc'
+++ for x in '/sys/module/*_ircc' '/sys/module/*_ircc2'
++++ basename '/sys/module/*_ircc2'
+++ x='*_ircc2'
+++ '[' '*_ircc2' '!=' nsc_ircc ']'
+++ modprobe -r '*_ircc2'
+++ '[' -d /sys/module/ndiswrapper ']'
+++ modprobe -r ndiswrapper
+++ MODULES=' ndiswrapper'
+++ for x in '/sys/class/net/*'
+++ '[' -e /sys/class/net/eth0/device/driver ']'
+++++ readlink /sys/class/net/eth0/device/driver
++++ tr '[:upper:]' '[:lower:]'
++++ basename ../../../../bus/pci/drivers/skge
+++ MODULES=' ndiswrapper skge'
+++ for x in '/sys/class/net/*'
+++ '[' -e /sys/class/net/lo/device/driver ']'
+++ '[' -d /sys/module/netconsole ']'
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/65-services-stop.sh ']'
++ . /etc/acpi/suspend.d/65-services-stop.sh
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/70-modules-unload.sh ']'
++ . /etc/acpi/suspend.d/70-modules-unload.sh
+++ for x in '$MODULES'
+++ modprobe -r ndiswrapper
+++ for x in '$MODULES'
+++ modprobe -r skge
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/75-console-switch.sh ']'
++ . /etc/acpi/suspend.d/75-console-switch.sh
++++ fgconsole
+++ CONSOLE=7
+++ chvt 12
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/80-video-pci-state.sh ']'
++ . /etc/acpi/suspend.d/80-video-pci-state.sh
+++ '[' x = xtrue ']'
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/80-video-vesa-state.sh ']'
++ . /etc/acpi/suspend.d/80-video-vesa-state.sh
+++ '[' xtrue = xtrue ']'
++++ vbetool vbemode get
+++ VBEMODE=3
+++ '[' 3 '!=' 3 ']'
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/85-alsa-state.sh ']'
++ . /etc/acpi/suspend.d/85-alsa-state.sh
+++ '[' -x /etc/init.d/alsa-utils ']'
+++ /etc/init.d/alsa-utils stop
 * Shutting down ALSA...                                                 [ OK ] 
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/90-framebuffer-stop.sh ']'
++ . /etc/acpi/suspend.d/90-framebuffer-stop.sh
+++ '[' xtrue = xtrue ']'
+++ vbetool dpms off
+++ for x in '/sys/class/graphics/*'
+++ '[' -f '/sys/class/graphics/*/state' ']'
+ '[' x = xtrue ']'
+ echo -n mem
+ '[' x = xtrue ']'
+ '[' x = xtrue ']'
+ . /etc/acpi/resume.sh
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/10-thinkpad-standby-led.sh ']'
++ . /etc/acpi/resume.d/10-thinkpad-standby-led.sh
+++ . /usr/share/acpi-support/state-funcs
+++ setLEDThinkpadSuspending 1
++++ test 1 -ne 0
++++ echo blink
+++ action=blink
+++ test -w /proc/acpi/ibm/led
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/13-855-resolution-set.sh ']'
++ . /etc/acpi/resume.d/13-855-resolution-set.sh
+++ '[' -x /usr/sbin/855resolution ']'
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/15-video-post.sh ']'
++ . /etc/acpi/resume.d/15-video-post.sh
+++ '[' xtrue = xtrue ']'
+++ vbetool post
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/17-video-restore.sh ']'
++ . /etc/acpi/resume.d/17-video-restore.sh
+++ '[' xtrue = xtrue ']'
+++ vbetool vbestate restore
/etc/acpi/resume.d/17-video-restore.sh: line 5: /var/lib/acpi-support/vbestate: No such file or directory
+++ '[' 3 '!=' 3 ']'
+++ vbetool vgamode set 3
Function not supported
+++ '[' x = xtrue ']'
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/35-modules-load.sh ']'
++ . /etc/acpi/resume.d/35-modules-load.sh
+++ '[' -f /sys/class/firmware/timeout ']'
++++ cat /sys/class/firmware/timeout
+++ timeout=60
+++ echo 100
+++ for x in '$MODULES'
+++ modprobe ndiswrapper
+++ for x in '$MODULES'
+++ modprobe skge
+++ '[' -f /sys/class/firmware/timeout ']'
+++ echo 60
+++ '[' -x /sbin/pccardctl ']'
+++ pccardctl insert
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/40-infra-red.sh ']'
++ . /etc/acpi/resume.d/40-infra-red.sh
+++ '[' -f /var/run/irdadev ']'
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/49-855-resolution-set.sh ']'
++ . /etc/acpi/resume.d/49-855-resolution-set.sh
+++ '[' -x /usr/sbin/855resolution ']'
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/50-framebuffer-enable.sh ']'
++ . /etc/acpi/resume.d/50-framebuffer-enable.sh
+++ for x in '/sys/class/graphics/*'
+++ '[' -f '/sys/class/graphics/*/state' ']'
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/50-time.sh ']'
++ . /etc/acpi/resume.d/50-time.sh
+++ hwclock --hctosys
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/50-tosh-restore-brightness.sh ']'
++ . /etc/acpi/resume.d/50-tosh-restore-brightness.sh
+++ '[' x '!=' x ']'
+++ unset TOSH_LCD
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/55-screen.sh ']'
++ . /etc/acpi/resume.d/55-screen.sh
+++ '[' xtrue = xtrue ']'
+++ vbetool dpms on
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/58-proc-sysfs-restore-state.sh ']'
++ . /etc/acpi/resume.d/58-proc-sysfs-restore-state.sh
+++ '[' -r /var/run/proc-sysfs-save-state ']'
+++ read WHERE foo WHAT
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/60-asus-wireless-led.sh ']'
++ . /etc/acpi/resume.d/60-asus-wireless-led.sh
+++ . /usr/share/acpi-support/state-funcs
+++ isAnyWirelessPoweredOn
+++ for DEVICE in '/sys/class/net/*'
+++ '[' -d /sys/class/net/eth0/wireless -a -r /sys/class/net/eth0/device/power/state ']'
+++ for DEVICE in '/sys/class/net/*'
+++ '[' -d /sys/class/net/lo/wireless -a -r /sys/class/net/lo/device/power/state ']'
+++ for DEVICE in '/sys/class/net/*'
+++ '[' -d /sys/class/net/wlan0/wireless -a -r /sys/class/net/wlan0/device/power/state ']'
++++ cat /sys/class/net/wlan0/device/power/state
+++ '[' 0 -eq 0 ']'
+++ '[' -r /sys/class/net/wlan0/device/rf_kill ']'
+++ return 0
+++ setLEDAsusWireless 1
++++ test 1 -ne 0
++++ echo 1
+++ action=1
+++ test -w /proc/acpi/asus/wled
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/62-ifup.sh ']'
++ . /etc/acpi/resume.d/62-ifup.sh
+++ for x in '$INTERFACES'
+++ ifup lo
+++ for x in '$INTERFACES'
+++ ifup wlan0
ifup: interface wlan0 already configured
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/65-console.sh ']'
++ . /etc/acpi/resume.d/65-console.sh
+++ chvt 7
+++ '[' x = xtrue ']'
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/67-sound.sh ']'
++ . /etc/acpi/resume.d/67-sound.sh
+++ '[' -x /etc/init.d/alsa-utils ']'
+++ /etc/init.d/alsa-utils start
 * Setting up ALSA...                                                    [ OK ] 
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/69-services.sh ']'
++ . /etc/acpi/resume.d/69-services.sh
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/72-acpi-pain.sh ']'
++ . /etc/acpi/resume.d/72-acpi-pain.sh
+++ modprobe -r button
+++ modprobe button
+++ modprobe -r fan
+++ modprobe -r thermal
+++ modprobe fan
+++ modprobe thermal
++++ grep thinkpad_acpi /proc/modules
+++ '[' '' ']'
+++ for x in '/proc/acpi/fan/*'
+++ '[' -f '/proc/acpi/fan/*/state' ']'
+++ modprobe -r acpi_sbs
FATAL: Module acpi_sbs not found.
+++ modprobe -r ac
+++ modprobe ac
+++ modprobe -r battery
+++ modprobe battery
+++ modprobe acpi_sbs
FATAL: Module acpi_sbs not found.
+++ /etc/acpi/power.sh
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/85-anacron.sh ']'
++ . /etc/acpi/resume.d/85-anacron.sh
+++ /usr/sbin/invoke-rc.d anacron start
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/90-thinkpad-unstandby-led.sh ']'
++ . /etc/acpi/resume.d/90-thinkpad-unstandby-led.sh
+++ . /usr/share/acpi-support/state-funcs
+++ setLEDThinkpadSuspending 0
++++ test 0 -ne 0
++++ echo off
+++ action=off
+++ test -w /proc/acpi/ibm/led
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/90-xscreensaver.sh ']'
++ . /etc/acpi/resume.d/90-xscreensaver.sh
+++ pidof xscreensaver
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/98-acpi-unlock.sh ']'
++ . /etc/acpi/resume.d/98-acpi-unlock.sh
+++ sleep 10
mg@wsubu:/etc/acpi$ +++ rm /var/lock/acpisleep

```

can I do something with this or do I have to leave with the fact that I only can do S1 instead of S3.

PS: My MB is an Asus P4P800-Deluxe

---

### Post by El_Matthews on 2007-12-30
Ok I now know how to troubleshoot both and I will log new issues for all specific problems.

---

