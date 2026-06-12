---
title: "Live CD Fails to boot in UEFI Mode"
date: 2013-04-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Victini on 2013-04-08
I am having an issue with my Asus q500a in booting any version of ubuntu in UEFI mode Live CD where I get the Grub Menu and when i select try Ubuntu the cd makes a sound like its spinning up and then the laptop locks up. Same with all other options including install ubuntu. I have secure boot and fast boot disabled.
System Specs:
3rd generation I5 @ 2.50 GHz
6 Gigs of RAM
Intergrated Intel HD Graphics Card
Edit:  I finally figured out how to boot the live cd in UEFI mode and with some minor tweaks to the install process am able to install and boot without any issues. It seems to be a problem with grub and my laptop which is solved by replacing grub with gummiboot. If anyone needs me to explain how i did it PM me.

---

### Post by oldfred on 2013-04-08
I think some others have had issues with DVDs and others have had issues with flash drives.
But I would suggest using a flash drive.
Are you using the 64 bit version?

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

### Post by Victini on 2013-04-08
I am using the 64 bit version of ubuntu. I have also tried using USB I get the same result as if booting from DVD. Fast boot is turned off and i am booting in UEFI mode. If I boot the Live CD in BIOS mode I get to Unity however it installs it in BIOS mode and I am unable to boot it after re-booting

---

### Post by oldfred on 2013-04-08
Boot-Repair can convert a BIOS install to UEFI by uninstalling grub-pc and installing grub-efi.

       How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)
How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)

   Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.

---

### Post by Victini on 2013-04-08
I'll try it and see if it works

---

### Post by Victini on 2013-04-09
It didnt work. I get to the grub menu as as if its installed. Win8 boots fine from grub menu. Ubuntu does not however and completly locks up the computer the second I boot it.

---

### Post by black veils on 2013-04-09
what is the computer model?

---

### Post by oldfred on 2013-04-09
Do you have secure boot on or off. Some boot both Ubuntu & Windows with either, some with it on and some with it off.

Grub has the shim and a signed kernel, which may not be installed yet, but should be to make it work with secure boot.

---

### Post by Victini on 2013-04-10
its an asus q500a and I get a black screen on boot whether secure boot is on or off and i know its reading the shim right because when secure boot is on and the signature is invalid I get a different error than what im currently getting.

---

### Post by oldfred on 2013-04-10
If you get grub menu & can boot Windows and start Ubuntu then it is usually video issue or maybe other boot parameters.
What video card/chip?

       Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

 [http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by Victini on 2013-04-10
Its an Intel Intergrated HD Graphics Card. The kernel locks up on boot. crtl+alt+del does not work nor do sysrq keys.
EDIT: With Legacy Boot turned on CRTL+ALT+DEL does work but not sysrq keys.

---

### Post by oldfred on 2013-04-10
A variety of users have posted different things, not really sure what works.

Linux 3.2 To 3.8 Kernels With Intel Ivy Bridge Graphics
[http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1)
Intel HD4000
[http://communities.intel.com/thread/34221](http://communities.intel.com/thread/34221)
Also one used nolapic


 Limited resolutions with Sandybridge graphics
[http://ubuntuforums.org/showthread.php?t=2057807](http://ubuntuforums.org/showthread.php?t=2057807)
With 11.04:SandyBridge
[http://ubuntuforums.org/showthread.php?t=1817374](http://ubuntuforums.org/showthread.php?t=1817374)
acpi_osi=linux pci=noacpi
[http://ubuntuforums.org/showthread.php?t=1900897](http://ubuntuforums.org/showthread.php?t=1900897)
Testing of 12.04
[http://ubuntuforums.org/showthread.php?t=1927965](http://ubuntuforums.org/showthread.php?t=1927965)

   Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

   For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

---

### Post by Victini on 2013-04-23
I tried the video settings and it did not work. I did notice though that while booting from dvd that the dvd spins up after pressing f10 for a few seconds and then it stops all together and locks up. I also tried booting several other distros to see if they would fair any better however the problem still persisted. It also failed to boot the 13.04 beta.

---

### Post by oldfred on 2013-04-23
Some have reported that UEFI does not work so well from DVD. But others have reported some flash drives work better than others.

       Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

---

### Post by Victini on 2013-04-23
USB has what im assuming to be the same problem... I see the flash drive blink as if data is being accessed and then its stops blinking and i get the same symptoms as if booting from DVD.

---

### Post by oldfred on 2013-04-23
Maybe Video and/or you may need other boot parameters. Have you tried some of the settings from post #12 in grub linux line in place of splash quiet?

---

### Post by Victini on 2013-04-24
Yes i have.
Here is more in depth sytem hardware information outputed from systeminfo in Windows
System Model:              Q500A
System Type:               x64-based PC
Processor(s):              1 Processor(s) Installed.
                           [01]: Intel64 Family 6 Model 58 Stepping 9 GenuineIntel ~2501 Mhz
BIOS Version:              American Megatrends Inc. Q500A.205, 8/17/2012
Windows Directory:         C:\Windows
System Directory:          C:\Windows\system32
Boot Device:               \Device\HarddiskVolume2

---

