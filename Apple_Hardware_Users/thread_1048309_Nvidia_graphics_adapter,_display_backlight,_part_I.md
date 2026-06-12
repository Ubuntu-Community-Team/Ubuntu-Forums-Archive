---
title: "Nvidia graphics adapter, display backlight, part II"
date: 2009-01-23
forum: Apple Hardware Users
---

### Post by _mario_ on 2009-01-23
Hi all,

as reported in the [preceding thread]("http://ubuntuforums.org/showthread.php?t=977558"), NvClock is also able to change the display backlight by driving the chip's smartdimmer directly. After my recent examination, I found some time to have a closer look at NvClock and put it into a separate driver.

The new approach offers some advantages over mbp_nvidia_bl:
[LIST=1]
[*]More fine-grained brightness control: The chip supports 1024 levels.
[*]Lower minimum brightness, allowing to save power at night.
[*]Should work on the problematic machines (MacBook 5, MacBook Air 2) as well.
[/LIST]

Please give it a try and report whether it works. To do so, install nvidia-bl-dkms from the Mactel-PPA, replace the line for mbp_nvidia_bl in /etc/modules with
```
nvidia_bl shift=2
```
and reboot. Do not load both nvidia_bl and mbp_nvidia_bl.

Please note: The 'shift' parameter is necessary because some userland tools (either hal or g-p-m) seem to not play well with more than 256 levels. This parameter shifts all values by 2 bit, effectively reducing the valid range from 1024 to 256 levels for now.

After rebooting, the command
```
lshal -u /org/freedesktop/Hal/devices/computer_backlight
```
should output:
```
udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.capabilities = {'laptop_panel'} (string list)
  info.category = 'laptop_panel'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.LaptopPanel'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic Backlight Device'  (string)
  info.subsystem = 'backlight'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_backlight'  (string)
  laptop_panel.access_method = 'general'  (string)
  laptop_panel.num_levels = 256  (0x100)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'backlight'  (string)
  linux.sysfs_path = '/sys/devices/virtual/backlight/nvidia_backlight'  (string)
  org.freedesktop.Hal.Device.LaptopPanel.method_argnames = {'brightness_value', ''} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_execpaths = {'hal-system-lcd-set-brightness', 'hal-system-lcd-get-brightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_names = {'SetBrightness', 'GetBrightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_signatures = {'i', ''} (string list)

```

And you should be able to adjust brightness by running
```
echo 100 | sudo tee /sys/class/backlight/nvidia_backlight/brightness

```
as well as using the function keys.

**MacBook 5, MacBook Air 2 users**: Does it work using Nvidia's proprietary driver?

**MacBook Pro 5 users**: Since your machines incorporate 2 graphics chips, I, honestly, don't know which one to drive. I chose the first one. Does it work at all?

ciao,
Mario

---

### Post by hyperboloid on 2009-01-23
Hi Mario!

It works on a MBP 4,1.

Thanks for the good work.

---

### Post by ercoppa on 2009-01-23
On MacBook 5,1 && Nvidia driver it works (also F2/F3) :)
No problem with suspend to ram (it restores correctly the brightness).

Some issues:
- if "Use a ambient light to adjust LCD brightness"is set in gnome power manager, the brightness goes to 100% randomly.
- if "Dim display when idle" is set, when you resume after idle status (for example with a trackpad gesture or button pressing) the brightness goes more high that before idling.

> ercoppa@ercoppa-laptop:~$ lshal -u /org/freedesktop/Hal/devices/computer_backlight
udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.capabilities = {'laptop_panel'} (string list)
  info.category = 'laptop_panel'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.LaptopPanel'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic Backlight Device'  (string)
  info.subsystem = 'backlight'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_backlight'  (string)
  laptop_panel.access_method = 'general'  (string)
  laptop_panel.num_levels = 256  (0x100)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'backlight'  (string)
  linux.sysfs_path = '/sys/devices/virtual/backlight/nvidia_backlight'  (string)
  org.freedesktop.Hal.Device.LaptopPanel.method_argnames = {'brightness_value', ''} (string list)
  org.freedesktop.Hal.lsDevice.LaptopPanel.method_execpaths = {'hal-system-lcd-set-brightness', 'hal-system-lcd-get-brightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_names = {'SetBrightness', 'GetBrightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_signatures = {'i', ''} (string list)


**EDIT:** Ehm, in my output I have only 256 levels (/etc/module has the shift=2 param for nvidia_bl)

Greets, ercoppa.

P.s. @Mario: thanks for your work.
P.P.s It works also under KDE 4.2 RC & battery widget (that have a bar to control brightness like as brightness applet)

---

### Post by alexmurray on 2009-01-24
Just installed on MBP 5,1 and it doesn't seem to work, lshal reports correctly:

```
lshal -u /org/freedesktop/Hal/devices/computer_backlight
udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.capabilities = {'laptop_panel'} (string list)
  info.category = 'laptop_panel'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.LaptopPanel'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic Backlight Device'  (string)
  info.subsystem = 'backlight'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_backlight'  (string)
  laptop_panel.access_method = 'general'  (string)
  laptop_panel.num_levels = 256  (0x100)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'backlight'  (string)
  linux.sysfs_path = '/sys/devices/virtual/backlight/nvidia_backlight'  (string)
  org.freedesktop.Hal.Device.LaptopPanel.method_argnames = {'brightness_value', ''} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_execpaths = {'hal-system-lcd-set-brightness', 'hal-system-lcd-get-brightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_names = {'SetBrightness', 'GetBrightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_signatures = {'i', ''} (string list)

```

But when pressing brightness keys it doesnt't change the brightness and doing

```
echo 1 | sudo tee /sys/class/backlight/nvidia_backlight/brightness

```

doesn't have any effect either.

It correctly detects the 9600M GT:
```

[   17.825672] nvidia_bl: Supported Nvidia graphics 10de:0647 detected

```

So am reverting back to mbp_nvidia_bl for now. Let me know if I can do any more debugging for you.

---

### Post by buntuLo on 2009-01-25
hi everybody, first of all thanks for the great work you have been doing here with the new apple hardware. i've been reading these pages since a few months, and put my hands on a MBP5.1 two weeks ago. kubuntu user since two years, i immediately installed kubuntu 8.10 it on my first apple machine. and thanks to the great documentation on the forum, now also well organised in the help pages, i was able to get most things working. i'm obviously still working on a few kinks, one of them being the media keys.
sorry for my introduction in your tech post, Mario, but here i'm back to your alternative nvidia module.

i ran both the nvidia-glx-177 and now nvidia-glx-180 proprietary drivers with all kernel modules from mactel/ppa. with the mbp_nvidia_bl module loaded, in the kde4 guidance power manager, the sliders for display brightness pop-up and do work.
moreover the keyboard backlight can be controlled with the echo command, thanks to the hal-applesmc module (if any other kde-user confirms this, it can be corrected in the mactel wiki page).
i just didn't get the media keys to control these settings. in fact even eject does not work, the only ones working are volume up/down. i'm aware that it might be related with the keyboard mapping layout, but after trying all possible combinations (including the mbp/us combination) i came back to modules.

hence i tried to install the nvidia-bl-dkms, commenting out mbp_nvidia_bl and adding nvidia_bl shift=2 in the file /etc/modules. after rebooting, the media keys (apart from volume up/down) still didn't work, and the sliders in the power manager disappeared. moreover the sensor application didn't start, complaining about missing modules, as well as the echo command to the fans would have no effect. is it a conflict with applesmc.768?
reverting the /etc/modules file and removing nvidia-bl-dkms, fixed it back. but i had to reboot four times to get back the fans spinning faster and the aluminium brick to start cooling down..

if what i did is correct, i report this module not working for me.
thanks for your time spent working on this and all other issues!
greetings, Lo.

---

### Post by _mario_ on 2009-01-25
> **alexmurray said:**
> Just installed on MBP 5,1 and it doesn't seem to work, lshal reports correctly: ...
Let me know if I can do any more debugging for you.

yes, you can. that's what i almost expected. the driver seems to drive the wrong graphics chip. please send me the output of:
```
lspci
``` as well as ```
lspci -n
```

thanks & ciao,
Mario

---

### Post by _mario_ on 2009-01-25
> **buntuLo said:**
> 
hence i tried to install the nvidia-bl-dkms, commenting out mbp_nvidia_bl and adding nvidia_bl shift=2 in the file /etc/modules. after rebooting, the media keys (apart from volume up/down) still didn't work, and the sliders in the power manager disappeared. moreover the sensor application didn't start, complaining about missing modules, as well as the echo command to the fans would have no effect. is it a conflict with applesmc.768?

reverting the /etc/modules file and removing nvidia-bl-dkms, fixed it back. but i had to reboot four times to get back the fans spinning faster and the aluminium brick to start cooling down..

thanks for your testing. i'm not an expert for KDE. but the module is not conflicting with applesmc. i use both. what you observed is indeed very strange... right now, it doesn't work on your MBP5,1. please, use mbp_nvidia_bl for now.

regarding the function keys: do they work in KDE at all? i mean: on other machines. i'm asking because Macs aren't different in this case. what does the lshal test mentioned in my initial post output?

ciao,
Mario

---

### Post by buntuLo on 2009-01-25
Mario,
the lshal output seems correct with both modules.
with mbp_nvidia_bl loaded:
```
lo@lomac:/etc$ lshal -u /org/freedesktop/Hal/devices/computer_backlight

udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.capabilities = {'laptop_panel'} (string list)
  info.category = 'laptop_panel'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.LaptopPanel'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic Backlight Device'  (string)
  info.subsystem = 'backlight'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_backlight'  (string)
  laptop_panel.access_method = 'general'  (string)
  laptop_panel.num_levels = 16  (0x10)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'backlight'  (string)
  linux.sysfs_path = '/sys/devices/virtual/backlight/mbp_backlight'  (string)
  org.freedesktop.Hal.Device.LaptopPanel.method_argnames = {'brightness_value', ''} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_execpaths = {'hal-system-lcd-set-brightness', 'hal-system-lcd-get-brightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_names = {'SetBrightness', 'GetBrightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_signatures = {'i', ''} (stringlist)
```
with nvidia-bl-dkms loaded:
```
lo@lomac:~$ lshal -u /org/freedesktop/Hal/devices/computer_backlight

udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.capabilities = {'laptop_panel'} (string list)
  info.category = 'laptop_panel'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.LaptopPanel'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic Backlight Device'  (string)
  info.subsystem = 'backlight'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_backlight'  (string)
  laptop_panel.access_method = 'general'  (string)
  laptop_panel.num_levels = 256  (0x100)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'backlight'  (string)
  linux.sysfs_path = '/sys/devices/virtual/backlight/nvidia_backlight'  (string)
  org.freedesktop.Hal.Device.LaptopPanel.method_argnames = {'brightness_value', ''} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_execpaths = {'hal-system-lcd-set-brightness', 'hal-system-lcd-get-brightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_names = {'SetBrightness', 'GetBrightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_signatures = {'i', ''} (stringlist)
```
by the way, loaded it back to copy this output, and now fans and sensors are working properly.. weird, i'm pretty sure i didn't change anything else the previous time. moreover the brightness sliders in the power manager are there, but they have no effects.

about the function keys under kde, they all works on my old laptop running 7.10 and kde3.5, using some asus-acpi modules.
cia'cia', Lo.

---

### Post by bobcopro on 2009-01-25
This works great on my 13" MacBook (Unibody) 5.1, both the slider on the menu bar and the F1/F2 keys on the keyboard.  The instructions worked as stated.  Had a little trouble sorting out the packages to get it to work, but that was due to my inexperience with Linux.  

It appeared (brightness level) to be a little sporadic sometimes, changing brightness a little after I've set it.  It seems to happen when the ambient light sensor settings is turned on in the Gnome power management.  Although with the ambient setting on it doesn't seem to change the brightness with actual changes in the ambient light.

Thank you so much for your work on this.  I would be happy to help with updating the MacBook install instructions with this information if I'm allowed to.  So much info on the web pertaining to this is out of date (or plain wrong) and I'd be happy to help out with that so you can keep doing the important stuff, like updating actual code.  PS - if you want to work on power management and sound next I can edit whatever you'd like.  Bob

---

### Post by sterlingy on 2009-01-25
I added the mactel repository to my system, and enabled nvidia_bl_dkms, but I can't seem to get any further.

There is no nvidia line in my /etc/modlues file

I think something isn't installed properly.

Any thoughts?

-Sterling

System info:
Macbook 13" 5.1
Ubuntu 8.10

---

### Post by buntuLo on 2009-01-25
> **sterlingy said:**
> I added the mactel repository to my system, and enabled nvidia_bl_dkms, but I can't seem to get any further.
There is no nvidia line in my /etc/modules file
I think something isn't installed properly.
Any thoughts? -Sterling
 that line has to be added manually in /etc/modules, and at the same time the line
mbp_nvidia_bl
has to be removed or commented out. finally reboot the system.

---

### Post by alexmurray on 2009-01-25
lspci & lspci -n outputs on a MBP 5,1:

```

alex@alex-laptop:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 06)

```

```
alex@alex-laptop:~$ lspci -n
00:00.0 0600: 10de:0a82 (rev b1)
00:00.1 0500: 10de:0a88 (rev b1)
00:03.0 0601: 10de:0aae (rev b2)
00:03.1 0500: 10de:0aa4 (rev b1)
00:03.2 0c05: 10de:0aa2 (rev b1)
00:03.3 0500: 10de:0a89 (rev b1)
00:03.4 0500: 10de:0a98 (rev b1)
00:03.5 0b40: 10de:0aa3 (rev b1)
00:04.0 0c03: 10de:0aa5 (rev b1)
00:04.1 0c03: 10de:0aa6 (rev b1)
00:06.0 0c03: 10de:0aa7 (rev b1)
00:06.1 0c03: 10de:0aa9 (rev b1)
00:08.0 0403: 10de:0ac0 (rev b1)
00:09.0 0604: 10de:0aab (rev b1)
00:0a.0 0200: 10de:0ab0 (rev b1)
00:0b.0 0101: 10de:0ab5 (rev b1)
00:0c.0 0604: 10de:0ac4 (rev b1)
00:15.0 0604: 10de:0ac6 (rev b1)
00:16.0 0604: 10de:0ac7 (rev b1)
00:17.0 0604: 10de:0ac7 (rev b1)
02:00.0 0300: 10de:0647 (rev a1)
04:00.0 0280: 14e4:432b (rev 01)
05:00.0 0c00: 11c1:5901 (rev 06)

```

---

### Post by _mario_ on 2009-01-26
> **alexmurray said:**
> lspci & lspci -n outputs on a MBP 5,1: ...

that's interesting. according to your output, there's only one graphics adapter listed (9600M GT). where's the 9400M? i initially thought i drove the wrong adapter. but no it's the 9600M GT. maybe Apple does something different on the MBP5,1.

btw: does NvClock work on your machine? the CVS version? you can check it out and compile like this:
```
cvs -z3 -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock co -P nvclock
cd nvclock
configure
make

```
(you might need some additional development packages/tools.)

thanks & ciao,
Mario

---

### Post by _mario_ on 2009-01-26
> **buntuLo said:**
> ... moreover the brightness sliders in the power manager are there, but they have no effects.

that means it did detect the hal interface, but unfortunately the driver doesn't seem to work on the MBP5,1. see the conversation with alexmurray. and if you can, it would be nice to follow the steps described there to trace down the problem.

> **buntuLo said:**
> about the function keys under kde, they all works on my old laptop running 7.10 and kde3.5, using some asus-acpi modules.
cia'cia', Lo.

KDE4 is different from KDE3, but, nevertheless, it should at least react upon the media player and volume keys, because they are available on other machines as well.

ciao,
Mario

---

### Post by buntuLo on 2009-01-26
all the following output is obtained on a mbp5.1 running the nvidia-bl-dkms module instead of the mbp_bvidia_bl one.
here's the output of lspci and lspci -n:
```
lo@lomac:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 06)

lo@lomac:~$ lspci -n
00:00.0 0600: 10de:0a82 (rev b1)
00:00.1 0500: 10de:0a88 (rev b1)
00:03.0 0601: 10de:0aae (rev b2)
00:03.1 0500: 10de:0aa4 (rev b1)
00:03.2 0c05: 10de:0aa2 (rev b1)
00:03.3 0500: 10de:0a89 (rev b1)
00:03.4 0500: 10de:0a98 (rev b1)
00:03.5 0b40: 10de:0aa3 (rev b1)
00:04.0 0c03: 10de:0aa5 (rev b1)
00:04.1 0c03: 10de:0aa6 (rev b1)
00:06.0 0c03: 10de:0aa7 (rev b1)
00:06.1 0c03: 10de:0aa9 (rev b1)
00:08.0 0403: 10de:0ac0 (rev b1)
00:09.0 0604: 10de:0aab (rev b1)
00:0a.0 0200: 10de:0ab0 (rev b1)
00:0b.0 0101: 10de:0ab5 (rev b1)
00:0c.0 0604: 10de:0ac4 (rev b1)
00:15.0 0604: 10de:0ac6 (rev b1)
00:16.0 0604: 10de:0ac7 (rev b1)
00:17.0 0604: 10de:0ac7 (rev b1)
02:00.0 0300: 10de:0647 (rev a1)
04:00.0 0280: 14e4:432b (rev 01)
05:00.0 0c00: 11c1:5901 (rev 06)

```
i read in other posts that the choice of graphic card in macos is saved in some efi variables, and that the boot process through refit and grub doesn't allow to activate the 9400m. if it is true, it sounds very much like apple hided the possibility for other oses to build up a comparable power management on the new machines.

going on, nvclock installed from repositories doesn't recognise the card, but when forced it gives:
```
lo@lomac:~$ nvclock -T -f
Error: temperature monitoring isn't supported on your videocard.

lo@lomac:~$ nvclock -info -f
-- General info --
Card:           Unknown Nvidia card
Architecture:   G96 C1
PCI id:         0x0
GPU clock:      -2147483.750 MHz
Bustype:        PCI
-- Memory info --
Amount:         256 MB
Type:           64 bit SDR
Clock:          -2147483.750 MHz
```
the gui 'nvidia x-server settings' works properly, it now shows a reasonable gpu core temp of 55 deg C (both fans at 4000 rpm).
'sensors' works too, and i report that for the mbp5.1 'temp8' corresponds to the 9600mgt gpu core.

unluckily i didn't manage to compile the cvs version of nvclock:
```
lo@lomac:~/nvclock$ sudo apt-get remove nvclock
lo@lomac:~/nvclock$ sudo apt-get install cvs
lo@lomac:~/nvclock$ cvs -z3 -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock co -P nvclock
lo@lomac:~/nvclock$ sudo apt-get install pkg-config
lo@lomac:~/nvclock$ ./configure
(...)
checking for x11... configure: error: "X11 required for nvcontrol support"
```
tried to look for a X11 dev package, can't figure out which one.

about the function keys, i was actually wrong: the media player controls do work (in amarok), together with volume up/down. the ones not working are: display brightness up/down, keyboard backlight up/down, volume mute, eject cd.

one more note: every time apt-get finishes installing nvidia-bl-dkms, kmix (kde audio mixer) crashes and restarts.
ciaa', Lo.

---

### Post by ercoppa on 2009-01-26
> checking for x11... configure: error: "X11 required for nvcontrol support"
Try with:
```
./configure --disable-nvcontrol
```

Greets, ercoppa.

---

### Post by buntuLo on 2009-01-26
thanks Ercoppa, that did it. i didn't pay attention about the 'macbook aluminium' page being updated, and not the 'macbook5-1/intrepid' one (which i thought was a replacement).
anyhow, the cvs version of nvclock does detect properly the card, but nvclock -S does not change the brightness for me.
the power manager sliders do not work, nor the echo command does.
cia'cia', Lo.

---

### Post by cyberdork33 on 2009-01-26
> **buntuLo said:**
> i didn't pay attention about the 'macbook aluminium' page being updated, and not the 'macbook5-1/intrepid' one (which i thought was a replacement).
It is... You should not be using or updating the old "Macbook Aliuminum" Page.

---

### Post by buntuLo on 2009-01-27
ooh ok, i said this cause the instructions for installing nvclock from cvs are only on the old aluminium page. if this trick works for many people (even if not for me), shall we add it to the new doc page?
ciao, Lo.

---

### Post by cyberdork33 on 2009-01-27
> **buntuLo said:**
> shall we add it to the new doc page?
Yes, please, and any further new information.

If you could please compare the two pages and migrate anything else of interest to the newer page would could then replace the old page with a redirect to the new page.

---

### Post by cyberdork33 on 2009-01-27
dbl posted...

---

### Post by ercoppa on 2009-01-27
> if this trick works for many people (even if not for me), shall we add it to the new doc page?
I think that NvClock and his doc it's not need in the new page because:
- if you have MacBook 5,1 --> nvidia_bl works better of NvClock
- if you have MacBook PRO 5,1 --> mbp_nvidia_bl (and nvidia_bl in the future) works better of NvClock

Am I in wrong?

P.s. I update the "MacBook5-1/Intrepid" with all info (some sections must be re-write in the future days) for the MacBook 5,1 (not Pro, because the correct page for it is "MacBookPro5-1/Intrepid").

Greets, ercoppa.

---

### Post by cyberdork33 on 2009-01-27
> **ercoppa said:**
>  I update the "MacBook5-1/Intrepid" with all info (some sections must be re-write in the future days) for the MacBook 5,1 (not Pro, because the correct page for it is "MacBookPro5-1/Intrepid").Great
Yep, the MBP5,1 page is here:
[https://help.ubuntu.com/community/MacBookPro5-1/Intrepid](https://help.ubuntu.com/community/MacBookPro5-1/Intrepid)
not much there yet as the MBP got overlooked for some reason when all this work started.

---

### Post by buntuLo on 2009-01-28
> **ercoppa said:**
> I think that NvClock and his doc it's not need in the new page because:
- if you have MacBook 5,1 --> nvidia_bl works better of NvClock
- if you have MacBook PRO 5,1 --> mbp_nvidia_bl (and nvidia_bl in the future) works better of NvClock
Am I in wrong?
P.s. I update the "MacBook5-1/Intrepid" with all info (some sections must be re-write in the future days) for the MacBook 5,1 (not Pro, because the correct page for it is "MacBookPro5-1/Intrepid").
Greets, ercoppa.

Ercoppa, thanks for taking care of the MB5.1/intrepid page, i don't feel really confident in writing about a machine i do not own and cannot test.
indeed, nvclock does not work for me. and if MB5.1 owners are not using it (thanks to the latest developments of nvidia-bl-dkms), it definitely should not go on the doc page.
i will take care of filling up the MBP5.1/intrepid page instead, just give me a couple of days to finish some work and i'll be back to it.
greetings to all, Lo.

---

### Post by _mario_ on 2009-01-28
> **buntuLo said:**
> 
anyhow, the cvs version of nvclock does detect properly the card, but nvclock -S does not change the brightness for me.
the power manager sliders do not work, nor the echo command does.
cia'cia', Lo.

sorry. my fault. i should have posted more comprehensive instructions. i was short on time this day. thanks for your effort.

however, if nvclock -S does not work, we have a serious problem. that means either Apple didn't connect the chips' smartdimmer signals to the display logic (maybe due to the second graphics adapter) and uses a different mechanism not yet discovered, or the registers have been moved (once again), which isn't very likely, though. that's not very satisfying ...

ciao,
Mario

---

### Post by warrenc5 on 2011-05-15
Here is a script which use the web-camera to "measure" the lux (candela/luminescence) and then set the screen brightness automatically. Thanks again for the module, and please enjoy.

---

