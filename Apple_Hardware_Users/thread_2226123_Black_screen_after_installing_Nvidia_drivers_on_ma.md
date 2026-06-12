---
title: "Black screen after installing Nvidia drivers on mackbook pro 7.1 :("
date: 2014-05-25
forum: Apple Hardware Users
---

### Post by Euphoria on 2014-05-25
Hi,

im have a macbook pro 7.1 with nvidia geforce 320M. Im install with only ubuntu Gnome (no macOS), gpt partition and default partition scheme. update the system and reboot,all work fine (little hot but this is configuration issue). im modify the grub2 and erase spash and see when is start. after install the nividia driver, use nvidia-xconfig and reboot. just when is go on welcome screen for login got black screen. ctrl+shfit+fx not work but have ssh access :D

-im try install nvidia-current
- try to install nvidia-331 (on a new setup)
- try to install nvidia-337 (from ppa x edge)
- install acpi
- unistall nouveau drivers
- try sudo nvidia-xconfig
- blacklist nouveau in /etc/modprode.d/blacklist.conf



Now im have the last 337 installed,nvidia-xconfig, blacklist nouveau, install acpi, remove nouveau, sudo update-initramfs -u but got black screen

no idea whats is the problem and how to solve it.

here my nvidia config:
[http://pastebin.ubuntu.com/7516466/](http://pastebin.ubuntu.com/7516466/)

Thx. soo much in advance for help :) im dont have any idea whats is the problem.

---

### Post by Euphoria on 2014-05-26
Hi again,

after search a lot, im find the answer: Nvidia drivers not work with EFI boot :( (here where im find the info [https://wiki.archlinux.org/index.php/MacBook_Pro_7,1#Nvidia](https://wiki.archlinux.org/index.php/MacBook_Pro_7,1#Nvidia))

now im made a clean install of macos with custom partition:
1 partition: 60gb (for MacOS)
2 partition: 2gb (for swap)
3 partition: 60gb (for /)

the idea is install macos, install refind in macos, install ubuntu with swap and / and not install grub bootloader. refresh refind and use ir for start linux or macOS.

Is this the right step? with this step are linux in bios mode? 

Thx. in advance.

Euphoria.

---

### Post by este.el.paz on 2014-05-29
> **Euphoria said:**
> Hi again,

after search a lot, im find the answer: Nvidia drivers not work with EFI boot :( (here where im find the info [https://wiki.archlinux.org/index.php/MacBook_Pro_7,1#Nvidia](https://wiki.archlinux.org/index.php/MacBook_Pro_7,1#Nvidia))

now im made a clean install of macos with custom partition:
1 partition: 60gb (for MacOS)
2 partition: 2gb (for swap)
3 partition: 60gb (for /)

the idea is install macos, install refind in macos, install ubuntu with swap and / and not install grub bootloader. refresh refind and use ir for start linux or macOS.

Is this the right step? with this step are linux in bios mode? 

Thx. in advance.

Euphoria.

@Euphoria:

I'm running a triple boot MBPro, but I used the "Additional Drivers" GUI app to select the "recommended" nVidia driver . . . after the install, and rebooting back into the ubuntu desktop--if you did that was the screen working?  I'm not sure if the Archlinux nVidia data is compatible with ubuntu.  If you use the GUI app it shows whether the particular number of the nVidia driver is "recommended" and shows other options that you could try--it's easier.

 But, yeah, probably a better idea to install OSX, then rEFInd, then install the ubuntu flavor . . . I did set up a GRUB partition, so I can't say whether or not you could boot ubuntu right from rEFInd without GRUB.  But, with it, when I reboot the computer holding down the option key and the OSX Boot Manager opens, it shows a disk as "Windows" but it's the Linux system, when I select it the GRUB window opens and then we go to the splash . . . it just adds a bit of time, probably easier to have the 10MB "bios_grub" partition set up before the install, than to waste time installing without it and then find out it's not booting up . . . .  And swap should be about 1.5 x RAM . . . ???

e.e.p.

---

