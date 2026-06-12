---
title: "live cd boot for diskless intel based macbook?"
date: 2013-05-21
forum: Apple Hardware Users
---

### Post by tdbtdb on 2013-05-21
I have a 4 year old macbook with no hard drive. I want to boot it into ubuntu with a live cd or dvd. 

* Do I ned a special cd or dvd image, or will just the standard one from [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD) do okay? No mention of apple of mqacintosh on that page.

* do I need to replace the hard drive before booting? I'd rather not, I just want this for web surfing, usb stick and cloud storage good enough for me.

* bios vs. [rEFIt]("http://refit.sourceforge.net/")?

I found another page that describes how to boot from USB  ([http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/](http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/)),  not what I want (though maybe a workaround).

thanks,
TDB

---

### Post by binaryhermit on 2013-05-21
I think there are special liveCDs/liveDVDs for Macs because their EFI doesn't deal well with stuff made to run on a computer with a BIOS (or something)
And you shouldn't need to reinstall a drive.

---

### Post by tdbtdb on 2013-05-21
Yeah, that's why I'm asking. But the live cd page says nothing about macs, has no link, so I am stumped. How did you find the disk image you used to install ubuntu on your mac?
TDB

---

### Post by binaryhermit on 2013-05-21
I don't actually have a Mac, I'm just repeating what I've heard elsewhere.

Anyway, it seems that the special Mac disk image only exists for lubuntu, so the other flavors might have the Mac support baked in.  I'd try using a regular 64 bit live CD and come back for help if necessary.

---

### Post by tdbtdb on 2013-05-22
When I put in the dvd for ubuntu-12.04.2-desktop-amd64.iso and boot, I get white screen, then icons lower middle screen (keybd=man) on black background, then blinking cursor upper left. That's all.

Then I tried the USB key method. White screen, then I see a menu with "try ubuntu without installing" at the top, hit enter, black screen, the end.

This is on a macbook pro, 2009 vintage, no hard drive.

---

### Post by tdbtdb on 2013-05-22
I tried lubuntu's mac-specific disk image. Similar to the USB deal, I ended up with a useless blinking cursor on a black background. maybe this model is not compatible?

---

### Post by GhettoMrBob on 2013-05-25
That model should be compatible. I'd skip the lubuntu distro and instead boot to 12.04 AMD64 disk that you have. When you power on the machine hold down the alt/option key. You should see a selection for that disk. If possible select the EFI one.

---

### Post by miguelnegrao on 2013-05-29
What is the model of the macbook pro ?

```

sudo dmidecode -s system-product-name
```

if you have two graphic cards you probably need to boot in efi mode using rfefit and change the grub entry manually to disable the discrete card. That is what happened to me with a macbookpro 8,2. 

Try changing the grub entry so it looks similar to this:

```

recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod btrfs
    set root='hd0,gpt3'
    outb 0x728 1
    outb 0x710 2
    outb 0x740 2
    outb 0x750 0
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  f2e4e4d3-2d8e-4764-a818-de9176405c4b
    else
      search --no-floppy --fs-uuid --set=root f2e4e4d3-2d8e-4764-a818-de9176405c4b
    fi
    echo    'A carregar Linux 3.8.0-22-lowlatency ...'
    linux    /@/boot/vmlinuz-3.8.0-22-lowlatency root=UUID=f2e4e4d3-2d8e-4764-a818-de9176405c4b ro rootflags=subvol=@   video=efifb i915.modeset=1 i915.lvds_channel_mode=2 i915.lvds_use_ssc=0 nosplash
    echo    'A carregar ramdisk inicial ...'
    initrd    /@/boot/initrd.img-3.8.0-22-lowlatency
```

The things to add are:
```

    outb 0x728 1
    outb 0x710 2
    outb 0x740 2
    outb 0x750 0

```

and

```

video=efifb i915.modeset=1 i915.lvds_channel_mode=2 i915.lvds_use_ssc=0

```

Everytime I boot from my usb stick I have to enter this code by hand...

best,
Miguel

---

### Post by tdbtdb on 2013-06-07
I did this, EFi shows up but not selectable, no arrow underneath. So I  choose windows, it flashes the bootlogo, then goes black and dies. I think it let me select EFI once, but still did not work. (I've done it several times.)

---

### Post by tdbtdb on 2013-06-07
I can't do dmidecode because I can't boot. I don't know how to get to grub when booting from the DVD.

Here is info from a laptop I think is identical:


                                                                                                             Model Name:	MacBook   Model Identifier:	MacBook5,1   Processor Name:	Intel Core 2 Duo   Processor Speed:	2.4 GHz   Number Of Processors:	1   Total Number Of Cores:	2   L2 Cache:	3 MB   Memory:	2 GB   Bus Speed:	1.07 GHz   Boot ROM Version:	MB51.007D.B03   SMC Version (system):	1.40f2   Serial Number (system):	   Hardware UUID:	D28EE0A5-122D-5CC0-B4F5-A36534D7970F   Sudden Motion Sensor:   State:	Enabled   Intel High Definition Audio:    Device ID:	0x10DECB79   Audio ID:	63   Available Devices:   Headphone:   Connection:	Combo   Line In:   Connection:	Combo   Speaker:   Connection:	Internal   Internal Microphone:   Connection:	Internal   External Microphone:   Connection:	1/8-Inch Jack   S/P-DIF Out:   Connection:	Combo   S/P-DIF In:   Connection:	Combo  Apple Bluetooth Software Version:	2.1.9f10   Services:   Bluetooth File Transfer:   Folder other devices can browse:	~/BLUETOOTH_EXCHANGE   Requires Authentication:	Yes   State:	Enabled   Bluetooth File Exchange:   Folder for accepted items:	~/BLUETOOTH_EXCHANGE   Requires Authentication:	Yes   When other items are accepted:	Ask   When PIM items are accepted:	Ask   When receiving items:	Prompt for each file   State:	Enabled   Incoming Serial Ports:   Serial Port 1:   Name:	Bluetooth-PDA-Sync   RFCOMM Channel:	3   Requires Authentication:	No   Outgoing Serial Ports:   Serial Port 1:   Address:	   Name:	Bluetooth-Modem   RFCOMM Channel:	0   Requires Authentication:	No  HL-DT-ST DVDRW  GS21N:    Firmware Revision:	SA18   Interconnect:	ATAPI   Burn Support:	Yes (Apple Shipping Drive)   Cache:	2048 KB   Reads DVD:	Yes   CD-Write:	-R, -RW   DVD-Write:	-R, -R DL, -RW, +R, +R DL, +RW   Write Strategies:	CD-TAO, CD-SAO, CD-Raw, DVD-DAO   Media:	Insert media and refresh to show available burn speeds  NVIDIA GeForce 9400M:    Chipset Model:	NVIDIA GeForce 9400M   Type:	Display   Bus:	PCI   VRAM (Total):	256 MB   Vendor:	NVIDIA (0x10de)   Device ID:	0x0863   Revision ID:	0x00b1   ROM Revision:	3385   Displays: Color LCD:   Resolution:	1280 x 800   Depth:	32-Bit Color   Core Image:	Hardware Accelerated   Main Display:	Yes   Mirror:	Off   Online:	Yes   Quartz Extreme:	Supported   Built-In:	Yes Display Connector:   Status:	No Display Connected  Memory Slots:    ECC:	Disabled  BANK 0/DIMM0:    Size:	1 GB   Type:	DDR3   Speed:	1067 MHz   Status:	OK   Manufacturer:	0x802C   Part Number:	0x384A53463132383634485A2D314731463120   Serial Number:	0xFB000E91

---

