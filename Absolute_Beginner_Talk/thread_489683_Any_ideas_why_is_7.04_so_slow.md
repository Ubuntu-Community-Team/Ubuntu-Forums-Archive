---
title: "Any ideas why is 7.04 so slow?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by pancakelizard on 2007-07-01
I searched and couldn't find anything but I have a dual 3.0 with 3.5gig of ram and a 10k hdd and ubuntu runs slower than a 33mhz running windows 95. everything takes atleast 10 seconds to come up - even games and shortcuts in the system menu. 

i have a swap drive so i don't know what the issue could be.
any ideas?

i forgot to mention, to actually boot into the os takes about 3 minutes also (several hanging spots)
and this is a fresh install on a dual boot with windows xp pro

---

### Post by annda on 2007-07-01
unless you are using the liveCD, best bet would be to find out what is using your memory, although i can't think of anything that whould eat up so much RAM.
```

top
```

and SHIFT+m to sort by memory usage.

what about the graphic card drivers? have you installed them? for some cards, generic drivers can cause great delays in X system response.

---

### Post by steveneddy on 2007-07-01
Maybe, just maybe, the data on the CD was corrupt - did you check the md5 sums before burning the CD?

---

### Post by mrbungle on 2007-07-01
i also built a new dual core system with tons of memory and installed ubuntu 7.04 and was thinking it was going to blaze!  but found it to be a tad slow, so i moved to xubuntu and got that blazing speed i was hoping for.

---

### Post by Crafty Kisses on 2007-07-01
> **annda said:**
> unless you are using the liveCD, best bet would be to find out what is using your memory, although i can't think of anything that whould eat up so much RAM.
```

top
```

and SHIFT+m to sort by memory usage.

what about the graphic card drivers? have you installed them? for some cards, generic drivers can cause great delays in X system response.

That's what I was thinking too.

---

### Post by RTrev on 2007-07-01
> **pancakelizard said:**
> I searched and couldn't find anything but I have a dual 3.0 with 3.5gig of ram and a 10k hdd and ubuntu runs slower than a 33mhz running windows 95. everything takes atleast 10 seconds to come up - even games and shortcuts in the system menu. 

i have a swap drive so i don't know what the issue could be.
any ideas?

i forgot to mention, to actually boot into the os takes about 3 minutes also (several hanging spots)
and this is a fresh install on a dual boot with windows xp pro

I'm running a very similar system to what you describe, even down to the Raptor ;) and mine boots in 15-20 seconds.  Something is clearly amiss.  Have you looked at your log files (System | Administration | System Log) and followed the bootup sequence to see where things at getting hung up?

Your system should *fly*.. this isn't normal at all.  We just have to figure out what's going on.

---

### Post by steveneddy on 2007-07-01
Yeah - my Core 2 Duo with 2 GIG RAM flies on Ubuntu.

Try reinstalling after trying another DLed .iso and slow burn?

---

### Post by RTrev on 2007-07-01
> **steveneddy said:**
> Yeah - my Core 2 Duo with 2 GIG RAM flies on Ubuntu.

Try reinstalling after trying another DLed .iso and slow burn?

Yep, I always use 1x for burning .iso files of this kind.  You lose some time in the beginning, but...  :D

---

### Post by pancakelizard on 2007-07-01
> **annda said:**
> unless you are using the liveCD, best bet would be to find out what is using your memory, although i can't think of anything that whould eat up so much RAM.
```

top
```

and SHIFT+m to sort by memory usage.

what about the graphic card drivers? have you installed them? for some cards, generic drivers can cause great delays in X system response.

nothing really major here
firefox using 12% of cpu and 1.3% of mem
gnome using 6% of cpu and 1.3% of mem
everything else is under 4%

as far as the video drivers - i have a geforce 5500 with the latest updated drivers. i should note that if i use the restricted drivers or not, the speed isn't changed.


> **steveneddy said:**
> Maybe, just maybe, the data on the CD was corrupt - did you check the md5 sums before burning the CD?

yes i did before installing.

---

### Post by pancakelizard on 2007-07-01
> **RTrev said:**
> I'm running a very similar system to what you describe, even down to the Raptor ;) and mine boots in 15-20 seconds.  Something is clearly amiss.  Have you looked at your log files (System | Administration | System Log) and followed the bootup sequence to see where things at getting hung up?

Your system should *fly*.. this isn't normal at all.  We just have to figure out what's going on.

which log file should i be looking in?

---

### Post by RTrev on 2007-07-01
I'd look in the kernel log, at least for a start.  Note the timestamps next to each entry.  Normally things are happening fast, with multiple lines per second.  If you suddenly see where the time stamp jumps by many seconds or (god forbit) a minute or so, you may have zeroed in on what's slowing things down so badly.

---

### Post by pancakelizard on 2007-07-01
from the kernal log
these seem like lag points.

Jun 28 00:04:15 leland-desktop kernel: [    1.567424] input: AT Translated Set 2 keyboard as /class/input/input1
Jun 28 00:04:15 leland-desktop kernel: [    7.395042] Capability LSM initialized
Jun 28 00:04:15 leland-desktop kernel: [    7.491533] ACPI: Processor [CPU0] (supports 8 throttling states)

Jun 28 00:04:15 leland-desktop kernel: [    7.491554] ACPI: Processor [CPU1] (supports 8 throttling states)
Jun 28 00:04:15 leland-desktop kernel: [    8.370491] usbcore: registered new interface driver usbfs

Jun 28 00:04:15 leland-desktop kernel: [    9.551814] scsi1 : ata_piix
Jun 28 00:04:15 leland-desktop kernel: [   10.211415] ata2.00: ATAPI, max UDMA/33

Jun 28 00:04:15 leland-desktop kernel: [   10.435091] hub 6-0:1.0: over-current change on port 7
Jun 28 00:04:15 leland-desktop kernel: [   10.778911] usb 2-1: new low speed USB device using uhci_hcd and address 4
Jun 28 00:04:15 leland-desktop kernel: [   10.980903] usb 2-1: configuration #1 chosen from 1 choice
Jun 28 00:04:15 leland-desktop kernel: [   11.226701] usb 2-2: new low speed USB device using uhci_hcd and address 5
Jun 28 00:04:15 leland-desktop kernel: [   11.416626] usb 2-2: configuration #1 chosen from 1 choice

Jun 28 00:04:15 leland-desktop kernel: [   11.923368] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jun 28 00:04:15 leland-desktop kernel: [   40.364976] ata2.01: qc timeout (cmd 0xef)
Jun 28 00:04:15 leland-desktop kernel: [   40.364985] ata2.01: failed to set xfermode (err_mask=0x4)
Jun 28 00:04:15 leland-desktop kernel: [   40.364991] ata2: failed to recover some devices, retrying in 5 secs
Jun 28 00:04:15 leland-desktop kernel: [   46.186440] ata2.00: configured for UDMA/33
Jun 28 00:04:15 leland-desktop kernel: [   76.172080] ata2.01: qc timeout (cmd 0xef)
Jun 28 00:04:15 leland-desktop kernel: [   76.172088] ata2.01: failed to set xfermode (err_mask=0x4)
Jun 28 00:04:15 leland-desktop kernel: [   76.172097] ata2.01: limiting speed to UDMA/33:PIO3
Jun 28 00:04:15 leland-desktop kernel: [   76.172099] ata2: failed to recover some devices, retrying in 5 secs
Jun 28 00:04:15 leland-desktop kernel: [   81.989546] ata2.00: configured for UDMA/33
Jun 28 00:04:15 leland-desktop kernel: [  111.979186] ata2.01: qc timeout (cmd 0xef)
Jun 28 00:04:15 leland-desktop kernel: [  111.979196] ata2.01: failed to set xfermode (err_mask=0x4)
Jun 28 00:04:15 leland-desktop kernel: [  111.979202] ata2.01: disabled
Jun 28 00:04:15 leland-desktop kernel: [  111.979206] ata2: failed to recover some devices, retrying in 5 secs
Jun 28 00:04:15 leland-desktop kernel: [  116.980831] ata2.00: failed to set xfermode (err_mask=0x40)
Jun 28 00:04:15 leland-desktop kernel: [  116.980837] ata2: failed to recover some devices, retrying in 5 secs
Jun 28 00:04:15 leland-desktop kernel: [  122.638371] ata2.00: configured for UDMA/33

Jun 28 00:04:15 leland-desktop kernel: [  123.185247] EXT3-fs: mounted filesystem with ordered data mode.
Jun 28 00:04:15 leland-desktop kernel: [  137.434207] PM: Writing back config space on device 0000:05:02.0 at offset b (was 165314e4, writing 12bc103c)

Jun 28 00:04:15 leland-desktop kernel: [  137.434253] PM: Writing back config space on device 0000:05:02.0 at offset 0 (was 165314e4, writing 169614e4)
Jun 28 00:04:15 leland-desktop kernel: [  139.112071] NET: Registered protocol family 17

Jun 28 00:04:15 leland-desktop kernel: [  140.907057] Adding 1943824k swap on /dev/disk/by-uuid/7c6c215b-d34b-485a-a60a-6f47620ea820.  Priority:-1 extents:1 across:1943824k
Jun 28 00:04:15 leland-desktop kernel: [  141.014401] EXT3 FS on sda3, internal journal
Jun 28 00:04:15 leland-desktop kernel: [  143.021249] NET: Registered protocol family 10
Jun 28 00:04:15 leland-desktop kernel: [  143.021403] lo: Disabled Privacy Extensions
Jun 28 00:04:15 leland-desktop kernel: [  148.792761] Using specific hotkey driver
Jun 28 00:04:15 leland-desktop kernel: [  149.215848] ibm_acpi: ec object not found

Jun 28 00:04:15 leland-desktop kernel: [  149.375335] No dock devices found.
Jun 28 00:04:15 leland-desktop kernel: [  150.147286] pcc_acpi: loading...
Jun 28 00:04:15 leland-desktop kernel: [  153.375629] eth0: no IPv6 routers present
Jun 28 00:06:34 leland-desktop kernel: [  294.783702] ppdev: user-space parallel port driver
Jun 28 00:06:34 leland-desktop kernel: [  295.016830] mtrr: no more MTRRs available

Jun 28 00:06:36 leland-desktop kernel: [  296.530197] Bluetooth: RFCOMM ver 1.8
Jun 28 00:06:50 leland-desktop kernel: [  308.934233] eth0: no IPv6 routers present

Jun 28 00:04:15 leland-desktop kernel: [  153.375629] eth0: no IPv6 routers present
Jun 28 00:06:34 leland-desktop kernel: [  294.783702] ppdev: user-space parallel port driver

---

### Post by RTrev on 2007-07-01
> **pancakelizard said:**
> from the kernal log
these seem like lag points.

Jun 28 00:04:15 leland-desktop kernel: [  149.375335] No dock devices found.
Jun 28 00:04:15 leland-desktop kernel: [  150.147286] pcc_acpi: loading...
Jun 28 00:04:15 leland-desktop kernel: [  153.375629] eth0: no IPv6 routers present
Jun 28 00:06:34 leland-desktop kernel: [  294.783702] ppdev: user-space parallel port driver
Jun 28 00:06:34 leland-desktop kernel: [  295.016830] mtrr: no more MTRRs available

Jun 28 00:06:36 leland-desktop kernel: [  296.530197] Bluetooth: RFCOMM ver 1.8
Jun 28 00:06:50 leland-desktop kernel: [  308.934233] eth0: no IPv6 routers present

Jun 28 00:04:15 leland-desktop kernel: [  153.375629] eth0: no IPv6 routers present
Jun 28 00:06:34 leland-desktop kernel: [  294.783702] ppdev: user-space parallel port driver

Yike!  It will take someone smarter than I to determine exactly what's going on here, but you've zeroed in on where things are getting hung up.  And I presume it's the same thing that's causing continued slowness once you've finished booting.  I've never noticed anything like that parallel port driver or the MTTR issue.  Let's see what the smart folks think of this...

---

### Post by DBStevens on 2007-07-01
Jun 28 00:06:34 leland-desktop kernel: [ 295.016830] mtrr: no more MTRRs available

This is a potential nasty if the memory cannot be properly covered by mtrrs it is likely you have sections of memory that can't be cached.  If that is the case you will have one pokey system.  
 
Do a Google on " trim memory not covered by WB MTRRs"

and read.

---

### Post by DBStevens on 2007-07-01
Please provide the output of:

cat /proc/mtrr

---

### Post by pancakelizard on 2007-07-01
> **DBStevens said:**
> Please provide the output of:

cat /proc/mtrr

here you go:
leland@leland-desktop:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg02: base=0xc0000000 (3072MB), size= 256MB: write-back, count=1
reg03: base=0xd0000000 (3328MB), size= 128MB: write-back, count=1
reg04: base=0xd8000000 (3456MB), size=  64MB: write-back, count=1
reg05: base=0xdc000000 (3520MB), size=  32MB: write-back, count=1
reg06: base=0xde000000 (3552MB), size=  16MB: write-back, count=1
reg07: base=0xdf000000 (3568MB), size=   8MB: write-back, count=1

---

### Post by DBStevens on 2007-07-01
Ouch,

Could you also provide the results of lspci -v and the output from  cat /var/log/Xorg.0.log

It looks like you ran out of mtrrs and there is no mtrr to handle your video card in write combined mode.

---

### Post by DBStevens on 2007-07-01
Is your memory configuration 1gb 1gb 1gb 512mb  and did you install the memory (in other words are you comfortable installing parts in a pc)?

A solution for you might be to remove the 512mb stick and see what transpires.  This situataion is frequently a Bios memory mapping issue.  Currently the kernel folks are working on a few patches in the handling of mtrrs.

---

### Post by pancakelizard on 2007-07-01
I supplied both of the outputs, please see below

because of the limit of attachment sizes, i had to edit the xorg file.
this was the only thing i took out

SetGrabKeysState - disabled
SetGrabKeysState - enabled

which was repeated about 20 times.

as well as this from the bottom:
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(II) NVIDIA(0): Setting mode "1024x768"
(II) NVIDIA(0): Setting mode "1680x1050"
----------------------------
As far as the RAM configuration

It's in 3x1gb and 1x512mb ram sticks
I think I might have a 512 I could swap out for it.

---

### Post by DBStevens on 2007-07-01
How does the memory have to be setup on that motherboard?

What I'm aiming for is only two mtrrs being needed to map memory caching leaving 6 to cover any requirements of the pci/agp cards if they can use them.

I have a simple system and this is what my system has for the mtrr setup:

reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
reg01: base=0xd0000000 (3328MB), size= 128MB: write-combining, count=1

1GB of ram and the nvidia video card in write combining mode.

---

### Post by AllenGG on 2007-07-01
Noted that you said:
"
i forgot to mention, to actually boot into the os takes about 3 minutes also (several hanging spots) and this is a fresh install on a dual boot with windows xp pro"

Does XP boot and run OK ??

---

### Post by RTrev on 2007-07-02
> **DBStevens said:**
> How does the memory have to be setup on that motherboard?

What I'm aiming for is only two mtrrs being needed to map memory caching leaving 6 to cover any requirements of the pci/agp cards if they can use them.

I have a simple system and this is what my system has for the mtrr setup:

reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
reg01: base=0xd0000000 (3328MB), size= 128MB: write-combining, count=1

1GB of ram and the nvidia video card in write combining mode.

If it's of any help, I have 4G of RAM (four 1G sticks) and an Nvidia GeForce 7300 GT PCI-Express (16) video card, and this is what mine looks like:

```

bob@ub64:~/Desktop$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size= 512MB: write-back, count=1
reg02: base=0xa0000000 (2560MB), size= 256MB: write-back, count=1
reg03: base=0x100000000 (4096MB), size=1024MB: write-back, count=1
reg04: base=0x140000000 (5120MB), size= 256MB: write-back, count=1

```

Is that more what you would expect his to look like, or is mine screwed up too?  I see that I also have no write-combining mode.  This is the 64-bit Feisty if that makes a difference.  Would a change of the settings in the BIOS make a difference for either of us?  I noticed I had a setting for something like remapping holes in the BIOS memory.. I can reboot and check the exact name if it might matter for either of us?  I haven't run out of mtrr's, so things seem to run fine, but maybe this problem is common with systems having over X amount of RAM?

---

### Post by AllenGG on 2007-07-02
```
allengg@Raven:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
reg01: base=0xe0000000 (3584MB), size= 256MB: write-combining, count=1
reg02: base=0x40000000 (1024MB), size= 512MB: write-back, count=1
```Mine works OK, as above.

---

### Post by RTrev on 2007-07-02
> **RTrev said:**
> If it's of any help, I have 4G of RAM (four 1G sticks) and an Nvidia GeForce 7300 GT PCI-Express (16) video card, and this is what mine looks like:

```

bob@ub64:~/Desktop$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size= 512MB: write-back, count=1
reg02: base=0xa0000000 (2560MB), size= 256MB: write-back, count=1
reg03: base=0x100000000 (4096MB), size=1024MB: write-back, count=1
reg04: base=0x140000000 (5120MB), size= 256MB: write-back, count=1

```


Hey, just made a discovery that I hope will help!

My values are now:

```

bob@ub64:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x100000000 (4096MB), size=2048MB: write-back, count=1

```

I hope you can do the same.  My BIOS is a Phoenix Award Workstation BIOS v6.00PG.

I went into Advanced Chipset Features, then selected DRAM Configuration, and finally I [COLOR="Red"]disabled H/W memory hole remapping[/COLOR].

I really, really, really hope this helps!!  :D

Bob

---

### Post by DBStevens on 2007-07-02
Yes that would make a difference if only because it rearranges the physical memory mapping, anything that rearranges memory in anyway would make a difference, the question then becomes does it allow the the other resources that could could use the mtrrs to get one assigned.  The OP system was attempting to do that and discovered it was out, so I'm taking a leap of faith that having at least one more would help. Memory is one thing, BIOS settings are one more thing, BIOS errors are another, and then the kernel gets to play.  Plenty of room for "fun and games" to happen.

I haven't taken a look at the the other slow down points in the boot sequence.  That mtrr line stood out because of all of the mtrr related messages on lkml at this time.

As for should write combining being on in the other case, I can't say, normally that call gets made between the driver and the rest of the system mentioned above, yet more room for if you get my drift.

---

### Post by DBStevens on 2007-07-02
The other thing is it looks like your hard drives appear to be set in the slowest possible mode for some reason.   This could be because what I'm looking at is unused IDE ports, or the BIOS setting mandate it, or an incorrect cable for normal operation.

So maybe a description of your hard drive system is in order.

---

### Post by pancakelizard on 2007-07-02
> **AllenGG said:**
> Noted that you said:
"
i forgot to mention, to actually boot into the os takes about 3 minutes also (several hanging spots) and this is a fresh install on a dual boot with windows xp pro"

Does XP boot and run OK ??

Booting into XP is the same speed as always without any hangs or lag on the system.


> **RTrev said:**
> Hey, just made a discovery that I hope will help!

My values are now:

```

bob@ub64:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x100000000 (4096MB), size=2048MB: write-back, count=1

```

I hope you can do the same.  My BIOS is a Phoenix Award Workstation BIOS v6.00PG.

I went into Advanced Chipset Features, then selected DRAM Configuration, and finally I [COLOR="Red"]disabled H/W memory hole remapping[/COLOR].

I really, really, really hope this helps!!  :D

Bob

I can try that when I get home but I have a HP so I don't know if the BIOS will allow the end user that feature.


> **DBStevens said:**
> The other thing is it looks like your hard drives appear to be set in the slowest possible mode for some reason.   This could be because what I'm looking at is unused IDE ports, or the BIOS setting mandate it, or an incorrect cable for normal operation.

So maybe a description of your hard drive system is in order.

My hdd is a sata2 though not ide

---

### Post by DBStevens on 2007-07-02
"My hdd is a sata2 though not ide"

Ok, then they were unused IDE ports, now about your sata2 setup where is that in the logs?

Maybe a dmesg needs to be posted or attached.

---

### Post by ubuntujonez on 2007-07-02
Dear Gurus,

I'm also having Feisty problems. I tried an upgrade, from Edgy (? forget... 6.10), and it seemed to have some serious problems: keyboard via vnc and burn:/// not working, and nautilus problems. Since I couldn't really do anything as using the keyboard via vnc seemed to be corrupted, I turned to the forums. Before upgrading, I was happy with the system and the performance and figured I could benefit from the new release so I upgraded to Feisty via ubuntu desktop. To make a long story short after seeing a lot of people having trouble with no resolution, I downladed the alternate install iso for a terminal install. This is a headless server which I vnc and ssh to, to manage.

Booting is slow and is clearly getting hung up. I haven't really installed anything and  after slow reboot #1, I proceeded to install ssh and the system asked that I reinsert the CD but /dev/scd0 no longer exists. 
I really have no idea what I might try but everything was pretty much ok with Edgy Eft and I will probably go back to that as it seems like I'm having serious problems with Feisty.

Any help will be greatly appreciated.

Thanks,
jonez

/var/log/dmesg:

```

$ cat /var/log/dmesg
[    0.000000] Linux version 2.6.20-15-server (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:41:34 UTC 2007 (Ubuntu 2.6.20-15.27-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 00000000000a0000 end: 00000000000a0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fd70000 end: 000000001fe70000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fe70000 size: 0000000000002000 end: 000000001fe72000 type: 4
[    0.000000] copy_e820_map() start: 000000001fe72000 size: 0000000000021000 end: 000000001fe93000 type: 3
[    0.000000] copy_e820_map() start: 000000001fe93000 size: 000000000006d000 end: 000000001ff00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fecf0000 size: 0000000000001000 end: 00000000fecf1000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 0000000000070000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000010000 end: 00000000fee10000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fe70000 (usable)
[    0.000000]  BIOS-e820: 000000001fe70000 - 000000001fe72000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fe72000 - 000000001fe93000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fe93000 - 000000001ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 130672) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130672
[    0.000000]   HighMem    130672 ->   130672
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130672
[    0.000000] On node 0 totalpages: 130672
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 988 pages used for memmap
[    0.000000]   Normal zone: 125588 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000feba0
[    0.000000] ACPI: RSDT (v001 DELL    4600    0x00000007 ASL  0x00000061) @ 0x000fd1b7
[    0.000000] ACPI: FADT (v001 DELL    4600    0x00000007 ASL  0x00000061) @ 0x000fd1eb
[    0.000000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffd1914
[    0.000000] ACPI: MADT (v001 DELL    4600    0x00000007 ASL  0x00000061) @ 0x000fd25f
[    0.000000] ACPI: BOOT (v001 DELL    4600    0x00000007 ASL  0x00000061) @ 0x000fd2cb
[    0.000000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:ded00000)
[    0.000000] Detected 2793.222 MHz processor.
[   10.225996] Built 1 zonelists.  Total pages: 129652
[   10.226000] Kernel command line: root=UUID=ed4de100-c3c4-4aaf-bf75-a8d975bb6c91 ro quiet splash
[   10.226156] mapped APIC to ffffd000 (fee00000)
[   10.226158] mapped IOAPIC to ffffc000 (fec00000)
[   10.226161] Enabling fast FPU save and restore... done.
[   10.226164] Enabling unmasked SIMD FPU exception support... done.
[   10.226173] Initializing CPU#0
[   10.226246] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   10.227735] Console: colour VGA+ 80x25
[   10.227991] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.228219] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.238092] Memory: 507292k/522688k available (2020k kernel code, 14868k reserved, 893k data, 328k init, 0k highmem)
[   10.238102] virtual kernel memory layout:
[   10.238103]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
[   10.238104]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   10.238105]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
[   10.238106]     lowmem  : 0xc0000000 - 0xdfe70000   ( 510 MB)
[   10.238108]       .init : 0xc03df000 - 0xc0431000   ( 328 kB)
[   10.238109]       .data : 0xc02f9114 - 0xc03d8754   ( 893 kB)
[   10.238110]       .text : 0xc0100000 - 0xc02f9114   (2020 kB)
[   10.238113] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.385979] Calibrating delay using timer specific routine.. 5589.54 BogoMIPS (lpj=27947734)
[   10.386022] Security Framework v1.0.0 initialized
[   10.386030] SELinux:  Disabled at boot.
[   10.386045] Mount-cache hash table entries: 512
[   10.386189] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   10.386202] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   10.386206] CPU: L2 cache: 512K
[   10.386208] CPU: Hyper-Threading is disabled
[   10.386210] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   10.386222] Compat vDSO mapped to ffffe000.
[   10.386226] Remapping vsyscall page to ffffe000
[   10.386238] Checking 'hlt' instruction... OK.
[   10.426010] SMP alternatives: switching to UP code
[   10.426197] Freeing SMP alternatives: 11k freed
[   10.426388] Early unpacking initramfs... done
[   10.688747] ACPI: Core revision 20060707
[   10.689236] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   10.713522] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[   10.713565] Total of 1 processors activated (5589.54 BogoMIPS).
[   10.713698] ENABLING IO-APIC IRQs
[   10.713882] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   10.925099] Brought up 1 CPUs
[   10.925336] Booting paravirtualized kernel on bare hardware
[   10.925415] Time: 22:04:54  Date: 06/02/107
[   10.925441] NET: Registered protocol family 16
[   10.925536] EISA bus registered
[   10.925541] ACPI: bus type pci registered
[   10.925628] PCI: PCI BIOS revision 2.10 entry at 0xfbb15, last bus=1
[   10.925630] PCI: Using configuration type 1
[   10.925632] Setting up standard PCI resources
[   10.951290] ACPI: Interpreter enabled
[   10.951294] ACPI: Using IOAPIC for interrupt routing
[   10.955688] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.955697] PCI: Probing PCI hardware (bus 00)
[   10.955716] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   10.957894] Boot video device is 0000:00:02.0
[   10.958253] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   10.958257] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   10.958509] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[   10.958579] PCI: Transparent bridge - 0000:00:1e.0
[   10.958602] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.126300] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   11.142145] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   11.142874] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[   11.143599] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   11.144326] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   11.145070] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   11.145817] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   11.146562] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   11.147295] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   11.147456] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.147467] pnp: PnP ACPI init
[   11.177151] pnp: PnP ACPI: found 11 devices
[   11.177157] PnPBIOS: Disabled by ACPI PNP
[   11.177210] PCI: Using ACPI for IRQ routing
[   11.177214] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.182091] NET: Registered protocol family 8
[   11.182093] NET: Registered protocol family 20
[   11.182102] NetLabel: Initializing
[   11.182104] NetLabel:  domain hash size = 128
[   11.182105] NetLabel:  protocols = UNLABELED CIPSOv4
[   11.182117] NetLabel:  unlabeled traffic allowed by default
[   11.188714] pnp: 00:0a: ioport range 0x800-0x85f could not be reserved
[   11.188717] pnp: 00:0a: ioport range 0xc00-0xc7f has been reserved
[   11.188721] pnp: 00:0a: ioport range 0x860-0x8ff could not be reserved
[   11.189012] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   11.189017] PCI: Bridge: 0000:00:1e.0
[   11.189021]   IO window: d000-dfff
[   11.189027]   MEM window: fea00000-feafffff
[   11.189031]   PREFETCH window: disabled.
[   11.189045] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   11.189072] NET: Registered protocol family 2
[   11.274515] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   11.274590] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   11.274660] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   11.274696] TCP: Hash tables configured (established 16384 bind 8192)
[   11.274698] TCP reno registered
[   11.304501] checking if image is initramfs... it is
[   11.817541] Freeing initrd memory: 6638k freed
[   11.817732] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[   11.817735] Simple Boot Flag at 0x7a set to 0x1
[   11.817965] audit: initializing netlink socket (disabled)
[   11.817979] audit(1183413895.450:1): initialized
[   11.818082] VFS: Disk quotas dquot_6.5.1
[   11.818099] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.818146] io scheduler noop registered
[   11.818149] io scheduler anticipatory registered
[   11.818152] io scheduler deadline registered (default)
[   11.818161] io scheduler cfq registered
[   11.818440] isapnp: Scanning for PnP cards...
[   12.174737] isapnp: No Plug & Play device found
[   12.201030] Real Time Clock Driver v1.12ac
[   12.201078] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.201191] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.201976] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.202217] mice: PS/2 mouse device common for all mice
[   12.202823] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.203053] input: Macintosh mouse button emulation as /class/input/input0
[   12.203089] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   12.203093] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   12.203333] PNP: PS/2 Controller [PNP0303:KBD] at 0x60,0x64 irq 1
[   12.203336] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   12.207031] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.207039] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.207203] EISA: Probing bus 0 at eisa.0
[   12.207242] EISA: Detected 0 cards.
[   12.237293] TCP cubic registered
[   12.237302] NET: Registered protocol family 1
[   12.237323] Using IPI No-Shortcut mode
[   12.237392] ACPI: (supports S0 S1 S3 S4 S5)
[   12.237438]   Magic number: 15:3:97
[   12.237888] Freeing unused kernel memory: 328k freed
[   12.242809] Time: tsc clocksource has been installed.
[   12.252201] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.390173] Capability LSM initialized
[   12.425919] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   12.900861] usbcore: registered new interface driver usbfs
[   12.900886] usbcore: registered new interface driver hub
[   12.900915] usbcore: registered new device driver usb
[   12.901912] USB Universal Host Controller Interface driver v3.0
[   12.901969] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   12.901982] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.901986] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.902127] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   12.902154] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[   12.902260] usb usb1: configuration #1 chosen from 1 choice
[   12.902286] hub 1-0:1.0: USB hub found
[   12.902294] hub 1-0:1.0: 2 ports detected
[   12.974691] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   12.974695] e100: Copyright(c) 1999-2006 Intel Corporation
[   13.021501] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   13.021516] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.021520] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.021547] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.021574] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[   13.021665] usb usb2: configuration #1 chosen from 1 choice
[   13.021690] hub 2-0:1.0: USB hub found
[   13.021697] hub 2-0:1.0: 2 ports detected
[   13.073383] FDC 0 is a post-1991 82077
[   13.141235] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   13.141249] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.141253] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.141283] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.141310] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[   13.141395] usb usb3: configuration #1 chosen from 1 choice
[   13.141421] hub 3-0:1.0: USB hub found
[   13.141428] hub 3-0:1.0: 2 ports detected
[   13.261012] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   13.261026] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   13.261030] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   13.261053] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   13.261080] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
[   13.261168] usb usb4: configuration #1 chosen from 1 choice
[   13.261192] hub 4-0:1.0: USB hub found
[   13.261200] hub 4-0:1.0: 2 ports detected
[   13.386653] SCSI subsystem initialized
[   13.393096] libata version 2.20 loaded.
[   13.394565] ata_piix 0000:00:1f.1: version 2.10ac1
[   13.394583] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   13.394604] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   13.395824] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   13.395871] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   13.395893] scsi0 : ata_piix
[   13.430650] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   13.591530] ata1.00: ata_hpa_resize 1: sectors = 156250000, hpa_sectors = 156250000
[   13.591535] ata1.00: ATA-6: WDC WD800BB-75FRA0, 77.07W77, max UDMA/100
[   13.591538] ata1.00: 156250000 sectors, multi 8: LBA48
[   13.621444] ata1.00: ata_hpa_resize 1: sectors = 156250000, hpa_sectors = 156250000
[   13.621447] ata1.00: configured for UDMA/100
[   13.621459] scsi1 : ata_piix
[   13.621583] usb 2-1: configuration #1 chosen from 1 choice
[   13.636063] usbcore: registered new interface driver libusual
[   13.639928] Initializing USB Mass Storage driver...
[   13.639997] scsi2 : SCSI emulation for USB Mass Storage devices
[   13.640047] usbcore: registered new interface driver usb-storage
[   13.640050] USB Mass Storage support registered.
[   13.640148] usb-storage: device found at 2
[   13.640151] usb-storage: waiting for device to settle before scanning
[   13.969840] ata2.00: ATAPI, max UDMA/33
[   19.388585] usb-storage: device scan complete
[   19.904626] scsi 2:0:0:0: Direct-Access     LaCie    BigDisk               PQ: 0 ANSI: 0
[   19.914578] SCSI device sda: 976794336 512-byte hdwr sectors (500119 MB)
[   19.919565] sda: Write Protect is off
[   19.919568] sda: Mode Sense: 10 00 00 00
[   19.919570] sda: assuming drive cache: write through
[   19.924556] SCSI device sda: 976794336 512-byte hdwr sectors (500119 MB)
[   19.929547] sda: Write Protect is off
[   19.929550] sda: Mode Sense: 10 00 00 00
[   19.929551] sda: assuming drive cache: write through
[   19.929593]  sda: sda1
[   19.945605] sd 2:0:0:0: Attached scsi disk sda
[   19.950510] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   43.926220] ata2.00: qc timeout (cmd 0xef)
[   43.926229] ata2.00: failed to set xfermode (err_mask=0x4)
[   43.926273] ata2: failed to recover some devices, retrying in 5 secs
[   79.213265] ata2.00: qc timeout (cmd 0xef)
[   79.213274] ata2.00: failed to set xfermode (err_mask=0x4)
[   79.213319] ata2.00: limiting speed to UDMA/33:PIO3
[   79.213321] ata2: failed to recover some devices, retrying in 5 secs
[  114.500320] ata2.00: qc timeout (cmd 0xef)
[  114.500330] ata2.00: failed to set xfermode (err_mask=0x4)
[  114.500373] ata2.00: disabled
[  115.009508] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BB-75FR 77.0 PQ: 0 ANSI: 5
[  115.009832] SCSI device sdb: 156250000 512-byte hdwr sectors (80000 MB)
[  115.009845] sdb: Write Protect is off
[  115.009848] sdb: Mode Sense: 00 3a 00 00
[  115.009864] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  115.009912] SCSI device sdb: 156250000 512-byte hdwr sectors (80000 MB)
[  115.009922] sdb: Write Protect is off
[  115.009924] sdb: Mode Sense: 00 3a 00 00
[  115.009939] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  115.009943]  sdb: sdb1 sdb2 < sdb5 >
[  115.059907] sd 0:0:0:0: Attached scsi disk sdb
[  115.059949] sd 0:0:0:0: Attached scsi generic sg1 type 0
[  115.075603] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[  115.075621] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[  115.075640] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[  115.076234] ata3: SATA max UDMA/133 cmd 0x0001fe00 ctl 0x0001fe12 bmdma 0x0001fea0 irq 18
[  115.076265] ata4: SATA max UDMA/133 cmd 0x0001fe20 ctl 0x0001fe32 bmdma 0x0001fea8 irq 18
[  115.076277] scsi3 : ata_piix
[  115.250427] ata3.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[  115.250432] ata3.00: ATA-6: WDC WD2500JD-22GBB0, 02.05D02, max UDMA/100
[  115.250435] ata3.00: 488397168 sectors, multi 8: LBA48
[  115.250437] ata3.00: applying bridge limits
[  115.270390] ata3.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[  115.270393] ata3.00: configured for UDMA/100
[  115.270406] scsi4 : ata_piix
[  115.450088] ata4.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[  115.450093] ata4.00: ATA-6: WDC WD2500JD-22GBB0, 02.05D02, max UDMA/100
[  115.450095] ata4.00: 488397168 sectors, multi 8: LBA48
[  115.450097] ata4.00: applying bridge limits
[  115.470056] ata4.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[  115.470060] ata4.00: configured for UDMA/100
[  115.470172] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500JD-22G 02.0 PQ: 0 ANSI: 5
[  115.470484] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[  115.470497] sdc: Write Protect is off
[  115.470500] sdc: Mode Sense: 00 3a 00 00
[  115.470516] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  115.470567] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[  115.470577] sdc: Write Protect is off
[  115.470579] sdc: Mode Sense: 00 3a 00 00
[  115.470594] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  115.470598]  sdc: sdc1
[  115.494035] sd 3:0:0:0: Attached scsi disk sdc
[  115.494073] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  115.502393] scsi 4:0:0:0: Direct-Access     ATA      WDC WD2500JD-22G 02.0 PQ: 0 ANSI: 5
[  115.502630] SCSI device sdd: 488397168 512-byte hdwr sectors (250059 MB)
[  115.502642] sdd: Write Protect is off
[  115.502645] sdd: Mode Sense: 00 3a 00 00
[  115.502661] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  115.502705] SCSI device sdd: 488397168 512-byte hdwr sectors (250059 MB)
[  115.502715] sdd: Write Protect is off
[  115.502717] sdd: Mode Sense: 00 3a 00 00
[  115.502733] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  115.502737]  sdd: sdd1
[  115.514011] sd 4:0:0:0: Attached scsi disk sdd
[  115.514054] sd 4:0:0:0: Attached scsi generic sg3 type 0
[  115.525770] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 19
[  115.548397] e100: eth0: e100_probe: addr 0xfeaff000, irq 19, MAC addr 00:0C:F1:D8:2D:A6
[  115.548556] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
[  115.548569] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[  115.548573] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[  115.548606] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[  115.548639] ehci_hcd 0000:00:1d.7: debug port 1
[  115.548645] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[  115.548658] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80800
[  115.552529] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[  115.552617] usb usb5: configuration #1 chosen from 1 choice
[  115.552644] hub 5-0:1.0: USB hub found
[  115.552651] hub 5-0:1.0: 8 ports detected
[  115.937743] usb 5-3: new high speed USB device using ehci_hcd and address 2
[  115.964981] kjournald starting.  Commit interval 5 seconds
[  115.964993] EXT3-fs: mounted filesystem with ordered data mode.
[  116.090633] usb 5-3: configuration #1 chosen from 1 choice
[  116.091124] scsi5 : SCSI emulation for USB Mass Storage devices
[  116.091259] usb 2-1: USB disconnect, address 2
[  116.091634] usb-storage: device found at 2
[  116.091636] usb-storage: waiting for device to settle before scanning
[  118.892575] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  120.106905] Linux agpgart interface v0.102 (c) Dave Jones
[  120.209537] agpgart: Detected an Intel 865 Chipset.
[  120.209628] agpgart: Detected 892K stolen memory.
[  120.224495] agpgart: AGP aperture is 128M @ 0xe8000000
[  120.281286] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  120.349171] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  120.373844] intel_rng: Firmware space is locked read-only. If you can't or
[  120.373847] intel_rng: don't want to disable this in firmware setup, and if
[  120.373848] intel_rng: you are certain that your system has a functional
[  120.373850] intel_rng: RNG, try using the 'no_fwh_detect' option.
[  120.459963] NET: Registered protocol family 10
[  120.460155] lo: Disabled Privacy Extensions
[  120.660820] iTCO_vendor_support: vendor-support=0
[  120.709887] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[  120.709958] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[  120.709987] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  120.763658] input: PC Speaker as /class/input/input2
[  120.831864] parport: PnPBIOS parport detected.
[  120.831915] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[  121.127804] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[  121.127831] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  121.457886] intel8x0_measure_ac97_clock: measured 57539 usecs
[  121.457890] intel8x0: clocking to 48000
[  121.833206] usb-storage: device scan complete
[  121.907178] lp0: using parport0 (interrupt-driven).
[  122.306364] Adding 1502036k swap on /dev/disk/by-uuid/47dc7422-93de-4980-a759-a2d1ca39182e.  Priority:-1 extents:1 across:1502036k
[  122.345765] scsi 5:0:0:0: Direct-Access     LaCie    BigDisk               PQ: 0 ANSI: 0
[  122.347345] SCSI device sda: 976794336 512-byte hdwr sectors (500119 MB)
[  122.348339] sda: Write Protect is off
[  122.348342] sda: Mode Sense: 10 00 00 00
[  122.348344] sda: assuming drive cache: write through
[  122.349211] SCSI device sda: 976794336 512-byte hdwr sectors (500119 MB)
[  122.350210] sda: Write Protect is off
[  122.350212] sda: Mode Sense: 10 00 00 00
[  122.350214] sda: assuming drive cache: write through
[  122.350254]  sda: sda1
[  122.366371] sd 5:0:0:0: Attached scsi disk sda
[  122.366417] sd 5:0:0:0: Attached scsi generic sg0 type 0
[  122.508495] EXT3 FS on sdb1, internal journal


```

---

### Post by pancakelizard on 2007-07-02
I did some more trouble shooting, I think I had a bad stick of ram (the 512mb) i removed it but it still took forever to boot up.
I restored the defaults to my bios and the same thing happened
I replugged in my sata connector, unplugged external enclosure and the same thing. 

I ram memtest and no errors.

Now it boots faster and Linux and is alot faster than before however when the status bar comes up, it still freezes in that spot, but once it gets past that point it doesn't freeze again. Plus I don't have any lag in the desktop enivroment at all.

Here are the results from cat (I have 3.0 gigs now)
leland@leland-desktop:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg02: base=0xfeda0000 (4077MB), size= 128KB: write-back, count=1

Here is the lag points, I just copy and pasted anything over a second of response time:
Jul  2 20:04:49 leland-desktop kernel: [    0.000000] Detected 2992.988 MHz processor.
Jul  2 20:04:49 leland-desktop kernel: [   20.446537] Built 1 zonelists.  Total pages: 780273

Jul  2 20:04:49 leland-desktop kernel: [   26.099763] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jul  2 20:04:49 leland-desktop kernel: [   55.499760] ata2.01: qc timeout (cmd 0xef)

Jul  2 20:04:49 leland-desktop kernel: [   61.317471] ata2.00: configured for UDMA/33
Jul  2 20:04:49 leland-desktop kernel: [   91.304367] ata2.01: qc timeout (cmd 0xef)

Jul  2 20:04:49 leland-desktop kernel: [   97.122081] ata2.00: configured for UDMA/33
Jul  2 20:04:49 leland-desktop kernel: [  127.108977] ata2.01: qc timeout (cmd 0xef)

Jul  2 20:04:49 leland-desktop kernel: [  127.108995] ata2: failed to recover some devices, retrying in 5 secs
Jul  2 20:04:49 leland-desktop kernel: [  132.110827] ata2.00: failed to set xfermode (err_mask=0x40)

Jul  2 20:04:49 leland-desktop kernel: [  138.600860] EXT3-fs: mounted filesystem with ordered data mode.
Jul  2 20:04:49 leland-desktop kernel: [  145.654803] PM: Writing back config space on device 0000:05:02.0 at offset c (was fffb0000, writing 0)

Jul  2 20:04:49 leland-desktop kernel: [  150.050298] lo: Disabled Privacy Extensions
Jul  2 20:04:49 leland-desktop kernel: [  154.871374] Using specific hotkey driver

Jul  2 20:04:49 leland-desktop kernel: [  155.138476] pcc_acpi: loading...
Jul  2 20:04:53 leland-desktop kernel: [  159.455084] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.

Jul  2 20:04:55 leland-desktop kernel: [  161.726250] Bluetooth: RFCOMM ver 1.8
Jul  2 20:05:46 leland-desktop kernel: [  175.156303] eth0: no IPv6 routers present

---

### Post by Erdaron on 2007-07-02
My machine also seems to hang up during boot due to the same "qc timeout" error.

I don't know how to fix that, but I'm subscribing to this thread :).

---

### Post by DBStevens on 2007-07-02
jonez,

You also start slowing down when the kernel was probing the IDE ports on the machine, in fact you were on your way to beating my system in the bootup race but my time to swap space add was 59.28+ and yours was 122.30+  Our machines are almost identical in terms of raw clocks.

Just for giggles would you mind posting the output of cat /proc/mtrr and lspci -v from the server?

---

### Post by RTrev on 2007-07-02
> Here is the lag points, I just copy and pasted anything over a second of response time:


What are you seeing as lags here?  If you look at the timestamp in the far left column, all of these events are happening during the same second.. 04:49.

```

Jul  2 20:04:49 leland-desktop kernel: [   97.122081] ata2.00: configured for UDMA/33
Jul  2 20:04:49 leland-desktop kernel: [  127.108977] ata2.01: qc timeout (cmd 0xef)

Jul  2 20:04:49 leland-desktop kernel: [  127.108995] ata2: failed to recover some devices, retrying in 5 secs
Jul  2 20:04:49 leland-desktop kernel: [  132.110827] ata2.00: failed to set xfermode (err_mask=0x40)

Jul  2 20:04:49 leland-desktop kernel: [  138.600860] EXT3-fs: mounted filesystem with ordered data mode.
Jul  2 20:04:49 leland-desktop kernel: [  145.654803] PM: Writing back config space on device 0000:05:02.0 at offset c (was fffb0000, writing 0)

Jul  2 20:04:49 leland-desktop kernel: [  150.050298] lo: Disabled Privacy Extensions
Jul  2 20:04:49 leland-desktop kernel: [  154.871374] Using specific hotkey driver

```

Until we get to this point, and then there is a few (3-4) seconds while it does whatever it's doing.

```

Jul  2 20:04:49 leland-desktop kernel: [  155.138476] pcc_acpi: loading...
Jul  2 20:04:53 leland-desktop kernel: [  159.455084] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.

```

And what's happening here, I have no clue.  This one looks serious, as we have a pause of almost a full MINUTE for some reason.  But for the qc timeout stuff, I don't see any lag.. there must have been one, but it was way less than a second.  Am I mis-reading this in some way?

```

Jul  2 20:04:55 leland-desktop kernel: [  161.726250] Bluetooth: RFCOMM ver 1.8
Jul  2 20:05:46 leland-desktop kernel: [  175.156303] eth0: no IPv6 routers present

```

Bob

---

### Post by DBStevens on 2007-07-02
pancakelizard,

So the system is more responsive once it finished booting, in addition I suspect you might have at least one device on your system that is a lot happier that it got an mtrr to play with.

Now I don't know if your bios has an option that is called write combine if it does I'll bet it is disabled and if you were to enable it you might see that third mtrr go to write combined mode provided the video driver supports it.  If the memory driver supports it you will gain additional speed for the display handling.

Now do you have any devices attached to your IDE ports? If so what are they and how are they connected.

The only times I've had problems with IDE port probes was when cables to the devices were loose (including the power cables) and had improper terminations that is two slaves or two masters on a channel.

---

### Post by Erdaron on 2007-07-02
> **DBStevens said:**
> 
The only times I've had problems with IDE port probes was when cables to the devices were loose (including the power cables) and had improper terminations that is two slaves or two masters on a channel.

Does it matter if the pin settings on devices are cable select / cable select instead of explicit master / slave?

---

### Post by DBStevens on 2007-07-02
Erdaron,

Depends on the drives and the cable.

---

### Post by DBStevens on 2007-07-02
Bob,

[  127.108995] ata2: failed to recover some devices, retrying in 5 secs
[  132.110827] ata2.00: failed to set xfermode (err_mask=0x40)

The times in the brackets are what I'm going by note the retrying in 5 seconds matches the difference between 132.11 - 127.11  pretty dang closely even though the date and time says otherwise.  I think you have a buffer flush to disk date and time for the front of the line but a runing clock from start inside the brackets.   It has been some time since I checked any of the logging code.  So I might be mis remembering it happens when you get along in years ;-).

---

### Post by RTrev on 2007-07-02
> **DBStevens said:**
> Bob,

[  127.108995] ata2: failed to recover some devices, retrying in 5 secs
[  132.110827] ata2.00: failed to set xfermode (err_mask=0x40)

The times in the brackets are what I'm going by note the retrying in 5 seconds matches the difference between 132.11 - 127.11  pretty dang closely even though the date and time says otherwise.  I think you have a buffer flush to disk date and time for the front of the line but a runing clock from start inside the brackets.   It has been some time since I checked any of the logging code.  So I might be mis remembering it happens when you get along in years ;-).

Ahah!!  Now I get it.  Thank you.. I'm learning a lot in this thread!  :)

Bob

---

### Post by DBStevens on 2007-07-02
I'm glad to be able to answer some of the questions.

What slows things down is that most questions come without any real information to go on and frequently involve more than one problem with multiple causes and sometimes even more than one possible working solution.   

I've spent a lot of time with things made of silicon that push electrons around and have more than a fair amount of patience, if folks can provide answers to my requests for information eventually we will find an answer.

---

### Post by pancakelizard on 2007-07-02
hey dbstevens, these are the ones i'm really wondering about

Jul 2 20:04:49 leland-desktop kernel: [ 26.099763] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jul 2 20:04:49 leland-desktop kernel: [ 55.499760] ata2.01: qc timeout (cmd 0xef)

This is 29.399997 seconds


Jul 2 20:04:49 leland-desktop kernel: [ 61.317471] ata2.00: configured for UDMA/33
Jul 2 20:04:49 leland-desktop kernel: [ 91.304367] ata2.01: qc timeout (cmd 0xef)

This is 29.986896 seconds


Jul 2 20:04:49 leland-desktop kernel: [ 97.122081] ata2.00: configured for UDMA/33
Jul 2 20:04:49 leland-desktop kernel: [ 127.108977] ata2.01: qc timeout (cmd 0xef)

This one is also 29.986896 seconds

---

### Post by pancakelizard on 2007-07-02
> **DBStevens said:**
> pancakelizard,

So the system is more responsive once it finished booting, in addition I suspect you might have at least one device on your system that is a lot happier that it got an mtrr to play with.

Now I don't know if your bios has an option that is called write combine if it does I'll bet it is disabled and if you were to enable it you might see that third mtrr go to write combined mode provided the video driver supports it.  If the memory driver supports it you will gain additional speed for the display handling.

Now do you have any devices attached to your IDE ports? If so what are they and how are they connected.

The only times I've had problems with IDE port probes was when cables to the devices were loose (including the power cables) and had improper terminations that is two slaves or two masters on a channel.

I'm about to go look in the BIOS but I don't think I saw anything like that - I'm using an HP motherboard so the BIOS features are lacking.

I have 2 IDE optical drives connected. A CDRW and DVDRW both on the same IDE cable on IDE1.


Update:
I rebooted and that option wasn't in the BIOS.
The bootup was the same but only these seriously lag spots

Jul  2 22:11:16 leland-desktop kernel: [   19.413943] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jul  2 22:11:16 leland-desktop kernel: [   47.612780] ata2.01: qc timeout (cmd 0xef)

Jul  2 22:11:16 leland-desktop kernel: [   47.612799] ata2: failed to recover some devices, retrying in 5 secs
Jul  2 22:11:16 leland-desktop kernel: [   53.430505] ata2.00: configured for UDMA/33
Jul  2 22:11:16 leland-desktop kernel: [   83.417395] ata2.01: qc timeout (cmd 0xef)

Jul  2 22:11:16 leland-desktop kernel: [   89.235101] ata2.00: configured for UDMA/33
Jul  2 22:11:16 leland-desktop kernel: [  119.221991] ata2.01: qc timeout (cmd 0xef)

Everything else seems to be fine.

---

### Post by DBStevens on 2007-07-02
"I have 2 IDE optical drives connected. A CDRW and DVDRW both on the same IDE cable on IDE1"

How are they jumpered?  Hopefully one is master and one slave, if not and they aren't both cable select with a proper cable they should be ....

---

### Post by pancakelizard on 2007-07-02
> **DBStevens said:**
> "I have 2 IDE optical drives connected. A CDRW and DVDRW both on the same IDE cable on IDE1"

How are they jumpered?  Hopefully one is master and one slave, if not and they aren't both cable select with a proper cable they should be ....

The DVDRW is master and the CDRW is slave. Nothing cable select.

---

### Post by borris.morris on 2007-07-02
are the cables plugged in all the way?

---

### Post by pancakelizard on 2007-07-02
> **borris.morris said:**
> are the cables plugged in all the way?

yes they are

---

### Post by RTrev on 2007-07-02
Might it be worth a process of elimination... disconnect the optical drives, see what happens, then work your way through other things until we find the culprit?

---

### Post by borris.morris on 2007-07-02
> **pancakelizard said:**
> yes they are

well, try to disable the second ide port. also does your ide go port 0 and then 1? or is it 1 and then 2?

---

### Post by DBStevens on 2007-07-02
I'll give you something to try if you discover that the cables are fully plugged in and things still are slow booting.

It is that I hadn't found anything to indicate a need for it.

---

### Post by DBStevens on 2007-07-03
An additional boot option for the grub line.

Try adding irqpoll to the end of the boot options.

I have little use for such an option but hey it might at least give us a starting point.

I'm out of here until at least 9:30 PM Eastern July 3

---

### Post by pancakelizard on 2007-07-03
I reseated the cables and booted with the same effect.
Then placed the IDE cable into slot 1 instead of slot 0 and same effect.
I got annoyed and just unplugged it from the motherboard and now the boot time is around maybe 15 seconds total.

So I think the IDE cable is bad, I'm going to replace it and find out.
I know in the past the simplest fixes with performance issues have been by replacing the IDE cable.

---

### Post by pancakelizard on 2007-07-03
Update:

I went out and got a new IDE cable assuming this would be the solution and it wasn't.
The DVDRW drive works fine when connected but the CDRW drive seems to be the problem with the lag in the system. However I don't understand how since there isn't a problem using the drive in Windows XP.

So basically the drive isn't connected right now and things seem to be fine.

I would like to see about getting a firmware update or a linux driver for the CDRW - it's a TDK 5200B and it's probably the best CDRW I've ever had. There aren't any broken pins and it's jumper setting is correct and if I shake the drive, there isn't anything rattling inside. I'm hoping it's just a driver issue.

---

### Post by ubuntujonez on 2007-07-03
> **DBStevens said:**
> jonez,

You also start slowing down when the kernel was probing the IDE ports on the machine, in fact you were on your way to beating my system in the bootup race but my time to swap space add was 59.28+ and yours was 122.30+  Our machines are almost identical in terms of raw clocks.

Just for giggles would you mind posting the output of cat /proc/mtrr and lspci -v from the server?

This system didn't seem to have any slow boot problems with FC2,3,4, Dapper, or Efty... I'm guessing it's something with the 2.6.20 kernel. After one Feisty upgrade and 2 Feisty installs from scratch I finally have things working ok, except for this really slow boot. *sigh*

I'll keep following this thread, but I actually have a job and work to do :(  If you need any more output or want me to try something just ask.

-jonez

--
$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size= 512MB: write-back, count=1
reg01: base=0x1ff00000 ( 511MB), size=   1MB: uncachable, count=1
reg02: base=0xe8000000 (3712MB), size= 128MB: write-combining, count=1

$ sudo lspci -v

```

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
        Subsystem: Dell Unknown device 0174
        Flags: bus master, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [e4] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 0174
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ed98 [size=8]
        Capabilities: [d0] Power Management version 1

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0174
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0174
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ff60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0174
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ff40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0174
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ff20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 0174
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fea00000-feafffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 0174
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Dell Unknown device 0174
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at fe00 [size=8]
        I/O ports at fe10 [size=4]
        I/O ports at fe20 [size=8]
        I/O ports at fe30 [size=4]
        I/O ports at fea0 [size=16]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: Dell Unknown device 0174
        Flags: medium devsel, IRQ 3
        I/O ports at eda0 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Dell Unknown device 0174
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at ee00 [size=256]
        I/O ports at edc0 [size=64]
        Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
        Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
        Subsystem: Dell Unknown device 0174
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at feaff000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at df40 [size=64]
        Capabilities: [dc] Power Management version 2


```

---

### Post by DBStevens on 2007-07-03
Going through some additional information I came across many mentions of issues with  ata_piix which is slowly replacing an older driver, it appears that there have been issues with a number of cdrw drives.  This has been noticed by Fedora Core, openSuse, and others including the current Gutsy Gibbon test release folks.   I'd say from the looks of this issue it is also a problem with Fiesty.

Folks with the slow boots showing the timeout messages might want to file a launchpad bug report.   Someone might have specific patches that address particular cdrw devices.  They might even want someone to test a patch that they can't because they don't have the hardware to test it on.

---

### Post by steven_vo on 2007-07-03
I also think that the trouble is your CD
try to burn Feisty 7.04 again, do install it
Dont use live CD

---

### Post by pancakelizard on 2007-07-03
> **DBStevens said:**
> Going through some additional information I came across many mentions of issues with  ata_piix which is slowly replacing an older driver, it appears that there have been issues with a number of cdrw drives.  This has been noticed by Fedora Core, openSuse, and others including the current Gutsy Gibbon test release folks.   I'd say from the looks of this issue it is also a problem with Fiesty.

Folks with the slow boots showing the timeout messages might want to file a launchpad bug report.   Someone might have specific patches that address particular cdrw devices.  They might even want someone to test a patch that they can't because they don't have the hardware to test it on.

I'll do that. Thanks a million for your help with everything.


Launchpad Address:
[https://bugs.launchpad.net/ubuntu/+bug/123905](https://bugs.launchpad.net/ubuntu/+bug/123905)

---

### Post by DBStevens on 2007-07-04
steven_vo,

What makes you think it is a bad burn?  

It is extremely unlikely that a bad burn would allow a system to even get close to the point that pancakelizard's system is.  The problems he had were related to resources to setup proper memory caching and from what I'm seeing a driver that is lacking proper information for specific cdrw devices. 

The same driver had no trouble with his dvdrw device and after mtrrs were freed up his memory caching was corrected and his sluggish system is no longer sluggish.

I rarely see coasters anymore and if folks checked their cds after they created them then this issue would be totally moot.

As for not using a liveCD, that I can see because the liveCD uses far more resources and relies on different software to do the install.  The difference in resource usage alone can prevent a liveCD from working on a resource constrained system.  I know because I've successfully installed the three major flavors of Ubuntu using the alternate install cds and never once has the liveCD for any distribution worked for my hardware.  In fact the current  platform I'm posting from and which isn't resource constrained just will not function with the liveCD versions.

---

### Post by DBStevens on 2007-07-04
Ubuntujonez and Erdaron,

You might want to look at the launchpad entery that pancakelizard made sign on and provide the information requested by the Ubuntu team member in the bug report that is a full dmesg and a lspaci -vvnn for your system, mentioning that you have the same general kind of issue and tell them what is attached to your IDE ports.

That way they will have multiple sources of information to work with and they'll understand that the problem affects more than one person.

I'd join in but I don't have any equipment that causes the gremlin to jump up and laugh at me.

Good luck and keep pluging away at it.

---

### Post by ubuntujonez on 2007-07-04
> **DBStevens said:**
> 
You might want to look at the launchpad entery that pancakelizard made sign on and provide the information requested by the Ubuntu team member in the bug report that is a full dmesg and a lspaci -vvnn for your system, mentioning that you have the same general kind of issue and tell them what is attached to your IDE ports.

...


Done. 

I finally got around to powering down and removing the SONY CD-R/RW CRX210E1. This took about 105 seconds off the boot time and results in a much happier system. Thankfully, I have USB DVD RW connected so I don't yet have to simply reinstall Efty  ;-)

-jonez

---

### Post by Erdaron on 2007-07-08
Same here. I removed my Sony CRX215E5 CDRW drive, and bootup went a lot faster (down by about 100 seconds). No more "qc timeout" messages in the kern.log, either.

Although in my case, the drive may have been defective - it has stopped reading data CDs.

This drive was factory installed in HP Pavilion 410e (although the only things left from the original box are CPU, case, and power supply).

Should I try finding a CDRW by a different manufacturer, or would this bug affect all of them? (My guess would be all of them).

I also have a Pioneer DVD drive, but that seems to cause no problems.

---

### Post by DBStevens on 2007-07-08
Erdaron,

Don't write that drive off yet.  Add your informationto that allready provided in that bug report.

The more information the better that means a dmesg, a lspci -vvnn, and the make/model of the devices on the IDE ports.

The bug is already marked high priority, whatever that means.

---

### Post by sml on 2007-07-21
> **steveneddy said:**
> Maybe, just maybe, the data on the CD was corrupt - did you check the md5 sums before burning the CD?

Oh please buddy. Why does everyone suggest that? The chances must be so very very low? I should start a new thread and actually check. That should be the very last resort to advise, not the first.

---

