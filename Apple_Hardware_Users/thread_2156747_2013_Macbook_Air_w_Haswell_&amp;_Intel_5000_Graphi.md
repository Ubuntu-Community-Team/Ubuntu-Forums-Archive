---
title: "2013 Macbook Air w/ Haswell &amp; Intel 5000 Graphics"
date: 2013-06-22
forum: Apple Hardware Users
---

### Post by SmithErick on 2013-06-22
Has anyone got any distro installed on the new 2013 Macbook Air? I have been attempting everything I know all day! 

I keep getting hung on black screen with cursor, no cursor, or purple screen

Live CD Boots fine!

---

### Post by rkabir on 2013-06-23
I'm having similar troubles.

Have you gotten wireless to work with the Live CD?

---

### Post by CQIT on 2013-06-24
Very interested in this--will be acquiring one of these in the near future and hopefully we can get it running some Linux goodness!

---

### Post by quantumboy on 2013-06-24
I got a Macbook Air with the new hardware on Friday (6/21/13) & I'm having a similar issue while booting from a USB Live disk. Though, instead of a blank screen, I see error logs that appear to be CPU related. From looking around a bit online, it appears that there's still work to be done on Linux Haswell support (e.g [http://www.pcper.com/news/General-Tech/How-well-does-Haswell-do-Ubuntu](http://www.pcper.com/news/General-Tech/How-well-does-Haswell-do-Ubuntu)). So you may be stuck with OS X until then.

One thing I did notice is that when I connect or disconnect an external display via a Thunderbolt adapter, the error messages went away & I got the GUI back. Unfortunately this didn't get me all the way thru the install process.

I've gotten Ubuntu 13.04 to work fine in VirtualBox however.

---

### Post by rkabir on 2013-06-27
Looks like someone had some luck installing a nightly build of 13.10:

[http://www.phoronix.com/scan.php?page=article&item=apple_mba2013_ubuntu&num=1](http://www.phoronix.com/scan.php?page=article&item=apple_mba2013_ubuntu&num=1)

i'll give it a go tomorrow and report back.

---

### Post by rkabir on 2013-06-27
I downloaded the latest mac ISO from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) last night and just tried it.

Installed fine - even seemed to find the network interface from the livecd in the installer, but then I couldn't get the installed ubuntu to load. It seemed to hang after the login screen. Further than I got before, though. I'll tinker around with it more in the coming days.

(For reference, I have the 13" i7)

---

### Post by kosumi68 on 2013-06-27
It would be great to get some details on these machines:
```

sudo lspci -vvv > lspci-MBA.txt
sudo lsusb -v > lsusb-MBA.txt

```

Thanks!

---

### Post by rkabir on 2013-06-27
> **kosumi68 said:**
> It would be great to get some details on these machines:
```

sudo lspci -vvv > lspci-MBA.txt
sudo lsusb -v > lsusb-MBA.txt

```

Thanks!

Done!

Couldn't attach the files (uploader complained they exceeded forum's filesize for txt), so dropbox links:

[https://dl.dropboxusercontent.com/u/81130/lspci-MBA.txt](https://dl.dropboxusercontent.com/u/81130/lspci-MBA.txt)
[https://dl.dropboxusercontent.com/u/81130/lsusb-MBA.txt](https://dl.dropboxusercontent.com/u/81130/lsusb-MBA.txt)

---

### Post by kosumi68 on 2013-06-28
So the wireless device is the new BCM4360, and the trackpad is also new (hence no multitouch for now). Looks like the arch people made some progress with the wlan: [https://bbs.archlinux.org/viewtopic.php?pid=1292233](https://bbs.archlinux.org/viewtopic.php?pid=1292233). As always, it will be a while before everything works smoothly. Thanks for the info!

---

### Post by plymouth on 2013-06-28
If you are interested in information about the new touchpad, you can follow the kernel bug 60181 ([https://bugzilla.kernel.org/show_bug.cgi?id=60181](https://bugzilla.kernel.org/show_bug.cgi?id=60181)).  I would suggest commenting on the bug to let the kernel input-driver team know it is of importance and helping with any logs that they may need to update the driver.

ArchLinux also has a thread following some of the touchpad details: [https://bbs.archlinux.org/viewtopic.php?id=165854](https://bbs.archlinux.org/viewtopic.php?id=165854).

---

### Post by plymouth on 2013-06-28
> **plymouth said:**
> If you are interested in information about the new touchpad, you can follow the kernel bug 60181 ([https://bugzilla.kernel.org/show_bug.cgi?id=60181](https://bugzilla.kernel.org/show_bug.cgi?id=60181)).  I would suggest commenting on the bug to let the kernel input-driver team know it is of importance and helping with any logs that they may need to update the driver.

ArchLinux also has a thread following some of the touchpad details: [https://bbs.archlinux.org/viewtopic.php?id=165854](https://bbs.archlinux.org/viewtopic.php?id=165854).

There is now a Ubuntu launchpad bug regarding the touchpad issue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1195822](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1195822).

---

### Post by e-gandalf on 2013-07-10
anyone managed to get Ubuntu 13.10 on MBA 2013?

I installed it from usb stick (had to turn ACPI off at boot), and it boots most of the time (sometimes hangs at boot, but rarely), but I can't seem to get wifi to work. I installed bcmwl 6.30.223.30 driver and it makes my network kinda work, but cannot see any networks. Any ideas how to solve it?

---

### Post by fakbill on 2013-07-13
[**[COLOR=#000000]@e-gandalf[/COLOR]**]("http://ubuntuforums.org/member.php?u=52824") : 13.10 boots most of the time?? without switching off the ACPI??
Looking at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451) it seems that the kernel lacks some kind of ACPI support;

---

### Post by e-gandalf on 2013-07-15
> **fakbill said:**
> [**[COLOR=#000000]@e-gandalf[/COLOR]**]("http://ubuntuforums.org/member.php?u=52824") : 13.10 boots most of the time?? without switching off the ACPI??
Looking at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451) it seems that the kernel lacks some kind of ACPI support;

Yeah, I only had o switch off ACPI to boot from livecd. After installation it boots properly most of the time (freezes at ~15% of boots)

---

### Post by andrew-fullam on 2013-08-01
Hi Guys,

Are there any more updates on how Ubuntu is running on the new Macbook Air?
What's currently working well and what isn't?
I'm keen to give it a go but I want to make sure it's running fairly well first.

Thanks guys

---

### Post by e-gandalf on 2013-08-06
Can't say about Ubuntu 13.04, but I keep trying to switch to Ubuntu 13.10 on my new MBA. I still can boot from livecd after turning acpi off, but can't get wifi to work.

I install bcmwl-kernel-source and after that it seems that Ubuntu recognizes that I have a wifi card, but it doesn't see any network nor does it let me connect manually to any. Anyone managed to get wifi on 2013 MBA with Ubuntu 13.10?

---

### Post by t7v3-sean-lzh7 on 2013-08-09
Fedora has actually made better progress.  Still blocked by suspend/resume with backlight issues and audio issues

[http://mattoncloud.org/2013/07/18/fedora-19-on-a-macbook-air-2013-model/](http://mattoncloud.org/2013/07/18/fedora-19-on-a-macbook-air-2013-model/)

Sean

---

### Post by andrew-fullam on 2013-09-20
Hi guys,

Are there any updates on this? Do you think 13.10 will be better supported on the latest macbook air? I'm dying to switch from my virtualbox ubuntu to native :)

Thanks

---

### Post by spezimas on 2013-10-17
Hi all, 
I managed to install the 13.10 Beta2 on the macbook air 6,2. It was a bit fiddling and it took me some time to get things in order to really boot into ubuntu.
Here my notes on how to succeed.

# Installation of Ubuntu 13.10 on Macbook Air 6,2 (Mid2013)

## Prerequisites
1. MacBookAir6,2 (check with `sudo dmidecode -s system-product-name`)
2. Apple USB-Ethernet Adapter
3. `ubuntu-13.10-beta2-desktop-amd64.iso` from []([http://releases.ubuntu.com/13.10/](http://releases.ubuntu.com/13.10/))
4. USB-Stick (1GB at least)

## Partition Harddisk
1. Boot Macbook Air into OSX
2. Open Disk Utility
```
open /Applications/Utility/Disk\ Utility.app

```
3. Select "Macintosh HD" > (Tab)Partition
Add (+) 3 more partitions
4. 2nd Partition: Set 30-40GB for Ubuntu
4th Partition: Set 4GB for Linux Swap partition
3rd Partition: Use as much space as left

## Prepare USB-Stick
1. In OSX
2. Download iso image to ~/Downloads
3. Open Terminal (a detailed description can be found [here]([http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx))
```

cd ~/Downloads
# convert iso
hdiutil convert -format UDRW -o ubuntu-13.10-beta2-desktop-amd64.img ubuntu-13.10-beta2-desktop-amd64.iso
open /Applications/Utilities/Disk\ Utility.app
# format the USB stick with MS-DOS VFAT
diskutil list
# check which /dev/diskX contains the USB stick - here it is "disk1"
# then unmount the usb-stick
diskutil unmountDisk /dev/disk1
# write img to usb stick - /!\ BE CAREFUL THAT disk1 REALLY IS YOUR USB-STICK
sudo dd if=ubuntu-13.10-beta2-desktop-amd64.img of=/dev/rdisk1 bs=1m

```

## Install Ubuntu 13.10
1. Restart and press "Alt"-Key on startup.
2. Make sure that the USB-Ethernet Adapter is NOT inserted. (With a network connection the bcmwl-kernel-source module gets downloaded during the installation process which prevents grub to get installed; DKMS module insertion stops installation process).
Select first USB-device labled "EFI-Boot" and press "Enter"
No splash screen shall be displayed but the Ubuntu installation menu. 
Check  [Identifying if the computer boots the Ubuntu DVD in EFI mode]([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI))
Select "Install Ubuntu" and press "e"-Key to edit
change the cursor to the line
```

linux /boot/vmlinuz-3.11.0-8-generic.efi.signed root=UUID=xxx ro quite splash

``` 
and change to 
```

linux /boot/vmlinuz-3.11.0-8-generic.efi.signed root=UUID=xxx ro acpi=off

```
Press "F10" to start installation.
3. Choose "Something else" for partitioning.
Please check the sizes in the list according to the partitioning for the step above. 
OSX Disk Utility leaves unallocated partitions inbetween which usually are arround 128MB in size.
Do not try to delete these "blank" partitions.
2nd partition should be ext4 formatted and mounted "/".
3rd partition should be ext3 formatted and mounted "/home". (I use ext3 in order to use fuse-ext2 from OSX; ext4 is yet not supported) 
4th partition should be swap (no format and mountpoint required)
Proceed...
4. The installation process should run through smoothly. 
5. Restart with pressed "Alt"-Key.
Unfortunately selecting the "Windows" labled Partition (HW-icon) only displayed a black screen with a blinking cursor.
Reboot into OSX again and install `refind`.
Download [Binary Zip-File]([http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html))
Open a Terminal
```

cd Downloads
unzip  refind-bin-0.7.4.zip 
cd refind-bin-0.7.4
bash install.sh 

```
6. Restart again with USB-Ethernet Adapter plugged-in. Now a Ubuntu labled /efi/grubx64.efi should be shown.
Select this an start it, now the grub-menu should be displayed.
Select "Advanced options for Ubuntu"
Select "Ubuntu, with Linux 3.11.0-8-generic"
Press again "e" for edit and add `acpi=off`. (See above). Otherwise booting is not possible.
Now Ubuntu should boot.

## Update Ubuntu to kernel 3.11.0-12

1. Log into ubuntu 13.10 and open a terminal (Ctrl+Alt+t)
2. Enter the following commands
```

sudo su
apt-get update
apt-get upgrade

```
Unfortunately this did not install the latest kernel 3.11.0-12.
Enter again `apt-get upgrade` and install all hold back packages with `apt-get install <name all packages>`
3. Start "Software & Updates" (/usr/bin/python3 /usr/bin/software-properties-gtk)
Select (Tab)Additional Drivers and install Broadcom 802.11 Linux STA wireless driver from bcmwl-kernel-source
4. Now reboot again

## What works and what does not

| Feature | Support status |
|----------|----------------|
| LCD Panel              | Partly | After Suspend only off or on possible
| Suspend, Hibernate     | Partly |
| Shut-down and Reboot   | OK  |
| Keyboard functions (Brightness,volume,...) | OK |
| Keyboard backlight     | OK  |
| Touchpad               | OK  |
| Wireless               | OK  |
| Bluetooth              | OK  |
| iSight                 | NO  | camera is not an usb device
| Sound                  | OK  |
| Microphone             | OK | 
| External Monitor       | ? | need an adapter to check
| Thunderbolt            | ? | no hw yet which uses this interface
| SD card slot           | OK |
| Fan Control            | ? | should be ok - no idea yet on how to verify
| HFS+ (OS X disc partition) | OK | mount ro
| Sensors (temps & fans) | ? | should be ok - no idea yet on how to verify
| GPU Power Save         | ? |

[B]Issues left:
* Backlight on/off after resume
* iSight HD webcam does not work[/B]

NOTE:
* Alt+F2+Fn (Run Application) not working 
Enabling via (Menu)System Settings > (Item)Keyboard > (Tab)Shortcuts > (Item)Launchers > Key to Show the HUD == Disabled
```

sudo apt-get install compizconfig-settings-manager
# after install start in terminal with
ccsm
# (Chaper)General > (Item)Gnome Compatibility > (Item)Run Dialog > Grab Key-Combination "<Alt>F2"

``` 

## Finetuning Powersave

1. Install powertop
```

sudo su
apt-get install powertop
powertop

```
Toggle through with "TAB" to Tunables
Lots of "Bad" values should be displayed.
2. Install TLP
For detailed Instructions refer to []([http://thinkwiki.de/TLP_-_Linux_Stromsparen](http://thinkwiki.de/TLP_-_Linux_Stromsparen)).
```

sudo su
add-apt-repository ppa:linrunner/tlp
apt-get update
apt-get install tlp tlp-rdw

```
3. Edit tlp config (only changes are shown)
```

DISK_APM_LEVEL_ON_BAT="126 126"
RUNTIME_PM_ALL=1
RESTORE_DEVICE_STATE_ON_STARTUP=1

```
Restart tpl with `sudo /etc/init.d/tlp restart` 
Check if settings took effect with `powertop`.

With this and bluetooth disabled and wifi on I get arround 10h battery time.

---

### Post by dougphy on 2013-10-18
Using spezimas method: (anyone have a fix for this?)
 
When booting to the EFI boot option, I get a quick error message saying missing a file
boot/<something>.efi .. it flashes quickly and then moves on to the grub screen
When I hit "e" on the grub screen I then don't have the option to edit the linux /boot/vmlinuz.... line to the correct format because it's very short and doesn't include my UUID, etc. Basically, there is a line starting with "linux" but it's not of the format spezimas lists.

---

### Post by spezimas on 2013-10-18
Saucy final is now released. Did you use the ubuntu-13.10-desktop-amd64+mac.iso or the ubuntu-13.10-desktop-amd64.iso ? Please try with the ubuntu-13.10-desktop-amd64.iso if not used so far.
I have successfully installed 13.10 now. Detailed instructions follow...

---

### Post by dougphy on 2013-10-18
I used the final release desktop-amd64.iso
I was able to get a full read of the error I get when booting:
```

Could not open "\EFI\BOOT\fallback.efi"

```

---

### Post by spezimas on 2013-10-18
# Installation of Ubuntu 13.10 on Macbook Air 6,2 (Mid2013)

## Prerequisites
1. MacBookAir6,2 
   * Check on OSX with `sysctl hw.model`
   * Check on linux with `sudo dmidecode -s system-product-name`
2. Apple USB-Ethernet Adapter
3. USB-Stick (1GB at least)
4. `ubuntu-13.10-desktop-amd64.iso` from [http://releases.ubuntu.com/13.10/](http://releases.ubuntu.com/13.10/). 
   Note: Do not use the 'amd64+mac' iso image as here the USB-Stick cannot boot. (Do not ask me why.)

## Partition Harddisk
1. Boot Macbook Air into OSX
2. Open Disk Utility
```

open /Applications/Utility/Disk\ Utility.app

```
3. Select "Macintosh HD" > (Tab)Partition
   Add (+) 3 more partitions
4. 2nd Partition: Set 30-40GB for Ubuntu "/"
   4th Partition: Set 4GB for Linux Swap partition
   3rd Partition: Use as much space as left for "/home"

## Prepare USB-Stick
1. In OSX
2. Download iso image to ~/Downloads
3. Open Terminal (a detailed description can be found [here]([http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx))
```

cd ~/Downloads
# convert iso
hdiutil convert -format UDRW -o ubuntu-13.10-desktop-amd64.img ubuntu-13.10-desktop-amd64.iso
open /Applications/Utilities/Disk\ Utility.app
# format the USB stick with MS-DOS VFAT
diskutil list
# check which /dev/diskX contains the USB stick - here it is "disk1"
# then unmount the usb-stick
diskutil unmountDisk /dev/disk1
# write img to usb stick - /!\ BE CAREFUL THAT disk1 REALLY IS YOUR USB-STICK
sudo dd if=ubuntu-13.10-desktop-amd64.img.dmg of=/dev/rdisk1 bs=1m

```

## Install Ubuntu 13.10
1. Restart and press "Alt"-Key on startup.
2. Make sure that the USB-Ethernet Adapter is NOT inserted. (With a network connection the bcmwl-kernel-source module gets downloaded during the installation process which prevents grub to get installed; DKMS module insertion stops installation process).
   Select first USB-device labled "EFI-Boot" and press "Enter"
   No splash screen shall be displayed but the Ubuntu installation menu. 
   Check  [Identifying if the computer boots the Ubuntu DVD in EFI mode]([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI))
   Select "Install Ubuntu"
3. Choose "Something else" for partitioning.
   Please check the sizes in the list according to the partitioning for the step above. 
   OSX Disk Utility leaves unallocated partitions inbetween which usually are arround 128MB in size.
   Do not try to delete these "blank" partitions.
   2nd partition should be ext4 formatted and mounted "/".
   3rd partition should be ext3 formatted and mounted "/home". (I use ext3 in order to use fuse-ext2 from OSX; ext4 is yet not supported) 
   4th partition should be swap (no format and mountpoint required)
   Proceed...
4. The installation process should run through smoothly. 
5. Restart with pressed "Alt"-Key.
   Unfortunately selecting the "Windows" labled Partition (HD-icon) only displayed a black screen with a blinking cursor.
   Reboot into OSX again and install `refind`.
   Download [Binary Zip-File]([http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html))
   Open a Terminal
```

cd Downloads
unzip  refind-bin-0.7.4.zip 
cd refind-bin-0.7.4
bash install.sh 

```
6. Restart again. Now a Ubuntu labled '/efi/grubx64.efi' should be shown.
   Select this an start it, now the grub-menu should be displayed.
   Select "Ubuntu".
   Now Ubuntu should boot.
   
## Update Ubuntu and install Wifi driver

1. Log into ubuntu 13.10 and open a terminal (Ctrl+Alt+t).
   Enter the following commands
```

sudo apt-get update
sudo apt-get upgrade

```
   This updates all packages
2. Start (Panel) > (Menu)System Settings > (Icon)Software & Updates (or from terminal `/usr/bin/python3 /usr/bin/software-properties-gtk`)
   Select (Tab)Additional Drivers and install Broadcom 802.11 Linux STA wireless driver from bcmwl-kernel-source
3. Now reboot again
   Select "Ubuntu"
   
## What works and what does not work

[table="width: 500, class: grid"]
[tr][td] Feature                [/td][td] Support status [/td][td] Notes [/td][/tr]
[tr][td]------------------------[/td][td]----------------[/td][td]-------[/td][/tr]
[tr][td] LCD Panel              [/td][td] Partly [/td][td] After Suspend only off or on possible [/td][/tr]
[tr][td] Suspend, Hibernate     [/td][td] OK [/td][td] Suspend works, hibernate not tried out yet [/td][/tr]
[tr][td] Shut-down and Reboot   [/td][td] OK [/td][td]  [/td][/tr]
[tr][td] Keyboard functions (Brightness,volume,...) [/td][td] OK [/td][td]  [/td][/tr]
[tr][td] Keyboard backlight     [/td][td] OK [/td][td]  [/td][/tr]
[tr][td] Touchpad               [/td][td] OK [/td][td]  [/td][/tr]
[tr][td] Wireless               [/td][td] OK [/td][td]  [/td][/tr]
[tr][td] Bluetooth              [/td][td] OK [/td][td]  [/td][/tr]
[tr][td] iSight                 [/td][td] NO [/td][td] camera is not an usb device [/td][/tr]
[tr][td] Sound                  [/td][td] OK [/td][td]  [/td][/tr]
[tr][td] Microphone             [/td][td] OK [/td][td] sound recoder is broken but recording with audacity works [/td][/tr]
[tr][td] External Monitor       [/td][td] NO [/td][td] External Monitor cannot be found (see note below) [/td][/tr]
[tr][td] Thunderbolt            [/td][td] ?  [/td][td] To be verified [/td][/tr]
[tr][td] SD card slot           [/td][td] OK [/td][td]  [/td][/tr]
[tr][td] HFS+ (OS X disc partition) [/td][td] OK [/td][td] mount read-only ok [/td][/tr]
[tr][td] Fan Control            [/td][td] OK [/td][td] according to `tlp stat` [/td][/tr]
[tr][td] Sensors (temps & fans) [/td][td] OK [/td][td] according to `tlp stat` [/td][/tr]
[tr][td] GPU Power Save         [/td][td] OK* [/td][td] Needs some extra kernel args. See below [/td][td] 
[/table]

**Issues left:**

* Backlight on/off after resume:
  Before suspend + resume the behaviour of the backlight pressing F1 or F2 key is linear.
  Checking the register `sys/class/backlight/intel_backlight/brightness` the range from 0 to 2770 can be operated in 21 steps.
  After resume still the full range is triggered with the F1 to F2 keys but here the backlight is turned off for all values less than 2330.
* iSight HD webcam does not work:
  The camera is not recognized as USB device. The current iSight-Firmware cutter does not help here.
* External Monitors are not detected properly. 
  Sometimes they get detected by accident and "Undetected display" is shown. 
  Then only VGA resolutions can be selected but not the external monitor native ones.

### Workarround for Backlight issue after resume

If led-backlight is set to low after resume the screen is to dark to enter the password.
The following script solves the problem of having to enter the password after resume in darkness.
  But this does not solve the issue of readjusting the brightness
  Paste the below code and copy it into a file nemed `99displayfix`. This copy into the folder `/etc/pm/sleep.d/`
```

#!/bin/sh

# installation instructions
#   sudo cp 99displayfix /etc/pm/sleep.d/
#   sudo chmod +x /etc/pm/sleep.d/99displayfix

case "$1" in
	thaw|resume)
		# set max brightness
		echo 2550 > /sys/class/backlight/intel_backlight/brightness
		;;
	*)
		;;
esac

exit $?

```

**NOTE:**
* Alt+F2+Fn (Run Application) not working 
  Enabling via (Menu)System Settings > (Item)Keyboard > (Tab)Shortcuts > (Item)Launchers > Key to Show the HUD == Disabled
```

sudo apt-get install compizconfig-settings-manager
# after install start in terminal with
ccsm
# (Chaper)General > (Item)Gnome Compatibility > (Item)Run Dialog > Grab Key-Combination "<Alt>F2"

``` 

### fn-Key change behaviour

I personally prefer to use fn+Fkeys for the brightness and sound settings but leave the Fkeys for the applications without pressing fn.
To change this behaviour 
```

echo options hid_apple fnmode=2 | sudo tee -a /etc/modprobe.d/hid_apple.conf
sudo update-initramfs -u -k all

```
Then reboot.
For further info on this topic check [here]([https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)).


## Finetuning Powersave

1. Install powertop
```

sudo su
apt-get install powertop
powertop

```
   Toggle through with "TAB" to Tunables
   Lots of "Bad" values should be displayed.
2. Install TLP
   For detailed Instructions refer to []([http://thinkwiki.de/TLP_-_Linux_Stromsparen](http://thinkwiki.de/TLP_-_Linux_Stromsparen)).
```

sudo su
add-apt-repository ppa:linrunner/tlp
apt-get update
apt-get install tlp tlp-rdw

```
3. Edit tlp config `/etc/default/tlp` (only changes are shown)
```

DISK_IDLE_SECS_ON_BAT=1
MAX_LOST_WORK_SECS_ON_BAT=15
DISK_APM_LEVEL_ON_BAT="1 1"
RUNTIME_PM_ALL=1
RESTORE_DEVICE_STATE_ON_STARTUP=1

```
   Restart tpl with `sudo /etc/init.d/tlp restart` 
   Check if settings took effect with `powertop`.
4. Dim the backlights for screen and keyboard. On startup the values are set to max-level.
   Edit `/etc/rc.local`
```

echo 400 > /sys/class/backlight/intel_backlight/brightness
echo 16 > /sys/class/leds/smc\:\:kbd_backlight/brightness
sleep 0.2s

```
   Without the sleep command broken Wifi is the result.
5. Run `sudo tlp stat` 
   Still
```

/sys/module/i915/parameters/i915_enable_rc6  = -1 (use per-chip default)
/sys/module/i915/parameters/i915_enable_fbc  = -1 (use per-chip default)
/sys/module/i915/parameters/lvds_downclock   =  0 (disabled)
/sys/module/i915/parameters/semaphores       = -1 (use per-chip default)

```
   Add the following line in `/etc/default/grub`
```

GRUB_CMDLINE_LINUX_DEFAULT="pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 acpi_backlight=vendor"

```
   Then run `sudo update-grub` and reboot.
   After that:
```

/sys/module/i915/parameters/i915_enable_rc6  =  1 (enabled)
/sys/module/i915/parameters/i915_enable_fbc  =  1 (enabled)
/sys/module/i915/parameters/lvds_downclock   =  1 (enabled)
/sys/module/i915/parameters/semaphores       = -1 (use per-chip default)

```   

**Issues left:**

* Bluetooth drains quite some battery and cannot be disabled at start.
  `sudo sed -i '$i /usr/sbin/rfkill block bluetooth' /etc/rc.local` does not allow to start bt from "System Settings" later on.
  Still looking for a possibility to disable this from command-line at startup.
* It would be nice to have the ambient sensor used to trigger the backlights.
  Trying 'lightum' `http://github.com/poliva/lightum` results in a crash.

---

### Post by spezimas on 2013-10-18
Did you use my recipe? 
Do you see the orange USB-icon on boot with Alt-key pressed?
Can you please follow the steps as described one by one? This should do. If not maybe you should change to a different USB-Stick.

---

### Post by dougphy on 2013-10-18
Yep and yep -- I'll give it one more try using the updated directions.

Got a message at the end of installation saying grub failed to be installed to ./target/ -- will try with a different stick

---

### Post by littlerob2 on 2013-10-22
Thanks a lot spezimas !
I follow all your detailed steps and I now have my favorite OS on my macbook air.
Just a few remarks/questions:

1. I didn't have any problem with wifi. The Broadcom driver installed itself during installation and everything worked from the first start.

2. The backlight issue is really anoying. After resume, I have a very bright screen, but I cannot decrease it (I can only hit F1 key 4 times, then the screen is totally black). Is it the same for you ? As you said, low brightness can save lots of battery life, so it would be very great to be able to better adjust brightness after resume.

3. This could be useful for others : I manage to change the timeout of refind (at startup), by editing the refind.conf file in EFI/refind/ directory (I logged in to mac os to do it). 

4. The link [https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard) is very useful to remap the keyboard. About that matter, I still don't know if it is possible to swap fn and ctrl key. It seems that we can't do it with the xmodmap as for others keys...

Anyway, thanks again, I tried mac os for one hour and I was not happy. Now I am !

---

### Post by littlerob2 on 2013-10-23
About the bluetooth issue : the third solution of the following guide works for me :
[http://linuxg.net/how-to-disable-bluetooth-at-startup-5-practical-methods/](http://linuxg.net/how-to-disable-bluetooth-at-startup-5-practical-methods/)
(paste '/etc/init.d/bluetooth stop' in the /etc/rc.local file).

---

### Post by littlerob2 on 2013-11-03
External monitors are properly detected when using latest version of the linux kernel : v3.12-rc7 (kernels can be downloaded frome : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)).

Finally, it seems that issues left reduce to :
* backlight issue after resume
* isight camera undetected

---

### Post by andyofmelbourne on 2013-11-22
Thanks littlerob2 for point 3. I was looking for that one.

However it seems that resetting timeout to 0 disables the wait completely, while choosing a float value (like 0.001) rounds to the nearest int (0 in this case). Currently I have set this value to 1, thus providing the shortest wait possible to boot into ubuntu. 

I wonder if refind has a mechanism for immediately booting to the preferred OS?

---

### Post by littlerob2 on 2013-11-23
I set this value to 1 too, but I don't know if the immediate boot is possible. Sorry !

---

### Post by kim7 on 2013-11-25
Hey guys,

I just installed the latest 13.10 Mac Build on my new Mac Air (I guess 6.2). My problem: Wifi not working.
But during the installation process Wifi was working and it did connect to my wireless network!

In order to boot correctly I have to add **acpi=off** to grub.

When booted up, wireless card seems to be recognized but does not show any networks?! Weird thing though is that it's listed as eth0...

**ifconfig:**
```
eth0      Link encap:Ethernet  HWaddr 5c:f9:38:9a:8d:26  
          inet6 addr: fe80::5ef9:38ff:fe9a:8d26/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:115216 (115.2 KB)  TX bytes:115216 (115.2 KB)
```
[B]
iwconfig:[/B]
```

eth0      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=200 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

**lspci | grep Network:**
```
03:00.0 Network controller: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter (rev 03)
```

Any idea? :) I have no ethernet connection so would have to move packages using usb!

Cheers,
Kim

---

### Post by kim7 on 2013-11-26
seems like I got it running. I did usb tethering with my Android phone and updated all packes + kernel.
Then I replaced the grub parameter acpi=off with nosmp.

works perfect so far. Stay tuned.

---

### Post by Monis on 2013-12-20
Hello.

Would like to come with an update here. I have installed Ubuntu 13.10 on my Macbook Air 2013 model, and everything works perfect! The keys, fan, touchpad, drivers, wireless, everything! And the battery last for around 5 hours with normal use. Just like Mac OSX.

I would like to share what I did to get it running :-)

I tried to install Ubuntu with rEFIt, but like everybody else, I just got the purple screen when booting. I really hated that... Then I came over rEFInd, an alternative to rEFIt, and it works amazing! I would like to make a little guide to make Ubuntu running on Macbook Air 2013:

1. Visit this site and download "A binary zip file": [http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

2. Extract that zip-file.

3. Run the file "install.sh" thought the terminal.

4. Voila, rEFInd is installed.

5. After installtion of rEFInd we should make sure that it will find our USB stick as an available boot option for EFI. To do that open up /EFI/refind/refind.conf using a texteditor and search for the line starting with "scanfor" and change it to the following: 

scanfor internal,external,optical,manual

You remove the hashtag.

6. Make space to Ubuntu with "Disc Utility".

7. Download Ubuntu from their site. PS! Don`t download the Mac-version, that won`t work. Download the regular 64-bit version.

8. Burn the iso-file to a USB-pen.

9. Boot up your Macbook Air. Now, you rEFInd will show up. Go to "EFI/boot/grubx64.efi" and press Enter.

10. Install Ubuntu (I assume people know how to do it)

11. Once you are finish with the install: Voila, you have Ubuntu, and everything should work from the first boot!

---

### Post by spezimas on 2013-12-23
Updated description on install procedure can now be found on [https://help.ubuntu.com/community/MacBookAir6-2/Saucy](https://help.ubuntu.com/community/MacBookAir6-2/Saucy)

---

### Post by spezimas on 2013-12-23
BTW. Has anyone got the CPU Turbo Boost feature reliably working on MacBookAir6,2?
If I boot on AC-Power using [FONT=Courier New]powertop[/FONT] I see that the freq scaling goes up to 2.5 GHz (This is what I want). 
After unplugging and replugging AC I will not get more that 1.3 GHz. Booting from battery does the same.
Does anyone experience the same?

---

### Post by peter27 on 2013-12-26
Has anyone solved the brightness issue after hibernation? 

Thanks in advance.

---

### Post by spezimas on 2013-12-28
@kim7
I updated install instructions here [https://help.ubuntu.com/community/MacBookAir6-2/Saucy#Manual_installation_without_USB-Ethernet_Adapter](https://help.ubuntu.com/community/MacBookAir6-2/Saucy#Manual_installation_without_USB-Ethernet_Adapter) 
Have tried it with a Live-CD (USB) and it worked. So hopefully it works with you as well

---

### Post by patrik-r-jakobsson on 2014-01-19
> **peter27 said:**
> Has anyone solved the brightness issue after hibernation? 

Thanks in advance.

I have a workaround for the brightness after suspend issue. It's a kernel module which can be found at:
[https://github.com/patjak/mba6x_bl](https://github.com/patjak/mba6x_bl)

It takes control of the backlight chip directly and disables backlight access for the Intel driver. It's experimental so use at your own risk.

---

### Post by rbaum on 2014-02-23
[QUOTE=littlerob2;12837395]External monitors are properly detected when using latest version of the linux kernel : v3.12-rc7 (kernels can be downloaded frome : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)).

Hello littlerob2,

can't confirm this on my machine: MacBookAir6,2 (13").
i've tried the kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc7-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc7-saucy/) which does not seem to work. Also some newer kernels like 3.13.X didn't bring my external display adapter up.

any suggestions?

sincerely

---

### Post by slicer on 2014-06-05
For anyone interested, I was able to make my Macbook Air 6,2 boot natively into Linux using efibootmgr:

```
# efibootmgr -v
BootCurrent: 0080
Timeout: 5 seconds
BootOrder: 0080
Boot0000* ubuntu	HD(1,800,100000,0b4f4362-26d1-4469-a3fa-b5b3052de9ed)File(\EFI\ubuntu\shimx64.efi)
Boot0080* 	ACPI(a0341d0,0)PCI(1c,5)PCI(0,0)03120a00000000000000HD(2,64028,e066090,51721a3e-5331-4eec-8937-d5266561d23c)File(\System\Library\CoreServices\boot.efi)
BootFFFF* 	ACPI(a0341d0,0)PCI(1c,5)PCI(0,0)03120a00000000000000HD(2,64028,e066090,51721a3e-5331-4eec-8937-d5266561d23c)File(\System\Library\CoreServices\boot.efi)
```

The 0080 and FFFF entries are leftovers from when there was Mac OS X on the machine. Changing permanently to Linux is as simple as setting the BootOrder. No rEFit/rEFInd needed. You might want to "apt-get install efibootmgr" though.

```
# efibootmgr --bootorder 0000
BootCurrent: 0000
Timeout: 5 seconds
BootOrder: 0000
Boot0000* ubuntu
Boot0080* 
BootFFFF*
```

---

### Post by urilabob on 2014-07-22
I know this is late, but try trusty tahr - works like a charm

---

