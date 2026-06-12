---
title: "Networking not always restarted after Hibernate"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by El_Matthews on 2007-12-30
Dear,

I have some problems with the Hibernate function. At resume it seems that the networking service is not always restarted. I am using the Wifi network with the NDIS wrapper.

I have added the following line in /etc/default/acpi-support
```
# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="networking"
```
I also unload following modules:
```
MODULES="ndiswrapper msp3400 bt878 bttv"
```

I also set the debugging options to the hibernate.sh script which provide me following output:
```
mg@wsubu:/etc/acpi$ sudo ./hibernate.sh
[sudo] password for mg:
+ . /etc/default/acpi-support
++ ACPI_HIBERNATE=true
++ ACPI_SLEEP_MODE=standby
++ MODULES='ndiswrapper msp3400 bt878 bttv'
++ MODULES_WHITELIST=
++ SAVE_VBE_STATE=false
++ VBESTATE=/var/lib/acpi-support/vbestate
++ POST_VIDEO=true
++ USE_DPMS=true
++ HIBERNATE_MODE=shutdown
++ LOCK_SCREEN=true
++ STOP_SERVICES=networking
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
+ . /usr/share/acpi-support/policy-funcs
+ '[' xtrue '!=' xtrue ']'
+ unset POST_VIDEO
+ unset USE_DPMS
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
+++ INTERFACES='eth0
lo
wlan0'
+++ for x in '$INTERFACES'
+++ ifdown eth0
ifdown: interface eth0 not configured
+++ ifconfig eth0 down
+++ for x in '$INTERFACES'
+++ ifdown lo
+++ ifconfig lo down
+++ for x in '$INTERFACES'
+++ ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5148
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
+++ MODULES='ndiswrapper msp3400 bt878 bttv ndiswrapper'
+++ for x in '/sys/class/net/*'
+++ '[' -e /sys/class/net/eth0/device/driver ']'
++++ tr '[:upper:]' '[:lower:]'
+++++ readlink /sys/class/net/eth0/device/driver
++++ basename ../../../../bus/pci/drivers/skge
+++ MODULES='ndiswrapper msp3400 bt878 bttv ndiswrapper skge'
+++ for x in '/sys/class/net/*'
+++ '[' -e /sys/class/net/lo/device/driver ']'
+++ '[' -d /sys/module/netconsole ']'
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/65-services-stop.sh ']'
++ . /etc/acpi/suspend.d/65-services-stop.sh
+++ for x in '$STOP_SERVICES'
+++ invoke-rc.d --quiet networking stop
 * Deconfiguring network interfaces...                                                                                                                                                                                               [ OK ] 
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/70-modules-unload.sh ']'
++ . /etc/acpi/suspend.d/70-modules-unload.sh
+++ for x in '$MODULES'
+++ modprobe -r ndiswrapper
+++ for x in '$MODULES'
+++ modprobe -r msp3400
+++ for x in '$MODULES'
+++ modprobe -r bt878
+++ for x in '$MODULES'
+++ modprobe -r bttv
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
+++ '[' xfalse = xtrue ']'
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/85-alsa-state.sh ']'
++ . /etc/acpi/suspend.d/85-alsa-state.sh
+++ '[' -x /etc/init.d/alsa-utils ']'
+++ /etc/init.d/alsa-utils stop
 * Shutting down ALSA...                                                                                                                                                                                                             [ OK ] 
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/90-framebuffer-stop.sh ']'
++ . /etc/acpi/suspend.d/90-framebuffer-stop.sh
+++ '[' x = xtrue ']'
+++ for x in '/sys/class/graphics/*'
+++ '[' -f '/sys/class/graphics/*/state' ']'
+ echo -n shutdown
+ '[' -x /sbin/s2disk ']'
+ echo -n disk
+ /usr/sbin/laptop_mode stop
Laptop mode disabled, not active.
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
+++ '[' x = xtrue ']'
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/17-video-restore.sh ']'
++ . /etc/acpi/resume.d/17-video-restore.sh
+++ '[' xfalse = xtrue ']'
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
+++ modprobe msp3400
+++ for x in '$MODULES'
+++ modprobe bt878
+++ for x in '$MODULES'
+++ modprobe bttv
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
+++ '[' x = xtrue ']'
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
+++ ifup eth0
+++ for x in '$INTERFACES'
+++ ifup lo
+++ for x in '$INTERFACES'
+++ ifup wlan0
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/65-console.sh ']'
++ . /etc/acpi/resume.d/65-console.sh
+++ chvt 7
ifup: interface wlan0 already configured
+++ '[' x = xtrue ']'
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/67-sound.sh ']'
++ . /etc/acpi/resume.d/67-sound.sh
+++ '[' -x /etc/init.d/alsa-utils ']'
+++ /etc/init.d/alsa-utils start
 * Setting up ALSA...                                                                                                                                                                                                                [ OK ] 
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/69-services.sh ']'
++ . /etc/acpi/resume.d/69-services.sh
+++ for x in '$STOP_SERVICES'
+++ invoke-rc.d --quiet networking start
 * Configuring network interfaces...                                                                                                                                                                                                 [ OK ] 
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

Even if this logs says that networking was started I had to do a manual```
sudo /etc/init.d/networking restart
``` to make everything work.

This is not always the case, sometimes it works.

Anybody an idea ?

---

### Post by El_Matthews on 2008-01-02
maybe this can help, I noticed that I have to restart the network manually only after the first hibernate. In the other cases it seems to work.

---

### Post by El_Matthews on 2008-01-08
nobody?

A small tip to proceed?

Please help, I am desperate ;)

---

### Post by orad on 2008-07-20
I have the same problem. i don't understand what those logs he printed on top are, but my internet also quits when I suspend or hibernate. I tried doing the command that restarts networking and that didn't work for me either :(

---

