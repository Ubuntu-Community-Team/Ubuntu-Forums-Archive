---
title: "Installing Ubuntu from USB on a MacBook Air 3,1-3,2 (nvidia card)"
date: 2014-03-06
forum: Apple Hardware Users
---

### Post by Julien Dutant on 2014-03-06
The [official documentation for MacBook Air installs]("https://help.ubuntu.com/community/MacBookAir") has no page for Pagolin (12.04) or Saucy (13.10) on a MacBook Air 3,2. Its [page for Raring]("https://help.ubuntu.com/community/MacBookAir3-2/Raring") (13.04) is useful but doesn't cover the EFI problem that arises when installing from USB stick (see below). I struggled a bit to get Ubuntu running, so here's howto for those who might need it. This should also work for other models that require nvidia-319 graphic drivers or other non-EFI-compatible.

The core problem with the installation is this. The graphic driver that Ubuntu installs by default (Nouveau) has bugs with the MacBook Air 3 graphic processor, the nvidia GeForce 320M (G320M). You can do a default install, it will boot normally, but you'll soon see little glitches here and there and the computer will normally crash after a few minutes of use (especially when transparency or shadow effects are used, it seems). The problem [exists with Raring]("https://help.ubuntu.com/community/MacBookAir3-2/Raring") and I expect it arises with Precise (though see ''alternative solutions" below). 

To avoid that, you need to install the proprietary nvidia driver. But here is the catch: the driver requires the computer to boot in "Legacy BIOS mode", not in "EFI" mode (see [here]("http://askubuntu.com/questions/264247/proprietary-nvidia-drivers-with-efi-on-mac-to-prevent-overheating") or [here]("http://askubuntu.com/questions/264247/proprietary-nvidia-drivers-with-efi-on-mac-to-prevent-overheating")). If you install the nvidia drivers while Ubuntu is in EFI mode, you'll get a blank/black screen at the beginning of the boot. (If you got to that stage, see the ''recovery for nvidia drivers EFI crash'' below). [On a PC you can force Ubuntu to install in BIOS Legacy mode]("https://help.ubuntu.com/community/UEFI#Set_up_the_BIOS_in_EFI_or_Legacy_mode") by selecting that mode in the computer BIOS. But on a Mac you can't (easily) do that, and if you install from a USB key by default you will be in EFI mode. 

So summing up, if you do a default installation of Ubuntu from a USB on a MacBook Air 3,1 or 3,2, you'll either have buggy graphics and random crashes, or you'll install the nvdida drivers and have a blank/black screen at startup.

I managed to install using the procedure sketched by [NoahR]("https://askubuntu.com/users/127933/noahr") here: [https://askubuntu.com/questions/399744/how-to-install-a-dual-boot-ubuntu-in-bios-mode-and-mac-os-x](https://askubuntu.com/questions/399744/how-to-install-a-dual-boot-ubuntu-in-bios-mode-and-mac-os-x) . I detail it below. Suggestions for alternative procedures / improvement are welcome (I note some ideas I found below).

[B]1. Install Ubuntu in BIOS Legacy mode
[/B]
If you want to dual-boot you have to repartition your disk to leave some space for the Ubuntu partitions. See [here for help]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:_Mac_OSX_and_Ubuntu").

**Option A: you have a CD/DVD drive**. Lucky you! Apparently installing from the Ubuntu CD automatically triggers the BIOS mode. (I say this because the [official instructions are based on a CD install]("https://help.ubuntu.com/community/MacBookAir3-2/Raring") and they don't run into the BIOS/EFI problem.) To check that your live CD does run in BIOS mode, it's easy: the [startup screen of the Live CD looks different]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode") depending on the active mode. If the Live CD started in BIOS mode, it will install a Ubuntu in BIOS mode. You can do a default install and jump to step 2. If the Live CD started on EFI mode, you have to follow the steps of option B (as with an USB install).

**Option B: USB stick or the CD runs in EFI mode**. From USB you need first to create a Mac-bootable USB stick, [see here]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx"). If you paln to dual-boot (keep OS X alongside Ubuntu) repartition to leave some space.

Boot the Live USB or CD (hold "option" at start-up). Choose "Try Ubuntu without installing it". 
[I]
Note on crashes during install[/I]. While you use the "Try Ubuntu without installing it" or run the Ubuntu installer there (see below), the computer may crash (because of the default Nouveau graphic driver). Don't worry, do a hard reboot (press off button three seconds), try again. If a crash occurs during the post-installation fixes (see below) you don't need to reinstall, but you should do all the post-installation fixes from the start again.

At the Ubuntu desktop open a terminal (Ctrl + Alt + T). Enter the following (launches the Ubuntu installer):
```
sudo ubiquity
```

When the installer asks you to choose between several types of install, choose "Something else". You will arrive to the partition editor. Create at least three partitions (if you want to wipe out the hard drive choose "New Partition Table", otherwise create them in the empty space you have created):
[LIST=1]
[*]A partition of 1MB (that's enough!), type "Reserved BIOS boot area". 
[*]A partition for Ubuntu, your choice of size, type ext4, mount point "/". Leave just enough MBs for the swap: 
[*]A partition for swamp memory, of the same size as your RAM (about 4096MB if you have 4Go RAM), type "swap". 
[/LIST]
At this stage you should note two things:
[LIST=1]
[*]the name of the hard drive, of the form "sdX". Below I use "sda", but replace if need be. 
[*]the name of the Ubuntu partition (number 2 above), of the form "sdXY". Below I use "sda2", but replace if need be. 
[/LIST]
Now complete the installer. DO NOT restart when the installation is over. (Your installation has been made in EFI mode but without EFI partition, so it simply won't boot. in the post-installation fixes we convert it to a BIOS one. If you restarted, you should reboot from the Live USB/CD and choose "Try without installing" again.)

Now for the post-installation fixes. 

Get back to (or reopen) the terminal. Do the following (replacing sda2 with the name of your Ubuntu partition):
```
sudo mount /dev/sda2 /mnt
```
Then the following (replacing "/dev/sda" with the name of your drive if need be):
```
grub-install --root-directory=/mnt /dev/sda
```
You should get "Installation finished. No error reported." Then:
```
grub-install --root-directory=/mnt --recheck /dev/sda
```
You should get "Installation finished. No error reported." again. At that point the BIOS version of GRUB (Ubuntu bootloader) is installed on the drive. But the drive still need to be configured:

Enter the following (line by line):
```
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
update-grub
exit
```

Now you should be able to restart Ubuntu from your hard drive. Congrats, go to step 2!

[B]2. Installing the nvidia driver and last fixes
[/B]
I assume you have Ubuntu installed on your hard drive in BIOS mode. (To check whether your Ubuntu is BIOS mode: see [here]("https://help.ubuntu.com/community/UEFI#Identifying_if_an_Ubuntu_has_been_installed_in_EFI_mode"), or simply open the Files and navigate to Computer > sys > firmware. if you see a folder named "efi", you're in EFI mode, if not, you're in Legacy BIOS mode). [I]

Note on graphic glitches and crashes[/I]: as before, the computer may crash at some point because of the graphic driver. Simply restart and try again from this step.

You need to connect to the internet first. 

Open System Settings > Software and Updates > Additional Drivers. You will see a driver "nvidia-319 (proprietary, tested". Choose it, and click "Apply". It will download and install the driver.

Restart the computer (button on the top right of the screen). Now it's bug free! 

(At least it should be! If you got a blank/black screen, see section 3 to remove the nvidia driver, start again, and make sure you are running in BIOS mode.)

There is a last glitch, however: the light buttons don't work. Here's the fix (from [the official documentation]("https://help.ubuntu.com/community/MacBookAir3-2/Raring#Fixing_brightness_keys")). Once you've installed the nvidia drivers and restarted, run the "Nvidia X server settings" programme (click the Ubuntu sign top left and enter "Nvidia X settings", or open a terminal and enter "sudo nvidia-settings"). Go to "X Server Display configuration" and click "Save to X configuration file" at the bottom right. Then Quit.

Now open a terminal and do the following (to enter the text editor in "root" mode):
```
sudo gedit /etc/X11/xconf.org
```
Find the Device section - looks like this:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 320M"
EndSection
```
Add the following line to it:
```
Option         "RegistryDwords" "EnableBrightnessControl=1"
```
  So that it now looks like this:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 320M"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```

Save the file, close the text editor, restart. Now your brightness keys should be working.

I haven't found the other post-installation fixes of the official documentation needed. 

[B]3. Nvidia driver blank/black screen crash
[/B]
If you have installed the Nvidia driver and that you get a black/blank screen here is what you can do (cf. [this page]("http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely")). You need a network connection, Wifi will do but you should have configured it before getting blank screens.

During boot (white screen) press "Esc" once or twice. (On a dual boot select the Ubuntu start first.) This should bring the GRUB menu. Select "Boot in recovery mode". Select "Enable networking". Once the network is up select "Drop to root shell prompt". Enter the following, line by line:
```
sudo apt-get remove --purge nvidia-*
sudo apt-get install ubuntu-desktop
sudo rm /etc/X11/xorg.conf
echo 'nouveau' | sudo tee -a /etc/modules

```
And restart (enter "reboot").

This will put the Nouveau driver back. It's buggy and ultimately crashes, but it should be bootable.

**4. Alternative options?**

The [official documentation UEFI page]("https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode") suggests using Boot-Repair to switch an EFI installation to a BIOS Legacy one. I got it to work once, but it was after having tried different things - in particular, after trying to install grub-pc manually. I tried to do it again from a clean install. It didn't work: Boot-Repair would warn "The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating an EFI partition", and if you tried to ignore the warning it wouldn't complete the error procedure, but instead show the warning again, and so on until you gave up. (The one time when it worked, the message was displayed, but after ignoring it the repair went through.) 

The [official documentation UEFI page]("https://help.ubuntu.com/community/UEFIBooting#Tested_configurations") suggests that the default graphic driver (Nouveau) works with Ubuntu 12.04 kernel 3.3 (not the default Ubuntu 12.04 kernel).

 This page: [https://mailman.archlinux.org/pipermail/arch-general/2012-December/032461.html](https://mailman.archlinux.org/pipermail/arch-general/2012-December/032461.html) suggests a hack to stablize the Nouveau driver, but that would disable graphic acceleration.

---

