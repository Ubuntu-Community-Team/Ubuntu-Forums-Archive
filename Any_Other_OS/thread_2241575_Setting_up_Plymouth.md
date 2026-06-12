---
title: "Setting up Plymouth"
date: 2014-08-27
forum: Any Other OS
---

### Post by veddox on 2014-08-27
OK, I know this is a tough one, but I thought I'd just try my luck...

I've been trying to set up Plymouth on my Arch system to get a nice graphic boot splash, but it somehow isn't working out. I followed the instructions from the [Arch wiki]("https://wiki.archlinux.org/index.php/Plymouth"), and read up on all sorts of things to do with the boot process in Arch and Ubuntu (as Ubuntu also uses Plymouth), but no luck.

 My situation is as follows: I am triple-booting Windows 7, Ubuntu 14.04 and Arch Linux. GRUB is installed on the Ubuntu partition. When I boot into Arch, this is the log I get (copied out from /var/log, including shutdown process):

```
:: running hook [udev]
:: Triggering uevents...
:: running hook [plymouth]
:: performing fsck on '/dev/sda4'
ARCH: recovering journal
ARCH: clean, 144797/1602496 files, 1691512/6400000 blocks
********************** WARNING **********************
*                                                   *
*  The root device is not configured to be mounted  *
*  read-write! It may be fsck'd again later.        *
*                                                   *
*****************************************************
:: mounting '/dev/sda4' on real root
:: running late hook [plymouth]
:: running cleanup hook [udev]

Welcome to [0;36mArch Linux[0m!

[[32m  OK  [0m] Reached target Login Prompts.
[[32m  OK  [0m] Reached target Remote File Systems.
         Expecting device sys-subsystem-net-devices-wlp2s0.device...
[[32m  OK  [0m] Reached target Encrypted Volumes.
[[32m  OK  [0m] Set up automount Arbitrary Executable File Formats File System Automount Point.
         Expecting device dev-sda2.device...
[[32m  OK  [0m] Created slice Root Slice.
[[32m  OK  [0m] Listening on /dev/initctl Compatibility Named Pipe.
[[32m  OK  [0m] Listening on Delayed Shutdown Socket.
[[32m  OK  [0m] Listening on Device-mapper event daemon FIFOs.
[[32m  OK  [0m] Listening on Journal Socket (/dev/log).
[[32m  OK  [0m] Listening on LVM2 metadata daemon socket.
[[32m  OK  [0m] Listening on udev Kernel Socket.
[[32m  OK  [0m] Listening on udev Control Socket.
[[32m  OK  [0m] Created slice User and Session Slice.
[[32m  OK  [0m] Listening on Journal Socket.
[[32m  OK  [0m] Created slice System Slice.
         Starting File System Check on Root Device...
         Mounting Debug File System...
         Starting Set Up Additional Binary Formats...
         Starting Setup Virtual Console...
         Starting Create list of required static device nodes for the current kernel...
         Mounting POSIX Message Queue File System...
         Starting udev Coldplug all Devices...
         Starting Apply Kernel Variables...
         Mounting Configuration File System...
         Mounting Huge Pages File System...
[[32m  OK  [0m] Created slice system-netctl.slice.
[[32m  OK  [0m] Created slice system-getty.slice.
         Starting Journal Service...
[[32m  OK  [0m] Started Journal Service.
[[32m  OK  [0m] Reached target Slices.
         Mounting Temporary Directory...
         Mounting Arbitrary Executable File Formats File System...
[[32m  OK  [0m] Started Create list of required static device nodes for the current kernel.
[[32m  OK  [0m] Started Apply Kernel Variables.
[[32m  OK  [0m] Started udev Coldplug all Devices.
[[32m  OK  [0m] Mounted Arbitrary Executable File Formats File System.
[[32m  OK  [0m] Mounted Huge Pages File System.
[[32m  OK  [0m] Mounted Configuration File System.
[[32m  OK  [0m] Mounted POSIX Message Queue File System.
[[32m  OK  [0m] Mounted Debug File System.
[[32m  OK  [0m] Mounted Temporary Directory.
%G[[32m  OK  [0m] Started Set Up Additional Binary Formats.
[    9.281418] systemd-fsck[119]: ARCH: clean, 144797/1602496 files, 1691512/6400000 blocks
[[32m  OK  [0m] Started File System Check on Root Device.
         Starting Remount Root and Kernel File Systems...
[[32m  OK  [0m] Started Remount Root and Kernel File Systems.
         Activating swap /swapfile...
         Starting Create Static Device Nodes in /dev...
         Starting Load/Save Random Seed...
[[32m  OK  [0m] Activated swap /swapfile.
[[32m  OK  [0m] Reached target Swap.
[[32m  OK  [0m] Started Setup Virtual Console.
[[32m  OK  [0m] Started Create Static Device Nodes in /dev.
         Starting udev Kernel Device Manager...
[[32m  OK  [0m] Reached target Local File Systems (Pre).
[[32m  OK  [0m] Started udev Kernel Device Manager.
         Starting Show Plymouth Boot Screen...
[[32m  OK  [0m] Started Load/Save Random Seed.
[[32m  OK  [0m] Started Show Plymouth Boot Screen.
[[32m  OK  [0m] Reached target Paths.
[[32m  OK  [0m] Created slice system-systemd\x2dbacklight.slice.
         Starting Load/Save Screen Backlight Brightness of backlight:intel_backlight...
[[32m  OK  [0m] Created slice system-systemd\x2drfkill.slice.
         Starting Load/Save RF Kill Switch Status of rfkill0...
[[32m  OK  [0m] Started Load/Save Screen Backlight Brightness of backlight:intel_backlight.
[[32m  OK  [0m] Started Load/Save RF Kill Switch Status of rfkill0.
         Starting Load/Save RF Kill Switch Status of rfkill1...
[[32m  OK  [0m] Started Load/Save RF Kill Switch Status of rfkill1.
[[32m  OK  [0m] Found device BCM4313 802.11bgn Wireless Network Adapter.
[[32m  OK  [0m] Reached target Sound Card.
[[32m  OK  [0m] Found device ST500LT012-9WS142 DATA.
         Mounting /home/daniel/Data...
[[32m  OK  [0m] Mounted /home/daniel/Data.
[[32m  OK  [0m] Reached target Local File Systems.
         Starting Trigger Flushing of Journal to Persistent Storage...
         Starting Tell Plymouth To Write Out Runtime Data...
         Starting Create Volatile Files and Directories...
[[32m  OK  [0m] Started Trigger Flushing of Journal to Persistent Storage.
[[32m  OK  [0m] Started Create Volatile Files and Directories.
         Starting Update UTMP about System Boot/Shutdown...
[[32m  OK  [0m] Started Tell Plymouth To Write Out Runtime Data.
[[32m  OK  [0m] Started Update UTMP about System Boot/Shutdown.
[[32m  OK  [0m] Reached target System Initialization.
[[32m  OK  [0m] Listening on D-Bus System Message Bus Socket.
[[32m  OK  [0m] Reached target Sockets.
[[32m  OK  [0m] Reached target Timers.
[[32m  OK  [0m] Reached target Basic System.
         Starting The Vedder home wireless network...
         Starting D-Bus System Message Bus...
[[32m  OK  [0m] Started D-Bus System Message Bus.
         Starting Login Service...
         Starting Permit User Sessions...
[[32m  OK  [0m] Started Permit User Sessions.
         Starting Wait for Plymouth Boot Screen to Quit...
         Starting GNOME Display Manager...
[[32m  OK  [0m] Started Login Service.
[[32m  OK  [0m] Started GNOME Display Manager.
         Starting Accounts Service...
         Starting Authorization Manager...
[[32m  OK  [0m] Started Authorization Manager.
[[32m  OK  [0m] Started Accounts Service.
[[32m  OK  [0m] Created slice user-120.slice.
         Starting User Manager for UID 120...
[[32m  OK  [0m] Started User Manager for UID 120.
         Starting Daemon for power management...
[[32m  OK  [0m] Started Daemon for power management.
         Mounting FUSE Control File System...
[[32m  OK  [0m] Mounted FUSE Control File System.
         Starting Manage, Install and Generate Color Profiles...
[[32m  OK  [0m] Started Manage, Install and Generate Color Profiles.
         Starting RealtimeKit Scheduling Policy Service...
[[32m  OK  [0m] Started RealtimeKit Scheduling Policy Service.
         Starting Locale Service...
[[32m  OK  [0m] Started Locale Service.
         Starting Location Lookup Service...
[[32m  OK  [0m] Started Location Lookup Service.
         Starting Disk Manager...
[[32m  OK  [0m] Started Disk Manager.
[[1;31mFAILED[0m] Failed to start The Vedder home wireless network.
See 'systemctl status netctl@vedder_wifi.service' for details.
[[32m  OK  [0m] Reached target Network.
[[32m  OK  [0m] Created slice user-1000.slice.
         Starting User Manager for UID 1000...
[[32m  OK  [0m] Started User Manager for UID 1000.
         Starting Location Lookup Service...
[[32m  OK  [0m] Started Location Lookup Service.
[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (33s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (34s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (34s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (35s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (35s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (36s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (36s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (37s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (37s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (38s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (38s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (39s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (39s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (40s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (40s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (41s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (41s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (42s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (42s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (43s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (43s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (44s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (44s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (45s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (45s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (46s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (46s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (47s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (47s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (48s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (48s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (49s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (49s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (50s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (50s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (51s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (51s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (52s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (52s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (53s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (53s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (54s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (54s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (55s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (55s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (56s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (56s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (57s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (57s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (58s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (58s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (59s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (59s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 1s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 1s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 2s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 2s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 3s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 3s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 4s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 4s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 5s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 5s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 6s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 6s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 7s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 7s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 8s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 8s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 9s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 9s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 10s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 10s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 11s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 11s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 12s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 12s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 13s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 13s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 14s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 14s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 15s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 15s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 16s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 16s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 17s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 17s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 18s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 18s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 19s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 19s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 20s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 20s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 21s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 21s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 22s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 22s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 23s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 23s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 24s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 24s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 25s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 25s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 26s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 26s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 27s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 27s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 28s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 28s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 29s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 29s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 30s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 30s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 31s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 31s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 32s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 32s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 33s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 33s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 34s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 34s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 35s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 35s / no limit)
[K         Starting Hostname Service...
[[1;31m*[0m[31m*    [0m] (2 of 2) A start job is running for Hostname Service (156ms / 1min 30s)
[K[[32m  OK  [0m] Started Hostname Service.
[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 41s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 41s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 42s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 42s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 43s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 43s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 44s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 44s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 45s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 45s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 46s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 46s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 47s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 47s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 48s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 48s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 49s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 49s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 50s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 50s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 51s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 51s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 52s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 52s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 53s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 53s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 54s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 54s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 55s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 55s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 56s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 56s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 57s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 57s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 58s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 58s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 59s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (1min 59s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 1s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 1s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 2s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 2s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 3s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 3s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 4s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 4s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 5s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 5s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 6s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 6s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 6s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 7s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 7s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 8s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 8s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 9s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 9s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 10s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 10s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 11s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 11s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 12s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 12s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 13s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 13s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 14s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 14s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 15s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 15s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 16s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 16s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 17s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 17s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 18s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 18s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 19s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 19s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 20s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 20s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 21s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 21s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 22s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 22s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 23s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 23s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 24s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 24s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 25s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 25s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 26s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 26s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 27s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 27s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 28s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 28s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 29s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 29s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 30s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 30s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 31s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 31s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 32s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 32s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 33s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 33s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 34s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 34s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 35s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 35s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 36s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 36s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 37s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 37s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 38s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 38s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 39s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 39s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 40s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 40s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 41s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 41s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 42s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 42s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 43s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 43s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 44s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 44s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 45s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 45s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 46s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 46s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 47s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 47s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 48s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 48s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 49s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 49s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 50s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 50s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 51s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 51s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 52s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 52s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 53s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 53s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 54s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 54s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 55s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 55s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 56s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 56s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 57s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 57s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 58s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 58s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 59s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (2min 59s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 1s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 1s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 2s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 2s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 3s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 3s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 4s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 4s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 5s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 5s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 6s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 6s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 7s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 7s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 8s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 8s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 9s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 9s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 10s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 10s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 11s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 11s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 12s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 12s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 13s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 13s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 14s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 14s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 15s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 15s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 16s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 16s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 17s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 17s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 18s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 18s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 19s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 19s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 20s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 20s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 21s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 21s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 22s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 22s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 23s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 23s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 24s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 24s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 25s / no limit)
[K[[0m[31m*     [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 25s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 26s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 26s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 27s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 27s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 28s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 28s / no limit)
[K[     [31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 29s / no limit)
[K[    [31m*[1;31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 29s / no limit)
[K[   [31m*[1;31m*[0m[31m*[0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 30s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 30s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 31s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 31s / no limit)
[K[[1;31m*[0m[31m*    [0m] A start job is running for Wait for Plymouth Boot Screen to Quit (3min 32s / no limit)
[K[[32m  OK  [0m] Stopped target Sound Card.
[[32m  OK  [0m] Stopped target Network.
[[32m  OK  [0m] Removed slice system-netctl.slice.
[[32m  OK  [0m] Removed slice system-getty.slice.
         Stopping User Manager for UID 1000...
         Stopping Disk Manager...
         Stopping RealtimeKit Scheduling Policy Service...
         Stopping Manage, Install and Generate Color Profiles...
         Stopping Daemon for power management...
         Stopping User Manager for UID 120...
         Stopping Authorization Manager...
         Stopping Accounts Service...
[[32m  OK  [0m] Stopped target Graphical Interface.
[[32m  OK  [0m] Stopped target Multi-User System.
         Stopping D-Bus System Message Bus...
         Stopping Login Service...
[[32m  OK  [0m] Stopped target Login Prompts.
         Stopping Wait for Plymouth Boot Screen to Quit...
         Stopping GNOME Display Manager...
         Starting Generate shutdown-ramfs...
[[32m  OK  [0m] Stopped D-Bus System Message Bus.
[[32m  OK  [0m] Stopped Wait for Plymouth Boot Screen to Quit.
[[32m  OK  [0m] Stopped Accounts Service.
[[32m  OK  [0m] Stopped Authorization Manager.
[[32m  OK  [0m] Stopped Daemon for power management.
[[32m  OK  [0m] Stopped Manage, Install and Generate Color Profiles.
[[32m  OK  [0m] Stopped RealtimeKit Scheduling Policy Service.
[[32m  OK  [0m] Stopped Disk Manager.
[[32m  OK  [0m] Stopped Login Service.
[[32m  OK  [0m] Stopped User Manager for UID 1000.
[[32m  OK  [0m] Stopped User Manager for UID 120.
[[32m  OK  [0m] Removed slice user-120.slice.
[[32m  OK  [0m] Removed slice user-1000.slice.
[[32m  OK  [0m] Started Generate shutdown-ramfs.
[[32m  OK  [0m] Stopped GNOME Display Manager.
         Starting Show Plymouth Reboot Screen...
         Stopping Permit User Sessions...
[[32m  OK  [0m] Stopped Permit User Sessions.
[[32m  OK  [0m] Stopped target Basic System.
[[32m  OK  [0m] Stopped target Slices.
[[32m  OK  [0m] Removed slice User and Session Slice.
[[32m  OK  [0m] Stopped target Paths.
[[32m  OK  [0m] Stopped target Timers.
[[32m  OK  [0m] Stopped target Sockets.
[[32m  OK  [0m] Closed D-Bus System Message Bus Socket.
[[32m  OK  [0m] Stopped target System Initialization.
         Stopping Load/Save RF Kill Switch Status of rfkill1...
         Stopping Load/Save RF Kill Switch Status of rfkill0...
         Stopping Load/Save Screen Backlight Brightness of backlight:intel_backlight...
         Stopping Apply Kernel Variables...
[[32m  OK  [0m] Stopped Apply Kernel Variables.
         Stopping Set Up Additional Binary Formats...
[[32m  OK  [0m] Stopped Set Up Additional Binary Formats.
         Stopping Setup Virtual Console...
[[32m  OK  [0m] Stopped Setup Virtual Console.
[[32m  OK  [0m] Stopped target Encrypted Volumes.
         Stopping Load/Save Random Seed...
         Stopping Update UTMP about System Boot/Shutdown...
[[32m  OK  [0m] Stopped target Swap.
         Deactivating swap /swapfile...
[[32m  OK  [0m] Stopped target Remote File Systems.
[[32m  OK  [0m] Started Show Plymouth Reboot Screen.
[[32m  OK  [0m] Stopped Load/Save RF Kill Switch Status of rfkill1.
[[32m  OK  [0m] Stopped Load/Save RF Kill Switch Status of rfkill0.
[[32m  OK  [0m] Stopped Load/Save Screen Backlight Brightness of backlight:intel_backlight.
[[32m  OK  [0m] Stopped Load/Save Random Seed.
[[32m  OK  [0m] Stopped Update UTMP about System Boot/Shutdown.
[[32m  OK  [0m] Deactivated swap /swapfile.
         Stopping Create Volatile Files and Directories...
[[32m  OK  [0m] Stopped Create Volatile Files and Directories.
[[32m  OK  [0m] Stopped target Local File Systems.
         Unmounting /run/user/1000/gvfs...
         Unmounting /run/user/120...
         Unmounting /home/daniel/Data...
         Unmounting Temporary Directory...
[[32m  OK  [0m] Removed slice system-systemd\x2dbacklight.slice.
[[32m  OK  [0m] Removed slice system-systemd\x2drfkill.slice.
[[32m  OK  [0m] Unmounted /run/user/1000/gvfs.
[[32m  OK  [0m] Unmounted /run/user/120.
[[32m  OK  [0m] Unmounted Temporary Directory.
         Unmounting /run/user/1000...
[[32m  OK  [0m] Unmounted /home/daniel/Data.
[[32m  OK  [0m] Unmounted /run/user/1000.
[[32m  OK  [0m] Reached target Unmount All Filesystems.
[[32m  OK  [0m] Stopped target Local File Systems (Pre).
         Stopping Remount Root and Kernel File Systems...
[[32m  OK  [0m] Stopped Remount Root and Kernel File Systems.
         Stopping Create Static Device Nodes in /dev...
[[32m  OK  [0m] Stopped Create Static Device Nodes in /dev.
[[32m  OK  [0m] Reached target Shutdown.
[[32m  OK  [0m] Reached target Final Step.
         Starting Reboot...
Sending SIGTERM to remaining processes...
Sending SIGKILL to remaining processes...
Hardware watchdog 'iTCO_wdt', version 0
Unmounting file systems.
Unmounting /oldroot/sys/fs/cgroup/blkio.
Unmounting /oldroot/sys/fs/cgroup/net_cls.
Unmounting /oldroot/sys/fs/cgroup/freezer.
Unmounting /oldroot/sys/fs/cgroup/devices.
Unmounting /oldroot/sys/fs/cgroup/memory.
Unmounting /oldroot/sys/fs/cgroup/cpu,cpuacct.
Unmounting /oldroot/sys/fs/cgroup/cpuset.
Unmounting /oldroot/sys/fs/pstore.
Unmounting /oldroot/sys/fs/cgroup/systemd.
Unmounting /oldroot/sys/fs/cgroup.
Unmounting /oldroot/dev/shm.
Unmounting /oldroot/sys/kernel/security.
Unmounting /oldroot.
Unmounting /oldroot/dev/pts.
Unmounting /oldroot/run.
Unmounting /oldroot/dev.
Unmounting /oldroot/sys.
Unmounting /oldroot/proc.
Unmounting /oldroot.
Unmounting /oldroot/dev/pts.
```

Based on this log, it would seem to me that plymouth is actually running, it just doesn't display any graphics. Instead, I get the same commandline output that I got before as well.

(NB: The recurring output "A start job is running for Wait for Plymouth Boot Screen to Quit (2min 41s / no limit)" is a known bug, but AFAIK should not affect the actual working of Plymouth. All it means is that Plymouth doesn't actually get stopped unless you do it manually.)

Does anybody have any bright ideas what I could try next?

---

