---
title: "Macbook Pro 11,5 Ubuntu 18.04.1 LTS - Intel Video"
date: 2019-01-07
forum: Apple Hardware Users
---

### Post by ecartman84 on 2019-01-07
I have just setup Ubuntu 18.04.1 LTS on my Macbook Pro 11,5 (2015 - 15 in) and it is working great except for the battery life. From what I can tell this computer has the AMD Radeon R9 M370X with 2 GB of dedicated GDDR5 memory and an integrated Intel Iris 5200 Pro graphics processor with 128 MB of "Crystalwell" embedded DRAM (and shared system memory). The system only shows this as the enabled graphics and does not allow me to switch between the AMD and Intel Graphics: "Advanced Micro Devices, Inc [AMD/AIT] Venus XT [Radeon HD 8870M / R9 M270X/M370X]". How can I disable the AMD Graphics at bootup and enable the Intel graphics to save battery life? I have tried everything that I have found online and none of it seems to work with this laptop.

Thanks!

---

### Post by gsahli on 2019-01-08
Although it's for a Dell Latitude laptop, I think this gives enough info to work through this yourself:
[https://askubuntu.com/questions/1038271/intel-amd-hybrid-graphics-ubuntu-18-04](https://askubuntu.com/questions/1038271/intel-amd-hybrid-graphics-ubuntu-18-04)

---

### Post by ecartman84 on 2019-01-09
> **gsahli said:**
> Although it's for a Dell Latitude laptop, I think this gives enough info to work through this yourself:
[https://askubuntu.com/questions/1038271/intel-amd-hybrid-graphics-ubuntu-18-04](https://askubuntu.com/questions/1038271/intel-amd-hybrid-graphics-ubuntu-18-04)


Thank you for the suggestion! I am thinking that I may have found the missing information that I needed at the link below. It looks like Macbooks will disable the Intel Graphics if you boot anything other than MacOS and I think that this is what I am running into. When I run the command to list the adapters it only shows the AMD one so I am not able to switch. I am going to do some testing and see if the if the apple set os resolves the problem.

[https://unix.stackexchange.com/questions/193425/enabling-intel-iris-pro-syslinux-tails-system-macbook-pro-15-retina-late-2013](https://unix.stackexchange.com/questions/193425/enabling-intel-iris-pro-syslinux-tails-system-macbook-pro-15-retina-late-2013)

---

### Post by ecartman84 on 2019-01-10
I think that I finally have this install working correctly and my battery life is way better now! I ended up using rEFInd with spoof_osx_version 10.9 enabled so that it would turn on the Intel graphics when Ubuntu was started. I then used the gpu-switch script from 'https://github.com/0xbb/gpu-switch' to switch the default graphics to integrated. And finally I used crontab -e to have vgaswitcheroo power off the AMD graphics at startup. Here is the basic steps for the install of Ubuntu on my 15" 2015 Macbook Pro:

-----------------------------------------------
MacBook Pro 11,5 Ubuntu 18.04.1 LTS install
-----------------------------------------------


- Connect Wifi if you didn't during the install from the live usb


- Install rEFInd
sudo apt-add-repository ppa:rodsmith/refind
$ sudo apt-get update
$ sudo apt-get install refind


- Uncomment "spoof_osx_version 10.9" in /boot/efi/EFI/refind/refind.conf which forces the MacBook to enable the Intel graphics adapter when booting into an OS other than MacOS. This has to be done as root so you have to run 'sudo su' before changing into the directory and editing the file.


- Reboot the machine and load ubuntu from rEFInd


* You can verify that the Intel graphics are enabled by running 'lspci -nn | grep -E 'VGA|Display' to list the enabled adapters *


- Download the gpu-switch script from [https://github.com/0xbb/gpu-switch](https://github.com/0xbb/gpu-switch)
- run 'chmod +x' on gpu-switch to make it executable
- run sudo ./gpu-switch -I to switch the gpu to the integrated intel adapter on the next reboot
- Reboot the machine again


- Make sure the screen brightness is set at startup and the Radeon Graphics are shut off to conserve battery power.


1. run "sudo crontab -e" has to be run as sudo because the backlight file cannot be modified by a non root user
2. select nano for editing the cron file
3. Add this script in your cron file to shut off Radeon graphics and reset the brightness on reboot
----------------------------------
@reboot echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
@reboot echo 30 > /sys/class/backlight/gmux_backlight/brightness
-----------------------------------
4. Save the file in nano


- Reboot the machine again


* You can verify that you are using the Integrated graphics and that the ATI one is disabled by running 'sudo cat /sys/kernel/debug/vgaswitcheroo/switch' IGD should have a plus sign if it is active. DIS should be set to off if the ATI adapter is powered off *


- Turn off Bluetooth by adding a the script 'rfkill block bluetooth' in 'Startup Application Preferences' application.
- Turn off Automatic brightness in 'Settings --> Power --> Power Saving'
- Turn off Tap to Click in 'Settings --> Devices --> Touchpad'
- Change Time Format to 'AM/PM' in 'Settings --> Details'
- Install powertop and tlp to optimize battery usage
sudo apt-get install powertop tlp 
- Unplug the laptop from the power adapter and then Run: 
"sudo powertop --calibrate" and then "sudo powertop --auto-tune"
- Use crontab -e again and add '@reboot power top --auto-tune' so that it will run at startup
- Run "sudo tlp start" this should run automatically on each reboot after it is installed. You can check to see if it is running with 'sudo tlp-stat -s'
- Install Gnome Tweaks and setup the window buttons to be on the left side and date in the top bar

- Reboot the machine one final time

---

