---
title: "Canon camera detected in Xubuntu Gutsy but won't automount"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by yosenut on 2008-03-10
Hello. I have read all the similar threads here (and elsewhere) to try to fix my problem, I but have been as yet unable. I'd appreciate any crumbs of help.

I am new to Ubuntu (and Linux) and my Dell 2650 laptop now sees my Canon S70 camera according to the CLI of gphoto2, but I can't get it to automount after hotplugging. 

Output of $ tail /var/log/messages is

Mar  9 16:23:41 MicrobialUnit kernel: [18262.668000] usb 1-1: USB disconnect, address 6

Mar  9 16:32:42 MicrobialUnit kernel: [18803.980000] ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]

Mar  9 16:32:42 MicrobialUnit kernel: [18803.980000] ACPI Exception (dswexec-0462): AE_TIME, While resolving operands for [OpcodeName unavailable] [20070126]

Mar  9 16:32:42 MicrobialUnit kernel: [18803.980000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.LPCB.BAT1._BST] (Node d606fae0), AE_TIME

Mar  9 16:32:42 MicrobialUnit kernel: [18803.980000] ACPI Exception (battery-0206): AE_TIME, Evaluating _BST [20070126]

Mar  9 16:39:15 MicrobialUnit kernel: [19196.788000] usb 1-1: new full speed USB device using uhci_hcd and address 7

Mar  9 16:39:15 MicrobialUnit kernel: [19196.952000] usb 1-1: configuration #1 chosen from 1 choice

Mar  9 16:40:02 MicrobialUnit kernel: [19244.432000] usb 1-1: USB disconnect, address 7

Mar  9 16:42:16 MicrobialUnit kernel: [19378.156000] usb 1-1: new full speed USB device using uhci_hcd and address 8

Mar  9 16:42:16 MicrobialUnit kernel: [19378.320000] usb 1-1: configuration #1 chosen from 1 choice



Lots of errors there.


Then,  I get $ lsusb:

Bus 002 Device 002: ID 045e:0053 Microsoft Corp.

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 007: ID 04a9:30b1 Canon, Inc.

Bus 001 Device 001: ID 0000:0000  


and


$ sudo fdisk -l:

Disk /dev/sda: 30.0 GB, 30005821440 bytes

255 heads, 63 sectors/track, 3648 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x41172ba5

  Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        3507    28169946   83  Linux

/dev/sda2            3508        3648     1132582+   5  Extended

/dev/sda5            3508        3648     1132551   82  Linux swap / Solaris


I know it sees my camera and 1GB CF card because I get:

$ gphoto2 --summary

Loading camera drivers from '/usr/l... |                     \   0.0%    Loading camera drivers from '/usr/l... |                     |   1.8%    Loading camera drivers from '/usr/l... |-                    /   3.5%    Loading camera drivers from '/usr/l... |-                    -   5.3%    Loading camera drivers from '/usr/l... |-                    \   7.0%    Loading camera drivers from '/usr/l... |--                   |   8.8%    Loading camera drivers from '/usr/l... |--                   /  10.5%    Loading camera drivers from '/usr/l... |---                  -  12.3%    Loading camera drivers from '/usr/l... |---                  \  14.0%    Loading camera drivers from '/usr/l... |---                  |  15.8%    Loading camera drivers from '/usr/l... |----                 /  17.5%    Loading camera drivers from '/usr/l... |----                 -  19.3%    Loading camera drivers from '/usr/l... |----                 \  21.1%    Loading camera drivers from '/usr/l... |-----                |  22.8%    Loading camera drivers from '/usr/l... |-----                /  24.6%    Loading camera drivers from '/usr/l... |------               -  26.3%    Loading camera drivers from '/usr/l... |------               \  28.1%    Loading camera drivers from '/usr/l... |------               |  29.8%    Loading camera drivers from '/usr/l... |-------              /  31.6%    Loading camera drivers from '/usr/l... |-------              -  33.3%    Loading camera drivers from '/usr/l... |-------              \  35.1%    Loading camera drivers from '/usr/l... |--------             |  36.8%    Loading camera drivers from '/usr/l... |--------             /  38.6%    Loading camera drivers from '/usr/l... |--------             -  40.4%    Loading camera drivers from '/usr/l... |---------            \  42.1%    Loading camera drivers from '/usr/l... |---------         Make sure that your sda1 folder appears in the /mnt/ folder in root.   |  43.9%    Loading camera drivers from '/usr/l... |----------           /  45.6%    Loading camera drivers from '/usr/l... |----------           -  47.4%    Loading camera drivers from '/usr/l... |----------           \  49.1%    Loading camera drivers from '/usr/l... |-----------          |  50.9%    Loading camera drivers from '/usr/l... |-----------          /  52.6%    Loading camera drivers from '/usr/l... |-----------          -  54.4%    Loading camera drivers from '/usr/l... |------------         \  56.1%    Loading camera drivers from '/usr/l... |------------         |  57.9%    Loading camera drivers from '/usr/l... |-------------        /  59.6%    Loading camera drivers from '/usr/l... |-------------        -  61.4%    Loading camera drivers from '/usr/l... |-------------        \  63.2%    Loading camera drivers from '/usr/l... |--------------       |  64.9%    Loading camera drivers from '/usr/l... |--------------       /  66.7%    Loading camera drivers from '/usr/l... |--------------       -  68.4%    Loading camera drivers from '/usr/l... |---------------      \  70.2%    Loading camera drivers from '/usr/l... |---------------      |  71.9%    Loading camera drivers from '/usr/l... |---------------      /  73.7%    Loading camera drivers from '/usr/l... |----------------     -  75.4%    Loading camera drivers from '/usr/l... |----------------     \  77.2%    Loading camera drivers from '/usr/l... |-----------------    |  78.9%    Loading camera drivers from '/usr/l... |-----------------    /  80.7%    Loading camera drivers from '/usr/l... |-----------------    -  82.5%    Loading camera drivers from '/usr/l... |------------------   \  84.2%    Loading camera drivers from '/usr/l... |------------------   |  86.0%    Loading camera drivers from '/usr/l... |------------------   /  87.7%    Loading camera drivers from '/usr/l... |-------------------  -  89.5%    Loading camera drivers from '/usr/l... |-------------------  \  91.2%    Loading camera drivers from '/usr/l... |-------------------- |  93.0%    Loading camera drivers from '/usr/l... |-------------------- /  94.7%    Loading camera drivers from '/usr/l... |-------------------- -  96.5%    Loading camera drivers from '/usr/l... |---------------------|  98.2%                                                                             D

Detected a 'Canon:PowerShot S70 (normal mode)'.

Camera summary:

Camera identification:

 Model: Canon:PowerShot S70 (normal mode)

 Owner:

Power status: on battery (power OK)

Flash disk information:

 Drive D:

     999'632 bytes total

     641'168 bytes available

Time: 2008-03-09 17:00:35 (host time +0 seconds)




My USB drive (only 1.1) is fine because it automatically recognized both my Microsoft mouse and a pendrive. Besides, in its previous life under XP, this drive saw this camera/pics just fine. The camera was on and in review mode for all the above commands.

Do I need to give a mounting command, and if so, what is my camera called? Are the permissions wrong (I don't know how to go into the root directory yet)?

I agree that no love is lost between Canon and the Linux community and I've given up on my Canon printer, but I need my camera to work to keep Xubuntu. Thank you for any suggestions!

---

### Post by philinux on 2008-03-10
Try running Gthumb or Gimp. Then plug the camera in.

---

### Post by red_Marvin on 2008-03-10
I don't know about the S70 but on my camera (350d) there are two communication modes, print ptp and computer connection, and I remember having problems with communication using one of those. If you have such a setting on your camera you could try changing it to the other.

---

### Post by yosenut on 2008-03-10
Hi philinux,

Thank you for responding to me! 

This is why I am an "Absolute Beginner." I have launched each of those programs, but neither one sees my camera or images. (When I go to "Add camera," there are no default choices and when I when I pick the S70 from a list, nothing happens after that.)

I'm sure I'm doing something stupid.

---

### Post by philinux on 2008-03-10
I'm on Ubuntu not Xubuntu. Find the equivalent of System>Preferences>**Removable Drives and Media.**

On my setup there's a camera tab and also what actions to take when hotplugged.

---

### Post by yosenut on 2008-03-10
red_marvin, that is a good point. Thank you for the tip. I looked into it and found that oh-so-great Canon doesn't support my RAW files getting downloaded in PTP, so since I shoot mostly RAW, I'd probably have to find a workaround.

philinux, I also appreciate your great idea. I went to Xubuntu's equivalent for removable drives/devices and checked the box "Import digital photos when connected." In the Command box, I put gtkam usb:/
Now, when I hotplug my camera, it turns on (as it had been doing), and gtkam launches. In the left menu, the Canon appears, but I also get an error message "Could not list folders in '/'." (Gimp didn't do anything but launch when I put it in the command space instead and GQview didn't even launch with the same treatment.)

So strange because CLI list all my files by name when I query them using gphoto2 --list-files (it is a supported camera).

Argghh. Getting there, thanks to you.

---

### Post by yosenut on 2008-03-11
I tried more troubleshooting. I then realized that gthumb was not the program I had installed. When I did, I could open it while the camera was connected and access all my photos. I'm still looking for a RAW solution, but am excited that I can now get my jpgs.

Thank you, philinux! Your help was invaluable!

---

### Post by crjackson on 2008-03-11
> **yosenut said:**
> I tried more troubleshooting. I then realized that gthumb was not the program I had installed. When I did, I could open it while the camera was connected and access all my photos. I'm still looking for a RAW solution, but am excited that I can now get my jpgs.

Thank you, philinux! Your help was invaluable!

[[SIZE="4"]**_RawStudio_**[/SIZE]]("http://www.getdeb.net/download/2009/0") should solve your problem.

---

