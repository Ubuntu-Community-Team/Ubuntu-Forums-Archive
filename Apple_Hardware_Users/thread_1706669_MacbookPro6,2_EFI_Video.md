---
title: "MacbookPro6,2 EFI Video"
date: 2011-03-14
forum: Apple Hardware Users
---

### Post by dgoodlad on 2011-03-14
Hi all

I've got a completely EFI-only installation of Natty in my MacBookPro6,2. I'm having trouble getting any video driver for X to load (intel, nouveau, nvidia proprietary). Here's a bit of background on what I've got setup:

I use rEFIt to boot grub2 (1.99~rc1) from /EFI/grub2/grub.efi on the EFI system partition. I dumped my video bios and the int10 vector while booted into bios mode, and load them using `loadbios` in my grub.cfg. My grub.cfg looks like this:

```
set debug=video
set pager=1

set timeout=20
default 0

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

insmod efi_gop
search --set -f /vmlinuz

menuentry "Natty (with vbios dump)" {
  loadbios /boot/vbios.bin /boot/int10.bin
  linux /boot/vmlinuz-2.6.38-6-generic root=/dev/sdb3 video=efifb quiet splash --
  initrd /boot/initrd.img-2.6.38-6-generic
}
menuentry "Natty (with video fix and vbios dump)" {
  fix_video
  loadbios /boot/vbios.bin /boot/int10.bin
  linux /boot/vmlinuz-2.6.38-6-generic root=/dev/sdb3 video=efifb quiet splash --
  initrd /boot/initrd.img-2.6.38-6-generic
}
menuentry "Natty (fakebios)" {
  fakebios
  linux /boot/vmlinuz-2.6.38-6-generic root=/dev/sdb3 video=efifb quiet splash --
  initrd /boot/initrd.img-2.6.38-6-generic
}

```

The kernel is built from the latest ubuntu kernel sources, with the addition of the 'EFI in physical mode' patch from [https://patchwork.kernel.org/patch/119823/](https://patchwork.kernel.org/patch/119823/) which allows me to boot without the 'noefi' kernel option.

A small note: dmesg reports the intel kernel module complaining that it is disabling 'turbo graphics' because it "can't find i915 symbols". (sorry, I haven't got an exact copy of the kernel messages)

Once I've booted to a text console, I can kill off gdm and try different configurations in xorg.conf. Trying the "intel" and "nouveau" drivers results in X complaining that it can't find any devices. The intel one throws a warning that it can't setup a pixmap for fbdev, while nouveau just doesn't find anything. If I try the nvidia module, it turns off the backlight and I get no video output whatsoever. Pressing the power button in this situation, though, does trigger an acpi power event and ubuntu shuts down normally a few seconds later.

I've tried playing with sending commands to the apple gmux from grub, based on the contents of apple_gmux.c from [http://andreas.meetr.de/gmux/apple_gmux/apple_gmux.c](http://andreas.meetr.de/gmux/apple_gmux/apple_gmux.c) . I'm definitely able to affect the display but mostly it just seems to turn off the backlight...

Has anyone else managed to get this setup going? Any further suggestions?

---

### Post by morean51 on 2011-03-14
had same problem unable to manage can anyone help out thank you in advance

---

### Post by metatechbe on 2011-03-14
> **dgoodlad said:**
> Hi all

A small note: dmesg reports the intel kernel module complaining that it is disabling 'turbo graphics' because it "can't find i915 symbols". (sorry, I haven't got an exact copy of the kernel messages)



Hi,

Did you try blacklisting "i915" and "intel_agp" as suggested here ?
[http://ubuntuforums.org/showpost.php?p=10446118&postcount=10](http://ubuntuforums.org/showpost.php?p=10446118&postcount=10)
Did you try without the BIOS dump ?

metatech

---

### Post by dgoodlad on 2011-03-14
> **metatechbe said:**
> Did you try blacklisting "i915" and "intel_agp" as suggested here ?
[http://ubuntuforums.org/showpost.php?p=10446118&postcount=10](http://ubuntuforums.org/showpost.php?p=10446118&postcount=10)

I haven't, no, and I will try that later today.

> **metatechbe said:**
> Did you try without the BIOS dump? 

Yes, most of my initial testing was done using grub's fakebios, and I wasn't able to get X to start at all.

Last night I managed to find a way to get nouveau to work properly. By removing (or alternatively, I'm sure, by blacklisting) the proprietary nvidia driver, nouveau took over and was able to start X properly. Installing the experimental 3d support even works! The only thing that isn't working is dual-head; I can't get nouveau to see the monitor that I attach via MiniDP-to-DP.

Once I've got things in a more 'settled' state, I'll write about my whole setup and include config files, etc.

---

### Post by metatechbe on 2011-03-15
> **dgoodlad said:**
> 
Last night I managed to find a way to get nouveau to work properly. 

Great !
> 
Once I've got things in a more 'settled' state, I'll write about my whole setup and include config files, etc.

Yes, please share your magic trick.
Can you already tell us to which temperature your machine is operating ?

Thanks.

metatech

---

### Post by dgoodlad on 2011-03-15
> **metatechbe said:**
> Yes, please share your magic trick.

Here's my grub.cfg:

```
set debug=video
set pager=1

set timeout=20
default 0

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

insmod efi_gop

# Semi-randomly the Apple SD card reader is detected before the 
# SATA controller, so make sure to use UUIDs instead of device
# paths
search --no-floppy --fs-uuid --set 24ab6963-c923-4cf4-98ad-1a69747bf65c

# This is what I use normally
menuentry "Natty (nvidia display)" {
  # Load the dumped video bios and int10 vectors
  loadbios /boot/vbios.bin /boot/int10.bin
  # Load the kernel like natty would normally. The interesting
  # kernel parameters are:
  # i915.modeset=0
  #   stops the intel i915 driver from trying to set the framebuffer
  #   mode, which would blank the internal display
  # video=nouveau
  #   not absolutely necessary, but a good hint to the kernel that
  #   it should replace the efifb with nouveau's fb driver
  linux	/boot/vmlinuz-2.6.38-6-generic root=UUID=24ab6963-c923-4cf4-98ad-1a69747bf65c ro crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7 i915.modeset=0 video=nouveau --
  initrd /boot/initrd.img-2.6.38-6-generic
}

# For testing the Intel IGP instead of the discrete card. Does not
# work for the internal display at the moment, but DOES successfully
# drive an external monitor connected via MiniDP-DVI adapter
menuentry "Natty (Intel display)" {
  # Switch display and DDC to internal card
  outb 0x728 1
  outb 0x710 2
  outb 0x740 2
  # Power down discrete controller
  outb 0x750 0
  # Load the video bios and int10 vector dumps
  loadbios /boot/vbios.bin /boot/int10.bin
  # Load the kernel, as before. This time, allow i915 to set the fb mode
  linux	/boot/vmlinuz-2.6.38-6-generic root=UUID=24ab6963-c923-4cf4-98ad-1a69747bf65c ro crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7 i915.modeset=1 --
  initrd /boot/initrd.img-2.6.38-6-generic
}
```

I have to switch my xorg.conf depending on which of the two boot options I use. In the nvidia case:

```
Section "Device"
  Identifier "Device0"
  Driver "nouveau"
  BusID "1:0:0"
EndSection
```

In the intel case:

```
Section "Device"
  Identifier "Device0"
  Driver "intel"
  BusID "0:2:0"
EndSection
```

I do NOT have the proprietary nvidia driver installed:

```
aptitude remove nvidia-current
```

I do have the experimental gallium 3d support for nouveau installed:

```
aptitude install libgl1-mesa-dri-experimental
```

Also, remember that I'm using a 2.6.38-6 kernel patched with the 'EFI in physical mode' patch (see my first post for a link).

> **metatechbe said:**
> Can you already tell us to which temperature your machine is operating ?

```
~ $ cat /sys/devices/platform/coretemp.0/temp1_input
50000
~ $ cat /sys/devices/platform/coretemp.2/temp1_input
54000
```

Looks like about 50 degrees C. This is with the nvidia card running, and no heavy processor usage.

I hope to solve the issues with the internal display when using the intel card soon, but need to get some real work done :) Let me know how you go!

---

### Post by metatechbe on 2011-03-16
> **dgoodlad said:**
> 
```
Section "Device"
  Identifier "Device0"
  Driver "intel"
  BusID "0:2:0"
EndSection
```

Are you sure the BusID is 0:2:0 ?  I thought other users reported 2:0:0.

> **dgoodlad said:**
> Also, remember that I'm using a 2.6.38-6 kernel patched with the 'EFI in physical mode' patch (see my first post for a link).


For the troubleshooting guide, which problem or error message do you see when you do not install this patch ?

> **dgoodlad said:**
> 
Looks like about 50 degrees C. This is with the nvidia card running, and no heavy processor usage.


That already sounds reasonable.  I suppose the temperature is even lower with the Intel graphics ?

Thanks,

metatech

---

### Post by dgoodlad on 2011-03-16
> **metatechbe said:**
> Are you sure the BusID is 0:2:0 ?  I thought other users reported 2:0:0.

Yes, 100% sure. I've seen references to 2:0:0 for other models too, but everything I can see on my machine says the Intel chip is at 0:2:0 (lspci, efi console, kernel logs, etc).

> **metatechbe said:**
> For the troubleshooting guide, which problem or error message do you see when you do not install this patch ?

Without the patch, the machine will hard-lock before showing any kernel log output on the console. You can get around this by passing the 'noefi' parameter (which is how I got the Ubuntu install disc to boot properly, since it uses a vanilla kernel). However, 'noefi' breaks brightness control, among other things.

> **metatechbe said:**
> I suppose the temperature is even lower with the Intel graphics ?

I actually haven't checked, but would assume that to be the case. Once I get the internal display working with the Intel card, I'll measure the effect on both temperature and power consumption.

I thought about adding this info to the wiki, but within the standard template there didn't seem to be a good place to put it. It sounds like you're putting something together (you mentioned a troubleshooting guide)...?

Cheers
Dave

---

### Post by metatechbe on 2011-03-16
> **dgoodlad said:**
> Yes, 100% sure. I've seen references to 2:0:0 for other models too, but everything I can see on my machine says the Intel chip is at 0:2:0 (lspci, efi console, kernel logs, etc).

Can you try to not specify the BusID in xorg.conf ? I think it should only be necessary to specify it when 2 graphics cards of the same brand are present in the machine, which is only the case for MacBookPro5,x.  This would simplify the configuration for other models.

> **dgoodlad said:**
> 
I thought about adding this info to the wiki, but within the standard template there didn't seem to be a good place to put it. It sounds like you're putting something together (you mentioned a troubleshooting guide)…?


The troubleshooting guide is here :
[http://grub.enbug.org/TestingOnMacbook#preview](http://grub.enbug.org/TestingOnMacbook#preview)

Thanks.

metatech

---

### Post by metatechbe on 2011-03-22
> **dgoodlad said:**
> 
I hope to solve the issues with the internal display when using the intel card soon, but need to get some real work done :) Let me know how you go!

Please try the patch "Implement manual override of LVDS single/dual channel mode" patch described here : 
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

Thanks.
metatech

---

### Post by dgoodlad on 2011-03-22
> **metatechbe said:**
> Please try the patch "Implement manual override of LVDS single/dual channel mode" patch described here : 
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

Thanks.
metatech

Sorry, haven't posted here recently, haven't had much time for testing!

I did try that patch, and it helped. The internal display still goes blank (looks like no backlight even) as soon as the kernel loads, but wakes back up when X initialises. Interestingly enough, it will happily drive both the internal and an external display simultaneously, even though OSX forbids it. Using gfxCardStatus in OSX to force the intel graphics adapter, you can't use an external display.

EDIT: I had actually applied a different patch that performed the same function but was far more naive (it forced dual-channel no matter what, thus was not generally applicable). I'll test the patch that you linked today.

I will post here again when I've had time for more testing/hacking.

Cheers
Dave

---

### Post by metatechbe on 2011-03-23
> **dgoodlad said:**
> 
I did try that patch, and it helped. The internal display still goes blank (looks like no backlight even) as soon as the kernel loads, but wakes back up when X initialises. Interestingly enough, it will happily drive both the internal and an external display simultaneously, even though OSX forbids it. Using gfxCardStatus in OSX to force the intel graphics adapter, you can't use an external display.


It is not clear from your post : after X loads, is the machine normally usable without problems or not ? Is there only a black display during the boot process ?

If there are still problems, you can try Sidolin's other patches, [http://ubuntuforums.org/showpost.php?p=10168915&postcount=5](http://ubuntuforums.org/showpost.php?p=10168915&postcount=5), but I believe they are only needed for dynamically switching between integrated and discrete graphics.

Cheers,
metatech

---

### Post by dgoodlad on 2011-03-23
> **metatechbe said:**
> It is not clear from your post : after X loads, is the machine normally usable without problems or not ? Is there only a black display during the boot process ?

Sorry I wasn't clear :) Once X initializes, the internal display works correctly. I rebuilt my kernel with the lvds_channels patch which seems much better than the original patch that I'd used which always forced dual-channel..

> **metatechbe said:**
> If there are still problems, you can try Sidolin's other patches, [http://ubuntuforums.org/showpost.php?p=10168915&postcount=5](http://ubuntuforums.org/showpost.php?p=10168915&postcount=5), but I believe they are only needed for dynamically switching between integrated and discrete graphics.

Right, that's what I figured as well. I'm going to have a play with a kernel patched with those and the apple_gmux module when I have more time.

When booted with the intel card selected and the nvidia card powered down, though, the machine doesn't seem to come out of suspend properly. That's my next mission!

Cheers
Dave

---

### Post by metatechbe on 2011-03-24
> **dgoodlad said:**
> Sorry I wasn't clear :) Once X initializes, the internal display works correctly. I rebuilt my kernel with the lvds_channels patch which seems much better than the original patch that I'd used which always forced dual-channel..

Thanks for the good news !

> **dgoodlad said:**
> 
When booted with the intel card selected and the nvidia card powered down, though, the machine doesn't seem to come out of suspend properly. That's my next mission!


Does the graphical logout work ?

Thanks,

metatech

---

### Post by axflash on 2011-03-24
> **dgoodlad said:**
> 
When booted with the intel card selected and the nvidia card powered down, though, the machine doesn't seem to come out of suspend properly. That's my next mission!
Cheers
Dave

Please keep us updated if you nail that one down. Same thing happens here.

---

### Post by metatechbe on 2011-03-30
> **dgoodlad said:**
> Sorry I wasn't clear :) Once X initializes, the internal display works correctly. I rebuilt my kernel with the lvds_channels patch which seems much better than the original patch that I'd used which always forced dual-channel..


Dave,

What happens when you have an external monitor ? Do you need single or double channel ?
What happens when you have both an internal and an external monitor ?

Thanks,

metatech

---

### Post by dgoodlad on 2011-04-01
> **metatechbe said:**
> What happens when you have an external monitor ? Do you need single or double channel ?

The lvds channels patch doesn't affect the behavior of external displays, since lvds is only how the internal display is connected. The external display works both with and without the lvds channel patch.

> **metatechbe said:**
> What happens when you have both an internal and an external monitor ?

I'm using that right now, and it works fine:

```
$ xrandr
Screen 0: minimum 320 x 200, current 3360 x 1050, maximum 8192 x 8192
LVDS1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1680x1050      59.9*+
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1680x1050+1680+0 (normal left inverted right x axis y axis) 459mm x 296mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
```

I'm going to rebuild the kernel with a couple of other patches in order to support the apple_gmux module, and see how vga swticheroo goes.

Dave

---

### Post by metatechbe on 2011-04-01
> **dgoodlad said:**
> The lvds channels patch doesn't affect the behavior of external displays, since lvds is only how the internal display is connected. The external display works both with and without the lvds channel patch.


It makes sense, indeed.
Does the graphical logout work when the discrete graphic card is powered down ?
Do the other physical terminals work ? (Ctrl-Alt-F1..6)

metatech

---

