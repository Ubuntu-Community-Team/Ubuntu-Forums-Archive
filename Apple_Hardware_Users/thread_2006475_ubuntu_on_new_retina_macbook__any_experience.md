---
title: "ubuntu on new retina macbook : any experience ?"
date: 2012-06-19
forum: Apple Hardware Users
---

### Post by pounsg on 2012-06-19
Hi,
I'm just creating this threat to know if someone have any experience with linux on the new retina macbook pro...
Does it work ?
Thanks for sharing :)

---

### Post by AntiHero86 on 2012-06-19
Want this unit too. Only got to play with it for a few minutes at BestBuy but was very fast in OSX and Ubuntu off a flash drive. The screen would only do 1024 x 768 but it also had no internet connection to look for drives. So another question, how well does Ubuntu work with thunderbolt (thunderbolt to ethernet)

[[IMG]http://img690.imageshack.us/img690/4596/imag0221lv.jpg[/IMG]](http://imageshack.us/photo/my-images/690/imag0221lv.jpg/)

---

### Post by pounsg on 2012-06-22
So it boots :)
thanks

---

### Post by ASven on 2012-06-22
Hello!

Can anybody make some statements regarding the hardware support?

I want to know what works under Linux and what does not.

And maybe somebody can post the output of "lspci " and "lsusb"?

Thanks,
 Sven

---

### Post by houkouonchi on 2012-06-24
I have been pain-stakingly trying to get this working in linux (migrating my gentoo install to it).

Migrating was a PITA due to the fact that hunderbolt ethernet does not work at all on linux. I bought some usb ones oneline in the meantime but they have not yet arrived.

I had to do my install by rsyncing off my desktop to my latop (while running windows) and accessing the drive in a vm (mounting the root file-system) and then manually installing grub 0.97 after.


Right now I am able to triple boot. I was having a long boot delay with the 2.6.39.4 kernel I initially had but using 3.4.1 with some of the patches for the retina macbook its much faster during udev stuff (I believe due to the apple_smc stuff).

One guy reported getting full 3d working on opensuse. I am not sure how as I cannot for the life of me to get the nvidia drivers to work. I just get:

(==) Jun 22 04:00:03 NVIDIA(0): Using HW cursor
(==) Jun 22 04:00:03 NVIDIA(0): Video key set to default value of 0x101fe
(==) Jun 22 04:00:03 NVIDIA(0): Not mapping the primary surface by default.
(**) Jun 22 04:00:03 NVIDIA(0): Enabling 2D acceleration
(EE) Jun 22 04:00:03 NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
(EE) Jun 22 04:00:03 NVIDIA(0):     check your system's kernel log for additional error
(EE) Jun 22 04:00:03 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) Jun 22 04:00:03 NVIDIA(0):     README for additional information.
(EE) Jun 22 04:00:03 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Jun 22 04:00:03 NVIDIA(0): Failing initialization of X screen 0

and kmesg:

nvidia 0000:01:00.0: irq 47 for MSI/MSI-X
NVRM: failed to copy vbios to system memory.
NVRM: RmInitAdapter failed! (0x30:0xffffffff:858)
NVRM: rm_init_adapter(0) failed


I was able to get wireless working using the method mentioned here from the ubuntu live cd:

[http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html](http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html)

However; it was 802.11g and i was getting so much packetloss after doing a large transfer i was lucky to get 200-300 KB/sec (compared to 9-10 megabytes/sec I get from Mac OS X and windows).

So I am not having much luck so far. A real bomber as the main purpose of buying this macbook was to run linux.

---

### Post by gschwind on 2012-06-25
Hello houkouonchi,

did you try an up-to-date kernel and switcheroo ?

[http://en.gentoo-wiki.com/wiki/Vga_switcheroo](http://en.gentoo-wiki.com/wiki/Vga_switcheroo)

I don't find a better howto. As far as remenber the best way to start is to start without modeset enable ( nomodeset=1 as kernel option ). from that you can select your video card with /sys/kernel/debug/vgaswitcheroo/switch then load the coresponding driver.

I know switcheroo working with radeon (I already used it), but I have no idea whether it's work with nvidia.

Another question is since nvidia driver doesn't work, do intel driver work ?

Thank you

---

### Post by houkouonchi on 2012-06-25
> **gschwind said:**
> Hello houkouonchi,

did you try an up-to-date kernel and switcheroo ?

[http://en.gentoo-wiki.com/wiki/Vga_switcheroo](http://en.gentoo-wiki.com/wiki/Vga_switcheroo)

I don't find a better howto. As far as remenber the best way to start is to start without modeset enable ( nomodeset=1 as kernel option ). from that you can select your video card with /sys/kernel/debug/vgaswitcheroo/switch then load the coresponding driver.

I know switcheroo working with radeon (I already used it), but I have no idea whether it's work with nvidia.

Another question is since nvidia driver doesn't work, do intel driver work ?

Thank you


I am running kernel 3.4.1. I do have vga_switcheroo set to y in my kernel but doesn't appear to do anything (no /sys/kernel/debug/vgaswitcheroo dir).

---

### Post by gschwind on 2012-06-25
you have to enable debug file system :

```
Kernel hacking --->
   
[*] Debug Filesystem

```and then mount it as root :
```
mkdir -p /sys/kernel/debug
mount -t debugfs /sys/kernel/debug

```then you should have the vgaswitcheroo should apear, you can make cat over it to get the list of videocards

[EDIT]
I can't enable it on my system, so I can't be more precise
You mustn't start X to be able to switch, if you use gentoo use : rc-update del xdm

---

### Post by houkouonchi on 2012-06-25
> **gschwind said:**
> you have to enable debug file system :

```
Kernel hacking --->
   
[*] Debug Filesystem

```and then mount it as root :
```
mkdir -p /sys/kernel/debug
mount -t debugfs /sys/kernel/debug

```then you should have the vgaswitcheroo should apear, you can make cat over it to get the list of videocards

[EDIT]
I can't enable it on my system, so I can't be more precise
You mustn't start X to be able to switch, if you use gentoo use : rc-update del xdm

All my kernels I build myself and X was not set to start at boot (the only way for me to get X working at all is via the VESA driver).

Anyway I  have CONFIG_DEBUG_FS=y and /sys/kernel/debug is mounted. I see quite a few directories/files in there but no vga_switcheroo =(

I verified it is enabled even with zcat /proc/config.gz.

---

### Post by gschwind on 2012-06-26
it's not a good news :/ , I hope this could be solved.

then do you are able to start X at native resolution with intel driver ?

Thanks for you report, That help me to make my choice.

---

### Post by houkouonchi on 2012-06-26
No. my X installation is pretty old and no intel driver new enough for it. Can't get the full resolution at all right now.

---

### Post by Omni-Vi on 2012-06-30
Would you be willing to try the new Ubuntu alpha 2? It features a recent kernel and comes as Apple version.

---

### Post by atte on 2012-07-09
Using rEFIt and booting USB with Alpha 2 gives boot menu but both Try w/o install and Install Ubuntu just gives black screen. Maybe I can get it to boot not so silently...


Oh, like you said, there is a Mac version, will give that one a try.

---

### Post by atte on 2012-07-09
Sorry, even the Mac version of A2 gave black screen. Even when I removed silent and splash from the kernel boot line... any ideas?

---

### Post by blayne on 2012-07-09
> **atte said:**
> Sorry, even the Mac version of A2 gave black screen. Even when I removed silent and splash from the kernel boot line... any ideas?

I have been playing with the Xubuntu Alpha2 installer, I got it the "Install Xubuntu" option running by adding "nointremap nomodeset" to the grub boot parameters.

I made the mistake of using btrfs as my home filesystem as there is a bug in the 3.5 rc kernels causing segfaults. (I think its fixed in 3.5-rc6, Havent had time to test it yet.)

Before btrfs started segfaulting, I had a working terminal install (No X). 

Thunderbolt semi works, booting with a apple thunderbolt ethernet connected, it gets detected in lspci but gave no network access. plugging it in after boot it was not detected.

---

### Post by blayne on 2012-07-10
> **blayne said:**
> I have been playing with the Xubuntu Alpha2 installer, I got it the "Install Xubuntu" option running by adding "nointremap nomodeset" to the grub boot parameters.

I made the mistake of using btrfs as my home filesystem as there is a bug in the 3.5 rc kernels causing segfaults. (I think its fixed in 3.5-rc6, Havent had time to test it yet.)

Before btrfs started segfaulting, I had a working terminal install (No X). 

Thunderbolt semi works, booting with a apple thunderbolt ethernet connected, it gets detected in lspci but gave no network access. plugging it in after boot it was not detected.

So after updating to 3.5-rc6 everything is now comming together.

I installed the 302.17 Nvidia drivers I now have X working perfectly! I have dual screens working with a thunderbolt to DVI adapter. There are some issues with DPI on some applications. Some websites in chrome also render with tiny text.

I installed the broadcom wifi drivers they installed with out problems following the instructions on [http://linuxwireless.org/en/users/Drivers/b43/](http://linuxwireless.org/en/users/Drivers/b43/) I get about 2-3MB/s using rsync (about 1MB/s slower than in OSX)

Battery life is a little lacking, it is looking around 4 hours on wifi while surfing / apt-get installing packages.

Still no luck on the thunderbolt ethernet adapter, it is a :
```
0a:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57762 Gigabit Ethernet PCIe
	Subsystem: Apple Inc. Device 00f6
	Physical Slot: 9
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 0
	Region 0: Memory at ce100000 (64-bit, prefetchable) [disabled] [size=64K]
	Region 2: Memory at ce110000 (64-bit, prefetchable) [disabled] [size=64K]
	Expansion ROM at ce120000 [disabled] [size=64K]
	Capabilities: <access denied>

``` 

It looks like it should be supported via the tg3 module, however the tg3 module that came with 3.5-rc6 doesnt seem to support it. I had a quick look at building it myself as the source code does mention the model number. But I am having issues getting it to build.

---

### Post by raccoonone on 2012-07-10
I got Ubuntu 12.04 mostly working on my Macbook Pro Retina, and wrote up a short [blog post]("http://cberner.com/2012/07/10/installing-ubuntu-12-04-on-macbook-pro-retina/") about it.

The thing I'm having the most trouble with now is the graphics. Neither the HDMI nor the DVI to Thunderbolt connector I got seem to work, so I can't use my external monitor. May have to give Quantal a try, since it sounds like people have been having some luck with that.

---

### Post by raccoonone on 2012-07-10
> **blayne said:**
> So after updating to 3.5-rc6 everything is now comming together.

I installed the 302.17 Nvidia drivers I now have X working perfectly! I have dual screens working with a thunderbolt to DVI adapter. There are some issues with DPI on some applications. Some websites in chrome also render with tiny text.

I installed the broadcom wifi drivers they installed with out problems following the instructions on [http://linuxwireless.org/en/users/Drivers/b43/](http://linuxwireless.org/en/users/Drivers/b43/) I get about 2-3MB/s using rsync (about 1MB/s slower than in OSX)

Battery life is a little lacking, it is looking around 4 hours on wifi while surfing / apt-get installing packages.

Still no luck on the thunderbolt ethernet adapter, it is a :
```
0a:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57762 Gigabit Ethernet PCIe
	Subsystem: Apple Inc. Device 00f6
	Physical Slot: 9
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 0
	Region 0: Memory at ce100000 (64-bit, prefetchable) [disabled] [size=64K]
	Region 2: Memory at ce110000 (64-bit, prefetchable) [disabled] [size=64K]
	Expansion ROM at ce120000 [disabled] [size=64K]
	Capabilities: <access denied>

``` 

It looks like it should be supported via the tg3 module, however the tg3 module that came with 3.5-rc6 doesnt seem to support it. I had a quick look at building it myself as the source code does mention the model number. But I am having issues getting it to build.

Did you have to do anything special to get your second monitor working? I've been trying to make mine work, but so far the Thunderbolt-to-DVI connector I have doesn't seem to be working

---

### Post by blayne on 2012-07-11
> **raccoonone said:**
> Did you have to do anything special to get your second monitor working? I've been trying to make mine work, but so far the Thunderbolt-to-DVI connector I have doesn't seem to be working


in your blog post it mentions you are using the 295.59 nvidia drivers. Have you tried upgrading to the 302.17 drivers?

on a side note, I now have the thunderbolt ethernet adapter working.

I had to make a minor change to the tg3 kernel module. It needs to be plugged in at boot as I still havent worked out how to get hot plug working.

---

### Post by raccoonone on 2012-07-11
Ya, I tried the 302.17 drivers also, but didn't have any luck. I did an upgrade install from 12.04 though, so maybe I should just do a fresh install with 12.10 alpha.

---

### Post by raccoonone on 2012-07-11
> **blayne said:**
> in your blog post it mentions you are using the 295.59 nvidia drivers. Have you tried upgrading to the 302.17 drivers?

on a side note, I now have the thunderbolt ethernet adapter working.

I had to make a minor change to the tg3 kernel module. It needs to be plugged in at boot as I still havent worked out how to get hot plug working.

Just tried a fresh installation of 12.10 Alpha 2, and still no luck. Did you have to install Bumblebee or anything else to get your graphics working?

---

### Post by blayne on 2012-07-11
> **raccoonone said:**
> Just tried a fresh installation of 12.10 Alpha 2, and still no luck. Did you have to install Bumblebee or anything else to get your graphics working?
 
what sort of DVI adapter are you using? I am just using a $10 Deal extreme adapter. 
I read somewhere that adding the following option to your Xorg config might help.
```

Option         "UseDPLib" "off"

```


A couple other tricks I found on the net:

Keyboard backlight : (value between 0-255)
```

echo 250 > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness

```

Fans :
I cant get them to automatically change their speeds based on temp, I can manually control them using : (rpm value 2000-5900)
```
 
echo 1 > /sys/devices/platform/applesmc.768/fan1_manual
echo 5600 > /sys/devices/platform/applesmc.768/fan1_output
echo 1 > /sys/devices/platform/applesmc.768/fan2_manual
echo 5600 > /sys/devices/platform/applesmc.768/fan2_output

```

---

### Post by BlueDragonX on 2012-07-12
Blayne:
Can you post your kernel config? When I load the nvidia driver all I get is a blank screen. I figure I'm missing something.

---

### Post by blayne on 2012-07-12
> **BlueDragonX said:**
> Blayne:
Can you post your kernel config? When I load the nvidia driver all I get is a blank screen. I figure I'm missing something.

Sure it is just the default 3.5-2 config from ubuntu.

Ive also attached my xorg config, Xorg.log and my dmesg log incase any of that helps (ignore the applesmc errors in dmesg as I havent replaced my autoloading moudle with the patched version)

[http://c.ac.nz/log/2012-07-13/Xorg.0.log](http://c.ac.nz/log/2012-07-13/Xorg.0.log)
[http://c.ac.nz/log/2012-07-13/dmesg.log](http://c.ac.nz/log/2012-07-13/dmesg.log)
[http://c.ac.nz/log/2012-07-13/xorg.conf](http://c.ac.nz/log/2012-07-13/xorg.conf)
[http://c.ac.nz/log/2012-07-13/config-3.5.0-2-generic](http://c.ac.nz/log/2012-07-13/config-3.5.0-2-generic)

my grub menu entry : 
```

menuentry 'Ubuntu, with Linux 3.5.0-2-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set=root c0f05e89-7dd8-460b-ac15-52b4489a2177
	linux	/vmlinuz-3.5.0-2-generic root=UUID=95c51cc0-5fc3-4f8f-a1b9-43fba3165789 ro rootflags=subvol=@   nointremap nomodeset
	initrd	/initrd.img-3.5.0-2-generic
}

```

The applesmc patch I used was taken from [this forum post]("http://forums.opensuse.org/english/get-technical-help-here/laptop/476258-howto-2012-retina-display-macbook-pro-opensuse-linux-2.html#post2470778")

```

diff --git a/drivers/hwmon/applesmc.c b/drivers/hwmon/applesmc.c
index 2cde9ec..7f07c2b 100644
--- a/drivers/hwmon/applesmc.c
+++ b/drivers/hwmon/applesmc.c
@@ -174,7 +174,7 @@ static int __wait_status(u8 val)
 
 	for (us = APPLESMC_MIN_WAIT; us < APPLESMC_MAX_WAIT; us <<= 1) {
 		udelay(us);
-		if ((inb(APPLESMC_CMD_PORT) & APPLESMC_STATUS_MASK) == val)
+		if ((inb(APPLESMC_CMD_PORT) & val) == val)
 			return 0;
 	}
 
-- 


```

---

### Post by atte on 2012-07-13
Thank you blayne, nointremap and nomodeset did the job!

I now have 12.10 A2 insalled. Tried default nvidia-current and nvidia-current-updates but it is as if X does not manage to load the nvidia module.

Where did you install the driver from?

---

### Post by atte on 2012-07-13
Oh, never mind. After modprobe nvidia-current-updates and lightdm restart, X is now running!

---

### Post by BlueDragonX on 2012-07-14
I've patched in initial support for the nouveau open source video driver but I'm still having one problem. The screen's displaying as if the modeline is incorrect.

Can any of you post the X modeline that gets used when using the nvidia proprietary driver?

---

### Post by blayne on 2012-07-15
> **BlueDragonX said:**
> I've patched in initial support for the nouveau open source video driver but I'm still having one problem. The screen's displaying as if the modeline is incorrect.

Can any of you post the X modeline that gets used when using the nvidia proprietary driver?

Using 'xvidtune -show', is this what you want?

```

"2880x1800"   337.75   2880 2928 2960 3040   1800 1803 1809 1852 +hsync -vsync

```

---

### Post by BlueDragonX on 2012-07-15
Yes indeed, thanks.

That's the same modeline I have. Something's not quite right here.

---

### Post by blayne on 2012-07-15
> **BlueDragonX said:**
> Yes indeed, thanks.

That's the same modeline I have. Something's not quite right here.

whats going wrong?

without the 'nomodeset' boot parameter my screen goes all garbled when X starts, are you using that?

---

### Post by BlueDragonX on 2012-07-15
Actually I'm working on implementing nouveau support, so *not* using nomodeset is entirely the point :)

---

### Post by nsicad on 2012-07-15
Hi,

I managed to boot usb stick 2G using Linux Mint 13 (cinnamon). I downloaded linux mint 13 cinnamon .iso converted to .dmg and dd into usb stick. 

Linux Mint 13 has EFI boot that why it is possible to boot without even installing rEFit or reFind. It boots in 'compatibility mood'. I just play a bit, no internet (WIFI), no nvidia,  trackpad works. I have not installed in internal hdd. I am waiting for Mountain Lion to available so I don't need to reinstall linux again.

However, I am thinking of installing, linux mint or Ubuntu in external usb hard drive. I think this is possible based on what I see in the linux mint 13 installation .iso. I just have to upgrade the kernel into 3.5.x using the ubuntu kernel repository.

Any tips ideas how to make ubuntu 12.x using in external hard drive for new macbookpro (mid 2012)?

Edit: I managed to install Linux Mint 13 in external hard drive without touching my internal SSD. I partitioned my 1 Tb Toshiba using Mac OS X Lion Disk Utility and then I use Gparted in my liveusb (Mint 13) to further partitioning the drive. I got 2 Mac OS partition (HFS+), 3 ext4 partitions and 1 MSDOS Fat32 partition. My linux now boots with this exteral drive. Athought some errors still. No Wifi since the yet. I need to update the linux kernel into 3.5.x so I will got most of the drivers for this Mac (10.1).

---

### Post by ASven on 2012-07-16
Has anybody archieved running the MBPr with the Intel GPU only?
(and to disable the nVidia chip completly?)

---

### Post by BlueDragonX on 2012-07-16
> **ASven said:**
> Has anybody archieved running the MBPr with the Intel GPU only?
(and to disable the nVidia chip completly?)

No, not yet. Currently neither the nVidia or Intel chips are fully supported by the open source drivers. That will need to be achieved before work can be started on the gmux driver.

I'm currently working on full nouveau support. It's nearly a there. Once that's complete I'll move on to getting the Intel chip supported.

---

### Post by Omni-Vi on 2012-07-17
Just wanted to thank all of you for the work your putting into this. It's really appreciated!

:D

---

### Post by nsicad on 2012-07-18
lspci -vnn 

########
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0fd5] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Apple Inc. Device [106b:00f2]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at c0000000 (32-bit, non-prefetchable) [size=16M]
    Memory at 90000000 (64-bit, prefetchable) [size=256M]
    Memory at a0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 2000 [size=128]
    Expansion ROM at c1000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel modules: nouveau, nvidiafb

01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0e1b] (rev a1)
    Subsystem: Apple Inc. Device [106b:00f2]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at c1080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

03:00.0 Ethernet controller [0200]: Broadcom Corporation Device [14e4:16a3] (rev 10)
    Subsystem: Broadcom Corporation Device [14e4:16b4]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at c1800000 (64-bit, prefetchable) [size=64K]
    Memory at c1810000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at c1830000 [disabled] [size=2K]
    Capabilities: <access denied>

03:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10) (prog-if 01)
    Subsystem: Broadcom Corporation Device [14e4:96bc]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at c1820000 (64-bit, prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

04:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Apple Inc. Device [106b:00ef]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at c1900000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: bcma-pci-bridge
    Kernel modules: bcma

######

Still I could not make my wireless working?

I think there is bug on b43 with kernel
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/950295](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/950295)

---

### Post by nsicad on 2012-07-18
I am trying to use the latest kernel 3.5.0.rc7 (ubuntu) i386.

I got this problem.

"Refined TSC clocksoruce
Switching to clocksource"

Hung.

I tried these and it did not work.

tsc=reliable

clocksource=acpi_pm


The power to the external usb drive is cut (i.e. not power light).

---

### Post by BlueDragonX on 2012-07-18
> **nsicad said:**
> lspci -vnn 

...snip...

Still I could not make my wireless working?

I think there is bug on b43 with kernel
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/950295](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/950295)

There is no bug, wireless works fine. You need to load the firmware for the BCM4331 before it works.

You'll need to use fwcutter to pull the firmware out of a relatively new BCM driver.

1. Download driver:
wget [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)

2. Install fwcutter:
apt-get install b43-fwcutter

3. Extract firmware:
tar -xf broadcom-wl-5.100.138.tar.bz2
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.100.138/linux/wl_apsta.o

6. Reload your b43 kernel module:
sudo rmmod b43
sudo modprobe b43

7. Use your wireless.

> **nsicad said:**
> I am trying to use the latest kernel 3.5.0.rc7 (ubuntu) i386.

I got this problem.

"Refined TSC clocksoruce
Switching to clocksource"

Hung.

I tried these and it did not work.

tsc=reliable

clocksource=acpi_pm


The power to the external usb drive is cut (i.e. not power light).

Try passing on the kernel commandline on boot: noapic

I've been running 3.5.0-r7 since release. It has one of my patches in it =P

---

### Post by BlueDragonX on 2012-07-18
Is anyone else having issues resuming from suspend? Mine doesn't come back up after suspending in Gnome 3. I just get a blank screen. I end up having to long-press the power button to force it off.

---

### Post by blayne on 2012-07-18
> **BlueDragonX said:**
> Is anyone else having issues resuming from suspend? Mine doesn't come back up after suspending in Gnome 3. I just get a blank screen. I end up having to long-press the power button to force it off.

My suspend works fine, however I loose my apple thunderbolt ethernet when it loads back up.

I think this line is the reason for loosing my ethernet.
```

[ 5231.201061] tg3 0000:0a:00.0: eth0: No firmware running

```

trying to rmmod -> insmod the tg3 module gives me

```

[ 5296.931109] tg3 0000:0a:00.0: tg3_abort_hw timed out, TX_MODE_ENABLE will not clear MAC_TX_MODE=ffffffff
[ 5310.884115] pcieport 0000:00:01.1: wake-up capability enabled by ACPI
[ 5315.395102] tg3.c:v3.123 (March 21, 2012)
[ 5315.409132] pci_raw_set_power_state: 1 callbacks suppressed
[ 5315.409143] tg3 0000:0a:00.0: Refused to change power state, currently in D3
[ 5315.409176] tg3 0000:0a:00.0: Cannot find Power Management capability, aborting
[ 5315.409200] tg3: probe of 0000:0a:00.0 failed with error -5

```

What does your syslog say about the resume?

---

### Post by nsicad on 2012-07-19
> **BlueDragonX said:**
> There is no bug, wireless works fine. You need to load the firmware for the BCM4331 before it works.

You'll need to use fwcutter to pull the firmware out of a relatively new BCM driver.

1. Download driver:
wget [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)

2. Install fwcutter:
apt-get install b43-fwcutter

3. Extract firmware:
tar -xf broadcom-wl-5.100.138.tar.bz2
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.100.138/linux/wl_apsta.o

6. Reload your b43 kernel module:
sudo rmmod b43
sudo modprobe b43

7. Use your wireless.



Try passing on the kernel commandline on boot: noapic

I've been running 3.5.0-r7 since release. It has one of my patches in it =P


BlueDragonX,

Thank you for these tips and steps to make wireless working.

Yes, my wireless pci card (built-in) is working (both liveusb install and external drive).

Ubuntu 3.5.rc7 kernel with nointremap noapic nopci  boot parameters did not work for this kernel.

#####

I don't know which nvidia driver (proprietory or FOSS) in ubuntu repository works for retina.

I broke my Xorg install in my external hard drive. I need to reinstall again. It seems that at moment VESA is the one working with nvidia common.

Any tips which nvidia driver works best with the graphic card of retina.

Thanks.

Noli

---

### Post by blayne on 2012-07-19
> **nsicad said:**
> BlueDragonX,

Thank you for these tips and steps to make wireless working.

Yes, my wireless pci card (built-in) is working (both liveusb install and external drive).

Ubuntu 3.5.rc7 kernel with nointremap noapic nopci  boot parameters did not work for this kernel.

#####

I don't know which nvidia driver (proprietory or FOSS) in ubuntu repository works for retina.

I broke my Xorg install in my external hard drive. I need to reinstall again. It seems that at moment VESA is the one working with nvidia common.

Any tips which nvidia driver works best with the graphic card of retina.

Thanks.

Noli


I use 302.17. 

I'm not sure about your kernel parameters, 'noapic' and 'nopci' what are they meant to fix?
I don't use them my boot only has 'nointremap' and 'nomodeset' (my grub config is in a previous post)

---

### Post by nsicad on 2012-07-19
> **blayne said:**
> I use 302.17. 

I'm not sure about your kernel parameters, 'noapic' and 'nopci' what are they meant to fix?
I don't use them my boot only has 'nointremap' and 'nomodeset' (my grub config is in a previous post)

What is exactly the name of this "302.17" driver for nvidia? Which ubuntu release it is available, 12.04 or 12.10? Any URL link for this driver?

BlueDragonX suggested "noapci" to fix TSC clocksource hanging. It works as well with 3.2 kernel (Ubuntu 12.04 / Mint 13).

Edit: OK. I got the link for 302.17 Nvidia installation.

[http://www.unixmen.com/nvidia-302-17-has-been-released-install-in-ubuntu12-04-linuxmint13-fedora17/](http://www.unixmen.com/nvidia-302-17-has-been-released-install-in-ubuntu12-04-linuxmint13-fedora17/)

########
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings

#########

Thanks for the tip on 301.17 nviidia

---

### Post by blayne on 2012-07-19
> **nsicad said:**
> What is exactly the name of this "302.17" driver for nvidia? Which ubuntu release it is available, 12.04 or 12.10? Any URL link for this driver?

BlueDragonX suggested "noapci" to fix TSC clocksource hanging. It works as well with 3.2 kernel (Ubuntu 12.04 / Mint 13).


hmm it appears they updated the drivers to 304.22 [http://www.geforce.com/drivers/results/46524](http://www.geforce.com/drivers/results/46524)

I have just installed them, everything seems to be working fine.

---

### Post by YannBuntu on 2012-07-19
**@all:** has anyone been able to boot MacOS directly from the GRUB menu ? if yes, please could you indicate your [BootInfo URL]("https://help.ubuntu.com/community/Boot-Info")? thanks

---

### Post by nsicad on 2012-07-19
I used the 302.17 nvidia driver.

It did not fix my problem.

Here's part of the log Xorg.0.log.

#####
[   271.186] (II) LoadModule: "ramdac"
[   271.186] (II) Module "ramdac" already built-in
[   271.186] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   271.186] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   271.186] (II) Loading /usr/lib/xorg/modules/libfb.so
[   271.186] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   271.186] (==) NVIDIA(0): RGB weight 888
[   271.186] (==) NVIDIA(0): Default visual is TrueColor
[   271.186] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   271.186] (**) NVIDIA(0): Option "UseDPLib" "off"
[   271.186] (**) NVIDIA(0): Enabling 2D acceleration
[   271.397] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
[   271.397] (EE) NVIDIA(0):     check your system's kernel log for additional error
[   271.397] (EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
[   271.397] (EE) NVIDIA(0):     README for additional information.
[   271.397] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[   271.398] (II) UnloadModule: "nvidia"
[   271.398] (II) Unloading nvidia
[   271.398] (II) UnloadModule: "wfb"
[   271.398] (II) Unloading wfb
[   271.398] (II) UnloadModule: "fb"
[   271.398] (II) Unloading fb
[   271.398] (EE) Screen(s) found, but none have a usable configuration.
[   271.398] 
Fatal server error:
[   271.398] no screens found
[   271.398] 

######################

What is the problem here? 

Can somebody post their Xorg.conf that works with 302.17 nvidia driver?

Thanks.

Edit: I guess we have to remove the other driver for this driver to work. I find this entries here.

[https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting](https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting)

Also make sure that you don't have drivers installed for older cards. On Ubuntu, these are the packages nvidia-96, nvidia-173 and nvidia-180.

**Failed to initialize the NVIDIA GPU at PCI:1:0:0. Please ...**

  PCI:1:0:0 may vary, but take a look at the last lines of the kernel log (usually located at /var/log/kern.log, /var/log/kernel or /var/log/messages). You're probably using an outdated driver or messed a bit with improper ACPI calls (see above).



Now, I think we have to purge nvidia-*

sudo apt-get purge nvidia-96
sudo apt-get purge nvidia-173
sudo apt-get purge nvidia-180
Remove your xorg.conf
sudo rm /etc/X11/xorg.conf

Reinstall xorg completely (????, I don't know about this?)


sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64 

Re-configure Xorg
sudo dpkg-reconfigure xserver-xorg 

Reboot
sudo reboot

Note: 

These steps above did not solve the problem of nvidia current 302.17 working in this macbookpro retina - 2.3 Ghz (base model).

Removing all the nvidia and installing nvidia current again did not solve this problem.

This is the same problem experienced by OpenSuse for Retina.
[http://forums.opensuse.org/english/get-technical-help-here/laptop/476258-howto-2012-retina-display-macbook-pro-opensuse-linux-3.html](http://forums.opensuse.org/english/get-technical-help-here/laptop/476258-howto-2012-retina-display-macbook-pro-opensuse-linux-3.html)

---

### Post by nsicad on 2012-07-19
> **blayne said:**
> hmm it appears they updated the drivers to 304.22 [http://www.geforce.com/drivers/results/46524](http://www.geforce.com/drivers/results/46524)

I have just installed them, everything seems to be working fine.

Blayne, what is your kernel?

---

### Post by blayne on 2012-07-19
> **nsicad said:**
> Blayne, what is your kernel?

I am using 3.5-rc7 with a couple of patches.

1. tg3.c - enables thunderbolt Ethernet adapters
2. applesmc.c - allows reading/setting fan/keyboard backlight.

---

### Post by nsicad on 2012-07-19
> **blayne said:**
> I am using 3.5-rc7 with a couple of patches.

1. tg3.c - enables thunderbolt Ethernet adapters
2. applesmc.c - allows reading/setting fan/keyboard backlight.

Thanks Blayne,

I just to tell everybody that my macbookpro retina is base model - 2.3Ghz. It has problem with TSC clocksource with 3.5-rc7 ubuntu kernel.

This is the log for the TSC error:

#####

"Refined TSC clocksource calibration : 2294.786 Mhz
Switching to clocksource TSC"

######

The system hangs (i.e. cutoff the usb power to hard drive. 3.5-rc7 kernel does not like the 2.3Ghz CPU (i.e. 2294.786 Mhz).

Blayne, what is the CPU of your Macbookpro retina?

---

### Post by blayne on 2012-07-19
> **nsicad said:**
> 
Blayne, what is the CPU of your Macbookpro retina?
```

~ &#10140; cat /proc/cpuinfo | grep 'model name'
model name	: Intel(R) Core(TM) i7-3720QM CPU @ 2.60GHz

```

---

### Post by nsicad on 2012-07-19
> **blayne said:**
> ```

~ &#10140; cat /proc/cpuinfo | grep 'model name'
model name    : Intel(R) Core(TM) i7-3720QM CPU @ 2.60GHz

```

This explained why you are not getting the TSC error.

My CPU is:

Intel(R) Core(TM) i7-3615QM CPU @ 2.30GHz

---

### Post by BlueDragonX on 2012-07-20
> **nsicad said:**
> BlueDragonX suggested "noapci" to fix TSC clocksource hanging. It works as well with 3.2 kernel (Ubuntu 12.04 / Mint 13).


Just to be clear, it's noapic NOT noacpi. Why do you need nopci? That shouldn't be necessary.

 Without noapic mine would hang after the initrd was loaded. There is some configuration in my kernel preventing APIC from working but I haven't found it.

---

### Post by nsicad on 2012-07-20
> **BlueDragonX said:**
> Just to be clear, it's noapic NOT noacpi. Why do you need nopci? That shouldn't be necessary.

 Without noapic mine would hang after the initrd was loaded. There is some configuration in my kernel preventing APIC from working but I haven't found it.

BlueDragonX, what is your CPU and kernel that you are using?

---

### Post by BlueDragonX on 2012-07-20
> **nsicad said:**
> BlueDragonX, what is your CPU and kernel that you are using?

I have the 2.6GHz  CPU and I'm running 3.5-rc7 with a collection of patches.

---

### Post by nsicad on 2012-07-21
Just like to put this link ([Greg Kroah-Hartman]("https://plus.google.com/111049168280159033135"). He is trying to boot linux in his MacBookPro retina as well). 

[https://plus.google.com/111049168280159033135/posts](https://plus.google.com/111049168280159033135/posts)

My problem regarding MacBookPro retina users porting to linux, most of the blogs / porters not mentioning the CPU of their MacBookPro retina. I think the CPU plays either you can boot your MacBookPro retina with various Linux kernels.

MacBookPro Retina (2.3Ghz) one I got have problems with:

1. TSC clocksource in 3.5-rc7
2. nvidia native driver (307.12), the nvidia card in PCI slot is not recognized in 3.2 kernel (default - Linux mint 13 / 12.04).

---

### Post by SoulTechnologist on 2012-07-22
I have been using 12.04 and it works GREAT! :guitar:

---

### Post by nsicad on 2012-07-23
> **SoulTechnologist said:**
> I have been using 12.04 and it works GREAT! :guitar:

What is the CPU for your retina and the kernel?

Could post the results of ddcprobe in the terminal.

sudo ddcprobe

Edit: This is fedora forum for mac.

[http://forums.fedoraforum.org/forumdisplay.php?f=51](http://forums.fedoraforum.org/forumdisplay.php?f=51)

It seems that Ubuntu is ahead than fedora in booting Macbookpro retina.

Please note that if you are posting in this thread, kindly indicate your Macbookpro retina CPU and kernel that you are booting and also the upgrade if you make it working. It night also good which nvidia driver you are using and resolution.

Again, 2.6Ghz CPU macbookpro retina seems to be working well with current status of the kernel.

---

### Post by nsicad on 2012-07-23
> **BlueDragonX said:**
> I have the 2.6GHz  CPU and I'm running 3.5-rc7 with a collection of patches.

BlueDragonX,

Did you use this drver (i.e. nouveau)?

[http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)

Did you patched something in this driver, any link where to download it and instruction how to install it, if any?

---

### Post by BlueDragonX on 2012-07-23
> **nsicad said:**
> BlueDragonX,

Did you use this drver (i.e. nouveau)?


Go back and read my posts. I'm implementing support for the MBP Retina in nouveau right now.

> **nsicad said:**
> Did you patched something in this driver, any link where to download it and instruction how to install it, if any?

See my patches in my Gentoo overlay: [https://github.com/BlueDragonX/fm-overlay/tree/master/sys-kernel/retina-sources/files](https://github.com/BlueDragonX/fm-overlay/tree/master/sys-kernel/retina-sources/files)

---

### Post by houkouonchi on 2012-07-29
2.3 Ghz here working fine with my own custom built kernel (not using noapic and pretty sure kernel has apic support).

---

### Post by nsicad on 2012-07-29
> **houkouonchi said:**
> 2.3 Ghz here working fine with my own custom built kernel (not using noapic and pretty sure kernel has apic support).

What kernel are you using? 

Did you get nvidia driver working with pci-e? 

What resolution did manage to achieve and what driver?

Please post details.

---

### Post by houkouonchi on 2012-07-29
> **nsicad said:**
> What kernel are you using? 

Did you get nvidia driver working with pci-e? 

What resolution did manage to achieve and what driver?

Please post details.

I am using 3.4.1 I believe. Vanilla kernel plus the macbook patches which I believe is in this thread. I thought I posted in this thread already with details.

I have X working via the nvidia driver with full 2880x1800 resolution and 3d support (running XGL).

I assume the driver works with PCI-E as performance did not appear to be absolute crap but did not check nvidia-settings.

---

### Post by kkrull on 2012-07-30
> **nsicad said:**
> Hi,

I managed to boot usb stick 2G using Linux Mint 13 (cinnamon). I downloaded linux mint 13 cinnamon .iso converted to .dmg and dd into usb stick. 

Linux Mint 13 has EFI boot that why it is possible to boot without even installing rEFit or reFind...

I have not been so lucky with Linux Mint 13 Cinnamon x64 on my 2.3GHz 16G rMBP. I have not been able to complete loading from DVD, either through rEFIt or holding option\alt. My first error is:

0.066781 Kernel panic - not syncing: timer doesn't work through Interrupt remapped IO-APIC

You can see the full set of ten errors in the attached screenshot.

Any ideas?

---

### Post by nsicad on 2012-07-30
> **kkrull said:**
> I have not been so lucky with Linux Mint 13 Cinnamon x64 on my 2.3GHz 16G rMBP. I have not been able to complete loading from DVD, either through rEFIt or holding option\alt. My first error is:

0.066781 Kernel panic - not syncing: timer doesn't work through Interrupt remapped IO-APIC

You can see the full set of ten errors in the attached screenshot.

Any ideas?

Place [COLOR=#373737]**noapic noapci **in boot:

As mentioned in this post:
[http://philatwarrimoo.blogspot.com.au/2012/06/unubtu-1204-on-macbook-pro-91-non.html](http://philatwarrimoo.blogspot.com.au/2012/06/unubtu-1204-on-macbook-pro-91-non.html)
[/COLOR]

---

### Post by ASven on 2012-07-30
Hello!

How is the progress for using only the Intel HD4000 graphics chip and disabling the nVidia completly?
Anybody archieved this already?

Regards
 Sven

---

### Post by BlueDragonX on 2012-07-30
Is anyone having microphone issues? All I get is static over mine. It doesn't matter if I'm using the internal mic or if I plug one into the port.

> **houkouonchi said:**
> 2.3 Ghz here working fine with my own custom built kernel (not using noapic and pretty sure kernel has apic support).

Mind posting your config? Also, what kernel version?

---

### Post by gschwind on 2012-07-31
Hello,

To help I confirm here things written in this thread.

I have the following MBP10.1 :

CPU: Intel(R) Core(TM) i7-3820QM CPU @ 2.70GHz
RAM: 16G
HD: 512Go SSD

My rMBP can boot ubuntu 12.04 in BIOS mode and need noapic option.

The Installation of ubuntu from USB stick work fine but not with native screen resolution, I didn't try to install anything or configure anything, I use ubuntu as base to install Gentoo. (don't miss understand me, ubuntu is a great distribution)

In gentoo side with 3.5.0 kernel (noapic is not require), after try and fail:
In BIOS mode I can boot but I didn't get any success with nvidia proprietary driver.

In EFI I get NVIDIA proprietary driver working as follow:
- grub2 in efi with insmod efi_gop
- kernel with efi and efi frame buffer enable.
- nvidia driver 302.17 with Option "UseDPLib" "off" in xorg.conf

result: screen work in native resolution but console screens are black as soon as you start X. (you can use them before start X).

For peoples that want try install nvidia driver I recommend to have a working network configuration with sshd starting automatically at boot and a second computer on same network. this help to solve issue when no screen working.

For black console screen, a possible workaround is to start multi X server, and start console inside.

I didn't try nouveau driver yet.

I Hope this help

---

### Post by gschwind on 2012-08-08
@BlueDragonX: About video corruption, your guess about DP link bandwidth seems wrong, the code properly checking bandwidth and enable the screen.

Best regards

---

### Post by BlueDragonX on 2012-08-08
> **gschwind said:**
> @BlueDragonX: About video corruption, your guess about DP link bandwidth seems wrong, the code properly checking bandwidth and enable the screen.

Best regards

Yep, I'm aware of this. I've started looking at other caused of the issue.

---

### Post by gschwind on 2012-08-09
THIS DOCUMENT IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS  OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF  MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL NORMAN WALSH OR ANY OTHER CONTRIBUTOR BE LIABLE FOR  ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,  TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THIS  DOCUMENT OR THE USE OR OTHER DEALINGS IN THIS DOCUMENT. 


Good news for macbook pro retina, If find the issue that make display corrupted on intel hardware. the work around is the following :

require: boot on efi

- patch kernel 3.5.1 with the attached patch (use at you own risk), compile kernel with intel KMS module. (the patch override bit per pixel detection, DO NO USE WITH EXTERNAL SCREEN!)
- start OS X and use [http://codykrieger.com/gfxCardStatus](http://codykrieger.com/gfxCardStatus) to set integrated gpu only. (this option is persistent over reboot)
- reboot with you patched kernel.

Know issue:
grub-efi is very slow when intel GPU is enable.
DO NO USE WITH EXTERNAL SCREEN!
THIS IS A VERY EXPERIMENTAL PATCH.

The patch is a work around, not intend to used on other system that macbook pro retina. a safe and generic patch must be made. This patch point out that the intel driver doesn't detect the right bit per pixel of the screen.

Why I did this patch ?
Because se screen was corrupted and the width seemed to be 3/4 of the full screen, 6 bit per pixels to 8 bit you get the 1/4 missing.

Hope this help for BlueDragonX (I guess the issue is quite the same for nouveau driver)

---

### Post by BlueDragonX on 2012-08-09
Yes, that should help as I know where to look. I'll try out the same thing for nouveau.

---

### Post by BlueDragonX on 2012-08-10
I was able to get it working using a similar method. The driver was already selecting 8 as the proper BPC but the screen was corrupt anyways. I forced it to 6 and it works. I don't know the proper way of overriding that, but the hardcoded method works for now.

[https://bugs.freedesktop.org/show_bug.cgi?id=51971](https://bugs.freedesktop.org/show_bug.cgi?id=51971)

---

### Post by metatechbe on 2012-08-10
Here is the experience of Jens Axboe with rMBP :
[URL="https://plus.google.com/u/0/111643045511375507360/posts/DoK5qeLxG6K"]link
[/URL]

---

### Post by bfroemel on 2012-08-10
> **gschwind said:**
> 
Good news for macbook pro retina, If find the issue that make display corrupted on intel hardware. the work around is the following :

require: boot on efi


Together with:
[http://lists.freedesktop.org/archives/intel-gfx/2012-August/019522.html](http://lists.freedesktop.org/archives/intel-gfx/2012-August/019522.html)

that's a lot of progress!

I took a look at the new (?) gmux and managed to talk to it a bit. Communication isn't direct-mapped anymore but there are address, status and data registers and a simple protocol needs to be followed for access.
Currently, I am able to read out the backlight, set it and also disable the nvidia card (indicators: cooler laptop, nvidia module fails to insert).
Unfortunately, writing is unreliable right now as it fails sometimes... I'll debug some more and get back here with patches as soon as possible ;)

---

### Post by gschwind on 2012-08-10
I send you a private message, I don't know the behaviour of this kind of message, i replicate it here :

Can you provite tips to reverse engenering of gMux and knowledge you gathered ?

Thank you by advance :)

---

### Post by BlueDragonX on 2012-08-10
> **bfroemel said:**
> Together with:
[http://lists.freedesktop.org/archives/intel-gfx/2012-August/019522.html](http://lists.freedesktop.org/archives/intel-gfx/2012-August/019522.html)

that's a lot of progress!

I took a look at the new (?) gmux and managed to talk to it a bit. Communication isn't direct-mapped anymore but there are address, status and data registers and a simple protocol needs to be followed for access.
Currently, I am able to read out the backlight, set it and also disable the nvidia card (indicators: cooler laptop, nvidia module fails to insert).
Unfortunately, writing is unreliable right now as it fails sometimes... I'll debug some more and get back here with patches as soon as possible ;)

Very nice! Between the three of us we're well on our way to getting full video support across the board on the MBPr. I need to investigate where the proper place to put my fixes are in code, but this is looking quite nice.

---

### Post by bfroemel on 2012-08-11
Okay - highly experimental, but hopefully a step into the right direction:
[http://luna.vmars.tuwien.ac.at/~froemel/rmbp/fixgpu.c](http://luna.vmars.tuwien.ac.at/~froemel/rmbp/fixgpu.c)

I derived this from another earlier version of fixgpu.c that could be used for MBP6,2 (and similar) to turn the Nvidia GPU off and switch to Intel graphics in a Intel-only setup.
As you can see, the internal gmux registers seem to have remained the same.

In my setup, a script '10_fixgpu' in /etc/pm/sleep.d/ takes care of calling fixgpu after every resume:
```

#!/bin/sh
case "${1}" in
    hibernate|suspend)
            ;;
    resume|thaw)
        /usr/local/sbin/fixgpu
            ;;
esac

```
Of course, it also makes sense to call fixgpu during system boot -- otherwise the Nvidia GPU remains turned on (until the first suspend/resume cycle). On a side note: the (idle) Nvidia GPU requires about 7.2 W (additional discharge rate). On lowest brightness settings I could get down to a total of 13.8 W which resulted in an estimated 6 hours runtime.

For me this worked every time (~30 suspend/resume cycles) up until now. If you dual-boot into OSX and want to use discrete graphics again, it seems to be required to force the discrete GPU first (gfxcardstatus) and reboot.

Unfortunately, suspend takes quite long (~25 seconds to sleep, ~30 seconds to wake-up).

> 
Can you provite tips to reverse engenering of gMux and knowledge you gathered ?

I looked at the disassembly of AppleMuxControl.kext, a plugin of AppleGraphicsControl.kext

> I need to investigate where the proper place to put my fixes are in code, but this is looking quite nice.
You saved me a lot of time with your patches -- I only received my mbp10,1 two days ago and didn't expect so much progress already :)

I'll further investigate about the gmux mbox protocol and look into patching apple-gmux so that we have backlight control when using nvidia/nouveau (also backlight control for the Intel card benefits from apple-gmux because we have very fine grained control (0x400 distinct brightness steps!)).

---

### Post by gschwind on 2012-08-11
@bfroemel:

I currently review the code, you probably need to add an error checking if gmux_cmd_ready() or gmux_cmd_done() fail.

what do you write/read to get/set backlight ?
(gmux write and int32 LE at GMUX_PORT_BRIGHTNESS do it work ?)


do write a little endian int32 every time work (instead of using size parameter) ?

how to switch back to discrete gpu ?

Thank you, realy great job :)

I have to test the code them :D

EDIT: as far as I understand on new gMux, we do not asses it directly but we setup the value that we want send to gMux in 0x7c2-0x7c5 and the 'gMux register' (old offset) at 0x7d4, how to read value ?

---

### Post by bfroemel on 2012-08-11
[http://luna.vmars.tuwien.ac.at/~froemel/rmbp/patch-apple-gmux.txt](http://luna.vmars.tuwien.ac.at/~froemel/rmbp/patch-apple-gmux.txt)

You should see:
> apple_gmux: Found gmux version 3.2.19 [dpm]
in your kernel log.

I only tested marginally during Intel GPU use -- would be nice if someone could test if it works with Nvidia/Nouveau too. I'll submit the patch as soon as I could either further test myself or get feedback.

> 
you probably need to add an error checking if gmux_cmd_ready() or gmux_cmd_done() fail.

fixgpu is more like a quick'n'dirty proof of concept tool ;)
But of course, you're right and I included more checks in my apple-gmux patch.
Also because a protocol must be followed during access, we have concurrency issues with the fixgpu tool anyway.
I'll be looking into extending apple-gmux further so that it incorporates fixgpu's functionality.

> 
do write a little endian int32 every time work (instead of using size parameter) ?

I followed the 'specification' .. so I have no idea ;)

> 
how to switch back to discrete gpu ?

Within Linux? I don't know yet. I tried to turn the Nvidia GPU back on and I could see that the discharge rate increased nearly as high as before turning it off (but not quite as high .. 2-3 W less). Also, driver loading didn't succeed -- so currently, after turning Nvidia off you need to use OSX to turn it fully operational again.

---

### Post by gschwind on 2012-08-11
@bfroemel:

I will try your patch :)

I was on the same track as you about reading.

If you do not power off discrete card, do you are able to switch back to nvidia ?

What do you call "spec ?", where can I find it :)

---

### Post by bfroemel on 2012-08-11
On Nvidia: No joy :/ (at least by using the blob/closed source driver)
The gmux device seems to disappear/not answer as soon as the nvidia module is loaded. Also, it doesn't help to unload the nvidia module: when it's loaded once, gmux is gone until the machine is rebooted.
Interestingly, if the integrated GPU is forced in OSX then loading the nvidia module has no negative effect, i.e. the gmux device remains responsive.

> 
I will try your patch

Thanks!

> 
If you do not power off discrete card, do you are able to switch back to nvidia ?

Doesn't seem to work, but need to familiarize myself a bit more with the gmux device itself. Previously, I've been always content with only using the integrated graphics adapter.

> 
What do you call "spec ?", where can I find it 

Well, on your OSX partition, specifically the kernel extensions/drivers ;)

---

### Post by gschwind on 2012-08-11
I tested your kernel patch, it work for me, back light work fine.

with fix gpu I have issue, the intel card doesn't take the screen control, I cannot figure out why.

I also merged update to gmux with a patch for gmux-switcheroo but I have the same issue, screen turn off intel do not update output screen.

any idea ?

---

### Post by bfroemel on 2012-08-11
> **gschwind said:**
> I tested your kernel patch, it work for me, back light work fine.

Only to verify: you mean when you use the integrated GPU?

> 
with fix gpu I have issue, the intel card doesn't take the screen control, I cannot figure out why.

I tried another ~20 suspend/resume cycles -- it worked every time for me.
Are you certain that:
- you use 3.6rc1
- have forced to use the Intel GPU (gfxcardstatus)
?

I use the following kernel command line:
"nointremap nomodeset i915.lvds_channel_mode=2 i915.modeset=1 i915.lvds_use_scc=0"

> 
I also merged update to gmux with a patch for gmux-switcheroo but I have the same issue, screen turn off intel do not update output screen.

any idea ?
Do you mean: [https://lkml.org/lkml/2012/7/10/311](https://lkml.org/lkml/2012/7/10/311) ? I didn't read the whole discussion but seems like this is just what we need as well.

---

### Post by gschwind on 2012-08-11
I boot with nvidia enable on OS X, backlight control with gmux work, switch to intel do not, something happen, but screen goes black.

I will try same kernel option than you, I used 3.5.1.

> **bfroemel said:**
> 
Do you mean: [https://lkml.org/lkml/2012/7/10/311](https://lkml.org/lkml/2012/7/10/311) ? I didn't read the whole discussion but seems like this is just what we need as well.

Yes, this one exactly : [http://www.codon.org.uk/~mjg59/tmp/gmux_switcheroo.diff]("http://www.codon.org.uk/%7Emjg59/tmp/gmux_switcheroo.diff") , and this seems working, but I have the same bug than fixgpu them. I apply it to 3.5.1. I will see if I will merge it to 3.6-rc1 when I solved my current issue :)

---

### Post by bfroemel on 2012-08-11
> **gschwind said:**
> I boot with nvidia enable on OS X, backlight control with gmux work, switch to intel do not, something happen, but screen goes black.


Ah - I see. That doesn't work for me either and I didn't even work into that direction (yet). It seems that we have different assumptions/goals: I want to use my MBP10,1 mostly with the Intel GPU -- in fact my MBP6,2 has not been used with the Nvidia GPU since the community worked out the details about gmux and EFI boot.
Hence, fixgpu is only supposed to put the gmux back into 'Intel mode' after suspend/resume. --> without this (personal) key feature (i.e., to operate the laptop in 'low power'/cool mode incl. working suspend/resume) the MBP10,1 would be unusable for me.

As for runtime GPU switching: Personally this is not essential for me, but if time permits I like to play of course --  Also with the gmux communication we have at least some common ground ;)

---

### Post by gschwind on 2012-08-11
^^, so I understant better, I want being able to switch GPU from linux without using MAC OS X :)

Can you send me your material you use to reverse engineering (in private message) ?

I send you my email in private.

Best Regards.

---

### Post by bfroemel on 2012-08-12
> **gschwind said:**
> ^^, so I understant better, I want being able to switch GPU from linux without using MAC OS X :)

Yes, seems like that's the way to do it nowadays -- I mean the vgaswitcheroo stuff.

I am using now this:
[http://people.canonical.com/~sforshee/apple-gmux-patches/0012-apple-gmux-Add-display-mux-support.patch](http://people.canonical.com/~sforshee/apple-gmux-patches/0012-apple-gmux-Add-display-mux-support.patch)
+ merge with my previous work (I'll write a proper patch as soon as 0012-apple-gmux-Add-display-mux-support is submitted):
[http://luna.vmars.tuwien.ac.at/~froemel/rmbp/apple-gmux.c](http://luna.vmars.tuwien.ac.at/~froemel/rmbp/apple-gmux.c)

Locking is still missing, but suspend/resume works without fixgpu now -- turning the discrete GPU off should work as well, i.e. over the switcheroo interface. Also suspending/resuming is much quicker now (~5 secs); no idea why.

Could you advice how to get the vga_switcheroo stuff enabled? It appears that only one graphics adapter (Intel) is suitable, hence vga_switcheroo does not offer me /sys/kernel/debug/vgaswitcheroo/*
Do I need nouveau drivers?


> Can you send me your material you use to reverse engineering (in private message) ?
Sorry, don't have much. I really only looked at the disassembly of the OSX kernel exts by using otool --> all my knowledge is in the posted source.

---

### Post by gschwind on 2012-08-12
> **bfroemel said:**
> 
Could you advice how to get the vga_switcheroo stuff enabled? It appears that only one graphics adapter (Intel) is suitable, hence vga_switcheroo does not offer me /sys/kernel/debug/vgaswitcheroo/*
Do I need nouveau drivers?


yes switcheroo is enable if only if 2 video card are detected, so you have to enable i915 +  nouveau. but this currently not work without patch.


I use [http://www.codon.org.uk/~mjg59/tmp/gmux_switcheroo.diff]("http://www.codon.org.uk/%7Emjg59/tmp/gmux_switcheroo.diff")
over kernl 3.5.1 and I merged your last patch with apple-gmux.c. I attached my apple-gmux.c, until I make a propper patch.

Currently I improve my knowlege about gMux, I will try to provide documentation about what I discovered on gMux if usefull.

---

### Post by bfroemel on 2012-08-12
Thanks.


After playing some more around, I am relatively sure that the gmux device in MBP10,1 behaves similar as in previous models. In my opinion, the problems w.r.t display issues after the (runtime) GPU switching on MBPs seem to be partly related to i915, nouveau/nvidia and vga_switcheroo. See:
[https://lkml.org/lkml/2012/8/3/300](https://lkml.org/lkml/2012/8/3/300)
After this is fixed, I suppose that there is not much missing to get full vga_switcheroo support for MBP10,1 as well.

For example, after applying the quoted series of patches (the original ones, not the one from 10th Aug.) alongside with my previously posted apple-gmux I was able to exercise the following testcase:
-) force Intel graphics in OSX
-) boot into Linux
-) start X -> Intel is used: screen, backlight control suspend/resume and vt consoles work
-) stop X -> switch to DIS, turn OFF IGD
-) start X -> Nvidia (nouveau) is used: screen, backlight control suspend/resume and vt consoles all work as well; vt consoles appear to be in 1024x768 scaled out instead of 2880x1800
-) stop X -> switch back to IGD, turn OFF DIS -> start X -> all works as before


Unfortunately there are problems (probably because of the 'bleeding edge' nature of the mentioned patches):
-) if started with active Nvidia GPU, switching to the Intel GPU does not work: i915 claims that there is no available output:
> 
(WW) intel(0): No outputs definitely connected, trying again...

-) switching a 2nd time to the Nvidia GPU does not work: the screen remains black --> there seems to be a state-corruption problem on nouveau's part


I'd like to test some more and probably get in contact with Seth Forshee.

\edit: corrected link to patch series concerning i915 changes for hybrid graphics support on Macbooks

---

### Post by gschwind on 2012-08-12
About GPU switching, In my study of gMux I'm quite confuse, there is a some trick in apple code that I don't understand well. It seems to be more complicated than my current apple-gmux.c . I need more time :D

---

### Post by bfroemel on 2012-08-12
I added locking:
[http://luna.vmars.tuwien.ac.at/~froemel/rmbp/apple-gmux.c](http://luna.vmars.tuwien.ac.at/~froemel/rmbp/apple-gmux.c)

@gschwind: do you expect/found problems with my changes to the apple-gmux module? or is there just a general interest in reverse engineering?
I only looked at how register accesses are done, but the apple driver is a lot more complex for sure. At least it also takes care of on-the-fly/dynamic GPU switching, save/restore GPU/configurations in EFI variables, ..

---

### Post by gschwind on 2012-08-12
> @gschwind: do you expect/found problems with my changes to the  apple-gmux module? or is there just a general interest in reverse  engineering?
I only looked at how register accesses are done, but the apple driver is  a lot more complex for sure. At least it also takes care of  on-the-fly/dynamic GPU switching, save/restore GPU/configurations in EFI  variables, .. 	

Both.

The only thing new I found is that there seems to be 4 more register for backligth that store max_brightness/current brightness of both GPU. Apple seems to copy/update max_brightness /current_brightness depending on current used gpu.

Currently I can't find the order of write call (i.e. I don't find matching between kernel and apple code).

I will test/review your code when I get time

---

### Post by gschwind on 2012-08-13
suspend to ram seems working, with nouveau and your apple gmux. (suspend of gnome2)

EDIT: with minor patch

---

### Post by frigaut on 2012-08-13
Guys,
Impressive work ! 
However I am a bit lost here. You guys have been following your thread, difficult to follow for a newcomer in the discussion. Could one of you confirm:
[LIST=1]
[*]- The kernel tree you are using (3.6-rc1?)
[*]- The patches you used:
[LIST]
[*]- apple-gmux.c from [http://luna.vmars.tuwien.ac.at/~froe...p/apple-gmux.c](http://luna.vmars.tuwien.ac.at/~froe...p/apple-gmux.c)
[/LIST]
[*] What else?
[LIST]
[*]- need bpc fix in i915?
[*]  - vga_switcheroo?
[*]  - intel_panel?
[/LIST][/LIST]


Thanks in advance.

---

### Post by frigaut on 2012-08-14
OK, thanks to your work, I got it to work (i915 and switch off nvidia, which is what I wanted to do; I am now burning only ~13.5W instead of the 23+ before when using the discrete card).
Again, congrats for the three of you. You guys rock.
So to summarize what I extracted from this thread, and with goal of providing a self-contained recipe for others:
[LIST]
[*] Use the 3.6-rc1 tree (working applesmc within others fixes w.r.t. 3.5)
[*] Apply i915 intel_display patch to get bpc right (corrupted graphic), as per [http://lists.freedesktop.org/archives/intel-gfx/2012-August/019522.html](http://lists.freedesktop.org/archives/intel-gfx/2012-August/019522.html)
[*] Replace apple-gmux.c by the one at [http://luna.vmars.tuwien.ac.at/~froe...p/apple-gmux.c](http://luna.vmars.tuwien.ac.at/~froe...p/apple-gmux.c) (as per august 14)
[*] Build and install kernel
[*] Get fixgpu from [http://luna.vmars.tuwien.ac.at/~froemel/rmbp/fixgpu.c](http://luna.vmars.tuwien.ac.at/~froemel/rmbp/fixgpu.c), build it.
[*] Create a 10_fixgpu as per [http://ubuntuforums.org/showpost.php?p=12164230&postcount=77](http://ubuntuforums.org/showpost.php?p=12164230&postcount=77) to insure discrete card is turned off after every resume
[*] Rock and roll. Everything I need is now working on this laptop.
[/LIST]

Did I forgot anything?
I'm using the following kernel parameters on direct EFI boot: "nointremap nomodeset i915.lvds_channel_mode=2 i915.modeset=1", as per bfroemel suggestion. I assume the nomodeset is for nouveau and is overridden by i915.modeset for the intel card. Apart from the nointremap, I'm actually not sure the other parameters are necessary, but I'm tired of rebooting right now so won't try w/o them.

Btw, to summarize the capabilities (I know this was said earlier in this thread, but my goal is to try to summarize here within a single post), as far as graphics is concerned, this provided me with:
- intel integrated graphic card w/ i915 driver
- nvidia discrete graphic card turned off (or not, your choice, controlled by fixgpu)
- working backlight control (through /sys/class/backlight/gmux_backlight), suspend/resume (fast, 4-5 seconds), VT switching.

I haven't tried switching card, but not really interested in it right now.

Thanks again!

---

### Post by frigaut on 2012-08-14
On a related topic: As bfroemel, I do experience sometimes resume delays. I have noticed 2 things in dmesg:

1) very large noirq resume device times:

Aug 14 14:47:35 localhost kernel: [ 2595.438672] PM: noirq resume of devices complete after 8239.874 msecs
Aug 14 14:49:34 localhost kernel: [ 2708.154753] PM: noirq resume of devices complete after 793.189 msecs
Aug 14 15:07:57 localhost kernel: [ 3804.334099] PM: noirq resume of devices complete after 793.200 msecs
Aug 14 15:22:22 localhost kernel: [ 4514.832314] PM: noirq resume of devices complete after 8239.876 msecs
Aug 14 15:38:48 localhost kernel: [ 5493.971833] PM: noirq resume of devices complete after 8239.877 msecs
Aug 14 15:54:04 localhost kernel: [  244.661517] PM: noirq resume of devices complete after 8239.966 msecs
Aug 14 16:30:19 localhost kernel: [   38.795440] PM: noirq resume of devices complete after 4123.215 msecs

That's with 3.6-rc1 patched as described in a post above. Before, I was using 3.5 patched for applesmc and the noirq resume time were of the order a a few ms, example:

Aug 13 18:27:18 localhost kernel: [18703.083056] PM: noirq resume of devices complete after 1.294 msecs
Aug 13 19:39:19 localhost kernel: [21726.768319] PM: noirq resume of devices complete after 1.280 msecs

I've not idea what's inducing these delays but it's obviously related to the new config.
2) I got these messages:

Aug 14 16:27:50 localhost kernel: [ 2272.676368] azx_single_send_cmd: 760 callbacks suppressed
when resuming. That also polluted the VT and dmesg.
Turns out that there are of course 2 audio cards: the intel and the nvidia, both handled by the snd_hda_intel driver. Because I switch the nvidia OFF, snd_hda_intel is trying to restore communication with the nvidia (at resume) but of course fails because the card is off.

The cleanest solution I found is to actually remove the device at boot (see [https://bbs.archlinux.org/viewtopic.php?pid=908047#p908047](https://bbs.archlinux.org/viewtopic.php?pid=908047#p908047) ). This solved the issue for me.

---

### Post by frigaut on 2012-08-14
duh...
I should have thought of it when writing (2).
the noirq delays are also due to the fact that the kernel probe for the graphic card and it's powered off!
same solution:

# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fd5 (rev ff)
# find /sys/devices -name *01:00.0
/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0
# echo 1 > /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/remove
# modprobe -r nouveau

and pm-suspend resumes in 4-5 seconds!

and noirq resumes of device doesn't hang for seconds:
[ 1473.383626] PM: noirq resume of devices complete after 120.008 msecs
[ 1489.711023] PM: noirq resume of devices complete after 120.039 msecs

---

### Post by bfroemel on 2012-08-14
Note that Matthew Garret has found out about how to communicate with the new gmux device earlier than me ([http://www.spinics.net/lists/platform-driver-x86/msg03731.html](http://www.spinics.net/lists/platform-driver-x86/msg03731.html)) and submitted a similar patch (
[https://lkml.org/lkml/2012/8/13/597](https://lkml.org/lkml/2012/8/13/597)) which will probably go into the kernel.
For now it does not matter which patch you use: Matthew and I do the exact same.

Please don't use fixgpu (you will run into concurrency issues -- if not now then later) but apply these patches:
[http://people.canonical.com/~sforshee/apple-gmux-patches/](http://people.canonical.com/~sforshee/apple-gmux-patches/) (details: [https://lkml.org/lkml/2012/7/9/715](https://lkml.org/lkml/2012/7/9/715))
Also it's good to watch this: [https://lkml.org/lkml/2012/8/3/300](https://lkml.org/lkml/2012/8/3/300) . As soon as it works, it's not necessary to force the Integrated GPU anymore in OSX.

With this kernel you should get partially working vga_switcheroo support and the gmux configuration is preserved during suspend/resume (both is also fast (4-5 secs) as vgaswitcheroo takes care about device handling). So you only need to:
'echo OFF > /sys/kernel/debug/vgaswitcheroo/switch' once (best after system start) to turn the Nvidia GPU off.

---

### Post by frigaut on 2012-08-14
> **bfroemel said:**
> Please don't use fixgpu (you will run into concurrency issues -- if not now then later) but apply these patches:
[http://people.canonical.com/~sforshee/apple-gmux-patches/](http://people.canonical.com/~sforshee/apple-gmux-patches/) (details: [https://lkml.org/lkml/2012/7/9/715](https://lkml.org/lkml/2012/7/9/715))

That would be on 3.6-rc1? and on top of your apple-gmux?

> **bfroemel said:**
> Also it's good to watch this: [https://lkml.org/lkml/2012/8/3/300](https://lkml.org/lkml/2012/8/3/300) . As soon as it works, it's not necessary to force the Integrated GPU anymore in OSX.
Excellent. Thanks for the pointer.

> **bfroemel said:**
> With this kernel you should get partially working vga_switcheroo support and the gmux configuration is preserved during suspend/resume (both is also fast (4-5 secs) as vgaswitcheroo takes care about device handling). So you only need to:
'echo OFF > /sys/kernel/debug/vgaswitcheroo/switch' once (best after system start) to turn the Nvidia GPU off.
Great. Will try that. Cheers.

---

### Post by bfroemel on 2012-08-14
About kernel parameters:
I partly reused my old ones from my MBP6,2 which seem obsolete (e.g. lvds channels).
You only need: nointremap modeset=1 i915.lvds_use_ssc=0 nouveau.force_post=1

The last one allows you with BlueDragon's patches: [https://bugs.freedesktop.org/show_bug.cgi?id=51971](https://bugs.freedesktop.org/show_bug.cgi?id=51971)
to also operate the Nvidia GPU with nouveau. You can even do (limited, works currently only 2 times without reboots for the Nvidia GPU) runtime GPU switching.

---

### Post by bfroemel on 2012-08-14
> That would be on 3.6-rc1? and on top of your apple-gmux?
Yes, although order doesn't matter much -- you need to do some (straight forward) manual merging anyway.

---

### Post by gschwind on 2012-08-14
I don't have any success in switching from nvidia to intel.

I tested to switch them load i915 driver, but it does not detect any screen after that.

I follow the x86-platform mailling list :)

I will continue to investigate, but I think i915 developer will solve the issue before be.

---

### Post by frigaut on 2012-08-14
> **bfroemel said:**
> Yes, although order doesn't matter much -- you need to do some (straight forward) manual merging anyway.

OK. I believe I have everything (except BlueDragonX nouveau patch).
But something is wrong. First, I realised I didn't have a /sys/kernel/debug/vgaswitcheroo/switch
Investigating, I found this in /var/log/everything.log:


```
Aug 14 11:55:11 localhost kernel: [    4.638907] vga_switcheroo: enabled
Aug 14 11:55:11 localhost kernel: [    4.638920] BUG: unable to handle kernel NULL pointer dereference at           (null)
Aug 14 11:55:11 localhost kernel: [    4.638923] IP: [<          (null)>]           (null)
Aug 14 11:55:11 localhost kernel: [    4.638926] PGD 45ac9f067 PUD 45b2d8067 PMD 0 
Aug 14 11:55:11 localhost kernel: [    4.638929] Oops: 0010 [#1] PREEMPT SMP 
Aug 14 11:55:11 localhost kernel: [    4.638932] Modules linked in: arc4 b43 ssb pcmcia hid_generic mac80211 snd_hda_codec_cirrus cfg80211 rfkill usbhid pcmcia_core hid evdev microcode aesni_intel applesmc aes_x86_64 nouveau ablk_helper input_polldev aes_generic snd_hda_intel(+) i915(+) ghash_clmulni_intel cryptd snd_hda_codec kvm_intel asix usbnet kvm snd_hwdep mii snd_pcm mxm_wmi intel_agp intel_gtt snd_page_alloc wmi libphy i2c_algo_bit ttm sdhci_pci acpi_cpufreq drm_kms_helper snd_timer lpc_ich sdhci coretemp crc32c_intel pcspkr i2c_i801 mmc_core bcma drm snd mfd_core mei soundcore i2c_core mperf apple_gmux video button processor battery ac apple_bl ext4 crc16 jbd2 mbcache sd_mod ehci_hcd ahci libahci libata xhci_hcd scsi_mod usbcore usb_common
Aug 14 11:55:11 localhost kernel: [    4.638976] CPU 5 
Aug 14 11:55:11 localhost kernel: [    4.638978] Pid: 224, comm: systemd-udevd Not tainted 3.6.0-rc1-mainline #1 Apple Inc. MacBookPro10,1/Mac-C3EC7CD22292981F
Aug 14 11:55:11 localhost kernel: [    4.638981] RIP: 0010:[<0000000000000000>]  [<          (null)>]           (null)
Aug 14 11:55:11 localhost kernel: [    4.638984] RSP: 0018:ffff88045b3a3aa0  EFLAGS: 00010292
Aug 14 11:55:11 localhost kernel: [    4.638986] RAX: ffffffffa02128c0 RBX: ffff88045c345e00 RCX: 0000000000000028
Aug 14 11:55:11 localhost kernel: [    4.638988] RDX: 0000000000000041 RSI: 0000000000000046 RDI: 0000000000000246
Aug 14 11:55:11 localhost kernel: [    4.638990] RBP: ffff88045b3a3ad8 R08: 000000000000000a R09: 000000000000045d
Aug 14 11:55:11 localhost kernel: [    4.638992] R10: 0000000000000000 R11: 000000000000045c R12: 00000000ffffffff
Aug 14 11:55:11 localhost kernel: [    4.638994] R13: ffffffffa075c3c0 R14: ffff88045cfee000 R15: 0000000000000001
Aug 14 11:55:11 localhost kernel: [    4.638997] FS:  00007f2d3de0d780(0000) GS:ffff88046f340000(0000) knlGS:0000000000000000
Aug 14 11:55:11 localhost kernel: [    4.638999] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 14 11:55:11 localhost kernel: [    4.639001] CR2: 0000000000000000 CR3: 000000045ac9a000 CR4: 00000000001407e0
Aug 14 11:55:11 localhost kernel: [    4.639003] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 14 11:55:11 localhost kernel: [    4.639005] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 14 11:55:11 localhost kernel: [    4.639008] Process systemd-udevd (pid: 224, threadinfo ffff88045b3a2000, task ffff88045b18b790)
Aug 14 11:55:11 localhost kernel: [    4.639010] Stack:
Aug 14 11:55:11 localhost kernel: [    4.639011]  ffffffff8131c04b 0000000000000000 ffff88045cfee000 ffffffffa075c3c0
Aug 14 11:55:11 localhost kernel: [    4.639015]  0000000000000000 0000000010000000 0000000000000000 ffff88045b3a3af8
Aug 14 11:55:11 localhost kernel: [    4.639018]  ffffffff8131c1b8 ffff88045a5e1800 ffff88045bfd0000 ffff88045b3a3b78
Aug 14 11:55:11 localhost kernel: [    4.639022] Call Trace:
Aug 14 11:55:11 localhost kernel: [    4.639026]  [<ffffffff8131c04b>] ? register_client+0x10b/0x220
Aug 14 11:55:11 localhost kernel: [    4.639030]  [<ffffffff8131c1b8>] vga_switcheroo_register_client+0x38/0x50
Aug 14 11:55:11 localhost kernel: [    4.639043]  [<ffffffffa070eb93>] i915_driver_load+0xa03/0xbc0 [i915]
Aug 14 11:55:11 localhost kernel: [    4.639049]  [<ffffffffa01c36d0>] ? drm_get_minor+0x210/0x2f0 [drm]
Aug 14 11:55:11 localhost kernel: [    4.639055]  [<ffffffffa01c5d96>] drm_get_pci_dev+0x186/0x2c0 [drm]
Aug 14 11:55:11 localhost kernel: [    4.639067]  [<ffffffffa075ae99>] i915_pci_probe+0x4d/0x57 [i915]
Aug 14 11:55:11 localhost kernel: [    4.639070]  [<ffffffff81274a1c>] local_pci_probe+0x5c/0xd0
Aug 14 11:55:11 localhost kernel: [    4.639073]  [<ffffffff81275311>] pci_device_probe+0x111/0x120
Aug 14 11:55:11 localhost kernel: [    4.639077]  [<ffffffff81321bab>] driver_probe_device+0x7b/0x240
Aug 14 11:55:11 localhost kernel: [    4.639080]  [<ffffffff81321e1b>] __driver_attach+0xab/0xb0
Aug 14 11:55:11 localhost kernel: [    4.639083]  [<ffffffff81321d70>] ? driver_probe_device+0x240/0x240
Aug 14 11:55:11 localhost kernel: [    4.639086]  [<ffffffff8131fe65>] bus_for_each_dev+0x55/0x90
Aug 14 11:55:11 localhost kernel: [    4.639089]  [<ffffffff813216ee>] driver_attach+0x1e/0x20
Aug 14 11:55:11 localhost kernel: [    4.639092]  [<ffffffff81321280>] bus_add_driver+0x190/0x260
Aug 14 11:55:11 localhost kernel: [    4.639095]  [<ffffffffa0784000>] ? 0xffffffffa0783fff
Aug 14 11:55:11 localhost kernel: [    4.639098]  [<ffffffff813224e7>] driver_register+0x77/0x170
Aug 14 11:55:11 localhost kernel: [    4.639101]  [<ffffffffa0784000>] ? 0xffffffffa0783fff
Aug 14 11:55:11 localhost kernel: [    4.639103]  [<ffffffff8127559e>] __pci_register_driver+0x5e/0xe0
Aug 14 11:55:11 localhost kernel: [    4.639106]  [<ffffffffa0784000>] ? 0xffffffffa0783fff
Aug 14 11:55:11 localhost kernel: [    4.639111]  [<ffffffffa01c5fea>] drm_pci_init+0x11a/0x130 [drm]
Aug 14 11:55:11 localhost kernel: [    4.639114]  [<ffffffffa0784000>] ? 0xffffffffa0783fff
Aug 14 11:55:11 localhost kernel: [    4.639122]  [<ffffffffa0784066>] i915_init+0x66/0x68 [i915]
Aug 14 11:55:11 localhost kernel: [    4.639125]  [<ffffffff8100212a>] do_one_initcall+0x12a/0x180
Aug 14 11:55:11 localhost kernel: [    4.639129]  [<ffffffff810b912e>] sys_init_module+0x101e/0x1e30
Aug 14 11:55:11 localhost kernel: [    4.639132]  [<ffffffff810b4930>] ? sys_getegid16+0x50/0x50
Aug 14 11:55:11 localhost kernel: [    4.639136]  [<ffffffff81485369>] system_call_fastpath+0x16/0x1b
Aug 14 11:55:11 localhost kernel: [    4.639138] Code:  Bad RIP value.
Aug 14 11:55:11 localhost kernel: [    4.639141] RIP  [<          (null)>]           (null)
Aug 14 11:55:11 localhost kernel: [    4.639143]  RSP <ffff88045b3a3aa0>
Aug 14 11:55:11 localhost kernel: [    4.639145] CR2: 0000000000000000
Aug 14 11:55:11 localhost kernel: [    4.639147] ---[ end trace 3ea8e8da5be8e11c ]---

```

hum... I might be missing a patch in i915? Are you using drm/i915 from 3.6-rc1 untouched (except for the i915_display.c bpc eDP display corruption patch)?

Thanks.

---

### Post by gschwind on 2012-08-14
@frigaut:

as you quoted :

> you need to do some (straight forward) manual merging anyway.you need patch to add an init and client active function in apple_gmux, if I remember well.

```
static int gmux_init() {
        return 0;
}

static struct vga_switcheroo_handler gmux_handler = {
        .init = gmux_init,
        .switchto = gmux_switchto,
        .power_state = gmux_set_power_state,
        .get_client_id = gmux_get_client_id,
        .client_active = gmux_client_active,
};

```

---

### Post by frigaut on 2012-08-14
> **gschwind said:**
> @frigaut:

as you quoted :

you need patch to add an init and client active function in apple_gmux, if I remember well.


Thanks. I get some build error "unknown field 'client_active'.."
No worries. I'll survive with a perfectly working version using fixgpu for now. I guess all this should land in 3.7 eventually.

---

### Post by bfroemel on 2012-08-15
> No worries. I'll survive with a perfectly working version using fixgpu for now. I guess all this should land in 3.7 eventually.

In case you want to try anyway:

- start from linux-3.6-rc1
- i915 bpc fix: [http://lists.freedesktop.org/archives/intel-gfx/2012-August/019522.html](http://lists.freedesktop.org/archives/intel-gfx/2012-August/019522.html)
- nouveau fixes (beware, very specific to retina MBP and will be superseded with generic fixes soon): [https://bugs.freedesktop.org/show_bug.cgi?id=51971](https://bugs.freedesktop.org/show_bug.cgi?id=51971)
- apple-gmux mbox interface support: [http://luna.vmars.tuwien.ac.at/~froemel/rmbp/patch-apple-gmux_v2.txt](http://luna.vmars.tuwien.ac.at/~froemel/rmbp/patch-apple-gmux_v2.txt) (this version should do it correctly, see [https://lkml.org/lkml/2012/8/14/259](https://lkml.org/lkml/2012/8/14/259) for details . Also there should not be any merge conflicts later on)
- apple-gmux switcheroo: [http://people.canonical.com/~sforshee/apple-gmux-patches/](http://people.canonical.com/~sforshee/apple-gmux-patches/) (all of them)
- i915 switcheroo: [https://lkml.org/lkml/2012/8/3/300](https://lkml.org/lkml/2012/8/3/300) 1-5 (take the inital patches 1-5 for now, Seth is working on an improvement deeper down in the thread)

I can upload a cumulative patch of all changes from linux-3.6-rc1, but as you said: things are moving fast and soon patching won't be necessary anymore.

---

### Post by frigaut on 2012-08-15
bfroemel, Thanks for the consolidated list of patches.
I tried it. It applies cleanly (a few hunks for apple-gmux but went through ok).
Now I have 3.6 + the 21 patches you listed.
i915 and nouveau load and work (haven't tried nouveau yet).
suspend/resume work, backlight, etc. The only thing that doesn't is switcheroo. I can see *it is* enabled in dmesg (no error message now, I've put it at [http://maumae.net/retina/dmesg_3.6+patches](http://maumae.net/retina/dmesg_3.6+patches) ), but I don't have a /sys/kernel/debug/switcheroo. I'm kind of baffled. I have CONFIG_VGA_SWITCHEROO=y. I'm booting efi. I'm using the kernel boot parameters you indicated.  i915 and nouveau are loaded.
Just to make extra sure, here are the patches I have applied:

  366  patch -Np1 -i ../../intel-bpc-fix.patch 
  374  patch -Np1 -i ../../bluedragonx-1.patch 
  375  patch -Np1 -i ../../bluedragonx-2.patch 
  380  patch -Np1 -i ../../apple-gmux-froemel.patch 
  387  patch -Np1 -i ../../0001-efi-Build-EFI-stub-with-EFI-appropriate-options.patch 
  388  patch -Np1 -i ../../0002-X86-Improve-GOP-detection-in-the-EFI-boot-stub.patch 
  389  patch -Np1 -i ../../0003-EFI-Stash-ROMs-if-they-re-not-in-the-PCI-BAR.patch 
  390  patch -Np1 -i ../../0004-PCI-Add-pcibios_add_device.patch 
  391  patch -Np1 -i ../../0005-PCI-Add-support-for-non-BAR-ROMs.patch 
  392  patch -Np1 -i ../../0006-X86-Use-PCI-setup-data.patch 
  393  patch -Np1 -i ../../0007-efifb-Skip-DMI-checks-if-the-bootloader-knows-what-i.patch 
  394  patch -Np1 -i ../../0008-x86-EFI-Calculate-the-EFI-framebuffer-size-instead-o.patch 
  395  patch -Np1 -i ../../0009-apple-gmux-Fix-kconfig-dependencies.patch 
  396  patch -Np1 -i ../../0010-vga_switcheroo-Don-t-require-handler-init-callback.patch 
  397  patch -Np1 -i ../../0011-vga_switcheroo-Remove-assumptions-about-registration.patch 
  398  patch -Np1 -i ../../0012-apple-gmux-Add-display-mux-support.patch 
  411  patch -Np1 -i ../../RFC-1-5-drm-i915-Add-support-for-vga_switcheroo-reprobe.patch 
  412  patch -Np1 -i ../../RFC-2-5-drm-i915-separate-out-code-to-get-EDID-from-LVDS-panel.patch 
  413  patch -Np1 -i ../../RFC-3-5-drm-i915-register-LVDS-connector-even-if-we-can-t-get-a-panel-mode.patch 
  414  patch -Np1 -i ../../RFC-4-5-drm-i915-make-intel_lvds_get_edid-more-robust.patch 
  415  patch -Np1 -i ../../RFC-5-5-drm-i915-check-LVDS-for-EDID-on-GPU-switches.patch 

The "bluedragonx" are the 2 patches for nouveau.

Any idea would be welcome :-)

---

### Post by frigaut on 2012-08-15
Solved. I didn't have 
```
none                    /sys/kernel/debug debugfs defaults 0 0
```
in my fstab. Thus nothing at all was showing up in /sys/kernel/debug (I'm using arch, apparently this is done by default in ubuntu).

echoing OFF to switcheroo does turn off the nvidia, judged by the power consumption, but I still have the device listed in lspci. and noirq resume takes again 8000ms+, so I suspect Seth's patches are not taking care of removing the device after all.

Anyway, it works. Thanks a bunch, bfroemel.

---

### Post by bfroemel on 2012-08-15
> Anyway, it works. Thanks a bunch, 
You're welcome and great that its works! You are right about the noirq part -- I was already happy that it didn't take more than 30 seconds like when I tried first ;)


btw: small fix for the fully patched apple-gmux.c:
```

--- a/apple-gmux.c	2012-08-15 22:08:32.886014667 +0300
+++ b/apple-gmux.c	2012-08-15 18:52:25.679817764 +0300
@@ -399,6 +399,7 @@
 static int gmux_resume(struct pnp_dev *pnp)
 {
 	struct apple_gmux_data *gmux_data = pnp_get_drvdata(pnp);
+	gmux_enable_interrupts(gmux_data);
 	gmux_switchto(gmux_data->resume_client_id);
 	if (gmux_data->power_state == VGA_SWITCHEROO_OFF)
 		gmux_set_discrete_state(gmux_data, gmux_data->power_state);

```

Fixes: apple_gmux: Timeout waiting for gmux switch to complete

Already reported to Seth who will probably submit a nice patch series containing everything to the kernel soon. btw: It's really great that so many (core) kernel developers have an interest getting the rmbp supported. The last great obstacle seems to be Thunderbolt hotplug:
[http://mjg59.dreamwidth.org/15948.html](http://mjg59.dreamwidth.org/15948.html)
Personally, I also like to see support for 802.11n -- but like i915/nouveau this is supposed to only take time/need implementation work.

---

### Post by Baughn on 2012-08-15
Before I try to install this.. (and please tell me how I'm supposed to do that, when step 1 is "compile the kernel"; I need a pointer to an installation CD)

What is battery life like?

---

### Post by frigaut on 2012-08-15
@Baughn

There is no installation CD. This hardware is very new and not yet supported by the latest stable kernel, notwithstanding the latest ubuntu kernel.

If you don't know how to build a kernel, there are 2 options:

1) You learn how to do it, along with all the hacks you'll need to make this machine work. You are in for a long journey, full of frustrations but also full of joy. You'll learn linux on the way. It's fun and rewarding, but that's a significant time investment. If you choose this option, we can't hold your hand. That would defeat the learning exercise. You'll find tutorials all over the web.

2) You just wait for this machine to be supported. Most of the things to make it work properly should be in by the time 3.7 comes out, I assume, meaning 4-5 months from now.

I burn about 20W at full display brightness and 13W idle at low display brightness. So battery life is going to be anywhere between 4 and 6 hours depending on use and display brightness settings.

---

### Post by bfroemel on 2012-08-16
Concerning display port (i.e., not Thunderbolt): has anyone already experimented with external monitors/beamers/.. ?
I only tried briefly, but it seems that I only get output when the Nvidia GPU is active. On nouveau the internal screen isn't available as an output and .. which currently bothers me most: no 'hotplug' :/

Unfortunately, I can't try further myself until after the weekend.

---

### Post by Baughn on 2012-08-16
> **frigaut said:**
> @Baughn

There is no installation CD. This hardware is very new and not yet supported by the latest stable kernel, notwithstanding the latest ubuntu kernel.

If you don't know how to build a kernel, there are 2 options:

1) You learn how to do it, along with all the hacks you'll need to make this machine work. You are in for a long journey, full of frustrations but also full of joy. You'll learn linux on the way. It's fun and rewarding, but that's a significant time investment. If you choose this option, we can't hold your hand. That would defeat the learning exercise. You'll find tutorials all over the web.

2) You just wait for this machine to be supported. Most of the things to make it work properly should be in by the time 3.7 comes out, I assume, meaning 4-5 months from now.

I burn about 20W at full display brightness and 13W idle at low display brightness. So battery life is going to be anywhere between 4 and 6 hours depending on use and display brightness settings.

Well, I do know how to build a kernel. I was just hoping I wouldn't have to try cooking up my own installation.. USB stick, I suppose.

No matter. It'll be "fun".

---

### Post by frigaut on 2012-08-16
> **bfroemel said:**
> Concerning display port (i.e., not Thunderbolt): has anyone already experimented with external monitors/beamers/.. ?
I only tried briefly, but it seems that I only get output when the Nvidia GPU is active. On nouveau the internal screen isn't available as an output and .. which currently bothers me most: no 'hotplug' :/

Unfortunately, I can't try further myself until after the weekend.

I was able to display on external monitor with the nvidia blob. hotplug ok, but it's because it understands the connector as a minidisplay port, not a thunderbolt connector.

I haven't tried with nouveau.

With the intel card, I only get eDP1 and VGA1 available according to xrandr. I assume the card is not actually connected (physically?) to the miniDP and the HDMI connectors (?).

---

### Post by frigaut on 2012-08-17
> **Baughn said:**
> Well, I do know how to build a kernel. I was just hoping I wouldn't have to try cooking up my own installation.. USB stick, I suppose.

No matter. It'll be "fun".

Yes, USB stick. and don't forget the nointremap and nomodeset boot kernel option when booting the installer, otherwise it doesn't boot.
Good luck.

---

### Post by enchanterchi on 2012-08-19
> **frigaut said:**
> Yes, USB stick. and don't forget the nointremap and nomodeset boot kernel option when booting the installer, otherwise it doesn't boot.
Good luck.

How to add these two options? I can't access the USB stick from MAC OS on the MacBook Pro

---

### Post by frigaut on 2012-08-19
> **enchanterchi said:**
> How to add these two options? I can't access the USB stick from MAC OS on the MacBook Pro

I iuse another distro, but I assume the ubuntu install images come with GRUB. You can add these parameters in the grub entry (select the corretc line and hit tab).

---

### Post by atte on 2012-08-20
> **frigaut said:**
> I iuse another distro, but I assume the ubuntu install images come with GRUB. You can add these parameters in the grub entry (select the corretc line and hit tab).

I don't think it is grub on the CD/USB but just press 'e' to edit.

---

### Post by bfroemel on 2012-08-21
Thanks frigaut! I can confirm your findings about the outputs. Also it appears to be impossible to use an external screen in OSX if the Intel GPU is forced: so one must use the Nvidia GPU (and the closed source driver for now) for external screens/beamers.

btw: in case someone wants to see a Linux screenshot including a picture of the screen:
[https://plus.google.com/111653446152235408509/posts/g1N9VyfTv7t](https://plus.google.com/111653446152235408509/posts/g1N9VyfTv7t)

I used larger fonts/text scaling for all the open applications, although the Windows 7 virtual machine in the upper right part is using the default 96 dpi settings.

---

### Post by frigaut on 2012-08-22
> **bfroemel said:**
> Thanks frigaut! I can confirm your findings about the outputs. Also it appears to be impossible to use an external screen in OSX if the Intel GPU is forced: so one must use the Nvidia GPU (and the closed source driver for now) for external screens/beamers.


I can confirm that, although xrandr list the VGA as one of the output when using the intel driver, pluging in an external connector doesn't list anything available under the VGA1 output.
Bummer.

---

### Post by bfroemel on 2012-08-23
Can someone who could get switcheroo to work with 3.6-rc1 please try Intel GPU only operation on 3.6-rc3 (prestine)?
That is, please force Intel GPU in OSX, boot into 3.6-rc3, verify that really the Intel GPU is used, suspend/resume a few times and then apply this patch:
[http://luna.vmars.tuwien.ac.at/~froemel/rmbp/patch-apple-gmux_3.6-rc3.txt](http://luna.vmars.tuwien.ac.at/~froemel/rmbp/patch-apple-gmux_3.6-rc3.txt)
and try again?

Expected outcome: on 3.6-rc3 the gmux doesn't reliably switch back to the Intel GPU on resume without the patch.

Note: Nvidia GPU operation with nouveau drivers and without patches [1] will most likely lead to screen corruptions in 3.6-rc3.

[1] [https://bugs.freedesktop.org/show_bug.cgi?id=51971](https://bugs.freedesktop.org/show_bug.cgi?id=51971)

---

### Post by kosumi68 on 2012-08-25
> **bfroemel said:**
> Can someone who could get switcheroo to work with 3.6-rc1 please try Intel GPU only operation on 3.6-rc3 (prestine)?
That is, please force Intel GPU in OSX, boot into 3.6-rc3, verify that really the Intel GPU is used, suspend/resume a few times and then apply this patch:
[http://luna.vmars.tuwien.ac.at/~froemel/rmbp/patch-apple-gmux_3.6-rc3.txt](http://luna.vmars.tuwien.ac.at/~froemel/rmbp/patch-apple-gmux_3.6-rc3.txt)
and try again?

Expected outcome: on 3.6-rc3 the gmux doesn't reliably switch back to the Intel GPU on resume without the patch.

Note: Nvidia GPU operation with nouveau drivers and without patches [1] will most likely lead to screen corruptions in 3.6-rc3.

[1] [https://bugs.freedesktop.org/show_bug.cgi?id=51971](https://bugs.freedesktop.org/show_bug.cgi?id=51971)

With a pristine mainline head, i915 builtin, no nouveau, and your patch applied, I can finally resume (systemd variant) my MacBookPro10,1 to a functional screen. It works!

The reversal of the gwr logic looks intriguing... *reads thread*

Excellent, thank you.

EDIT: Moreover, after resuming once, I can actually switch graphics mode with xrandr, looking at sane default fonts for the first time. :-)

---

### Post by kosumi68 on 2012-08-25
On my setup (minimal distro, systemd, all modules builtin), my trackpad does not work, but reading from the appropriate /dev/input/eventX node results in a -ENOSPC. Has anyone else seen this? I have a patch for it, but I am puzzled that nobody else seems to need it...

---

### Post by frigaut on 2012-08-25
> **kosumi68 said:**
> On my setup (minimal distro, systemd, all modules builtin), my trackpad does not work, but reading from the appropriate /dev/input/eventX node results in a -ENOSPC. Has anyone else seen this? I have a patch for it, but I am puzzled that nobody else seems to need it...
Nope, not seen here. Might be systemd related?

---

### Post by kosumi68 on 2012-08-25
> **frigaut said:**
> Nope, not seen here. Might be systemd related?

The problem is there even when I boot with "init=/bin/bash". It is all very puzzling. :-(

---

### Post by bfroemel on 2012-08-25
> **kosumi68 said:**
> With a pristine mainline head, i915 builtin, no nouveau, and your patch applied, I can finally resume (systemd variant) my MacBookPro10,1 to a functional screen. It works!

The reversal of the gwr logic looks intriguing... *reads thread*

Excellent, thank you.

EDIT: Moreover, after resuming once, I can actually switch graphics mode with xrandr, looking at sane default fonts for the first time. :-)
Thanks for testing and glad that it works for you too! Turned out (Thanks to Seth Forshee) that not all changes are necessary -- I submitted this refined version of the patch:
[http://article.gmane.org/gmane.linux.drivers.platform.x86.devel/3794](http://article.gmane.org/gmane.linux.drivers.platform.x86.devel/3794)

---

### Post by peterpan891 on 2012-08-25
I have added a recipe to ge the Intel graphics driver going, in fact linked a full description of installing Ubuntu 12.04 on a Macbook Pro Retina from scratch. Please find this on 

[http://www.physik.uni-freiburg.de/~helger/retina.html](http://www.physik.uni-freiburg.de/~helger/retina.html)

---

### Post by kosumi68 on 2012-08-25
> **kosumi68 said:**
> The problem is there even when I boot with "init=/bin/bash". It is all very puzzling. :-(

Turns out the CONFIG_USB_EHCI_TT_NEWSCHED option is necessary because of the way the bcm5974 squeezes several transactions into one microframe. Obvious... ;-)

This option is common in the distros, so problem fixed for now.

---

### Post by bfroemel on 2012-08-26
> **kosumi68 said:**
> Turns out the CONFIG_USB_EHCI_TT_NEWSCHED option is necessary because of the way the bcm5974 squeezes several transactions into one microframe. Obvious... ;-)

Good find! Maybe you want to submit a dependency patch (drivers/input/mouse/Kconfig) to the linux kernel?

---

### Post by kosumi68 on 2012-08-26
> **bfroemel said:**
> Good find! Maybe you want to submit a dependency patch (drivers/input/mouse/Kconfig) to the linux kernel?

I sent a patch yesterday which makes bcm5974 work without the dependency.

---

### Post by frigaut on 2012-08-26
> **kosumi68 said:**
> I sent a patch yesterday which makes bcm5974 work without the dependency.

What I don't get is why we don't have the same problem.

---

### Post by bfroemel on 2012-08-27
> **kosumi68 said:**
> I sent a patch yesterday which makes bcm5974 work without the dependency.
Ha, didn't get that you're Henrik and as the maintainer probably found a much better suited solution ;)

---

### Post by kosumi68 on 2012-08-27
> **frigaut said:**
> What I don't get is why we don't have the same problem.

Very few people run a kernel with CONFIG_USB_EHCI_TT_NEWSCHED off, which is why noone else had seen it. In fact, it is even stupid to do so, since the "new" scheduler was introduced in 2006, with the aim to replace the old one. The right patch is likely the one that removes the config option altogether. :-)

---

### Post by enchanterchi on 2012-08-28
The MBP dosen't have eth0. So the HOSTID is "0000000000". But a lot of software's licenses need the HOSTID. Anyone has solution for it?

Thanks.

---

### Post by bfroemel on 2012-08-28
> The MBP dosen't have eth0. So the HOSTID is "0000000000". But a lot of software's licenses need the HOSTID. Anyone has solution for it?

Depending on your situation:
-) [easiest] use a Thunderbolt/USB ethernet dongle
-) [most practical, requires floating licenses] use a virtual machine (e.g., kvm) for licensing
-) [cleanest] rename device: e.g., [http://www.artwork.com/support/linux/eth0_configuration.htm](http://www.artwork.com/support/linux/eth0_configuration.htm)

---

### Post by ASven on 2012-08-28
> **bfroemel said:**
> Depending on your situation:
-) [easiest] use a Thunderbolt/USB ethernet dongle
-) [most practical, requires floating licenses] use a virtual machine (e.g., kvm) for licensing
-) [cleanest] rename device: e.g., [http://www.artwork.com/support/linux/eth0_configuration.htm](http://www.artwork.com/support/linux/eth0_configuration.htm)

Maybe this will work:
Load "dummy" network module (modprobe dummy)
Rename dummy0 device to eth0 (ip link set dummy0 name eth0)
Set mac address manually (ip link set eth0 address 11:22:33:44:55:66)

---

### Post by sauferkel on 2012-08-29
Hey guys,
 
i got some questions......
 
either i did not read it or you didn't mention it, but is the HDMI out supported? just with nvidia i guess, or also with intel only? 
 
did anyone get the screen backlight controlled? this is really a must, at least for me...
 
and you are all using efi boot , right ? 
 
thanks for the answers and especially for your nice work!!!
 
 
:)

---

### Post by frigaut on 2012-08-29
> **sauferkel said:**
> Hey guys,
 
i got some questions......
 
either i did not read it or you didn't mention it, but is the HDMI out supported? just with nvidia i guess, or also with intel only? 

Nope, the intel is not controlling the HDMI output, just the nvidia. I haven't checked the HDMI output yet, but now I'm curious.
> did anyone get the screen backlight controlled? this is really a must, at least for me...

You mean with nvidia? Last I tried, it didn't work with the nvidia blob. It works with the intel driver. Not sure with nouveau.
> 
and you are all using efi boot , right ? 

bfroemel and I are as well as devs that I have been following (Greg KH, Seth Forshee). Not sure about the general case.

---

### Post by gschwind on 2012-08-29
I just managed to make backlight working with this tips :

I have a kernel with lasted gmux patch and I use nvidia propietary driver 304.37.

if I boot nvidia driver seems disable gmux (gmux is detected but changing backlight value have no effect), and I cannot get backlight control, but after supend to RAM and turn on, backlight control is back :D

so it could be usefull :)

this could be a track.

---

### Post by magnumripper on 2012-08-30
> **gschwind said:**
> I have a kernel with lasted gmux patch and I use nvidia propietary driver 304.37.

Exactly what kernel did you base this on? Latest git or some earlier commit? I tried applying all mentioned patches (a couple seemed already applied in main tree now) upon latest git. Then I downloaded latest nvidia driver, but it (DKMS) fails to build due to some kind of function call protoype mismatch.

I just now tried not blacklisting nouveau, and I got this marvelous resolution except Linux thinks it's 96 dpi (it thinks my screen is 762x476 mm, that would be some laptop). I need to zoom a lot :)  But I was planning on running CUDA and OpenCL so nouveau wont do the job for me anyway.

BTW, does anyone know if it's even remotely possible to run the video on the Intel chip while at the same time running GPGPU on the nvidia? That would be really awesome.

---

### Post by gw280 on 2012-08-30
Hey guys, long time lurker, just wanted to share my experiences getting the rMBP running on Linux (although I'm using Fedora 17 rather than Ubuntu).

- 3.6.0-rc2 works pretty well with all the patches listed earlier in this thread.

- 3.6.0-rc3 works well with just the gmux patch to fix suspend/resume

- When using Intel graphics I've noticed the display tends to distort every so often. Sometimes it's really bad, sometimes it goes for hours without issue. The symptoms are that parts of the screen will update in the wrong place giving off a flickering-type effect. I haven't managed to pinpoint what exactly causes it; sometimes it does it when I move it, sometimes it does it without me even touching the machine. I'm not ruling out a physical hardware issue, but I haven't managed to reproduce in OS X with the Intel GPU force-enabled, nor have I reproduced on Linux when using the nVIDIA GPU (nouveau or nvidia)

- Switchable graphics kind of works, but it's not ideal. Recently I've found that the Intel GPU can be brought up by my Linux installation without the need to force-enable in OS X, oddly enough.

- Screen backlight works fine in Intel so long as you have an up to date xorg-x11-drv-intel package. It works in nVIDIA 304.43 after a suspend/resume cycle.

- Wireless is extremely flakey. b43 kind of works, but has low throughput (I was measuring 30-60kB/s on an 802.11g network earlier) and buggy power management (was experiencing high packet loss when too far or too close to the access point). ndiswrapper gives better throughput (have had 2MB/s on 802.11g) but seems unstable on 802.11n, and connections randomly drop more often than with b43.

- Power management is pretty good. With the nVIDIA blob drivers and backlight on ~50% my machine idles at about 17W with Thunderbird, Firefox, Skype open.  With Intel you gain another few W on average. nouveau has terrible power management support and doesn't seem to downclock the GPU when it's not under load, so expect the machine to run physically quite warm.

- Native EFI booting works well. I had a few issues with the Fedora installer but those issues are off topic here. Just ensure that the EFI boot volume is blessed properly and all should be well.

- Suspend and resume works fine with the Intel drivers as well as the nVIDIA ones. Nouveau is a no-go on this front.

- nVIDIA 304.34 had a serious issue where the EQ would overflow in the X server, and the driver would crash. I haven't yet noticed the issue on 304.43.

- Multitouch input is flakey at best. Despite lots of tweaking with xf86-input-mtrack, I still haven't found a configuration that doesn't register false clicks. My biggest issue is the case where I'm resting my thumb on the trackpad and moving the cursor with my index finger; when I want to register a left click, about 50% of the time it'll register as a right click because it'll think it's a two finger touch. For now I've worked around this by setting three finger click to be right click, four finger click to be a middle click and single and two finger clicks to be a left click.

- Microphone doesn't work, but speakers do. Headphone out works as well, and the little red LED that comes on inside the line out port is due to the IEC958 output (digital out) being active when it shouldn't. Just run "amixer -c0 set IEC958 mute" to turn it off.

- Keyboard backlight works, but you need the userspace to support it from the keyboard, otherwise you're going to need to prod /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness with echo -n.

- Webcam works, but without the microphone it's not a huge amount of use :)

That's all for now. I'm considering trying out the latest kernel from git but until then, 3.6.0-rc2 seems more stable to me than 3.6.0-rc3.

---

### Post by bfroemel on 2012-08-31
Thanks for the thorough report, gw280!

> - When using Intel graphics I've noticed the display tends to distort every so often. 
No issue here - I am on 3.6.0-rc3, and I use X.Org 1.12.3; although I force the Intel GPU in OSX.
Maybe you could make some pictures of the problem (and also screenshots and verify that at least they are correct) and post everything on [email]intel-gfx@lists.freedesktop.org[/email] 


> - Wireless is extremely flakey. 
Yes :/ .. currently one of my biggest issues with the laptop. I hope this is fixed soon; unfortunately I have no idea whats the exact b43 status and if this is already on someones schedule.

---

### Post by frigaut on 2012-08-31
> **magnumripper said:**
> I just now tried not blacklisting nouveau, and I got this marvelous resolution except Linux thinks it's 96 dpi (it thinks my screen is 762x476 mm, that would be some laptop). I need to zoom a lot :)

Oh, that's no surprise. X has rarely got my dpi right...but just startx - --dpi xxx and you're rolling (or set it in an xorg conf file or in your .xinitrc).

> BTW, does anyone know if it's even remotely possible to run the video on the Intel chip while at the same time running GPGPU on the nvidia? That would be really awesome.
That's a very good question. I haven't tried myself but I'd like to use the GPGPU eventually. Let us know if you experiment. I see at least one issue which is to install the intel and nvidia drivers in parallel, but that can be worked around.

---

### Post by frigaut on 2012-08-31
Yes, thanks for the very complete report and hints gw280.

Same here than bfroemel: no issues with distortions with the intel driver.

b43 is flaky for me only when I'm too close to the wireless station, for some unknown reason...otherwise getting regularly 3-400kBytes/s or more.

Not sure how I reconcile these 2 statements:
> 
- 3.6.0-rc2 works pretty well with all the patches listed earlier in this thread.
- 3.6.0-rc3 works well with just the gmux patch to fix suspend/resume
and
> 
[...] but until then, 3.6.0-rc2 seems more stable to me than 3.6.0-rc3.

---

### Post by catus on 2012-08-31
Hello everyone. I have been playing around with Ubuntu 12.04 on my rMBP the past few days, and now I finally get a usable environment.
First I want to say thanks to the Mactel Support Team and everyone else who posted a lot of hints and instructions. For a non-technical user like me, it wouldn't be possible even just to run the Ubuntu Live CD without your help. So I want to share my experience in hope of helping others and contributing to Ubuntu's Mactel support.

Laptop details:
[LIST=1]
[*]Memory: 8GB
[*]Intel® Core&#8482; i7-3615QM CPU @ 2.30GHz × 8
[*]Graphics: GeForce GT 650M/PCIe/SSE2 + Intel HD 4000
[*]256GB SSD
[/LIST]

Current system:
[LIST=1]
[*]Ubuntu 12.04 (x64) with Linux 3.5.0-13, no special kernel options. (I mean, I'm NOT using any of the following: nomodeset, noacpi, nointremap.)
[*]Installed nvidia-current.
[*]Booting from EFI
[*]Mactel PPA & xorg-edgers PPA used.
[/LIST]
Working:
[LIST=1]
[*]WiFi (This model is already supported, I just need to download and extract the firmware.)
[*]EFI (rEFIt + MBR at first, grub-efi installed later)
[*]Keyboard (Choose US Macintosh layout. Backlight controllable using F5 & F6.)
[*]Screen (Full resolution on nvidia-current, Linux 3.5. But I can't choose lower resolution and Brightness control sometimes work while sometimes doesn't, see below)
[*]Sound (Volume control working.)
[*]Touchpad (Gestures okay, but touchegg is not working, see below.)
[*]Camera (Native support w/o drivers.)
[*]Fans (Don't need special steps to setup.)
[*]Power management (Good battery life, with some minor optimization on the video card.)
[*]Suspend and resume
[/LIST]

Not working:
[LIST=1]
[*]Microphone
[*]Bluetooth (Not recognized. Missing driver?)
[*]Thunderbolt (including wired network via "Thunderbolt to Ethernet". I had to use WiFi all the time.)
[*]Hibernate (but suspension works, why?)
[*]Not able to choose lower screen resolution. (Modeline in xorg.conf doesn't work. xrandr reports resolution too small to fit the screen.) (I'm currently using a big font size in order to save my eye.)
[*]Brightness control sometimes doesn't work. (Oops, did I say that just now?)
[*]Intel HD Graphics (It never shows up. When I disable Nvidia driver or install bumblebee, Ubuntu says my video card is "Unknown" and falls back to Ubuntu 2D. Maybe newer kernels could help me switch the video cards. Or maybe I did something wrong?)
[*]touchegg (The deeper source should be in the evdev driver. I can't move my cursor when I use evdev, but I can click by pressing the touchpad. I'm using synaptics now.)
[*](Please tell me if I forgot about anything.)
[/LIST]

Some random hints:
The Ubuntu Live CD must have nomodeset and noacpi on in order to boot. These two options should be kept until you installed Linux 3.5 and nvidia drivers.
Before you do your partition, READ THIS: rEFIt will only sync the FIRST FOUR (4) GPT partitions to MBR. It's not a bug. The first will be EFI, the second will be Mac OS X, and the third will be Mac Recover. So you must install grub on the first linux partition you create, which will take the only position left in MBR.
You can't get full resolution when booting from MBR. Use EFI please.
When things are messed up, the Ubuntu Live CD can be used to revert changes.
Don't precisely follow the other WiFi setup instructions. Just install the two b43 packages, download the driver, and extract the firmware using b43-fwcutter. When you don't have internet connection, download *.deb and the driver using Mac OS X, or plug another WiFi via USB.
MyUnity can be used to increase system font size if your resolution can't go down. You can also tell your browser to zoom 200% by default.
Chromium will blacklist your GPUs. Don't worry, you can use --ignore-gpu-blacklist if your nvidia card is in use.


I would really like to describe what I've done after installation, but since I touched a lot of things, I don't know which step makes which feature work. If I have more time, I will write about it. I'm willing to add links to my report, but I don't know how.

---

### Post by frigaut on 2012-08-31
Guys,
What an active thread !

Well, I have some news about the microphone.

Booting with 
```
options snd-hda-intel model=imac27
``` 
in a modprobe.d conf file gives access to new inputs: line in, internal microphone and digital input.

selecting "internal microphone" and pushing the capture volume to max does give me something (as per pavucontrol and arecord / aplay). But it's very faint and a bit distorted. 

Your turn. It's very late here.

---

### Post by catus on 2012-08-31
> **frigaut said:**
> Guys,
What an active thread !

Well, I have some news about the microphone.

Booting with 
```
options snd-hda-intel model=imac27
``` 
in a modprobe.d conf file gives access to new inputs: line in, internal microphone and digital input.

selecting "internal microphone" and pushing the capture volume to max does give me something (as per pavucontrol and arecord / aplay). But it's very faint and a bit distorted. 

Your turn. It's very late here.

Sorry, that doesn't work for me...

P.S. I discovered that my Bluetooth is not recognized. I'll add it to the list.

---

### Post by catus on 2012-08-31
OK. So screen brightness control doesn't work on booting, but works after a suspend/resume. Any idea why?

---

### Post by frigaut on 2012-08-31
> **catus said:**
> Sorry, that doesn't work for me...
Well, it doesn't really "work" for me either, but it's a step in the right direction.

> P.S. I discovered that my Bluetooth is not recognized. I'll add it to the list.
For bluetooth, you have to apply this patch: [http://www.spinics.net/lists/linux-bluetooth/msg26954.html](http://www.spinics.net/lists/linux-bluetooth/msg26954.html)
I tested it, it works.

---

### Post by gw280 on 2012-09-01
> **bfroemel said:**
> Thanks for the thorough report, gw280!

No problem! Am here to provide feedback/assistance!

> **bfroemel said:**
> No issue here - I am on 3.6.0-rc3, and I use X.Org 1.12.3; although I force the Intel GPU in OSX.
Maybe you could make some pictures of the problem (and also screenshots and verify that at least they are correct) and post everything on [EMAIL="intel-gfx@lists.freedesktop.org"]intel-gfx@lists.freedesktop.org [/EMAIL] 
Out of interest, does your rMBP have the Samsung or the LG LCD panel? I think the LG is significantly more common, and mine has the Samsung. Could narrow down possibilities.

> **bfroemel said:**
> Yes :/ .. currently one of my biggest issues with the laptop. I hope this is fixed soon; unfortunately I have no idea whats the exact b43 status and if this is already on someones schedule.
I spoke with the b43 devs and they could provide no ETA on getting it up and running. Apparently they've not managed to reverse engineer the power management for the 802.11n Broadcom chips, and that's the major issue right now. You may have better luck with ndiswrapper.

Hopefully Broadcom will update their proprietary drivers to support the bcm4331 soon.

---

### Post by gw280 on 2012-09-01
> **frigaut said:**
> Yes, thanks for the very complete report and hints gw280.

Same here than bfroemel: no issues with distortions with the intel driver.

b43 is flaky for me only when I'm too close to the wireless station, for some unknown reason...otherwise getting regularly 3-400kBytes/s or more.

Not sure how I reconcile these 2 statements:
and
That's more of a gut feeling than any sort of hard statement. I noticed a couple of crashes on -rc3, but none on -rc2. It could have just been a fluke.

---

### Post by kosumi68 on 2012-09-01
> **catus said:**
> Sorry, that doesn't work for me...

P.S. I discovered that my Bluetooth is not recognized. I'll add it to the list.

The patch is applied to the bluetooth tree and will appear in mainline shortly.

---

### Post by kosumi68 on 2012-09-01
> **frigaut said:**
> Well, it doesn't really "work" for me either, but it's a step in the right direction.


For bluetooth, you have to apply this patch: [http://www.spinics.net/lists/linux-bluetooth/msg26954.html](http://www.spinics.net/lists/linux-bluetooth/msg26954.html)
I tested it, it works.

Disabling the nvidia controller (by disabling the pci entry in hda_intel.c) made the noise disappear, but I have had no luck getting any signal from the microphone either.

---

### Post by yahyavi on 2012-09-01
> **BlueDragonX said:**
> There is no bug, wireless works fine. You need to load the firmware for the BCM4331 before it works.

You'll need to use fwcutter to pull the firmware out of a relatively new BCM driver.

1. Download driver:
wget [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)

2. Install fwcutter:
apt-get install b43-fwcutter

3. Extract firmware:
tar -xf broadcom-wl-5.100.138.tar.bz2
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.100.138/linux/wl_apsta.o

6. Reload your b43 kernel module:
sudo rmmod b43
sudo modprobe b43

7. Use your wireless.



Try passing on the kernel commandline on boot: noapic

I've been running 3.5.0-r7 since release. It has one of my patches in it =P


Your post saved me a lot of time and effort. Thanks!

---

### Post by magnumripper on 2012-09-02
> **magnumripper said:**
> Exactly what kernel did you base this on? Latest git or some earlier commit? I tried applying all mentioned patches (a couple seemed already applied in main tree now) upon latest git. Then I downloaded latest nvidia driver, but it (DKMS) fails to build due to some kind of function call protoype mismatch.

That DKMS build problem I had (with 304.37) seem to be solved with nvidia 304.43.

Edit: so why do I get the VESA FB instead of nvidia in X? Do I need to upgrade the whole xorg stuff? Or do I need to set something or switch something somewhere at boot?

Edit2: Hm, kernel module does not load:
```
[    4.409977] nvidia: module license 'NVIDIA' taints kernel.
[    4.413213] nvidia: disagrees about version of symbol pci_enable_device
[    4.413216] nvidia: Unknown symbol pci_enable_device (err -22)
[    4.413223] nvidia: disagrees about version of symbol agp_bind_memory
[    4.413225] nvidia: Unknown symbol agp_bind_memory (err -22)
[    4.413228] nvidia: disagrees about version of symbol pci_enable_msi_block
[    4.413229] nvidia: Unknown symbol pci_enable_msi_block (err -22)
[    4.413235] nvidia: disagrees about version of symbol pci_dev_put
[    4.413236] nvidia: Unknown symbol pci_dev_put (err -22)
[    4.413242] nvidia: disagrees about version of symbol pci_get_device
[    4.413244] nvidia: Unknown symbol pci_get_device (err -22)
[    4.413248] nvidia: disagrees about version of symbol agp_enable
[    4.413250] nvidia: Unknown symbol agp_enable (err -22)
[    4.413253] nvidia: disagrees about version of symbol __pci_register_driver
[    4.413254] nvidia: Unknown symbol __pci_register_driver (err -22)
[    4.413262] nvidia: disagrees about version of symbol pci_disable_msi
[    4.413264] nvidia: Unknown symbol pci_disable_msi (err -22)
[    4.413276] nvidia: disagrees about version of symbol pci_bus_write_config_byte
[    4.413278] nvidia: Unknown symbol pci_bus_write_config_byte (err -22)
[    4.413291] nvidia: disagrees about version of symbol pci_unregister_driver
[    4.413293] nvidia: Unknown symbol pci_unregister_driver (err -22)
[    4.413295] nvidia: disagrees about version of symbol agp_backend_acquire
[    4.413297] nvidia: Unknown symbol agp_backend_acquire (err -22)
[    4.413313] nvidia: disagrees about version of symbol pci_bus_read_config_dword
[    4.413314] nvidia: Unknown symbol pci_bus_read_config_dword (err -22)
[    4.413319] nvidia: disagrees about version of symbol pci_bus_read_config_word
[    4.413320] nvidia: Unknown symbol pci_bus_read_config_word (err -22)
[    4.413343] nvidia: disagrees about version of symbol agp_free_memory
[    4.413345] nvidia: Unknown symbol agp_free_memory (err -22)
[    4.413359] nvidia: disagrees about version of symbol pci_get_domain_bus_and_slot
[    4.413360] nvidia: Unknown symbol pci_get_domain_bus_and_slot (err -22)
[    4.413379] nvidia: disagrees about version of symbol pci_bus_write_config_dword
[    4.413380] nvidia: Unknown symbol pci_bus_write_config_dword (err -22)
[    4.413393] nvidia: disagrees about version of symbol vga_tryget
[    4.413395] nvidia: Unknown symbol vga_tryget (err -22)
[    4.413399] nvidia: disagrees about version of symbol agp_allocate_memory
[    4.413400] nvidia: Unknown symbol agp_allocate_memory (err -22)
[    4.413402] nvidia: disagrees about version of symbol pci_set_master
[    4.413403] nvidia: Unknown symbol pci_set_master (err -22)
[    4.413409] nvidia: disagrees about version of symbol agp_unbind_memory
[    4.413410] nvidia: Unknown symbol agp_unbind_memory (err -22)
[    4.413420] nvidia: disagrees about version of symbol pci_bus_write_config_word
[    4.413421] nvidia: Unknown symbol pci_bus_write_config_word (err -22)
[    4.413432] nvidia: disagrees about version of symbol pci_get_class
[    4.413433] nvidia: Unknown symbol pci_get_class (err -22)
[    4.413456] nvidia: disagrees about version of symbol agp_copy_info
[    4.413457] nvidia: Unknown symbol agp_copy_info (err -22)
[    4.413462] nvidia: disagrees about version of symbol pci_disable_device
[    4.413463] nvidia: Unknown symbol pci_disable_device (err -22)
[    4.413470] nvidia: disagrees about version of symbol vga_set_legacy_decoding
[    4.413472] nvidia: Unknown symbol vga_set_legacy_decoding (err -22)
[    4.413476] nvidia: disagrees about version of symbol agp_backend_release
[    4.413478] nvidia: Unknown symbol agp_backend_release (err -22)
[    4.413481] nvidia: disagrees about version of symbol pci_bus_read_config_byte
[    4.413482] nvidia: Unknown symbol pci_bus_read_config_byte (err -22)

```

---

### Post by magnumripper on 2012-09-02
Linux is not as good at adopting to DPI as I thought it would. I did the following so far, running Mint 13:

First, I added this to xorg.conf (size was calculated for now, not measured):
```
--- xorg.conf.nvidia-xconfig-original    2012-09-03 00:40:51.646970701 +0200
+++ xorg.conf    2012-09-02 23:48:34.440074233 +0200
@@ -34,6 +34,7 @@
     HorizSync       28.0 - 33.0
     VertRefresh     43.0 - 72.0
     Option         "DPMS"
+    DisplaySize    322 201
 EndSection
 
 Section "Device"

```

Then:

1. set /desktop/mate/font_rendering/dpi to 220 in "configuration editor". This fixed a lot. Things like the Terminal Windows or Emacs (in X) are fine after this.
2. In Firefox and Thunderbird, set layout.css.dpi to 220, and double the default font sizes (click "Advanced" to get to the mono-space one)

git gui look terrible, and some other things too. A truckload of icons should be scaled.

---

### Post by tgwaste on 2012-09-05
rc3 & rc4 gave me garbled screens.  trying to install the driver from here:

[http://www.techlw.com/2012/06/install-nvidia-driver-in-ubuntu.html](http://www.techlw.com/2012/06/install-nvidia-driver-in-ubuntu.html)

gives me blackscreens.

I keep seeing people say they are forcing the usage of the intel 4000 driver.  how do you do that?

---

### Post by catus on 2012-09-05
I just installed Ubuntu 12.10 Beta, and my touchpad partially stopped working. I can't move the cursor by moving my fingers around, but I can use four-finger tapping to open Dash, and drag with 3 fingers to move windows. How strange.

touchegg still gives no response.

I think the problem is caused by evdev. 

EDIT: I installed xserver-xorg-input-synaptics just now, and the touchpad works after a reboot.

---

### Post by bfroemel on 2012-09-06
> Out of interest, does your rMBP have the Samsung or the LG LCD panel? I think the LG is significantly more common, and mine has the Samsung. Could narrow down possibilities.
No, mine is a Samsung too.

> Apparently they've not managed to reverse engineer the power management for the 802.11n Broadcom chips, and that's the major issue right now. You may have better luck with ndiswrapper.
I'll look into this as soon as I have a bit more spare time again. Having dongles for ethernet, beamers and now wireless too is just not the right way.

> I keep seeing people say they are forcing the usage of the intel 4000 driver. how do you do that? 
gfxcardstatus, but apparently this was/is a bug in gfxcardstatus and might be already fixed in the most recent version. I set the option 'Integrated Only' and shutdown. After that every boot into Linux is with the Intel GPU even across shutdowns.

---

### Post by tgwaste on 2012-09-06
> **bfroemel said:**
> No, mine is a Samsung too.


I'll look into this as soon as I have a bit more spare time again. Having dongles for ethernet, beamers and now wireless too is just not the right way.


gfxcardstatus, but apparently this was/is a bug in gfxcardstatus and might be already fixed in the most recent version. I set the option 'Integrated Only' and shutdown. After that every boot into Linux is with the Intel GPU even across shutdowns.

ya that doesnt really seem to do anything. :(

---

### Post by magnumripper on 2012-09-06
> **bfroemel said:**
> gfxcardstatus, but apparently this was/is a bug in gfxcardstatus and might be already fixed in the most recent version. I set the option 'Integrated Only' and shutdown. After that every boot into Linux is with the Intel GPU even across shutdowns.

What version are you using? We can pick old ones at [http://codykrieger.com/gfxCardStatus/changelog](http://codykrieger.com/gfxCardStatus/changelog)

---

### Post by tgwaste on 2012-09-06
> **magnumripper said:**
> What version are you using? We can pick old ones at [http://codykrieger.com/gfxCardStatus/changelog](http://codykrieger.com/gfxCardStatus/changelog)

mine appears to be stuck on intel now and I cant seem to change it.

---

### Post by tgwaste on 2012-09-06
> **tgwaste said:**
> mine appears to be stuck on intel now and I cant seem to change it.

fixed that and got it back to nvidia.

its a shame I can not get the display to do anything other than the crappy 1280x768 resolution no matter what I try.  I guess im missing some big step somewhere.

---

### Post by magnumripper on 2012-09-06
> **tgwaste said:**
> fixed that and got it back to nvidia.

its a shame I can not get the display to do anything other than the crappy 1280x768 resolution no matter what I try.  I guess im missing some big step somewhere.

I believe that means you get VESA frambuffer. You should be able to get nouveau working with full resolution, I get it as soon as I stop blacklisting it. My problem is need OpenCL, and nouveau is not anywhere near supporting that afaik.

---

### Post by bfroemel on 2012-09-07
> What version are you using?
2.2.1, apparently the 'fix' will be released in 2.3:
[https://github.com/codykrieger/gfxCardStatus/pull/92](https://github.com/codykrieger/gfxCardStatus/pull/92)

> mine appears to be stuck on intel now and I cant seem to change it. 
Yes, after you did this and boot the first time into OSX, OSX seems to not be able to switch to the discrete GPU. Another reboot fixes this; currently no issue for me, because I am using the laptop with Linux only.

---

### Post by bfroemel on 2012-09-07
btw: which kernel versions are you using? pre 3.6-rc3 require a lot of patches. 3.6-rc3 and rc4 should be good with:
[http://cgit.freedesktop.org/nouveau/linux-2.6/commit/?id=783659921839dea868471db9243e85eaf39d2a72](http://cgit.freedesktop.org/nouveau/linux-2.6/commit/?id=783659921839dea868471db9243e85eaf39d2a72)
[http://cgit.freedesktop.org/nouveau/linux-2.6/commit/?id=428f532b2f05ace4023ade7a3bef31e0b6cf5352](http://cgit.freedesktop.org/nouveau/linux-2.6/commit/?id=428f532b2f05ace4023ade7a3bef31e0b6cf5352)
[http://thread.gmane.org/gmane.linux.drivers.platform.x86.devel/3793/focus=3794](http://thread.gmane.org/gmane.linux.drivers.platform.x86.devel/3793/focus=3794)

---

### Post by sauferkel on 2012-09-07
Did anyone try a dualboot configuration with linux and windows ? :P

I would like to use the intel gpu in linux, but the nvidia gpu in windows ...and get rid of osx on this small harddisk, maybe put it on an external one...

but as i understood it, OSX is needed to switch the graphics card, right ?

---

### Post by bfroemel on 2012-09-07
> **sauferkel said:**
> 
but as i understood it, OSX is needed to switch the graphics card, right ?
Currently, yes - but this is only very temporary. As soon as the intel drivers can handle initialization without connected outputs, GPU switching should work in Linux (vgaswitcheroo) without any need of OSX/gfxcardstatus.

---

### Post by magnumripper on 2012-09-08
> **bfroemel said:**
> btw: which kernel versions are you using? pre 3.6-rc3 require a lot of patches. 3.6-rc3 and rc4 should be good with:
[http://cgit.freedesktop.org/nouveau/linux-2.6/commit/?id=783659921839dea868471db9243e85eaf39d2a72](http://cgit.freedesktop.org/nouveau/linux-2.6/commit/?id=783659921839dea868471db9243e85eaf39d2a72)
[http://cgit.freedesktop.org/nouveau/linux-2.6/commit/?id=428f532b2f05ace4023ade7a3bef31e0b6cf5352](http://cgit.freedesktop.org/nouveau/linux-2.6/commit/?id=428f532b2f05ace4023ade7a3bef31e0b6cf5352)
[http://thread.gmane.org/gmane.linux.drivers.platform.x86.devel/3793/focus=3794](http://thread.gmane.org/gmane.linux.drivers.platform.x86.devel/3793/focus=3794)

Thanks. When you say "should be good", do you mean I should be able to get the nvidia driver running? Or will it just work well with nouveau?

I still haven't tried downgrading gfxCardStatus, maybe that's my next step.

---

### Post by bfroemel on 2012-09-08
> **magnumripper said:**
> Thanks. When you say "should be good", do you mean I should be able to get the nvidia driver running? Or will it just work well with nouveau?

With the listed patches you should be able to use intel and nouveau + have working backlight control. Also suspend/resume should work well enough, although this is about 3-4 seconds slower than it have to be.

> 
I still haven't tried downgrading gfxCardStatus, maybe that's my next step.
afaik version 2.2.1 (currently most recent one) still contains the bug that we use to force the laptop to boot with the Intel GPU: no need to downgrade. Force integrated GPU, shutdown and boot into Linux.
Of course, if you want to use the Nvidia GPU only, there is no need to use gfxcardstatus and force the integrated GPU.

About nvidia blob driver) Try the most recent beta version; backlight control might not work, as the gmux device (that controls the backlight) seems to be disabled somehow by the nvidia driver.

---

### Post by magnumripper on 2012-09-08
> **bfroemel said:**
> With the listed patches you should be able to use intel and nouveau + have working backlight control. Also suspend/resume should work well enough, although this is about 3-4 seconds slower than it have to be.

The patches you listed does not apply though. Or did I screw something up? On master, RC4 or RC3 I get this error:

Applying: drm/nouveau/gpio: initialise to vbios defaults during init
error: drivers/gpu/drm/nouveau/core/include/subdev/gpio.h: does not exist in index
error: drivers/gpu/drm/nouveau/core/subdev/gpio/base.c: does not exist in index
Patch failed at 0001 drm/nouveau/gpio: initialise to vbios defaults during init

With the files not even existing, I can't even try to resolve it manually. The other two patches might be appliable with some manual work. I'm not sure how to proceed.

---

### Post by gw280 on 2012-09-09
I see that 3.6.0-rc5 is now out. Are the gmux patches in that now? How about the nouveau patches?

---

### Post by bfroemel on 2012-09-09
> The patches you listed does not apply though. 
My bad, comment 22 explains this:
[https://bugs.freedesktop.org/show_bug.cgi?id=51971](https://bugs.freedesktop.org/show_bug.cgi?id=51971)

Then you either need to use the patches listed in the above bug report that fixes nouveau drivers only for the retina mbp, wait for the appropriate backport or do it yourself.

> The other two patches might be appliable with some manual work.
They apply cleanly even on the recently released rc5, however they need at least rc3.

I suggest to wait a few weeks, at most a month or two and you probably have a much better user experience. Unfortunately, right now it's a bit of a mess/transitional phase where you have a much better (kernel) developer/tester experience ;)

---

### Post by bfroemel on 2012-09-09
> I see that 3.6.0-rc5 is now out. Are the gmux patches in that now?
Unfortunately no -- maybe the merge window for that part of the linux kernel driver has already closed; maybe the maintainer had no time or other reasons to not submit yet.

> How about the nouveau patches?
Not there yet:
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=history;f=drivers/gpu/drm/nouveau;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=history;f=drivers/gpu/drm/nouveau;hb=HEAD)

---

### Post by magnumripper on 2012-09-09
> **bfroemel said:**
> They apply cleanly even on the recently released rc5, however they need at least rc3.

The second does not apply cleanly but I resolved it. The "case DCB_OUTPUT_DP:" now reads "case OUTPUT_DP:", that's all.

The third actually applied cleanly after I fixed a copy/paste issue with it :-)

BTW, the third (your) patch was originally a patch 1 of 2. Should I not apply the second one of them? It too seems to apply cleanly. OTOH from looking at it, maybe it's just cosmetical.

---

### Post by magnumripper on 2012-09-09
> **bfroemel said:**
> My bad, comment 22 explains this:
[https://bugs.freedesktop.org/show_bug.cgi?id=51971](https://bugs.freedesktop.org/show_bug.cgi?id=51971)

Then you either need to use the patches listed in the above bug report that fixes nouveau drivers only for the retina mbp, wait for the appropriate backport or do it yourself.

But for running the nvidia driver and no nouveau, I should be fine with just the other two patches, right? I seem to be closer than ever now...

```
$ dmesg|grep -Ei nvidia\|NVRM
[    4.404369] nvidia: module license 'NVIDIA' taints kernel.
[    4.411597] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.43  Sun Aug 19 20:14:03 PDT 2012
[    5.095717] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input6
[    5.095797] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input7
[    5.095879] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[    5.579200] NVRM: failed to copy vbios to system memory.
[    5.584977] NVRM: RmInitAdapter failed! (0x30:0xffffffff:861)
[    5.584995] NVRM: rm_init_adapter(0) failed
[    8.642286] NVRM: failed to copy vbios to system memory.
[    8.647969] NVRM: RmInitAdapter failed! (0x30:0xffffffff:861)
[    8.647987] NVRM: rm_init_adapter(0) failed
[   11.836565] NVRM: failed to copy vbios to system memory.
[   11.842413] NVRM: RmInitAdapter failed! (0x30:0xffffffff:861)
[   11.842435] NVRM: rm_init_adapter(0) failed

```

---

### Post by bfroemel on 2012-09-09
> **magnumripper said:**
> The second does not apply cleanly but I resolved it. The "case DCB_OUTPUT_DP:" now reads "case OUTPUT_DP:", that's all.

The third actually applied cleanly after I fixed a copy/paste issue with it :-)

BTW, the third (your) patch was originally a patch 1 of 2. Should I not apply the second one of them? It too seems to apply cleanly. OTOH from looking at it, maybe it's just cosmetical.
There is the misunderstanding: I meant both patches and wanted to link to the start of the patch series not the 1 of 2; but the 2 of 2 is only cosmetic.

The first two links concern only nouveau and don't apply cleanly to 3.6. They need to be backported so that they work or you can apply the two patches in the linked bug report. However those are only hacks to get the screen working on the rmbp.

> ut for running the nvidia driver and no nouveau, I should be fine with just the other two patches, right? I seem to be closer than ever now...
Yes, actually you would require none of the patches to get the nvidia blob driver working. As I said, the gmux device seems to get disabled by the closed source nvidia driver (at least with version 304.32), so whether you have a working gmux driver or not is not relevant.
I see that there are newer non-beta drivers: 304.43 maybe try those, if you aren't already doing so. Regarding nvidia blob/noveau, I am sorry to not be able to help out much further: I am solely on Intel

---

### Post by vickumar on 2012-09-09
Hi guys.

I would like to thank you for all the hard work on this.  Just got the Mac Book Pro 10,1.  I downloaded the 64 bit AMD image to an external CD drive, booted, and installed Ubuntu 12.04.

I boot the kernal (I've updated now to 3.5.0-13-generic since install) with 'noapic' and 'nomodeset' options.

A note here, I only needed 'noapic' to get the kernal to boot w/o a panic from the timer interrupt.  I'm not even sure what 'nomodeset' is doing, or if it should be on or off for properly installing drivers (i've tried xserver-xorg-video-nouveau and also the nvidia-current & also nvidia with a combination of bumblebee, bumblebee-nvidia).

The wireless works after installing the b43-fwcutter and firmware-b43-installer packages manually.

So what isn't working as of right now, at least for me:

[LIST]
[*]   1)  Bluetooth, no blue tooth adapters under System Settings->Bluetooth.
[*]   2)  Retina display, the maximum resolution I get is 1024x768.  I suspect b/c it is using the integrated card with intel driver, rather than the discrete card (Nvidia GE Force 650M) with proprietary drivers.
[/LIST]
I can't figure out how to attach a file, but below is output from my 'lspci -nn' and 'flxinfo |grep OpenGL'.


```
00:00.0 Host bridge [0600]: Intel Corporation Ivy Bridge DRAM Controller [8086:0154] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Ivy Bridge PCI Express Root Port [8086:0151] (rev 09)
00:01.1 PCI bridge [0604]: Intel Corporation Ivy Bridge PCI Express Root Port [8086:0155] (rev 09)
00:01.2 PCI bridge [0604]: Intel Corporation Ivy Bridge PCI Express Root Port [8086:0159] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e57] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0fd5] (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0e1b] (rev a1)
03:00.0 Ethernet controller [0200]: Broadcom Corporation Device [14e4:16a3] (rev 10)
03:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
``````

OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
OpenGL version string: 2.1 Mesa 9.0-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
```
Sorry for the long post.  Any help greatly appreciated.  Thanks!

---

### Post by vickumar on 2012-09-09
Also, the BCM4331 looks like it works a lot faster if you ignore IPV6 packets.  I think I got that from some other post somewhere.

---

### Post by Gustav Andersson on 2012-09-10
Does anyone else have a problem with ctr alt F1 going to blank black screen (but ctrl alt F7 gets me back) using NVidia drivers?

I followed [peterpan891]("http://ubuntuforums.org/member.php?u=1413195")  recipes (thanks!) and got  2880X1800 set up using the fbdrv driver. ctrl alt F1 worked as it should. I then installed CUDA 5 (which works btw) but now ctrl alt f1 just gives me the blank black screen (same problem even if I install the latest non-cudadev NVidia driver)?

Another note, someone asked about the nomodeset option. Without it I could not get the computer to completely power down (or reboot for that matter).

Gustav
[]("http://ubuntuforums.org/member.php?u=1413195")

---

### Post by alexmurray on 2012-09-14
> **bfroemel said:**
> Unfortunately no -- maybe the merge window for that part of the linux kernel driver has already closed; maybe the maintainer had no time or other reasons to not submit yet.

Looks like your last couple fixes for apple-gmux should be in the next 3.6-rc and hence in 3.6 final when it is eventually released - mjg just sent a pull request to Linus - [https://lkml.org/lkml/2012/9/13/577](https://lkml.org/lkml/2012/9/13/577)

---

### Post by nsicad on 2012-09-15
> **alexmurray said:**
> Looks like your last couple fixes for apple-gmux should be in the next 3.6-rc and hence in 3.6 final when it is eventually released - mjg just sent a pull request to Linus - [https://lkml.org/lkml/2012/9/13/577](https://lkml.org/lkml/2012/9/13/577)

Hopefully, these fixes would in the next v3.6-rc6-quantal kernel (ubuntu kernel)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Anybody has experience using v3.6-rc5-quantal in retina?

Edit: 

v3.6-rc5-quantal is not patched for retina, reading the change logs.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc5-quantal/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc5-quantal/CHANGES)

We have just to wait until, we can see this entry.

######
Bernhard Froemel (2):
      apple-gmux: Obtain version info from indexed gmux
      apple-gmux: Fix index read functions######

Then, as for me ubuntu is worth a look again for MacBookPro retina.

---

### Post by magnumripper on 2012-09-16
> **nsicad said:**
> Hopefully, these fixes would in the next v3.6-rc6-quantal kernel (ubuntu kernel)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Anybody has experience using v3.6-rc5-quantal in retina?

Edit: 

v3.6-rc5-quantal is not patched for retina, reading the change logs.


v3.6-rc6-quantal includes Bernhard's patches!

---

### Post by frigaut on 2012-09-17
3.6-rc6 is running smoothly for me (no additional patch).
vga_switcheroo enabled (although I'm using only the intel graphics), good power management (11-13W), bluetooth listed in rfkill (haven't tried it), basically everything that used to work with the heavily patched 3.6rc1 is now working with the vanilla kernel. Thanks and good job to all the devs that pushed all of these patches so effectively to linus.
Note: Microphone still not working.

---

### Post by nsicad on 2012-09-18
> **frigaut said:**
> 3.6-rc6 is running smoothly for me (no additional patch).
vga_switcheroo enabled (although I'm using only the intel graphics), good power management (11-13W), bluetooth listed in rfkill (haven't tried it), basically everything that used to work with the heavily patched 3.6rc1 is now working with the vanilla kernel. Thanks and good job to all the devs that pushed all of these patches so effectively to linus.
Note: Microphone still not working.

I got a kernel panic using the default grub script 3.6-rc6 in my Mac retina 2.3 Ghz.

Could let us, if you are using any grub options to boot?

I am using 3.2 kernel to download the latest kernel (3.6rc6) but very basic no support for graphics. This is lint version. It is booting using usb hard drive.  I like to get good working resolution with 3.6-rc6 but it is not working (as mentioned above - kernel panic).

Is your mac retina 2.3 Ghz or you got a higher Ghz CPU?

Thanks.

---

### Post by frigaut on 2012-09-18
> **nsicad said:**
> I got a kernel panic using the default grub script 3.6-rc6 in my Mac retina 2.3 Ghz.

Could let us, if you are using any grub options to boot?

Lots. Most of them related to the i915 power management (see below). Note that I am booting efi direct (no grub). I'm using refind as the efi bootloader. I am also using systemd, and using archlinux (but that shouldn't make any difference if you build a non-patched 3.6-rc6 kernel).
```
root=/dev/sda4 init=/bin/systemd acpi_osi=Linux i915.lvds_channel_mode=2 i915.modeset=1 i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 drm.vblankoffdelay=1 i915.i915_enable_ppgtt=0 quiet add_efi_memmap
```

> I am using 3.2 kernel to download the latest kernel (3.6rc6) but very basic no support for graphics. This is lint version. It is booting using usb hard drive.  I like to get good working resolution with 3.6-rc6 but it is not working (as mentioned above - kernel panic).
As you've noticed, 3.6-rc6 doesn't even need the nointremap (napic) anymore, so I'm not sure what your kernel panic is caused by. Any message on the console relative to what's happening?

> Is your mac retina 2.3 Ghz or you got a higher Ghz CPU?
Thanks.
model name	: Intel(R) Core(TM) i7-3720QM CPU @ 2.60GHz

---

### Post by nsicad on 2012-09-18
> **frigaut said:**
> 
As you've noticed, 3.6-rc6 doesn't even need the nointremap (napic) anymore, so I'm not sure what your kernel panic is caused by. Any message on the console relative to what's happening?

model name    : Intel(R) Core(TM) i7-3720QM CPU @ 2.60GHz

It stop at this error message:

kernel_thread_helper+0x6/0x10

This error is discussed here:
 
[http://ubuntuforums.org/showthread.php?t=1640299It](http://ubuntuforums.org/showthread.php?t=1640299It) seems like a usb error. It is current the power to the usb 3.0 hard drive.

Yes, noacpi nointeremap and nomodeset did not help.

However, 3.2 kernel boots with this usb 3.0 hard drive.

Thanks

---

### Post by frigaut on 2012-09-18
So, to make sure I understand, you don't want to install linux on your internal disk but want to boot off the external usb drive?
Or is it temporary just for the 3.2 kernel?

---

### Post by nsicad on 2012-09-18
> **frigaut said:**
> So, to make sure I understand, you don't want to install linux on your internal disk but want to boot off the external usb drive?
Or is it temporary just for the 3.2 kernel?

Yes. I don't want to touch my internal drive except just installing refind (i.e. advanced refit that runs in Mountain Lion).

I have been running Linux mint 13 in external usb 3.0 hard drive for a while now with 3.2 kernel (default kernel).

I have been using usb (2 Gb stick) linux mint 13 as installer. I installed mint 13 in usb 3.0 external drive (1 Tb). The default kernel is 3.2. I updated the kernel to 3.5 but it did not work. Now, I updated the kernel to 3.6rc6 and now everything is not working, even the 3.2 kernel.

The problem is:

no init

I think the 3.6rc6 scripts is not properly understand the partition of my 1 Tb drive. It has partitions (2 Mac OS X, 2 MSDOS and 1 Linux).

My 3.2 kernel is also broken now.

Now, I am looking for 12.01 ubuntu with 3.6rc6 as default kernel so I can create another usb installer.

Anybody has ISO / bootable image with 3.6rc6 kernel as the default kernel?

Thanks.

EDIT:

I think the solution for Ubuntu Macbookpro retina is to remaster Ubuntu ISO (12.04) with the new kernel (3.6-rc3). Remastering Ubuntu with the new kernel 3.6-rc6, we can install this in external hard drive. Using Refind we can easily run external hard drive. I have done this with linux mint 13 with refit in it. It works with 3.2 kernel (just the basic one - screen resolution is only 1024, Wifi works as well).

Now, anybody in this list knows how to remaster the ISO, just replace the default kernel with the latest kernel?

Here are some tools in remastering ubuntu and some links.

Ubuntu Live CD remastering tool
[https://github.com/fluxer/customizer](https://github.com/fluxer/customizer)

Remastersys
[http://www.remastersys.com/index.html](http://www.remastersys.com/index.html)

Some remaster blog and site.
[http://extonlinux.wordpress.com/2012/06/16/ubuntu-barebone-12-04-32bit-exton-remix-live-cd/](http://extonlinux.wordpress.com/2012/06/16/ubuntu-barebone-12-04-32bit-exton-remix-live-cd/)

[http://www.junauza.com/2012/05/how-to-create-custom-linux-live-cdusb.html](http://www.junauza.com/2012/05/how-to-create-custom-linux-live-cdusb.html)

[http://www.extix.se/](http://www.extix.se/)

UCK
[http://www.howtogeek.com/109736/how-to-create-a-custom-ubuntu-live-cd-or-usb/](http://www.howtogeek.com/109736/how-to-create-a-custom-ubuntu-live-cd-or-usb/)



UNetbootin works well with Mac OS X. I used it for my usb installer.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Anybody managed to run ubuntu in Macbookpro retina with 3.6-rc6 can easily create a remaster ubuntu with 3.6-rc6 kernel using these tools.

Anybody likes to have a go?

Thanks.

Edit 2:

Manually upgrading the kernel.
[http://www.linuxforums.org/forum/ubuntu-linux/168658-solved-manually-upgrading-kernel-live-iso-file.html](http://www.linuxforums.org/forum/ubuntu-linux/168658-solved-manually-upgrading-kernel-live-iso-file.html)

My problem I could not see any initrd.gz in 3.6-rc2 kernel (data.tar.bz2). vmlinuz is present.

Any ideas, I guess I have to get this initrd.gz in the installed (broken installation) in hard drive.

Update:

I managed to use the 3.6-rc6 kernel in my usb linux mint 13 installer using this manual kernel upgrade. However, the method works however, the result is the same as my usb 3.0 hard drive install (i.e. thread helper error).

I can say that this 3.6-rc6 ubuntu kernel is no good yet for Macbookpro retina 2.3 Ghz. It seems that 3.6-rc6 kernel has problem with the usb booting.

Anybody using ubuntu manage to run this kernel (i.e. 3.6-rc6) in their MBpro retina?

I replaced 3.6-rc6 (i.e. initrd.gz and vminuz) (not working) with the old 3.2 kernel and usb installer (usb live) is working again.

Anybody manage to create / use a usb ubuntu installer using 3.6-rc6 kernel? Which one did you use (e.g. 12.04 , etc.) ISO?

---

### Post by francxk on 2012-09-19
Hi,

I read most of the pages of this thread, and i m a bit confused.

I try to summarize what i do:
[LIST]
[*]install kubuntu 12.04
[*]switch to kernel 3.6rc6
[*] sudo apt-get upgrade
[/LIST]

What is OK:
[LIST]
[*]wifi
[*]ethernet
[/LIST]

But i got only black screen...
I try things about nvidia-current, compile nvidia...
but nothing works

is someone has a GUI working ?

Thx for help

**Update:**
I restart from scratch:
installation 12.04 and then to kernel 3.6rc6
And it s roughtly ok.

Just very little meno and windows

**Update:**
Confused again, do some adjustement xorgs conf (size of screen), and other things i can t remember ==> blank screen again

I think nvidia-current (295.xx) doesn't work. I investigate.

Fracnk

---

### Post by bfroemel on 2012-09-20
> I think nvidia-current (295.xx) doesn't work. I investigate.

If it has to be Nvidia, try the xedgers PPA -- the first nvidia version I tried has been 3xx.xx. (but I don't actually know if it shouldn't work already with 295.xx)

---

### Post by gschwind on 2012-09-21
For old nvidia driver you probably need :

Option         "UseDPLib" "off"

in xorg.conf in nvidia device section

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "UseDPLib" "off"
EndSection
```

---

### Post by catus on 2012-09-22
Could anyone tell me how to make the Thunderbolt to Ethernet adapter work?
I googled for it, but I can't find a tutorial or something... I don't even know whether it is supported by linux.

---

### Post by gw280 on 2012-09-22
> **catus said:**
> Could anyone tell me how to make the Thunderbolt to Ethernet adapter work?
I googled for it, but I can't find a tutorial or something... I don't even know whether it is supported by linux.
Boot up with it plugged in; it should just work. Thunderbolt hotplug doesn't work yet.

---

### Post by MikeBraxner on 2012-09-22
Has anyone managed to get Bumblebee to work with the NVidia 304.43 drivers? 

I keep getting 'Could not load GPU driver' or 'Unknown Chipset Nev7' errors.

It's probably just me (n00b and all), but I'd really like this to work in order to use the NVidia to watch movies (should require less power than the i915).

(PS: with 3.6.0-rc6 bluetooth works just fine.)

---

### Post by francxk on 2012-09-22
Hello,

I have roughly a mac on kubuntu.
but firefox, chromium are hard to use because, i can t adjust size of font everywhere. anynone knows a tutorial ?

All icon are very small too?

Other big problem, my macbook can never wakeup after hibernate .

Franck

---

### Post by MikeBraxner on 2012-09-22
For the fonts, have a look at System Settings -> Application Appearance -> Fonts -> Force DPI; Set to 115 works for me, with  Font sizes 9 and 8 throughout.

I don't use Firefox, but check Chromium -> settings -> show advanced settings -> Web Content, and try Font Size Medium, and Page Zoom 125%.

---

### Post by francxk on 2012-09-22
> **MikeBraxner said:**
> For the fonts, have a look at System Settings -> Application Appearance -> Fonts -> Force DPI; Set to 115 works for me, with  Font sizes 9 and 8 throughout.

need to set DPI to 200, but it s ok

> **MikeBraxner said:**
> 
I don't use Firefox, but check Chromium -> settings -> show advanced settings -> Web Content, and try Font Size Medium, and Page Zoom 125%.
Page zoom to 175, but address bar and tabs still very small

Any idea about resuming and hbernate (i use kernel 3.6rc6)

---

### Post by sauferkel on 2012-09-23
Hey guys,

did one of you erase OSX completely?

I did so, in order to get a dualboot with Win8 and Ubuntu, but without any success, at least so far.
The Win8 installer fails to install on EFI mode, but works on Bios.
For Ubuntu, the opposite holds. No success in bios, just in EFI (using noapic and nomodeset).
But then Grub doesn't start. (Missing operating System)

Is this a common experience, or does it just hold for me? 

Edit:
I re installed OSX now... so its fine for now. 
But if you know what my problem is/was, please let me know since I would really like to get rid of OSX....


Thanks!

---

### Post by MikeBraxner on 2012-09-23
For some grounding in what works (dual/triple boots), and what doesn't (Win on EFI), using EFI on Mac's, have a look at [Rod Smith's]("http://www.rodsbooks.com/ubuntu-efi/index.html") material, as well as rEFInd's documentation. 

Remove OS X completely, retaining rEFInd as Boot Manager: 
After re-partitioning so that a clean OS X landed at the end of the disk, I ran a _[fairly standard installation]("http://www.physik.uni-freiburg.de/~helger/retina.html")_, though paying special attention to  _[EFI Issues]("http://www.rodsbooks.com/ubuntu-efi/index.html")_. Pay particular attention to Rod's section on 'Fixing the Installation' and using the Super GRUB 2 Disk.

Once I had the graphics card working the way I wanted, and rEFInd was installed from Linux onto the EFI partition, OS X was culled. 

At this point, rEFInd started to act up a little, i.e. trying to boot would take ~30 sec before rEFInd's menu came up. To correct this, I removed all superfluous bootmanager entries, and re-installed rEFInd  ... **use at your own risk** ...

1) mount the ESP (adjust sdaX to your installation) 
sudo mount /dev/sdaX /boot/efi

2) get a list of all known bootmanager entries
sudo efibootmgr

3) Using the reported BootXXXX id's, remove ALL entries **EXCEPT rEFInd's** (probably Boot0000) one at a time, e.g. ...
sudo efibootmgr -b 0081 -B

4) when only rEFInd's entry is left, i.e. all others are gone, including any 'un-named' ones, re-install rEFInd AGAIN, using the install script ...
sudo ./install.sh

... no more start-up delays.

Finally, my home partition was extended to gobble up the extra 12G.

(If you want to remove an OS X at the beginning of the disk, you'll probably have to boot from an external drive/live USB stick and use gparted to shift/enlarge your other partitions so as to utilize the freed up space.) 

**NB:** Just make sure you still have a **working OS X, as well as the installer**, somewhere, e.g. on a bootable USB-stick/external drive, in case you need to lock the graphics card into integrated only, or in case you might want to sell your rMBP at some point with OS X installed.

---

### Post by nsicad on 2012-09-23
Anybody managed to create an Ubuntu USB stick installer?

I tried these 2 isos (below) using unetbootin.app

1. ubuntu-12.04.1-desktop-amd64.iso, I got kernel panic here. (I think this one is using 3.2 kernel).

2. quantal-desktop-amd64+mac.iso (nightly build - 22 Sept. 2010), I work but with garbage display. It is using 3.5 kernel

I manage to get an working installer with Linux Mint 13 iso (3.2 kernel) but I don't know how to get the kernel upgraded to 3.6rc6.

I need a "proper' initrd.lz (3.5rc6), anybody got a good initrd.lz (3.5rc6 kernel) that they can share that works with usb installer. The initrd.lz must be bigger than 5Mb (~ 15Mb).

I like know how anybody was able to create a working usb installer from ubuntu ISO, what did you do in your usb installer.

Please share some info about your usb installer.

Edit: 

Please note that my Macbookpro retina is just the basic one (i.e. 2.3 Ghz). Again, 12.04 (3.5 kernel) and Linux mint 13 upgraded to 3.5 kernel have problem with this machine (kernel panic, etc.).

However, quantal-desktop-amd64+mac.iso (nightly build - 22 Sept. 2010) which also 3.5 kernel (probably a higher RC) works but the graphics is garbage (i.e. very distorted display).


Thanks.

---

### Post by sauferkel on 2012-09-24
@nsicad:
 
The mac image was not working for me. But the normal 64bit daily builds of ubuntu were working. Just used noapic and nomodest as kernel parameters. 
 
I created the stick with the ubuntu startup disk creator.
 
Edit: Sorry, forgot to say, i'm on 2,7Ghz Cpu.

---

### Post by lolleepop on 2012-09-24
So, overall Ubuntu 12.04 is still rather unstable and not 'feature complete' on MBP retina? Like, if one's work absolutely depended on having a stable Linux environment, MBP retina would not be an option yet?

---

### Post by MikeBraxner on 2012-09-24
Can't speak for anyone else, but 12.04 runs stable and fine for me, and with 3.6.0-rc6 you won't even have to patch anything, or use kernel parameters to get a clean boot. 

About the USB-stick: 
I used _[abock-image-usb-stick]("https://github.com/abock/image-usb-stick/tarball/master")_ with the standard '+mac' image for Kubuntu --- worked just fine with kernel parameters (noapic nomodeset) for the install. (If you get the broadcom-wl-5.100.138 -> wl_apsta.o  beforehand, you even get the wireless to work during install.)

---

### Post by sauferkel on 2012-09-24
> **MikeBraxner said:**
> Can't speak for anyone else, but 12.04 runs stable and fine for me, and with 3.6.0-rc6 you won't even have to patch anything, or use kernel parameters to get a clean boot. 


Does this include the microphone now?

---

### Post by MikeBraxner on 2012-09-24
@sauferkel: "Does this include the microphone now?"

Haven't the foggiest, since I can't remember when I last used an internal mic for anything (although as far as I know, there is no patch for the mic yet). Anyway, my work does not "absolutely depended on having" an internal mic --- just a stable system, which 12.04 offers in my utterly irrelevant, and highly subjective opinion. 

Besides, I referred to a 'clean boot' in the sense that you don't have to jump through a dozen different hoops just to get the system up and running. The 3.6.0-rc6 has all the previously necessary patches included, so just download, compile, install, reboot ... and smile.

---

### Post by nsicad on 2012-09-25
> **MikeBraxner said:**
> Can't speak for anyone else, but 12.04 runs stable and fine for me, and with 3.6.0-rc6 you won't even have to patch anything, or use kernel parameters to get a clean boot. 

About the USB-stick: 
I used _[abock-image-usb-stick]("https://github.com/abock/image-usb-stick/tarball/master")_ with the standard '+mac' image for Kubuntu --- worked just fine with kernel parameters (noapic nomodeset) for the install. (If you get the broadcom-wl-5.100.138 -> wl_apsta.o  beforehand, you even get the wireless to work during install.)

"I used _[abock-image-usb-stick]("https://github.com/abock/image-usb-stick/tarball/master")_ with the standard '+mac' image for Kubuntu", What is the default kernel of this ISO? 3.6.0-rc6 kernel?

There is no point discussing that 12.04 works or not, if you don't inform us what is your Macbookpro retina CPU.

Again, 2.7 Ghz macbookpro retina works with most of these iso. However, 2.3 Ghz retina is not working with these ISO's.

PLEASE Let us your CPU next time you post in this forum. It will help other users use info, otherwise. It just waste of time and resource trying to download, burn, etc.

---

### Post by MikeBraxner on 2012-09-25
> **nsicad said:**
> 2.3 Ghz retina is not working with these ISO's.

Well now, I use the 2.3GHz version, and I have not had any problems with any of the standard ISO's.

For the installation, I only used *unaltered* images straight from the _[Kubuntu Release site](http://cdimage.ubuntu.com/kubuntu/releases/12.04/release)_, more specifically _[this one for Kubuntu](http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/kubuntu-12.04-desktop-amd64+mac.iso)_, while the _[Ubuntu site](http://cdimage.ubuntu.com/releases/12.04/release)_ offers its equivalent. Whichever you choose to use, make sure it is the '+mac' version, e.g. 'kubuntu-12.04-desktop-amd64*+mac*.iso' or its Ubuntu equivalent (which explains why your earlier posted first ISO try did not work), and remember to use 'noapic nomodeset' as kernel parameters for the install. 

For something approaching a straight forward install guide, may I suggest _[Helger's advice](http://www.physik.uni-freiburg.de/~helger/retina.html)_ (the part about 'Getting the native resolution to work and UEFI booting' will probably already resolve your display problems with the Quantal ISO), _[Rod's](http://www.rodsbooks.com/ubuntu-efi/index.html)_ excellent info UEFI on Macs and his rEFInd work, _[Berner's](http://cberner.com/2012/07/10/installing-ubuntu-12-04-on-macbook-pro-retina/)_ uncomplicated summary and the _[ArchLinux Wiki](https://wiki.archlinux.org/index.php/MacBook)_ for additional background, as well as of course the earlier posts in this forum, particularly with reference to locking in the integrated graphics card using _[Cody Krieger's gfxCardStatus](http://codykrieger.com/gfxCardStatus)_. Once you *have* a working system, get, compile and install 3.6.0-rc6 (or a newer version if available).

---

### Post by BlueDragonX on 2012-09-25
> **nsicad said:**
> Again, 2.7 Ghz macbookpro retina works with most of these iso. However, 2.3 Ghz retina is not working with these ISO's.

I've not seen any evidence to support this. I talked about this with Greg K-H and he hasn't seen anything to indicate there's any difference.

Case in point:

> **MikeBraxner said:**
> Well now, I use the 2.3GHz version, and I have not had any problems with any of the standard ISO's.

---

### Post by nsicad on 2012-09-25
> **BlueDragonX said:**
> I've not seen any evidence to support this. I talked about this with Greg K-H and he hasn't seen anything to indicate there's any difference.

Case in point:

I totally disagree that the macboopro retina are exactly the same hardware configuration even the same Ghz (e.g. 2.3 Ghz). For example, mine comes with SAMSUNG retina display and other comes with LG retina display.

Samsung retina display does not suffer "ghosting effect" as some of the LG retina does.

For whatever reason, most of the ubuntu iSO I could not make working and I am not alone. 

 [http://philatwarrimoo.blogspot.com.au/2012/06/unubtu-1204-on-macbook-pro-91-non.html](http://philatwarrimoo.blogspot.com.au/2012/06/unubtu-1204-on-macbook-pro-91-non.html)

I got the same result with Phil (only Linux mint 13 is working). It is ubuntu but package differently.

I tried installing the linux mint 13 in usb stick and upgrade to 3.6-rc6 quantal kernel and I got the same result as upgrading usb hard drive to 3.6-rc6 quantal - kernel helper error.

Edit: 

Reading the  **MikeBraxner **posting above, it seems that we missed the "+mac" version of the ISO. I think this key element in ubuntu iso's, it has specific support for Mac machines. Coming from the PC laptops in most of my porting / hacking experience (e.g. triple booting (Windows, Linux and Mac OS X)), I thought that ubuntu has generic support for Laptop and Macs.

Thanks.

---

### Post by nsicad on 2012-09-26
> **MikeBraxner said:**
> Well now, I use the 2.3GHz version, and I have not had any problems with any of the standard ISO's.

For the installation, I only used *unaltered* images straight from the _[Kubuntu Release site]("http://cdimage.ubuntu.com/kubuntu/releases/12.04/release")_, more specifically _[this one for Kubuntu]("http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/kubuntu-12.04-desktop-amd64+mac.iso")_, while the _[Ubuntu site]("http://cdimage.ubuntu.com/releases/12.04/release")_ offers its equivalent. Whichever you choose to use, make sure it is the '+mac' version, e.g. 'kubuntu-12.04-desktop-amd64*+mac*.iso' or its Ubuntu equivalent (which explains why your earlier posted first ISO try did not work), and remember to use 'noapic nomodeset' as kernel parameters for the install. 


Thanks for posting this info.

Now, I know that we have to use '+mac'.iso's inorder to be able to boot properly with macbookpro.

I will try downloading this '+mac".iso and create usb installer.

Thanks again.

Edit:

However, if you read the ubuntu download for iso (below). You most likely to download the PC iso for intel chip set for Macbookpro.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Update:

It seems that even "+mac".iso got the same unuseable display (see the entry at the very end of this post).

[http://apple.stackexchange.com/questions/64014/has-anyone-tried-putting-ubuntu-on-the-new-retina-macbook-pro](http://apple.stackexchange.com/questions/64014/has-anyone-tried-putting-ubuntu-on-the-new-retina-macbook-pro)

Update 2:

I managed to install 12.10 night build but updating to 3.6-rc7 and 3.6 night build, AMD (i.e. mac) version. However, the keyboard is not working with this updates. This is ubuntu install is using external usb 3.0 hard drive. The default kernel (3.5) works in this install (usb external drive) but no nvidia and apple gmux yet. I refer linut mint 13 (classical UI) than Unity.

This is the problem with 3.6 kernels (i.e. HDIO get identity failed for dev/sdb invalid argument) installing in usb hard drive. 

[http://askubuntu.com/questions/191862/hdio-get-identity-failed-for-dev-sdb-invalid-argument](http://askubuntu.com/questions/191862/hdio-get-identity-failed-for-dev-sdb-invalid-argument)

  /dev/sdb to /dev/sdc problem

[http://serverfault.com/questions/34895/usb-drive-changes-name-from-dev-sdb-to-dev-sdc-and-back-again-when-copying](http://serverfault.com/questions/34895/usb-drive-changes-name-from-dev-sdb-to-dev-sdc-and-back-again-when-copying)

[http://ask.fedoraproject.org/question/427/usb-devsdb-renamed-devsdc-after-suspend](http://ask.fedoraproject.org/question/427/usb-devsdb-renamed-devsdc-after-suspend)

Update 3. 

Linux kernel 3.6-rc7

I tried updating 12.10 nightly build (22 September) and linux mint 13 with 3.6-rc7 kernel. I got the same problem attributed to Apple Bluetooth. It hangs and the power to usb drive stop as well. It is not booting.

Linux kernel 3.6 is released today by Linux. It has 2 bluetooth fixes and 1 usb fix as well. Hopeful these fixes solve this problem mentioned above.

Will try 3.6 ubuntu kernel when available.

Anybody managed to boot 3.6-rc7 ubuntu kernel with their Macbookpro? And what is the CPU?

Update 4.

Turning bluetooth ON in Mac OS X (with Intel graphic (integrate only)) before rebooting with usb 3.0 hard drive installation (updated to 3.6-rc7) boots to get the log screen. However, keyboard is not working (i.e. you can use the keyboard to login in). In 3.5 the keyboard is working.

Linux 3.6 kernel ubuntu is not avaiable. Time to install and test
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-quantal/)

The keyboard still the problem in 3.6 kernel. Keyboard backlit is ON but the keyboard is unusable.

3.5 kernel is still the best for retina. It needs just to be patched to get it fully working with ubuntu.

Waiting for 3.6 kernel ubuntu ISO.

---

### Post by MikeBraxner on 2012-09-27
I ran into a stability issue with Oracle's closed version of VirtualBox 4.2.

Since the install, there is a distinct interference between my display (i915 only) and the wireless. Wireless connections are constantly dropped, or peer-reset, while the screen goes *haywire*, presenting distortions akin to video-tearing. The higher the up-/download rate, the worse the distortions. 

Installing Win 7 (32 bit) or XP as guests works, but re-sizing the guest-window breaks the Guest installation (black guest window, appears irrecoverable). 

Switching over to discreet-card-only + NVidia-current resolves the display issue, and allows the guest-window to be freely re-sized, but the wireless remains somewhat unstable. Reverting to VirtualBox 4.1 does not appear to help either.

After a couple kernel panics on booting the host, I finally purged VirtualBox. The funny bit is that, since the first VirtualBox install, KDE reports a crashed program on start-up, with the illustrious declaration that I'm "not allowed" to receive further information about it --- go figure.

Has anyone else had better luck getting VirtualBox to work on an rMBP.

PS: It seems the crash is caused by bluedevil, which ran just fine before the VirtualBox install.

---

### Post by nsicad on 2012-10-03
**      [SIZE=2][Macbook Pro 10,1] eDP panel corruption with nouveau[/SIZE]**

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1058088](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1058088)

This bug might not be fixed in 3.6.0 kernel earlier release but hopefully fixed in the new ones.

---

### Post by nsicad on 2012-10-19
Ubuntu 12.10 with 3.5.3 kernel. Is good for retina?

[http://www.kernel.org/pub/linux/kernel/v3.0/ChangeLog-3.5.3](http://www.kernel.org/pub/linux/kernel/v3.0/ChangeLog-3.5.3)

Does this release boots well with MacbookPro retina?

Edit. 

It seems that it is 3.5.4 kernel, not 3.5.3.

I hope nvidia card works by default.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/1061667](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/1061667)

---

### Post by raccoonone on 2012-10-19
Yep, it works great, and has quite a bit better support than 12.04 did.

I'm still having trouble with the brightness control and the wifi is flaky sometimes, but overall it's way better.

I just wrote a [blog post about my experience installing 12.10]("http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/"). Hope it's helpful to you!

---

### Post by nsicad on 2012-10-19
> **raccoonone said:**
> Yep, it works great, and has quite a bit better support than 12.04 did.

I'm still having trouble with the brightness control and the wifi is flaky sometimes, but overall it's way better.

I just wrote a [blog post about my experience installing 12.10]("http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/"). Hope it's helpful to you!


Could you elaborate more about it? For example, nvidia card, resolution, etc.

---

### Post by raccoonone on 2012-10-19
Sure, the nvidia drivers work as long as you switch to EFI booting, and native resolution worked fine too.

Brightness and wifi were the only issues I ran into. Oh, and compiz crashed now and then.

---

### Post by MikeBraxner on 2012-10-21
I used to have some problems with the brightness controls, but found a simple enough way to overcome them (at least in KDE).

The main problem lay in the system using the wrong interface to adjust the backlight brightness. Additionally, when using the NVidia proprietary drivers, apple-gmux.c (quite properly) unregisters all backlight interfaces other than the gmux interface, except that the system does not appropriately re-adjusts the interface *it* uses. 

Keeping apple-gmux.c from un-registering the acpi_videoX interfaces can be done by simply commenting out the according instructions. The patch below should apply cleanly  to 3.5.x and 3.6.x kernels. (Otherwise just do it by hand.)

```
--- a/drivers/platform/x86/apple-gmux.c	2012-09-30 19:47:46.000000000 -0400
+++ b/drivers/platform/x86/apple-gmux.c	2012-10-11 09:02:32.100752458 -0400
@@ -511,8 +511,8 @@
 	 * Disable the other backlight choices.
 	 */
 	acpi_video_dmi_promote_vendor();
-	acpi_video_unregister();
-	apple_bl_unregister();
+	//acpi_video_unregister();
+	//apple_bl_unregister();
 
 	gmux_data->power_state = VGA_SWITCHEROO_ON;
```

Once recompiled and running, /sys/class/backlight will contain the two additional interfaces apci_video0 and acpi_video1. On the other hand, if your using the i915, then the system uses the intel_backlight interface. 

Either way, synchronizing changes from the DE used interface to the gmux one, can now be done using **inotify** via a simple script, which works equally well, regardless of which drivers your using.

```
#!/bin/bash
# 
# references: 2012/10/11, KDE 4.8.5, Kernel 3.6.0, NVidia drivers 304.51
#   requires: inotify-tools 
#             patched apple-gmux.c for use with NVidia drivers
# 
# On a MacbookPro 10,1 KDE has trouble adjusting the screen backlight, 
# automatically (timed dimming/power-state changes) as well as manually.
# 
# This results from a bug in KDE Powermanagement Tools, 
# (https://bugs.kde.org/show_bug.cgi?id=296403) which apparently 
# do not properly update which backlight interface to use.
# 
# This script synchronises backlight adjustments/changes to 
# /sys/class/backlight/gmux_backlight.
#
# NB: If i915 is used, no alterations are necessary.
#     If the proprietary NVidia drivers are to be used, apple-gmux.c needs
#     to be patched to stop it from disabling the acpi_videoX interfaces.
#     

# KDE adjusts either via intel_backlight or acpi_videoX,
# depending on which GPU and which driver is used
if [ -f /sys/class/backlight/intel_backlight/max_brightness ]; then
    # for i915 use intel_backlight
    ACPI_DIR=/sys/class/backlight/intel_backlight
fi
if [ -f /sys/class/backlight/acpi_video1/max_brightness ]; then
    # if NVidia drivers are used, and apple-gmux.c has been patched, use 
    # acpi_video0 or acpi_video1 ... whichever works
    ACPI_DIR=/sys/class/backlight/acpi_video1
fi

# gmux uses a different range of backlight adjustment, so we scale ...
ACPI_MAX_BRIGHTNESS=`cat ${ACPI_DIR}/max_brightness`
GMUX_MAX_BRIGHTNESS=`cat /sys/class/backlight/gmux_backlight/max_brightness`
MULTIPLIER=$(echo "scale=5;${GMUX_MAX_BRIGHTNESS}/(${ACPI_MAX_BRIGHTNESS}+1)"|bc)

# trigger minimum/maximum screen illumination if we're close enough,
# i.e. no 2% or 99% brightness ... it's just cleaner this way
MIN_BACKLIGHT_FACTOR=.05
FULL_BACKLIGHT_FACTOR=.95
GMUX_TRIGGER_MIN=$(echo "(${MIN_BACKLIGHT_FACTOR}*${GMUX_MAX_BRIGHTNESS})/1"|bc)
ACPI_TRIGGER_FULL=$(echo "(${FULL_BACKLIGHT_FACTOR}*${ACPI_MAX_BRIGHTNESS})/1"|bc)

# now sync all changes to gmux in scale 
# with cut-offs specified by min/full triggers
while inotifywait -e modify ${ACPI_DIR}/brightness >/dev/null 2>&1; do
    ACPI_BRIGHTNESS=`cat ${ACPI_DIR}/brightness`
    GMUX_BRIGHTNESS=$(echo "(${MULTIPLIER}*${ACPI_BRIGHTNESS})/1"|bc)
    if [ ${ACPI_BRIGHTNESS} -ge ${ACPI_TRIGGER_FULL} ]; then
	GMUX_BRIGHTNESS=$GMUX_MAX_BRIGHTNESS
    fi
    if [ ${GMUX_BRIGHTNESS} -le ${GMUX_TRIGGER_MIN} ]; then
        GMUX_BRIGHTNESS=0
    fi
    echo ${GMUX_BRIGHTNESS} > /sys/class/backlight/gmux_backlight/brightness
done
```

Just start the script from /etc/rc.local, and backlight adjustment should work just fine, with one exception. On my system (12.04) the brightness will not adjust under NVidia drivers after a boot, but works just peachy after a suspend.

---

### Post by gw280 on 2012-10-21
Looks like Linux 3.7 has support for the microphone now:

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=ef596a57b4d7d8b258beb570ed309ef85bf24dd1](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=ef596a57b4d7d8b258beb570ed309ef85bf24dd1)

---

### Post by f1ier on 2012-10-24
I got 12.10 running on the MacBook Pro Retina (10,1) wrote an extensive tutorial ;) Hope it helps.

[http://www.warp1337.com/content/install-ubuntu-1210-quantal-quetzal-macbook-pro-101-retina-solved](http://www.warp1337.com/content/install-ubuntu-1210-quantal-quetzal-macbook-pro-101-retina-solved)

Cheers,
fl0

---

### Post by plech.d on 2012-10-29
My brightness buttons work properly after wake up, not after boot. Solution working for me right now: After boot, put the computer to sleep and wake it up again.

Didn't need to do any kernel recompiling, which, it seems, leaded to the same result anyway.

Oh and if any of you are having trouble booting up after the second restart of your computer after installing the nvidia drivers, I found the following: After you install the drivers and reboot, notice that your xorg.conf timestamp has changed. Nvidia performs some changes after boot that mess everything up. To prevent this:

1) Install nvidia drivers as described by cberner.
2) Reboot.
3) Run ```
sudo nvidia-xconfig
``` again.
4) Reboot as many times as you wish now without trouble.

---

### Post by raccoonone on 2012-10-30
> **plech.d said:**
> My brightness buttons work properly after wake up, not after boot. Solution working for me right now: After boot, put the computer to sleep and wake it up again.

Didn't need to do any kernel recompiling, which, it seems, leaded to the same result anyway.

Oh and if any of you are having trouble booting up after the second restart of your computer after installing the nvidia drivers, I found the following: After you install the drivers and reboot, notice that your xorg.conf timestamp has changed. Nvidia performs some changes after boot that mess everything up. To prevent this:

1) Install nvidia drivers as described by cberner.
2) Reboot.
3) Run ```
sudo nvidia-xconfig
``` again.
4) Reboot as many times as you wish now without trouble.

Just had the same problem you described when I went back to test some new things on my retina. Running nvidia-xconfig a second time didn't help though. Did you make any other changes after you followed my guide?

---

### Post by plech.d on 2012-10-30
> **raccoonone said:**
> Just had the same problem you described when I went back to test some new things on my retina. Running nvidia-xconfig a second time didn't help though. Did you make any other changes after you followed my guide?

I don't believe I did. This is my experience:

I installed Ubuntu quite a few times, following your guide. I always ran into this problem and didn't know why. The only time I didn't run into it was when I upgraded to 3.6 rc6 BEFORE installing the nvidia drivers and efi grub. But then, my webcam wasn't working and Skype was making peculiar noises when playing sound notifications.

The final install went as follows:
1) Followed your guide exactly, didn't upgrade the kernel.
2) After I ran nvidia-xconfig, I checked that an xorg.conf file was created, and checked its timestamp.
3) Rebooted according to your guide.
4) Checked the timestamp of xorg.conf - it has changed. This brought me to believe that perhaps that is why on the following boot, nothing would pop up.
5) Ran nvidia-xconfig again, rebooted.
6) Boot ok. Checked timestamp again, it stayed the same now and hasn't changed again with subsequent boots.

I cannot say what had been changed in the xorg.conf file after the first boot, because I didn't look. I don't want to reinstall again to find out, I'm glad I'm up and running :] Everything works well now except for the internal microphone.

I do, however, wish to note the following two aspects:
- I have a USB WiFi adapter and used it to download updates while installing Ubuntu and I installed the updates before I ever installed efi grub or nvidia drivers.
- This working installation is the first time that I decided to directly choose /dev/sda for the boot loader installation during Ubuntu setup. Before I always chose my / partition, because that's what all previous general Ubuntu Mac install guides told me to do.

---

### Post by magnumripper on 2012-10-30
> **raccoonone said:**
> Just had the same problem you described when I went back to test some new things on my retina. Running nvidia-xconfig a second time didn't help though. Did you make any other changes after you followed my guide?

I too just ran into this. I had booted the Ubuntu partition numerous times with no problems. Last night I installed some Ubuntu updates before powering off and since then, I get no X. Running nvidia-xconfig did not help. I could look into the X logs and stuff but the console text is so dang small so I'm hoping someone else beat me to it :P
[I]
**EDIT**: Found the problem. Probably not the same as yours. I did not have kernel-headers installed so my new kernel did not get DKMS modules built for nvidia.[/I]

---

### Post by lukeco11 on 2012-11-06
I just came across this update and lose NVIDIA drivers problem. It wasn't after the initial install, it was up and working for a while. Just did a regular update and now I boot to command prompt. X won't start (no screens found) and nvidia-xconfig doesn't change anything. Magnumripper, can you detail how you solved this?

Thanks!

---

### Post by magnumripper on 2012-11-06
> **lukeco11 said:**
> I just came across this update and lose NVIDIA drivers problem. It wasn't after the initial install, it was up and working for a while. Just did a regular update and now I boot to command prompt. X won't start (no screens found) and nvidia-xconfig doesn't change anything. Magnumripper, can you detail how you solved this?

If you choose the older kernel in GRUB it will likely work fine, so you get a decent screen to fix it. I did not realize that until after fixing the problem using the almost unreadable little font in the console. Chin right above the keyboard :)

From memory, during re-installation of the nvidia driver (any version) I got a DKMS error hinting about the problem. I think I had to install kernel-source despite the fact kernel-headers should be enough. Then re-install the nvidia driver, so it builds the DKMS modules. If it says it did not successfully build the DKMS modules, you need something more. Installing kernel-package and all its recommends may be a short-cut to success in case you get stuck.

---

### Post by faronium on 2012-11-09
Can we extend this to the rMBP 13" model? I would guess that it's a little bit simpler case than the 15" given the Intel-only graphics. I'm hemming and hawing between a 13 retina and the MBA with the main issue being the ability to have a happy linux experience on the retina. I'm not knowledgeable enough to be a pioneer on this but if anyone else has done the pioneering, I'd love to hear it.

---

### Post by frigaut on 2012-11-12
Good news !
There's a new patch from Daniel Blueman/Alexander Stein/Takashi Iwai ([https://lkml.org/lkml/2012/11/4/11](https://lkml.org/lkml/2012/11/4/11)) that solves the microphone issue. It's apparently made it in 3.7-rc5, which I am currently running.
add:
options snd-hda-intel model=mbp101
in /etc/modprobe.d/alsa-base.conf
I have not seen regression in audio associated to this patch.

---

### Post by lukeco11 on 2012-11-18
Loving 12.10 on Retina Macbook Pro, but every time I put it down on a table the WiFi connection dies. If it sits in my lap, then it seems to work fine. Am I alone in this? Anyone have an idea on how to make the WiFi more stable?

---

### Post by maag3377 on 2012-11-19
Hi

I have a problem using my second screen. When I boot with the second screen plugged in, the second screen is active and the laptop screen is off. The internal screen is eDP-1 and xrandr reports:

> 
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 8192 x 8192
eDP-1 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1920x1080      50.0     60.0  
   1600x1200      60.0  
   1680x1050      59.9  
   1680x945       60.0  
   1400x1050      59.9  
   1600x900       60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0  
   1280x800       59.9  
   1280x768       60.0  
   1280x720       50.0     60.0  
   1024x768       60.0  
   1024x576       60.0  
   800x600        60.3     56.2  
   720x576        50.0  
   848x480        60.0  
   720x480        59.9  
   640x480        60.0  
HDMI-1 disconnected (normal left inverted right x axis y axis)


I'm running 3.7-rc5.

Any ideas?

Cheers,

Magnus

---

### Post by avehoudini on 2012-11-19
When I followed [this guide]("http://cberner.com/2012/10/") I thought that the problem with resolution was solved. Icons and text are so small that it’s hard to see what’s there. Or this problem is solved? May be I’m doing something wrong?

---

### Post by raccoonone on 2012-11-19
> **avehoudini said:**
> When I followed [this guide]("http://cberner.com/2012/10/") I thought that the problem with resolution was solved. Icons and text are so small that it’s hard to see what’s there. Or this problem is solved? May be I’m doing something wrong?

I'm pretty sure that's how it's going to be, if you run it at native resolution. Ubuntu doesn't support UI scaling like OSX does. So if you want the fonts to be larger you'll probably want to just run the screen at a lower resolution.

---

### Post by plech.d on 2012-11-21
> **avehoudini said:**
> When I followed [this guide]("http://cberner.com/2012/10/") I thought that the problem with resolution was solved. Icons and text are so small that it&#8217;s hard to see what&#8217;s there. Or this problem is solved? May be I&#8217;m doing something wrong?

Install gnome-tweak-tool. There, set the font scaling to 1.5. Sometimes I had to log out and back in afterwards for the change to take effect completely. Icons will stay small, Chrome tabs will be tiny, but the text will be perfectly readable. Also, in Chrome, go to Settings, Advanced Settings, and set scaling to 150%.

The main reason I installed Ubuntu on my rMBP 15" was for the extra screen estate. I don't want to go years behind and effectively have a resolution of 1440x900 on my 15" screen. I know I can kick up OS X to look like 1920x1200, but the UI lag then is horrible. I'm kind of angry with myself to have bought this computer, because I'm stuck with either 1440, or a very laggy 1920, which is not so great considering the cost of the laptop, and its proposed performance. Installing Ubuntu makes me a little happier, but it still doesn't adapt all that well to the resolution and not everything works.

---

### Post by lukeco11 on 2012-11-21
I've found a couple of things help with the resolution situation:

[LIST]
[*]Gnome-Shell over Unity - The Panels scale with the text, so not everything looks small (or bad). You can also edit the theme to use bigger icons in the dock, making everything much more manageable than Unity even when cranked up to the largest icons.
[*]Firefox over Chrome - I prefer Chrome normally, but in both Firefox and Thunderbird you can goto about:config  or advanced settings and set layout.css.devPixelsPerPx to a greater value, I have it set at 1.9. This eliminates zooming, and basically Firefox functions with normal tabs sizes and everything works pretty well. Sometimes some UI elements are small, but most of the time it acts as if it was on a non-retina display, just crisper.
[*]Text Scaling - As mentioned this helps, I have mine set on 1.7, up to you for what you like.
[/LIST]
What I haven't figured out how to change:

[LIST]
[*]Icons in Weird Places - For instance Gwibber and Nautilus both have icons/UI elements that are tiny compared to the text, makes using them either annoying or not worth it.
[*]Docky Text- I use Docky, but the mouse over text that appears is super small, still can't figured out if this can be changed.
[*]Flaky WIFI - The only thing holding me back from using Ubuntu full time on this computer is the flaky WiFi. If it is in my lap it is fine, if I put it down or closer to the router it gets really slow and disconnects, whereas OSX has no problem. I believe it is generally slower than OSX too, but that is just my feeling and I haven't tested.
[/LIST]

---

### Post by avehoudini on 2012-11-22
> **raccoonone said:**
> I'm pretty sure that's how it's going to be, if you run it at native resolution. Ubuntu doesn't support UI scaling like OSX does. So if you want the fonts to be larger you'll probably want to just run the screen at a lower resolution.

I could not make the screen resolution lower. There is always 2880x1800 and I can't change it. Could you please explain how to do it, if there is such opportunity? Thank you.

I really need Ubuntu for my embedded projects. I knew about this problem with resolution before buying this laptop, but I thought that it's easy to change the resolution.

**plech.d**, **lukeco11**, thank you guys for help. I'll try this at home :)

---

### Post by raccoonone on 2012-11-22
> **avehoudini said:**
> I could not make the screen resolution lower. There is always 2880x1800 and I can't change it. Could you please explain how to do it, if there is such opportunity? Thank you.

I really need Ubuntu for my embedded projects. I knew about this problem with resolution before buying this laptop, but I thought that it's easy to change the resolution.

**plech.d**, **lukeco11**, thank you guys for help. I'll try this at home :)

I haven't tried doing it myself, but this guide looks like it has directions for using 'cvt' to add new modelines: [https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf_--_resolution_lower_than_expected](https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf_--_resolution_lower_than_expected)

Alternately, if you just install Ubuntu without following the steps for EFI, then it should force you into a lower resolution.

---

### Post by sandy_ptc on 2012-11-22
** it is not working for me. Try opening [www.islamichouse.com](www.islamichouse.com). I can not read anything. **

---

### Post by plech.d on 2012-11-23
> **frigaut said:**
> Good news !
There's a new patch from Daniel Blueman/Alexander Stein/Takashi Iwai ([https://lkml.org/lkml/2012/11/4/11](https://lkml.org/lkml/2012/11/4/11)) that solves the microphone issue. It's apparently made it in 3.7-rc5, which I am currently running.
add:
options snd-hda-intel model=mbp101
in /etc/modprobe.d/alsa-base.conf
I have not seen regression in audio associated to this patch.

Hi, could you hint on how you installed the graphics on 3.7rc5?

I tried the following: Installed Ubuntu. Installed all updates. Installed rc6. Reboot. Installed grub efi. Installed nvidia-current. Run nvidia-xconfig. Reboot. I can't get past the console login. With nomodeset, I get directly to the console login. Without, I get the low graphics mode warning. 

Thanks for the information. 

Apart from that, without nvidia drivers, I can confirm that the microphone works.

---

### Post by magnumripper on 2012-11-23
> **plech.d said:**
> I tried the following: Installed Ubuntu. Installed all updates. Installed rc6. Reboot. Installed grub efi. Installed nvidia-current. Run nvidia-xconfig. Reboot. I can't get past the console login.

This should give you a good hint on what is happening:
dmesg | grep -Ei 'nvidia|nvrm'

When you installed nvidia-updates, did you see it successfully build DKMS modules? If not, purge nvidia-updates and then install it again and confirm it could build the modules.

---

### Post by magnumripper on 2012-11-23
> **lukeco11 said:**
> I've found a couple of things help with the resolution situation:

[LIST]
[*]Gnome-Shell over Unity - The Panels scale with the text, so not everything looks small (or bad). You can also edit the theme to use bigger icons in the dock, making everything much more manageable than Unity even when cranked up to the largest icons.
[*]Firefox over Chrome - I prefer Chrome normally, but in both Firefox and Thunderbird you can goto about:config  or advanced settings and set layout.css.devPixelsPerPx to a greater value, I have it set at 1.9. This eliminates zooming, and basically Firefox functions with normal tabs sizes and everything works pretty well. Sometimes some UI elements are small, but most of the time it acts as if it was on a non-retina display, just crisper.
[*]Text Scaling - As mentioned this helps, I have mine set on 1.7, up to you for what you like.
[/LIST]


Man, that layout.css.devPixelsPerPx fix was a good advice! Both Firefox and Thunderbird are excellent now. Thanks!

My biggest problem now is the silly trackpad. I'm used to Lenovo's trackpoint (which is excellent). Trackpads are a genuinly stupid idea. But in OSX I have much less problems with it so it can probably be tweaked.

---

### Post by plech.d on 2012-11-24
> **magnumripper said:**
> This should give you a good hint on what is happening:
dmesg | grep -Ei 'nvidia|nvrm'

When you installed nvidia-updates, did you see it successfully build DKMS modules? If not, purge nvidia-updates and then install it again and confirm it could build the modules.

Thanks for your help. The DKMS do build, but I did not install nvidia-updates, only nvidia-current, could that be the problem? On the other hand, I also tried the latest driver downloaded directly from nvidia, and it had the same issue. 

I'd like to try again, but this site isn't working today:
[http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline)
Would anyone be so kind as to upload the 3.7 debs somewhere for me? Thanks a lot in advance.

---

### Post by md78245 on 2012-11-25
I have a 13" macbook pro retina.... the audio hardware is not showing up... can someone help.... i'm new the ubuntu

---

### Post by plech.d on 2012-11-27
> **magnumripper said:**
> This should give you a good hint on what is happening:
dmesg | grep -Ei 'nvidia|nvrm'

When you installed nvidia-updates, did you see it successfully build DKMS modules? If not, purge nvidia-updates and then install it again and confirm it could build the modules.

Ok, now I'm really confused.

I tried a new installation, this time installing nvidia-current-updates on the 3.7rc5 kernel. I did have the kernel headers for 3.7rc5 installed. I get this message while installing nvidia-current-updates:

ERROR (dkms apport): kernel package linux-headers-3.7.0-030700rc5-generic is not supported
Error! Bad return status for module build on kernel: 3.7.0-030700rc5-generic (x86_64)

How is it possible that you have this up and running?
Thanks for your answer.

---

### Post by plech.d on 2012-11-28
> **plech.d said:**
> Ok, now I'm really confused.

I tried a new installation, this time installing nvidia-current-updates on the 3.7rc5 kernel. I did have the kernel headers for 3.7rc5 installed. I get this message while installing nvidia-current-updates:

ERROR (dkms apport): kernel package linux-headers-3.7.0-030700rc5-generic is not supported
Error! Bad return status for module build on kernel: 3.7.0-030700rc5-generic (x86_64)

How is it possible that you have this up and running?
Thanks for your answer.

Ok, I managed to install nvidia on 3.7 rc5 by going for the xedgers ppa and installing the 310 version of nvidia-current from there. That builds the dkms module properly. But it still doesn't boot. I would appreciate a step by step walkthrough from someone who has this kernel with nvidia drivers up and running.

Thank you very much in advance.

---

### Post by MikeBraxner on 2012-12-05
> **plech.d said:**
>  ... it still doesn't boot. 

Did you lock the graphics card into the right state before trying to boot up using the NVidia driver? Remember, the driver can't switch automatically to the dedicated GPU (see _[vga_switcheroo, Bumblebee)](https://help.ubuntu.com/community/HybridGraphics)_, so you'd have to force the right GPU into use via _[Cody Krieger's gfxCardStatus](http://codykrieger.com/gfxCardStatus)_.

---

### Post by FOXH0UND on 2013-01-01
How are people finding this? About to pull the trigger on a 13".

---

### Post by lukeco11 on 2013-01-07
I can only speak to the 15", but it is running pretty well with the exception of the Wifi. The Wifi is a mess and it keeps me from using it full time. It will work for a while fine, then drop out, reconnect, then work, drop out, etc. It just isn't consistant enough to use when you really need it.

---

### Post by MikeBraxner on 2013-01-09
VERY personal opinion ... 
Nice form-factor, OK weight, couple of irks ... BUT the graphics system is woefully under-powered.

I got the MBPr to use for coding, and for that, it's OK. Two main advantages are the higher resolution (allowing for smaller, yet still clear fonts), and the 'non-wide-screen' display dimensions, which gives more vertical space. 

However, everything requiring good graphics performance hits the same problem ... the NVidia card is just not up to the job, and it doesn't matter which OS you'll use. With a change of GPU (next gen.??) the situation might relax, but until then you'll either have to accept that even simple desktop effects remain bumpy, and video performance can be annoyingly degraded, or step down the resolution, which is essentially what OSX does --- but then why buy a MBPr.

So, if you're desperate for screen real estate that is non-wide-screen (and are willing to pay the price) the MBPr is all right. Otherwise, I would strongly suggest to take another look at, say, the 2nd gen Asus ZenBook.

---

### Post by bfroemel on 2013-01-10
> **lukeco11 said:**
> I can only speak to the 15", but it is running pretty well with the exception of the Wifi.
Strangely enough, wifi works with
kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc2-raring/
well enough for me. After suspend/resume a 'iwlist scan' and at the worst a 'rmmod b43/modprobe b43/iwlist scan' does the trick.

I didn't investigate yet, but the default kernel options may play a role: e.g., initially, I started from the kernel config of the 12.04 Ubuntu kernel and just used the defaults for any of the numerous newly introduced config options in the more recent linux kernel versions. That lead to very flaky wifi and even USB wifi sticks didn't work as reliable as on any other Linux box I tested them.

---

### Post by nsicad on 2013-01-10
Hi,

Has anybody tried 13.04 installing in external drive?

This guy (linked below) seems to installed it in external drive but the instruction is not so clear.  
**Ubuntu 13.04 Daily Build Macbook Pro Retina documentation and install guide**

[http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html](http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html)

Anybody would like have a go with instruction and post a clearer one?

For example this statement:

    " Now for the actual guide.  Hopefully it is easy enough that people who  are newer to linux can follow it.  The iso image for the daily build can  be grabbed here:

              (This guide assumes GUID/GPT drives, as MBR drives do not have EFI partitions.)

               /dev/sdXY means /dev/sd<Drive_Letter><Partition_Number> "

What he is talking about?

---

### Post by nsicad on 2013-01-10
> **bfroemel said:**
> Strangely enough, wifi works with
kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc2-raring/
well enough for me. After suspend/resume a 'iwlist scan' and at the worst a 'rmmod b43/modprobe b43/iwlist scan' does the trick.

I didn't investigate yet, but the default kernel options may play a role: e.g., initially, I started from the kernel config of the 12.04 Ubuntu kernel and just used the defaults for any of the numerous newly introduced config options in the more recent linux kernel versions. That lead to very flaky wifi and even USB wifi sticks didn't work as reliable as on any other Linux box I tested them.

Ubuntu 13.04, 3.8 kernel supports Macbookpro retina now as well, I suppose. 3.8-rc3 is just released as well.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc3-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc3-raring/)

**[Ubuntu 13.04 Daily Build Macbook Pro Retina documentation and install guide]("http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html")**

[http://linuxmacbookproretina.blogspot.com.au/](http://linuxmacbookproretina.blogspot.com.au/)

The instruction above is not clear. However, it is a lead that 13.04 works now for Apple Macbookpro retina 15 the base unti.

---

### Post by freeaks on 2013-01-12
i have trouble figuring how to use the intel integrated chip on my retina 15"..
right now i'm using ubuntu 13.04 raring (dev), kernel 3.8.0-0-generic
and lspci which used to show me before my two gfx chip does only list the nvidia one atm:

```

[ freeaks@kanzume ]$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:01.2 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fd5 (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0e1b (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation Device 16a3 (rev 10)
03:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
04:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
[ freeaks@kanzume ]$

```i tryed all kind of kernel option through grub, nothing worked so far.
all i get is the nouveau driver.
how can i get to use my intel chip ? nouveau is working fine btw, 
but i want to reduce heat and energy consumption.

---

### Post by Garlandg on 2013-01-15
I wrote the guide linked above by nsicad, and, yeah, it needs some cleaning up.  in the meantime, go ahead and ask about the unclear parts and I'll try to help you through it.

Suggestions for making it less confusing are also welcome.

I also updated a couple sections in an attempt to make them clearer.

---

### Post by freeaks on 2013-01-16
> **Garlandg said:**
> I wrote the guide linked above by nsicad, and, yeah, it needs some cleaning up.  in the meantime, go ahead and ask about the unclear parts and I'll try to help you through it..

thanks !
i've read the guide but it doesn't explain how to have ubuntu using i915 (if this is indeed the right driver for the integrated intel chip) instead of just nouveau.

as i said, lspci doesn't list my intel chip anymore,
i don't have /sys/kernel/debug/vgaswitcheroo
i tryed to boot with nomodeset, it made me using vesa driver, from there i inserted i915 driver manually and tryed to start Xorg with and without a Xorg.conf specifying the driver to i915/intel as shown below, without success. 
all i got was black screen with just a blinking cursor iirc.

file /usr/share/X11/xorg.conf.d/50-intel.conf
```

Section "Device"
    Identifier     "Intel Graphics"
    Driver         "i915"
    #Option        "AccelMethod" "sna"
    #Option        "AccelMethod" "uxa"
    BusID         "PCI:0:2:0"
    #Option "MetaModes" "1024x768"
EndSection

```i tryed to boot with various kernel options too, like:
```

nointremap i915.modeset=1 i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 drm.vblankoffdelay=1 i915.i915_enable_ppgtt=0 add_efi_memmap

```or just:
```

i915.modeset=1 nouveau.modeset=1

```nothing worked.
i'm at loss for clues on how to use my intel chip instead of nvidia's one.
i don't mind rebooting or logout/login again when switching gfx driver, i'm not trying to switch on the fly, i just want to be able to use my intel chip and right now i've never succeeded having it working. not even once.
btw, i don't have osx on my internal ssd drive, nor refind, i just use ubuntu and grub.

---

### Post by Garlandg on 2013-01-16
Well,  I haven't actually tried to enable intel graphics, though looking at this thread from the archlinux forum might help.  [https://bbs.archlinux.org/viewtopic.php?id=144255&p=2](https://bbs.archlinux.org/viewtopic.php?id=144255&p=2).  It looked like someone had managed to enable graphics switching, but I think the relevant parts will be near the bottom of the page.

There may be some differences in driver support between EFI booting and not EFI booting.  I believe nvidia drivers had a couple issues working in EFI mode, though they seem to be fixed, as I didn't have any problems.

I can't really help you with that, so I hope that thread helps.

---

### Post by freeaks on 2013-01-16
> **Garlandg said:**
> 
I can't really help you with that, so I hope that thread helps.

no, unfortunately, i've already read this thread, it's from there i took the xorg.conf.d/intel.conf file and most of the kernel options i've tryed.
i see ppl are successful here and there on using their retina's intel chip, but not me yet.
i wonder what am i missing..
thanks anyway for trying to help, garlandg

---

### Post by ksatta1 on 2013-01-16
nsicad:
I read your guide and instead of the b43fwcutter stuff you can just "sudo apt-get install linux-firmware-nonfree". Some time back I even diffed the resulting firmware files and they were exactly the same. But how much have you been using the WiFi? For me it works maybe an hour max. More info on what I've tried in the other thread ([http://ubuntuforums.org/showpost.php?p=12458590&postcount=7](http://ubuntuforums.org/showpost.php?p=12458590&postcount=7)).

freeaks and others with intel/nvidia problems, there's more on the subject in the other thread [http://ubuntuforums.org/showthread.php?t=2098304](http://ubuntuforums.org/showthread.php?t=2098304). (freeaks situation still unsolved as of now).

---

### Post by Garlandg on 2013-01-16
Just for clarity, the guide linked by nsicad was written by me.   I haven't tried the alternate method mentioned by ksatta1, but most of the time the Wifi works perfectly for me.  (The internet where I am is unreliable, so I can't be sure which is the culprit.) I almost always use the wifi, although here the internet has been dropping on Mac OSX some too (at home it's fine), so I have a wired connection too.

I have noticed that the microphone for say an iphone headset (I'm using an adapter for the audio jack) doesn't work in Linux (or WIndows for that matter), but the headphones do.  A solution for that would be really helpful, if anyone has one.  My internal mic works well though.

---

### Post by nsicad on 2013-01-16
> **Garlandg said:**
> Just for clarity, the guide linked by nsicad was written by me.   I haven't tried the alternate method mentioned by ksatta1, but most of the time the Wifi works perfectly for me.  (The internet where I am is unreliable, so I can't be sure which is the culprit.) I almost always use the wifi, although here the internet has been dropping on Mac OSX some too (at home it's fine), so I have a wired connection too.

I have noticed that the microphone for say an iphone headset (I'm using an adapter for the audio jack) doesn't work in Linux (or WIndows for that matter), but the headphones do.  A solution for that would be really helpful, if anyone has one.  My internal mic works well though.

Garlandg, 

I think you can improve your guide by making a bit logical (e.g. what to do first, before enumerating the current status). Have a look at these guides (below).

[http://cberner.com/2012/07/10/installing-ubuntu-12-04-on-macbook-pro-retina/](http://cberner.com/2012/07/10/installing-ubuntu-12-04-on-macbook-pro-retina/)
  
[http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/]("http://cberner.com/2012/07/10/installing-ubuntu-12-04-on-macbook-pro-retina/")

Edit: Just like to add these 2 other guides.

[http://www.warp1337.com/content/install-ubuntu-1210-quantal-quetzal-macbook-pro-101-retina-solved](http://www.warp1337.com/content/install-ubuntu-1210-quantal-quetzal-macbook-pro-101-retina-solved)

[http://www.physik.uni-freiburg.de/~helger/retina.html](http://www.physik.uni-freiburg.de/~helger/retina.html)

I hope somebody can create a clearer instruction how to install 13.04 in external drive using rEFIND.

Here's my take on this guide.

1. Download rEFIND, unzip it in one of the folder, 

[COLOR=#373737]sudo ./install.sh

We want only EFI boot loader in the internal drive where Mac OS X resides. The purpose of this boot loader is to boot the usb flash installer (usb live ubuntu installer.

2. Download the 13.04 iso for Mac OS. Use this iso to create a usb live ubuntu 13.04 installer.

3. Boot this usb live ubuntu installer. Be sure that you also plug in your usb external drive where you want to install 13.04 ubuntu.



[/COLOR]

---

### Post by raccoonone on 2013-01-16
> **Garlandg said:**
> Just for clarity, the guide linked by nsicad was written by me.   I haven't tried the alternate method mentioned by ksatta1, but most of the time the Wifi works perfectly for me.  (The internet where I am is unreliable, so I can't be sure which is the culprit.) I almost always use the wifi, although here the internet has been dropping on Mac OSX some too (at home it's fine), so I have a wired connection too.

I have noticed that the microphone for say an iphone headset (I'm using an adapter for the audio jack) doesn't work in Linux (or WIndows for that matter), but the headphones do.  A solution for that would be really helpful, if anyone has one.  My internal mic works well though.

Where you able to use the external monitor connectors? I never did manage to get those working right.

---

### Post by ksatta1 on 2013-01-17
> **raccoonone said:**
> Where you able to use the external monitor connectors? I never did manage to get those working right.

I think you have to use the nvidia adapter and install nvidia's proprietary drivers. (Haven't tried it myself yet, though). I think I read somewhere that works atleast. I'll probably connect an external monitor at some point and try to get it to work with intel adapter. But like I said, haven't tested at all yet.

> **Garlandg said:**
> Just for clarity, the guide linked by nsicad  was written by me.   I haven't tried the alternate method mentioned by  ksatta1, but most of the time the Wifi works perfectly for me.  (The  internet where I am is unreliable, so I can't be sure which is the  culprit.) I almost always use the wifi, although here the internet has  been dropping on Mac OSX some too (at home it's fine), so I have a wired  connection too.

Strange. I'll probably figure out what's going on with the WiFi some  day. I haven't tried 13.04 daily since christmas, so that might work.

Also  I don't know what's going on with my Macbook.. I've recently  experienced the "flashes" that other users have reported too when using  the intel display adapter. Today I tilted the Macbook and the display  started flashing (it's like it writes to the wrong mem address,  titlebars flash lower than they should be etc..), and I tested atleast 5  times, each time I tilted the Macbook it started flashing, when I  leveled it the flashing stopped. No problems so far in Windows or OS X,  but I'm on Linux maybe 95% of the time. And right now no flashing :)

> I have noticed that the microphone for say an iphone headset (I'm using  an adapter for the audio jack) doesn't work in Linux (or WIndows for  that matter), but the headphones do.  A solution for that would be  really helpful, if anyone has one.  My internal mic works well  though.Alsamixer shows the "Mic" channel in the capture section, but that's probably the Macbook's own mic. It seemed to be set to level "0" by default. Also can you choose the external mic as an input device from "pavucontrol" when it's connected? Just an idea.

---

### Post by freeaks on 2013-01-18
> **ksatta1 said:**
> nsicad:
freeaks and others with intel/nvidia problems, there's more on the subject in the other thread [http://ubuntuforums.org/showthread.php?t=2098304](http://ubuntuforums.org/showthread.php?t=2098304). (freeaks situation still unsolved as of now).

thanks for the reply :)
is there a place i could look at to get info about the state of the problem, so i could know when it gets fixed?
how did you know this is still unsolved?
i've read here and the on the various distros forums that some could successfully use their intel integrated chip. i wonder if they all had to recompile their kernel.

---

### Post by ksatta1 on 2013-01-18
> **freeaks said:**
> thanks for the reply :)
is there a place i could look at to get info about the state of the problem, so i could know when it gets fixed?
how did you know this is still unsolved?
i've read here and the on the various distros forums that some could successfully use their intel integrated chip. i wonder if they all had to recompile their kernel.

I think I used about 1 week on it total :D Right now I'm running 12.10 with kernel 3.8 rc3 (right now I'm using debs downloaded from ubuntu mainline site [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) . The raring-xx debs (they work on 12.10 too))

I marked it solved because it works for me, freeaks situation is special atleast so that he doesn't have refit, just straight grub boot. EDIT: just realized you're freeaks, LOL :)

Anyway the thing that got it working for me in the end was using the older gfxCardStatus in OS X. I have to boot to OS X, select Integrated Only, then reboot and ubuntu. Sometimes I have to do it a couple of times (ubuntu freezes at boot), but once it boots, no problems with it except the occasional flashes that others have reported too. I had some of those yesterday and this morning, but after that it's been fine.

Anyway now I have Xubuntu running, 2880x1800 res, battery life around 7 hrs etc.. Very happy with it except the WiFi, which seems to work very randomly.. no problems today so far, reason unknown.

EDIT2: I also posted a reply in the other thread yesterday (to try switching to integrated more than once), that's how I knew it's unsolved. Anyway if you can't get it to work, I can mark it unsolved.

---

### Post by Garlandg on 2013-01-19
I can confirm that the HDMI out works, though I am running the nvidia drivers.  I don't have a mini-DVI cable on me, so I can't test that.  

pavucontrol doesn't seem to see my mic either.  

I've updated the instructions with better outlining, hopefully a better explanation for the beginning parts, and more direct instructions.

I was having issues with Ubuntu and the time of the last mount of hard drives causing it to fail to boot.

I decided to try an experiment.  I installed Mint 14 onto the external hard drive using a different computer (using a similar procedure to my guide), chrooted into the install, and installed the raring 3.7.3 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.3-raring](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.3-raring)[/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.3-raring/")     

I had to add the raring restricted packages in the sources.list to get the nvidia drivers to work properly.  So far, it has been quite stable and it also made me decide to add a "Boot to shell" option in my guide and for my install.

Now if I could just get Ubuntu Software Center working...

---

### Post by nsicad on 2013-01-19
> **Garlandg said:**
> I can confirm that the HDMI out works, though I am running the nvidia drivers.  I don't have a mini-DVI cable on me, so I can't test that.  

pavucontrol doesn't seem to see my mic either.  

I've updated the instructions with better outlining, hopefully a better explanation for the beginning parts, and more direct instructions.

I was having issues with Ubuntu and the time of the last mount of hard drives causing it to fail to boot.

I decided to try an experiment.  I installed Mint 14 onto the external hard drive using a different computer (using a similar procedure to my guide), chrooted into the install, and installed the raring 3.7.3 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.3-raring](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.3-raring)[/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.3-raring/")     

I had to add the raring restricted packages in the sources.list to get the nvidia drivers to work properly.  So far, it has been quite stable and it also made me decide to add a "Boot to shell" option in my guide and for my install.

Now if I could just get Ubuntu Software Center working...

Thanks for updating your guide. It is clearer now.

[http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html](http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html)

I got one question on the 13.04 daily build iso, what is the default of this iso? Is is 3.8.x or 3.7.x?

I have problem in previous iso's once I update the kernel on the external drive (with installed ubuntu), I could not boot that external drive anymore. I am hoping that 13.04 comes with 3.8.x kernel.

Anybody have custom / remastered 13.04 iso that comes with 3.8.x linux kernel?

---

### Post by freeaks on 2013-01-20
> **nsicad said:**
> 
Anybody have custom / remastered 13.04 iso that comes with 3.8.x linux kernel?

daily build have kernel 3.8 since one week already.
grab a new iso burn it to usb stick like this:
```

sudo dd if=raring.iso of=/dev/sdb bs=8M

```
replace "raring.iso" and "/dev/sdb" by respectively, the iso filename (in the same dir you're typing the command) and the device of your usb stick. (when you insert your usb stick, type dmesg, it should show you the device name of the stick)

---

### Post by thhart on 2013-01-20
From my personal experience I still keep using Ubuntu in a Virtual environment (Parallels in my case). The graphic issues still are unresolved and it needs some time of kernel (driver,gmux) to fix it.
For all who still want to test please see this thread for information how to activate the Intel device: [http://ubuntuforums.org/showthread.php?p=12449607](http://ubuntuforums.org/showthread.php?p=12449607). An older GfxCardStatus has to be used to get the graphics switched. In my environment I can deactivated the discrete Nvidia device via vgaswitcheroo then and temperature and heat is getting down.

IMHO the Nvidia device is simply not usable in either Linux or OSX when not playing. The beast is getting hot and the fans are running all the time quite loud. I don't like this.
I am curious if somebody has an idea how to disable the Nvidia completely (BIOS/EFI wise). I have made some tests with the Intel device and the 3D numbers are not as bad.

---

### Post by Garlandg on 2013-01-20
The nvidia chip shouldn't be doing that.  I've been using it while gaming, and it doesn't reach 80C.  What temps are you seeing?  

Mine initially were really high, and i was concerned.  I did an SMC reset, and that fixed the issue:
[http://support.apple.com/kb/HT3964](http://support.apple.com/kb/HT3964)

---

### Post by thhart on 2013-01-27
> **Garlandg said:**
> The nvidia chip shouldn't be doing that.  I've been using it while gaming, and it doesn't reach 80C.  What temps are you seeing?  

Mine initially were really high, and i was concerned.  I did an SMC reset, and that fixed the issue:
[http://support.apple.com/kb/HT3964](http://support.apple.com/kb/HT3964)

It is not getting extremely hot but the fact that the fan is needed with a higher speed when not playing is not acceptable. The NVIDIA temp is showing 40-50 when idle and up to 60 while doing normal Desktop stuff. Even when I use OSX and the discrete is activated it has to be cooled noticeable.
I tried the SMC resetting without changes. 
As I stated already, the switching capability is a must for Linux and currently it is not working.
Again if anybody has a reliable solution I am very curious to hear about.

---

### Post by Umbra Diaboli on 2013-02-02
I really can't wait till Ubuntu works by default straight after installation (as my 4,2 Air does). I hate to use Ubuntu on Parallels :evil:

---

### Post by Sc0rian on 2013-02-05
just about to get my 13" macbook pro retina, is it good enough to run Ubuntu daily?

I'm hoping to use Ubuntu as my daily operating system.

Or is it really buggy and just a complete nightmare?

Do we have better support for intel drivers now?

---

### Post by Umbra Diaboli on 2013-02-06
Dear All,

Could anyone be kind enough to explain how to install the WiFi drivers without an ethernet adapter? I downloaded the driver on a separate machine, and used a USB to move it to my retina.

I was trying to install the driver following the instructions here:
[http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/](http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/)
And here:
[http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html](http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html)

I had to convert the tar.gz2 to .deb on a different machine using alien to install it as a .deb package.

The part where I seem to be having problems is executing the following command:

```
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.100.138/linux/wl_apsta.o
```

It comes out as b43-fwcutter command not found. I do have wl_apsta.o in my home folder.

I apologize, I'm a noob at this and any help guiding me through the process of installation will be very appreciated. 

Regards,
***Umbra Diaboli***

---

### Post by nsicad on 2013-02-06
> **Umbra Diaboli said:**
> Dear All,

Could anyone be kind enough to explain how to install the WiFi drivers without an ethernet adapter? I downloaded the driver on a separate machine, and used a USB to move it to my retina.

I was trying to install the driver following the instructions here:
[http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/](http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/)
And here:
[http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html](http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html)

I had to convert the tar.gz2 to .deb on a different machine using alien to install it as a .deb package.

The part where I seem to be having problems is executing the following command:

```
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.100.138/linux/wl_apsta.o
```It comes out as b43-fwcutter command not found. I do have wl_apsta.o in my home folder.

I apologize, I'm a noob at this and any help guiding me through the process of installation will be very appreciated. 

Regards,
***Umbra Diaboli***

Those instructions you mentioned require an internet connection.  

Use this instruction how to install offline, download first the files (below link)
** Offline install of b43-fwcutter and firmware for Broadcom Wireless cards**


[http://linuxforums.org.uk/index.php?topic=5842.0](http://linuxforums.org.uk/index.php?topic=5842.0)

---

### Post by Umbra Diaboli on 2013-02-07
> **nsicad said:**
> Those instructions you mentioned require an internet connection.  

Use this instruction how to install offline, download first the files (below link)
** Offline install of b43-fwcutter and firmware for Broadcom Wireless cards**


[http://linuxforums.org.uk/index.php?topic=5842.0](http://linuxforums.org.uk/index.php?topic=5842.0)

That worked!!!!! 

Thanks a lot!! Really!!!!

---

### Post by blayne on 2013-02-07
Has anyone had any experience replacing the wifi card with something that has better linux support.

I'm finding the broadcom chip will drop out after 10-30 minutes of use, then the way to get it working again is the reboot the system. It also doesn't support 802.11n

I was looking at ifixit it looks like it is a simple job to get to the wifi chip [Step 11]("http://www.ifixit.com/Teardown/MacBook+Pro+15-Inch+Retina+Display+Mid+2012+Teardown/9462/2").

It also looks like the [Airport Extreme Atheros AR5008]("http://www.ebay.com/itm/Apple-Mac-Book-Pro-Airport-Extreme-Wireless-N-WIFI-Card-Atheros-AR5BXB72-Mini-/110999878927?pt=US_Internal_Network_Cards&hash=item19d81bbd0f") should fit in fine and will give 802.11n too.

---

### Post by raccoonone on 2013-02-09
So, strange issue that I've run into. 

I have an EFI install, with the proprietary nvidia drivers, and it seems that if I leave my retina powered off for more than 24hrs, the nvidia drivers become corrupted somehow. When I boot back up, I get a blank screen, or sometimes some seemingly unrelated kernel messages. If I force the intel card from OSX then it boots fine.

Anyone else experienced this problem?

---

### Post by Sc0rian on 2013-02-09
Well on my MBPR 13" installed to the latest ubuntu 13.04 daily build. Pretty impressed, most things work out of the box. I had to mess around with modprobe to get Audio working. But thunderbolt works, screen res, backlight keyboard. Very impressed.

Now using it as my daily machine.

Issues:
No Microphone :( - fixed
When I pair my bluetooth headset. If I go to the sound control panel, I will get a kernel panic and have to reboot the machine. So that's not supported.
wireless works, but if I move it, it will cause the signal to pretty much stop. Have to fix it by reboot (or mobprobing probably)


I have a thunderbolt -> dvi cable, but when I plug it up I am limited to 1920X. Is this normal? I have a U3011, so this is pretty annoying. Maybe I should go and buy a HDMI cable?


Edit: Loaded the correct driver in mobprobe (mbp101) and internal mic now works (thanks for the patch link).


Bluetooth headset still crashes the kernel.

---

### Post by eeptman on 2013-02-09
Successfully installed Ubuntu 13.04 once  on rMBP 15" by following instruction mentioned here before. However, I reinstall it few days ago. The NVIDIA driver (v304) from ubuntu server seems screw up everything.

Showing nothing after the first prompt UBUNTU... window. Is there anyone know which version of NVIDIA driver is suitable for current Ubuntu 13.04 (v3.8.04 kernel)?

 Thanks.

---

### Post by MikeBraxner on 2013-02-09
After using the 915 solely for months, I wanted to try the NVidia Card once more ... and promptly fell at the first hurdle.

Trying to install the nvidia-current package now merely produces ...

```
Loading new nvidia-current-304.64 DKMS files...
First Installation: checking all kernels...
Building only for 3.6.0
Building for architecture x86_64
Building initial module for 3.6.0
ERROR (dkms apport): kernel package linux-headers-3.6.0 is not supported
Error! Application of patch blacklist-vga-pmu-registers.patch failed.
Check /var/lib/dkms/nvidia-current/304.64/build/ for more information.

```

I had the NVidia drivers installed (back when), and they worked fine. Any ideas what I'm doing wrong?

---

### Post by Sc0rian on 2013-02-09
Added these into my rc.local if anyone needs them:

```
echo 2 > /sys/module/hid_apple/parameters/fnmode #swap fn keys
echo 2 > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness #screen brightness
echo 100 > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness #backlight keyboard

```


I have a HDMI and thunderbolt dvi cable, but both only give me 1980. While my U3011 supports 2560x1600. I was able to force 2560 using xrandr, but only on the thunderbolt plug. It also was terrible, text was very fuzzy. Apparently you can get 2560, because someone on the Apple forums has (on windows). 

The support for higher res external outputs lack in Apple OS X too, which is annoying! 

I have actually got 3 screens working, Laptop, HDMI and thunderbolt DVI which is pretty cool! Although I did have a Kernel panic, relating to the HDMI. 


Can the mbpr 13" support 2560x, on a external screen? I'm pretty sure it can. And has anyone got this resolution working on a external screen here?


Thanks

---

### Post by raccoonone on 2013-02-09
> **Sc0rian said:**
> Added these into my rc.local if anyone needs them:

```
echo 2 > /sys/module/hid_apple/parameters/fnmode #swap fn keys
echo 2 > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness #screen brightness
echo 100 > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness #backlight keyboard

```


I have a HDMI and thunderbolt dvi cable, but both only give me 1980. While my U3011 supports 2560x1600. I was able to force 2560 using xrandr, but only on the thunderbolt plug. It also was terrible, text was very fuzzy. Apparently you can get 2560, because someone on the Apple forums has (on windows). 

The support for higher res external outputs lack in Apple OS X too, which is annoying! 

I have actually got 3 screens working, Laptop, HDMI and thunderbolt DVI which is pretty cool! Although I did have a Kernel panic, relating to the HDMI. 


Can the mbpr 13" support 2560x, on a external screen? I'm pretty sure it can. And has anyone got this resolution working on a external screen here?


Thanks

What driver were you using? I've gotten external monitors to work with the proprietary nvidia driver, but haven't gotten it to work with any of the open source ones

---

### Post by Sc0rian on 2013-02-09
I am using the driver that came with raring ringtail. I got a MBPR 13" not 15" so I do not have the nvidia problems... 

I have not got any fan control though... Anyone got some tips on this?

---

### Post by longint on 2013-02-13
Hey guys, I'm not using Ubuntu (yet) but get stuck with the nvidia stuff in other linux distributions. I've read several times that Ubuntu users have been able to use their MBPr running the proprietary nvidia drivers. Let me be clear - I've read this for other distributions as well but after digging deeper it turned out that it only worked in very special configurations using 3.6 kernel and specific (non recent) versions of the nvidia drivers. So what is your experience? If you are running the nvidia drivers I would be interested to hear which kernel, nvidia driver version, if you use EFI and if there is something special you did.

I also read about ubuntu 13.04 planning to get official support for this box and that the nightly builds (using kernel 3.8) are already working quite well, can you confirm this?

Other question: Is your SD-Card and Bluetooth working well?
I guess Thunderbold is also just working when plugged in before booting?

Thx a lot, looking forward to hear from your experiences, lets see if they can me make switch to ubuntu :-)

---

### Post by Sc0rian on 2013-02-14
I had to reinstall ubuntu, but not for some reason my audio has no bass at all. Sounds terrible.

/etc/rc.local

rmmod snd_hda_intel
modprobe snd_hda_intel

/etc/modprobe.d/alsa-base.conf 

options snd-hda-intel model=mbp101

Anyone know why?

---

### Post by Umbra Diaboli on 2013-02-14
> **longint said:**
> Hey guys, I'm not using Ubuntu (yet) but get stuck with the nvidia stuff in other linux distributions. I've read several times that Ubuntu users have been able to use their MBPr running the proprietary nvidia drivers. Let me be clear - I've read this for other distributions as well but after digging deeper it turned out that it only worked in very special configurations using 3.6 kernel and specific (non recent) versions of the nvidia drivers. So what is your experience? If you are running the nvidia drivers I would be interested to hear which kernel, nvidia driver version, if you use EFI and if there is something special you did.

I also read about ubuntu 13.04 planning to get official support for this box and that the nightly builds (using kernel 3.8) are already working quite well, can you confirm this?

Other question: Is your SD-Card and Bluetooth working well?
I guess Thunderbold is also just working when plugged in before booting?

Thx a lot, looking forward to hear from your experiences, lets see if they can me make switch to ubuntu :-)

Nightly builds? I'm sorry for my noobishness, but there is something called the nightly builds?

---

### Post by Sc0rian on 2013-02-15
nightly builds are developments builds. So they are built nightly with the changes. You are now out of date after a night, since you can get the update however nightly changes can mean you might pick up bugs since it has not been fully tested. This is where you use launchpad. 

@longlnt I got a 13", which means I do not have the nvidia worries.  However I would use the 13.04 build. Just wack it on a USB pen, boot up from it and see. My bluetooth does work (but cannot get audio working), SD-Card, not sure since I do not have the card type. Thunderbolt works fine, its only ethernet port does not work from cold boot.

---

### Post by nmushkin on 2013-02-17
Im triple booting windows, osx and ubuntu on my retina.  I used the windows ubuntu installer while in windows and ubuntu seems to be working pretty well.  From the linux boot manager i can choose to boot into all three os.  I got the wireless working, by sudo apt-get update, and then using the proprietary driver.  there are a few crashes here and there, what would cause this?

---

### Post by ksatta1 on 2013-02-21
Lots of replies, haven't had time to visit the forums for a while :)

> **Sc0rian said:**
> just about to get my 13" macbook pro retina, is it good enough to run Ubuntu daily?

I'm hoping to use Ubuntu as my daily operating system.

Or is it really buggy and just a complete nightmare?

Do we have better support for intel drivers now?

I have the 15" Retina model.

I'm using 12.10 Xubuntu with some stuff added from 13.04 daily (the WiFi drivers mainly). I use it at least 8h each day at work. I'm happy with it. It's stable etc, but there's some annoyances like for example the thunderbolt-ethernet adapter stops working after suspend, have to reboot. Using only the Intel adapter and turning off Nvidia, I get about 13W power usage when idling, battery time estimation 7h :)

In 13.04 more stuff works out-of-the-box, but for me some process keeps crashing and I get notified about it etc. Haven't had much time to look into it. 

> **Umbra Diaboli said:**
> Dear All,

Could anyone be kind enough to explain how to install the WiFi drivers  without an ethernet adapter? 
> **blayne said:**
> 
I'm finding the broadcom chip will drop out after 10-30 minutes of use,  then the way to get it working again is the reboot the system. It also  doesn't support 802.11n

It also looks like the [Airport Extreme Atheros AR5008]("http://www.ebay.com/itm/Apple-Mac-Book-Pro-Airport-Extreme-Wireless-N-WIFI-Card-Atheros-AR5BXB72-Mini-/110999878927?pt=US_Internal_Network_Cards&hash=item19d81bbd0f") should fit in fine and will give 802.11n too.

In 13.04 software properties / restricted drivers / broadcom. In 12.10 mine works with bcmwl..something package from 13.04.
EDIT: if you don't have an ethernet adapter, just downloading the bcmwl..something package (for 13.04) from packages.ubuntu.com on another computer should work.

With all the b43fwcutter methods etc I kept having disconnections etc, with the 13.04 restricted driver no problems.

That driver still doesn't support 802.11n though. By the way, I also purchased a cheap USB WiFi which had Linux drivers, but it kept disconnecting too. Haven't tested it in another machine yet (might just be faulty).

The Airport foo seems to be a new module to put inside the macbook, that might also fix it, but I suggest trying the 13.04 restricted driver first :)

> **Sc0rian said:**
> I have not got any fan control though... Anyone got some tips on this?

mactel ppa, package macfanctld

> **longint said:**
> Hey guys, I'm not using Ubuntu (yet) but get  stuck with the nvidia stuff in other linux distributions. I've read  several times that Ubuntu users have been able to use their MBPr running  the proprietary nvidia drivers. Let me be clear - I've read this for  other distributions as well but after digging deeper it turned out that  it only worked in very special configurations using 3.6 kernel and  specific (non recent) versions of the nvidia drivers. So what is your  experience? If you are running the nvidia drivers I would be interested  to hear which kernel, nvidia driver version, if you use EFI and if there  is something special you did.

I also read about ubuntu 13.04 planning to get official support for this  box and that the nightly builds (using kernel 3.8) are already working  quite well, can you confirm this?

Other question: Is your SD-Card and Bluetooth working well?
I guess Thunderbold is also just working when plugged in before booting?

Thx a lot, looking forward to hear from your experiences, lets see if they can me make switch to ubuntu :smile:

I have NVidia working in 13.04 daily with the latest NVidia driver from nvidia.com. I had to add:
Option "UseDPLib" "off"
to the "Device" section.

There's a black screen for maybe 10-20 seconds when it boots, but then it boots and works. Haven't tested it much yet though, ran some glxgears tests :)

And oh yes, I recently discovered that the MB can't use the external  video outputs with the Intel display adapter (it switches to Nvidia in  OSX when you plug in DVI or HDMI). My first disappointment with this MB  hardware-wise. Now I'm thinking of buying a USB display adapter :grin:  So that I don't have to use the discrete Nvidia adapter, which heats up  the Macbook and eats battery etc. And also there's no easy way to  switch between Nvidia and Intel in the same Ubuntu installation (I have  12.10 for daily use, 13.04 for testing some stuff, and Nvidia working  there). 


> **Sc0rian said:**
> I had to reinstall ubuntu, but not for some reason my audio has no bass at all. Sounds terrible.

/etc/rc.local

rmmod snd_hda_intel
modprobe snd_hda_intel

/etc/modprobe.d/alsa-base.conf 

options snd-hda-intel model=mbp101

Anyone know why?

The bass speaker sometimes goes to volume 0 or mute. I usually just check it with alsamixer from the command line (I use command line 99% of the time :) ). There's probably a way to get the bass channel to show up in the GUI mixer too.

> **Sc0rian said:**
> My bluetooth does work (but cannot get audio  working)

I have BT audio sink working on mine (streaming music from my Android phone to the MB), had to go to the bluetooth settings (right-click BT icon in Xubuntu), and enable "advanced audio receiver". It was skipping etc, but when I disable WiFi it works fine.
EDIT: In 12.10 I had to install pulseaudio-module-bluetooth to get it working, forgot that.
EDIT2: The BT setting is actually left click bt icon, then local services / advanced audio receiver

---

### Post by Sc0rian on 2013-02-21
Thank you for the help ksatta1.

I installed macfanctld and it works a treat.

I got WIFI and bluetooth working, I was missing pulseaudio-module-bluetooth. Once I installed it I was able to see the headset in sound. I installed bluez and got the AD2P profile working, they work great.

So currently I have a completely working laptop on Ubuntu (pretty much) (SD Card untested).

I am using [https://launchpad.net/~poliva/+archive/lightum-mba](https://launchpad.net/~poliva/+archive/lightum-mba) which works a treat. This uses the Mac's light sensor to control screen and keyboard brightness.

I installed [https://launchpad.net/~daniel.pavel/+archive/solaar](https://launchpad.net/~daniel.pavel/+archive/solaar) which allows my logitech K750 and MX performance mouse to work and up the DPI. Although from cold boot it does not work, have to unplug and plug the adapter. Cannot get it to scroll more than one line too, which is annoying. Also the unify device only work in one usb port, the right side. The left side just will not work :(. 

Not a big problem since I only run one monitor at work but at home:

I cannot run two external monitors. I have a mini display port -> display port, which allows me to run 2560x1600. I also have a HDMI cable. If I plug it up to both, the 3rd monitor will not enable. The only way I can get it to enable is if I run them all at the same resolution. I can obviously have them all working in Mac OS X no problem. I'm guessing it is a bug with Ubuntu.

I do sometimes get very slow WIFI, so that is not perfect.

---

### Post by longint on 2013-02-22
Hey guys, I'm on 13.04 based on the raring ringtail nighly builds now. For more informatoon have a look to this: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
I already did some dist-upgrades and got several new kenerls (3.8.0.7-21 or something like this at the momen), no major bugs which prevented me from using the box so far (beside playing around with installing/removing packages by my own :-).

Considering that 13.04 is supposed to support the box very well and there is a specific build for MAC there are quite a lot of hings not working well. Just want to share my own experiences: 
-- suspend is not working at all while it was working without a single issue in Fedora 18, already tried some things, would like to get some hints as this is quite important for me
-- touchpad is not supporting 3finger click as middle click (worked out of the box in Fedora18), please advice how to fix this :-)
++ battery life time is much, much better than in Fedora18! (there seems to be a long known but not solved bug in gnome-shell or Fedora eating up the machine) 
++ graphics performance ist much, much better than in Fedora 18, in F18 you have not even been able to watch fullscreen videos, both running not nvidia drivers 
- I've not been able to get nvidia drivers running, mainly I'm not on EFI yet
- adjusting backlight is not working while it was in F18
+ better support for basic stuff than F18 which restricted users in much tighter way (grabbing and renaming device names is really annoying)
- the Ubuntu UI (Unity?) is something really strange, but I'm willing to try further
- even compared to the already restricted gonme3 in F18 there are a lot of configuration possibilities missing. How to add additional workspaces?
- while there is less bloatware installed as in F18 there is still something one has to get rid of
- same issues with SDcards not read properly and bluetooth not working (for my devices), might be an general issue 

Conclusion: Given the much better better graphic performance and the much better battery lifetime I'll stay on Ubuntu for now. I'll definitely not go back to Fedora as I just did not like it in general. Might be I'll give Arch or Gentoo another try sometimes in the future. Looking forward to get the issues noted above solved, suspend and 3finger click is a must to have...  

Question:
* Did anyone install rEFInd right from Ubuntu or any other Linux and not from OSX? Thing is, I already removed OSX completely (first thing I did).

Update:
There is one thing which is really annoying and which I did not face before: The boxes freezes quite often. This only happens when running chrome and trying to input something into the adress bar. Any idea anyone?  Chrome got updated today to a new version but this still happens. Not sure if this is really related to chrome as I did not have any issues running it on F18...

---

### Post by longint on 2013-02-22
> **ksatta1 said:**
> 
I have NVidia working in 13.04 daily with the latest NVidia driver from nvidia.com. I had to add:
Option "UseDPLib" "off"
to the "Device" section.


ksatta1, you are running EFI?

---

### Post by Sc0rian on 2013-02-23
my laptop hangs for ages on boot. Does anyone else have this problem?

I think its because its trying to connect to the wireless network.

```
[    7.855895] type=1400 audit(1361628647.379:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1044 comm="apparmor_parser"
[    7.858014] type=1400 audit(1361628647.383:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1050 comm="apparmor_parser"
[    7.978769] init: lightdm main process (1161) killed by TERM signal
[    8.030136] init: anacron main process (1151) killed by TERM signal
[   31.239728] wlan0: authenticate with 00:xx:xx:xx:00:c2
[   31.263254] wlan0: send auth to 00:xx:xx:xx:00:c2 (try 1/3)
[   31.265138] wlan0: authenticated
[   31.265361] b43 bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   31.265368] b43 bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   31.267032] wlan0: associate with 00:xx:xx:xx:00:c2 (try 1/3)
[   31.269211] wlan0: RX AssocResp from 00:xx:xx:xx:00:c2 (capab=0x411 status=0 aid=4)

```

It also does it when it is not connecting to a WIFI network:

```
[    7.810706] type=1400 audit(1361664955.352:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1020 comm="apparmor_parser"
[    7.810972] type=1400 audit(1361664955.352:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1020 comm="apparmor_parser"
[    7.811327] type=1400 audit(1361664955.352:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1025 comm="apparmor_parser"
[    7.952151] init: lightdm main process (1130) killed by TERM signal
[   42.886225] applesmc: light sensor data length set to 10

```


What is causing it?

---

### Post by ksatta1 on 2013-02-24
I decided to "take a quick look" to see if there's any new info on GPU switching, but I ended up spending quite a while replying :D I really have to take a break from this thread LOL

> **Sc0rian said:**
> 
I am using [https://launchpad.net/~poliva/+archive/lightum-mba](https://launchpad.net/~poliva/+archive/lightum-mba) which works a treat. This uses the Mac's light sensor to control screen and keyboard brightness.
Cool, have to try that one day :)

> I do sometimes get very slow WIFI, so that is not perfect.I guess you've already tried 13.04 bcmwl..something restricted driver? It works best for me.

> **longint said:**
> -- suspend is not working at all while it was  working without a single issue in Fedora 18, already tried some things,  would like to get some hints as this is quite important for me
In  12.10 if I turn off the Nvidia adapter power (echo OFF >  /sys/kernel/debug/vgaswitcheroo/switch), I have to echo ON > ...  before susped and then echo OFF again after suspend (I have it all in  the suspend/resume scripts), otherwise I don't remember having any  problems suspending and resuming. The ethernet adapter stops working  after suspend, but anyway the computer suspends/resumes otherwise ok.

> -- touchpad is not supporting 3finger click as middle click  (worked out of the box in Fedora18), please advice how to fix this :smile:I  noticed in 13.04 that it has 3 finger dragging, probably also click.  You can probably set it with "synclient something". Just "synclient"  lists all the options.

> ++ battery life time is much, much  better than in Fedora18! (there seems to be a long known but not solved  bug in gnome-shell or Fedora eating up the machine) I have  7hrs battery life (estimated) when fully charged and idling :) This is  with only the intel adapter in use (and Nvidia powered off). (  [http://ubuntuforums.org/showthread.php?t=2098304](http://ubuntuforums.org/showthread.php?t=2098304) ). An addition those  instructions: atleast on 3.8 kernel you don't need any of the kernel  options (modeset etc).

> - same issues with SDcards not read  properly and bluetooth not working (for my devices), might be an  general issueMy bluetooth works best if I turn off WiFi. (To get BT audio working had to install pulseaudio-module-bluetooth).

> Question:
* Did anyone install rEFInd right from Ubuntu or any other Linux and not  from OSX? Thing is, I already removed OSX completely (first thing I  did).I tried, but couldn't get it to work.

I just "fought" with the EFI boot for one and a half  days :D It decided to stop booting into Linux or Windows. Anyway in the  end I think I fixed it like this:
- Installed refind in OSX, to the OSX partition (in Linux I couldn't get it installed right).
-  Installed the other stuff that boot-repair creates in the separate EFI  partition (fat32 partition in the beginning of the drive).

> **longint said:**
> ksatta1, you are running EFI?
Yes. I have to triple boot win/osx/linux and I think it's the only way to get intel adapter working?

> **Sc0rian said:**
> my laptop hangs for ages on boot. Does anyone else have this problem?
Probably nothing to do with your problem but:
In  13.04 I get a black screen for about 20-30 secs, with the Nvidia in  use. I had to add Option "UseDPLib" "off" to the "Device" section, to  get the latest drivers from nvidia.com working. Haven't played around  with 13.04 for a while, I use 12.10 for daily use.

Also, I have applesmc-dkms ver 0.18.2 (from mactel PPA) installed, and I only get (in dmesg):
```
[   11.039917] applesmc: key=491 fan=2 temp=44 index=43 acc=0 lux=2 kbd=1
```You  seem to have something else about applesmc in there, but might be  because of the light-sensor program, and nothing to do with the problem.

Looks like your lightdm is killed for some reason, I have no mention of lightdm in my syslog / dmesg. I'm running 12.10 with kernel from kernel.org, so that probably causes differences in the logs too.

---

### Post by ksatta1 on 2013-02-25
This looks interesting:
[http://www.mail-archive.com/platform-driver-x86@vger.kernel.org/msg04039.html](http://www.mail-archive.com/platform-driver-x86@vger.kernel.org/msg04039.html)

It seems it's possible to switch to/from nvidia just by restarting X and doing some stuff. (EDIT: and I think you have to use the gmux driver changes from there).

Might try it some day. Like it says "use at your own risk" :)

The reason I'd need this is that I need nvidia when I want an external monitor connected, otherwise just intel.

---

### Post by longint on 2013-02-25
Thx Ksatta1. Bluetooth is workig now after switching to the bcml (?) drivers. Used the b43 stuff before.

To EFI: I've rEFInd up and running on an USB stick able to boot from there directly my kernel from the root partition at the hdd conatining Ubuntu. I'd like to get this running without the need for the USB stick but have the warnings at the rEFInd in mind that installing it running Linux will destroy the BIOS/firmware of the MBPr!? As you said you tried and your box is still running I might rethink this and just do it...

powertop shows around 28W on my box meaning nvidia is active!? Strange as I never managed to get the proprietary drivers running...

Suspend not working is real NoGo for Ubuntu and I hope to get this running soon. According to your feedback it should work having the nvidia card active? Might be something specific for 13.04.

Thx for all the feedback and links, will keep me busy some days :-)


Update: Just installed rEFInd right from within Ubuntu, works like a charme :-).
Update2: Hehe, the 1st time I own the unit I got the proprietary nvidia drivers running!

Question to powertop: I do not see the power usage anymore!? Also, is there a way to staticaly set the options for the Tunables screen in there?

---

### Post by longint on 2013-02-26
BTW, these are the settings "powertop --html" is suggesting for tuning (powersaving) my box:

```

echo '0' > '/proc/sys/kernel/nmi_watchdog';
echo '1500' > '/proc/sys/vm/dirty_writeback_centisecs';
echo 'min_power' > '/sys/class/scsi_host/host0/link_power_management_policy';
echo 'auto' > '/sys/bus/usb/devices/3-1/power/control';
echo 'auto' > '/sys/bus/usb/devices/2-1.8.2/power/control';
echo 'auto' > '/sys/bus/usb/devices/2-1.8.1.3/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:06:06.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:01:00.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:00:01.2/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:00:01.1/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:00:01.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:06:00.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:06:03.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:06:04.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:06:05.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:08:00.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:09:00.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:00:16.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.3/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:00:1d.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:00:02.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:00:14.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:03:00.1/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:00:1c.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:00:1c.1/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:05:00.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:00:1a.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.0/power/control';
echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.2/power/control';
ethtool -s eth1 wol d;

```

After running my USB mouse is not working anymore but a simple replugin helps.

Next stop: Suspend! Really a show stopper at the moment!

---

### Post by MikeBraxner on 2013-02-26
longint --- to set the powertop suggested tunings on a permanent basis, create a /etc/pm/power.d/99_MBP following this pattern

```
#!/bin/bash
#
# MacbookPro Retina 10.1 power management script 
#
# location: /etc/pm/power.d/99_MBPr_10-1 
#


if ! on_ac_power ; then    # adjust for Battery ...

   # NMI watchdog should be turned off    
   echo '0' > '/proc/sys/kernel/nmi_watchdog'
        .
        .
        .
else                       # back on main power ...

   # SATA link power management to max_performance
   echo 'max_performance' > /sys/class/scsi_host/host0/link_power_management_policy

   # PCI express ASPM to performance
   echo 'performance' > /sys/module/pcie_aspm/parameters/policy
        .
        .
        .
fi

exit 0
```

That should do the trick.


Edit: Forgot to mention ... 

Any hook you place in /etc/pm/power.d will be handled by pm-utils, which also pull additional pre-set scripts from /usr/lib/pm-utils/power.d and mesh the lot. If both contain identically named scripts, then the one in /etc/pm/power.d overrides, and the /usr/lib/pm-utils/power.d one will *NOT* be executed. This can generate a problem, if you use a **generically named** script like 99_MBPr_10-1. 

Since pm-utils has no clue that you just enforced a setting for, say, the intel audio controller or the vm-writeback, it blithely runs the /usr/lib/pm-utils/power.d contained script, thus *overriding* your desired settings. Therefore, re-check that your desired values *actually make it through*, and if not, check for contrary scripts in /usr/lib/pm-utils/power.d. Should some exist, then you should re-locate the according settings into a separate script, named to override the pre-set one ... or you can remove the pre-set script, once you made sure that you handled ALL viable states (AC, BAT, BAT Charging, ...) in the way you see fit.

---

### Post by longint on 2013-02-26
> **MikeBraxner said:**
> longint --- to set the powertop suggested tunings on a permanent basis, create a /etc/pm/power.d/99_MBP following this pattern


Thx Mate, but what is wrong with keeping these values when running on AC? OK, more performance would be nice :-)

Other question:
What fps is glxgears showing on your box? Mine ist just showing 60 running proprietary nvidia drivers.

And any help getting suspend to work is very welcome :-)

Update:
After trying a "echo -n "mem" >/sys/power/state" suspend is suddenly working now. WTF? I didn't change anything, so what happend? Did some upgrades the last time, most likely there is has been changed something.

Next Stop: 3finger-midle click in Unity, one of the annoying things left...

---

### Post by MikeBraxner on 2013-02-26
Around 820-830 FPS ... of course, full-screen that kind'a drops to ~36-37 FPS using i915 only. Jokes aside, which NVidia driver version are you using, 310, 313???

Suspend ... I'm using 12.10, and I think you're concerned with 13.04??? Sorry.

---

### Post by longint on 2013-02-26
> **MikeBraxner said:**
> Around 820-830 FPS ... of course, full-screen that kind'a drops to ~36-37 FPS using i915 only. Jokes aside, which NVidia driver version are you using, 310, 313???

Suspend ... I'm using 12.10, and I think you're concerned with 13.04??? Sorry.

Yeah, I'm running 13.04, "official" apt package nvidia-310 installed.

---

### Post by MikeBraxner on 2013-03-01
Sensors & Fans 

After originally installing lmsensors and macfanctld in 12.10, I wasn't particularly concerned about the fans or any temperature issues. However, I had reason to review some temperature sensor readings in /sys/devices/platform/apple.smc.768 and got a nasty surprise ... a total of **9 sensors** (13, 17, 18, 19, 25, 32, 33, 34, 35) reported bogus values, one a plain 0, and **8 times -127 C**. You might want to take a quick look yourself ...
```
for i in $(seq 1 43) 
  do 
    echo $i  $(echo "(`cat /sys/devices/platform/applesmc.768/temp${i}_input`)")
  done



```That meant that the 'environment' average used by macfanctld tended to come up as a pleasant ~22 C, instead of the more appropriate 42-44 C range, thus maintaining the fans in a continuously happy 'idle' setting.

Now paying closer attention to the remaining readings, I was also left with the feeling that the difference between CPU Diode and CPU Proximity readings under load was somewhat larger than (I think) macfanctld assumes. Thus, until someone with some decent hardware knowledge can address this intelligently, I will opt for some more defensive settings in /etc/macfanctl.conf ...
```
temp_avg_floor: 45
temp_avg_ceiling: 55


temp_TC0P_floor: 43
temp_TC0P_ceiling: 53


temp_TG0P_floor: 50
temp_TG0P_ceiling: 58


exclude: 13 17 18 19 25 32 33 34 35

```
Could someone please comment on the temperature issue?

---

### Post by longint on 2013-03-01
These are my readings running kernel 3.8.0, Ubuntu 13.04, not running macfanctld:
```

1 (35750)
2 (35750)
3 (32500)
4 (77750)
5 (79750)
6 (59750)
7 (75000)
8 (75000)
9 (75000)
10 (75000)
11 (75000)
12 (76000)
13 (0)
14 (76000)
15 (76750)
16 (70250)
17 (81000)
18 (81500)
19 (75000)
20 (64000)
21 (64000)
22 (47500)
23 (64000)
24 (64000)
25 (64000)
26 (64000)
27 (58750)
28 (58250)
29 (58000)
30 (58000)
31 (65000)
32 (-127000)
33 (-127000)
34 (-127000)
35 (-127000)
36 (51000)
37 (43000)
38 (43000)
39 (49000)
40 (63750)
41 (30000)
42 (42250)
43 (45250)

```

---

### Post by longint on 2013-03-01
Did anyone succeed to boot rEFInd from any other partition than sda1?

---

### Post by raccoonone on 2013-03-02
I've been testing out the 13.04 daily releases, and I think I've finally got the steps down to install it smoothly with the nvidia driver working right. I wrote it up in a new blog post, if anyone is interested: [http://cberner.com/2013/03/01/installing-ubuntu-13-04-on-macbook-pro-retina/]("http://cberner.com/2013/03/01/installing-ubuntu-13-04-on-macbook-pro-retina/")

Summary:
* Wifi works way better, now that it's supported by the bcmwl-kernel-source driver
* Nvidia driver seems to work right, with the right xorg and kernel options
* modesetting is properly supported by the kernel now, so no more need for the nomodeset option

---

### Post by longint on 2013-03-02
Thx raccoone, why do you still need/install grub when using rEFInd anyway? Skip it.
Do you encounter any issues with suspend so far? This strange things is driving me crazy, mostly working now, but not always and for sure not some days ago...

---

### Post by MikeBraxner on 2013-03-02
raccoonone --- I saw that you still list the 'fonts too small' as an issue on your blog. May I suggest adding a DPI setting to your /etc/xorg.conf ...
```
Section "Monitor" 
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Apple Color LCD"
    HorizSync       30.0 - 111.1
    VertRefresh     60.0
     **Option         "DPI" "128 x 128"**
     DisplaySize     333 207
    Option         "DPMS"
EndSection
```

The 15" Retina has a natural ~220 DPI, so a setting from 125-135 DPI enlarges everything (fonts, icons, warts and all) effortlessly, as long as your graphics driver respects the X-settings ... which the NVidia's do.

---

### Post by longint on 2013-03-02
You should not specif both DPI and DisplaySize as they overwrite each other, I'd recommend to stick with Displaysize. This reveals 221x217 dpi for my 15" Retina.

```

# xdpyinfo | grep -B2 resolution
screen #0:
  dimensions:    2880x1800 pixels (331x211 millimeters)
  resolution:    221x217 dots per inch

```

---

### Post by MikeBraxner on 2013-03-02
longint --- I switch my NVidia GPU OFF to save power, and then I'm surprised when those three sensors give me bogus readings ... yeah. 

On the bright side, this at least identify some more sensors ...

Sensor 15    TG0D        HD 4000 GPU, Diode 
Sensor 16    TG0P        HD 4000 GPU, prob. Proximity 
Sensor 17    TG1D        NVidia GT 650, Diode 
Sensor 18    TG1F        NVidia GT 650, prob. Cooling Fin 
Sensor 19    TG1d        NVidia GT 650, prob. Proximity

BTW, you ARE aware that both you're CPU and GPU were running fairly hot?
59.750 C    Sensor 6        TC0P    CPU Proximity 
75.000 C    Sensor 7-10    TC1C    CPU Diodes – Core 1-4
76.750 C    Sensor 15        TG0D    HD 4000 GPU, Diode 
70.250 C    Sensor 16        TG0P     HD 4000 GPU, Proximity
81.000 C    Sensor 17        TG1D     NVidia GT 650, Diode
81.500 C    Sensor 18        TG1F     NVidia GT 650, prob. Cooling Fin
75.000 C    Sensor 19        TG1d     NVidia GT 650, Proximity

I don't know what you were doing, but you might want to either increase your fan speed by hand, or install macfanctld ... just a thought ;-)

---

### Post by MikeBraxner on 2013-03-02
longint: You should not specify both DPI and DisplaySize, as they overwrite each other.

Yeah, sorry about that, the displaySize was supposed to be commented out ... man, this really isn't my week.

Nevertheless, adjusting the DPI option resolves the 'tiny fonts and icons' issue.

---

### Post by longint on 2013-03-02
Heat is mainly due to running nvidia. Any advice how to install macfanctld correctly? Just did a manual build from git as the Mactel PPA seems not to support 13.04.

And do you switch off nvidia from within Linux? How?

---

### Post by MikeBraxner on 2013-03-02
longint --- Switching off the NVidia GPU is done via [vga_switcheroo]("https://help.ubuntu.com/community/HybridGraphics"), so ensure that your /etc/fstab contains ...
```
# /debug --- required for vgaswitcheroo
none                    /sys/kernel/debug debugfs defaults 0 0
```
... and mind that the vga_switcheroo mechanism will only be active when the kernel is booted with either the "modeset=1" kernel option *set*, and/or the "nomodeset" option being *absent*.

Now boot into OS X and use an **OLD** version of Cody Krieger's gfxCardStatus (2.2.1 works for me) to force the Integrated GPU ... mind, you might have to boot OS X twice to get gfxCardStatus to work properly (i.e. respond to a GPU switch with an on-screen status information). Once you're back in Linux, three simple commands suffice ...
```
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

The first ensures that *both* GPU's are powered up. The second forces the integrated GPU to be used, and the third powers the NVidia OFF. You can (and should) cross-check, i.e. ...
```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0
2:DIS-Audio:+:Off:0000:01:00.1 
```

The integrated GPU is powered, while the discreet one is switched off. You might want to take a look at both, your sensor readings, as well as your power consumption (powertop). Once you're happy with this, you can automate the lot via /etc/rc.local ...
```
if [ -f /sys/kernel/debug/vgaswitcheroo/switch ]; then
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
fi
```


NB: As [ksatta1]("http://ubuntuforums.org/showthread.php?t=2006475&page=30") pointed out, you *might* find that for suspend to work properly, you have to switch the discreet back on *before* suspend, and OFF again *after* resume ... best to automate. 
```
#!/bin/sh
#
# location: /etc/pm/sleep.d/00_MBPr_Sleep
#


. "${PM_FUNCTIONS}"


PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

suspend_usercustom()
{
    # do nothing
    DISPLAY=:0.0 su nat -c "echo ON > /sys/kernel/debug/vgaswitcheroo/switch"
}


resume_usercustom()
{
    export DISPLAY=:0.0
    DISPLAY=:0.0 su nat -c "echo ON > /sys/kernel/debug/vgaswitcheroo/switch"
    DISPLAY=:0.0 su nat -c "echo IGD > /sys/kernel/debug/vgaswitcheroo/switch"
    DISPLAY=:0.0 su nat -c "echo OFF > /sys/kernel/debug/vgaswitcheroo/switch"
}


case $1 in
    suspend|hibernate) suspend_usercustom & ;;
    resume|thaw)       resume_usercustom  & ;;
    *) exit $NA ;; 
esac


exit 0  


# suspend   system state saved   to   RAM
# resume    system state resumed from RAM
# hibernate system state saved   to   disk
# thaw      system state resumed from disk

```

... just remember to adjust to your user id, and add whatever else you want the system to handle before/after suspend/hibernate.


macfanctld ... 
With your sensors already working, it should require no more than a simple configuration file, /etc/macfanctld.conf. Mine looks currently like this ...
```
# Config file for macfanctl daemon
#
# Note: 0 < temp_X_floor < temp_X_ceiling
#       0 < fan_min < 6200       


fan_min: 2000


temp_avg_floor: 45
temp_avg_ceiling: 50


temp_TC0P_floor: 45
temp_TC0P_ceiling: 52


temp_TG0P_floor: 50
temp_TG0P_ceiling: 58


# Add sensors to be excluded here, separated by space, i.e.
# exclude: 1 7
# will disable reading of sensors temp1_input and temp7_input.


exclude: 13 17 18 19 25 32 33 34 35


# log_level values:
#   0: Startup / Exit logging only
#   1: Basic temp / fan logging
#   2: Log all sensors  


log_level: 0

```

Since macfanctld uses in part summarized averages to control the fans (see man macfanctld) you should exclude all sensors that report bogus readings. For a quick peek, try 'macfanctld -f', note the malefactors in the sensor lot, and amend the 'exclude' line accordingly. If you don't like my trigger values for the fans, set your own. Then a final "service macfanctld start" and you should be set.

If you want to keep an eye on the temps and fans' rpm for a while, set "log_level : 1", stop and restart macfanctld, and periodically check /var/log/macfanctld.log until you're satisfied, then reset the log_level.

---

### Post by longint on 2013-03-02
Sorry, I'm not going to reinstall OSX just to be able to switch to intel. Thatsway I asked if there is a way to do so from within Linux!?

Will try your macfanctld.conf, Thx. The default ones made my fans spin like crazy so I stopped it.

---

### Post by MikeBraxner on 2013-03-02
There's no need to plunk OS X onto the SSD, mate. Just slap it onto an external usb3 drive or stick, and your fine. Takes all of 20 min, and you more than double your exp. time on battery :)

PS: Just to clarify, once the GPU has been forced to integrated only, you don't boot OS X again, unless you want to switch to NVidia use again ... or decide that you prefer OS X after all ...

---

### Post by longint on 2013-03-02
So, how do I get the iso or something to install OSX? Having a quick look to apple.com I just happen to find updates and .dmg and the need to specify some ID...

---

### Post by MikeBraxner on 2013-03-02
You could of course use your 'rescue partition' ... OK, so you shredded that one, then have a look at these [install drive]("http://reviews.cnet.com/8301-13727_7-57479690-263/how-to-create-an-os-x-10.8-mountain-lion-install-drive/") / [i]("https://discussions.apple.com/thread/4147566?start=0&tstart=0")[nstaller]("https://discussions.apple.com/thread/4147566?start=0&tstart=0") / [USB installer]("http://gigaom.com/2012/07/26/quick-tip-create-a-usb-installer-for-mountain-lion/").

---

### Post by longint on 2013-03-02
Thx Mike, will have a look once I'm really fed up with the high power consumption. Having the possibility to switch between them would be really nice as it is said the HDMI output is not working running the Intel stuff!?

BTW: What is your xorg.conf looking alike running the Intel card? Did you specify some kernel options?

---

### Post by raccoonone on 2013-03-02
> **MikeBraxner said:**
> raccoonone --- I saw that you still list the 'fonts too small' as an issue on your blog. May I suggest adding a DPI setting to your /etc/xorg.conf ...
```
Section "Monitor" 
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Apple Color LCD"
    HorizSync       30.0 - 111.1
    VertRefresh     60.0
     **Option         "DPI" "128 x 128"**
     DisplaySize     333 207
    Option         "DPMS"
EndSection
```

The 15" Retina has a natural ~120 DPI, so a setting from 125-135 DPI enlarges everything (fonts, icons, warts and all) effortlessly, as long as your graphics driver respects the X-settings ... which the NVidia's do.

Just tried that and it didn't seem to work for me. Are you using the proprietary driver or the nouveau driver?

---

### Post by MikeBraxner on 2013-03-03
It worked fine for me using the Proprietary Drivers (304, 310) under KDE 4.9, Kubuntu 12.04 and 12.10.

PS: Please mind longint's comments that DPI and DisplaySize should not be used together. My screw-up ... please remove the DisplaySize and try again, since you're otherwise left with about the same DPI being used.

---

### Post by MikeBraxner on 2013-03-03
longint --- With the newer kernels (3.7.5, 3.8.x) I don't need to set any additional kernel options. 

My xorg.conf is all but default generated, selecting the fbdev. 
```
Section "Monitor"    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Apple Color LCD"
    HorizSync       30.0 - 111.1
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "fbdev"
    Option         "UseDPLib" "off"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
EndSection
```

The only non-standard bit is a configuration file to switch the buttons for my bluetooth mouse on connect ...
```
# Specialised Configuration File for a Microsoft Bluetooth Notebook Mouse 5000
# 
# xinput set-button-map "Microsoft Bluetooth Notebook Mouse 5000" 1 1 3 4 5 6 7 8 9 10 11 12
# works, BUT requires the bluetooth mouse to be connected and recognised by X.
# Since this fails on every boot and resume, since the bluetooth connection is established too late,
# this is the clean way to go.
#
# Location: /etc/X11/BluetoothMouse.conf


Section "InputClass"
    Identifier        "Microsoft Bluetooth Notebook Mouse 5000"
    MatchProduct        "Microsoft Bluetooth Notebook Mouse 5000"
    MatchIsPointer        "on"
    Option "ButtonMapping"   "1 1 3 4 5 6 7 8 9 10 11 12"
EndSection

```

---

### Post by raccoonone on 2013-03-03
> **MikeBraxner said:**
> It worked fine for me using the Proprietary Drivers (304, 310) under KDE 4.9, Kubuntu 12.04 and 12.10.

PS: Please mind longint's comments that DPI and DisplaySize should not be used together. My screw-up ... please remove the DisplaySize and try again, since you're otherwise left with about the same DPI being used.

Strange, I wonder if this is broken in 13.04. I tried it with just DPI, just DisplaySize, and both, and none of them worked. The odd thing is, if I check my Xorg log I see this line, so it certainly seems to be read by the driver:

```
[     7.367] (**) NVIDIA(0): DPI set to (192, 192); computed from "DPI" X config option
```

---

### Post by MikeBraxner on 2013-03-03
This might be daft to ask, but which DE are you using? KDE, Unity, Gnome, ...? I don't know if there are any significant differences that might otherwise impinge on the use of the DPI option. Anyhow, just to cover all bases, here's the full /etc/xorg.conf I use with NVidia's proprietary drivers ...
```
Section "ServerLayout"    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection


Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Apple Color LCD"
    HorizSync       30.0 - 111.1
    VertRefresh     60.0
    Option         "DPI" "128 x 128"
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 650M"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "UseDPLib" "off"
    Option         "NoLogo" "true"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by raccoonone on 2013-03-03
> **MikeBraxner said:**
> This might be daft to ask, but which DE are you using? KDE, Unity, Gnome, ...? I don't know if there are any significant differences that might otherwise impinge on the use of the DPI option. Anyhow, just to cover all bases, here's the full /etc/xorg.conf I use with NVidia's proprietary drivers ...

I'm using Unity with the 13.04 daily. Tried a couple other combinations of Xorg options, but to no avail. Here's the entire xorg.conf I'm using:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 304.64  (buildmeister@swio-display-x86-rhel47-12)  Tue Oct 30 12:04:46 PDT 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Apple Color LCD"
    HorizSync       30.0 - 111.1
    VertRefresh     60.0
    Option         "DPMS"
    Option         "DPI" "192x192"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
    Option         "UseDPLib" "off"
EndSection
```

---

### Post by MikeBraxner on 2013-03-03
racoonone ... Could you please try shifting the DPI setting from your Monitor Section to the NVidia specific **Device Section**, i.e. ...
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Apple Color LCD"
    HorizSync       30.0 - 111.1
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    [B]Option         "UseEdidDpi" "False"
    Option         "DPI" "130 x 130"[/B]
EndSection

```

If this doesn't work, then I'd guess it's either a Unity, or 13.04 issue. So if someone running KDE under 13.04 could try to resolve this question, please?

PS: "DPI" "192 x 192" ... I'd go easy on those values for a first try, else you might not be able to see anything but the top left corner of Unity's Menubar ;-)

---

### Post by raccoonone on 2013-03-03
> **MikeBraxner said:**
> racoonone ... Could you please try shifting the DPI setting from your Monitor Section to the NVidia specific **Device Section**, i.e. ...


If this doesn't work, then I'd guess it's either a Unity, or 13.04 issue. So if someone running KDE under 13.04 could try to resolve this question, please?

PS: "DPI" "192 x 192" ... I'd go easy on those values for a first try, else you might not be able to see anything but the top left corner of Unity's Menubar ;-)

Nope, that didn't work either :/ May have to try KDE, if my googling doesn't turn up something else

---

### Post by MikeBraxner on 2013-03-03
Some more options to try ...

1. Calculate a 'desired' DisplaySize using (Screen DPI/DPI-Desired)*25.4, i.e. ...
[INDENT]    (2880/130)*25.4 = 562.71
    (1800/130)*25.4 = 351.69
and use these as the setting in xorg.conf, i.e.[/INDENT]
[INDENT]DisplaySize     563 352

[/INDENT]
2. Check if gdm (or whatever you use) overrides the xorg.conf DPI settings, or offers an option to do so.

3. Add defaultserverargs="-dpi 96" to your /usr/bin/startx

4. Preset the DPI in ~/.Xdefaults or ~/.Xresources via "Xft.dpi:     130"

5. Try using xrandr --dpi 118, and if it works, use it in an apropriate start-up script.

---

### Post by raccoonone on 2013-03-03
> **MikeBraxner said:**
> Some more options to try ...

1. Calculate a 'desired' DisplaySize using (Screen DPI/DPI-Desired)*25.4, i.e. ...
[INDENT]    (2880/130)*25.4 = 562.71
    (1800/130)*25.4 = 351.69
and use these as the setting in xorg.conf, i.e.[/INDENT]
[INDENT]DisplaySize     563 352

[/INDENT]
2. Check if gdm (or whatever you use) overrides the xorg.conf DPI settings, or offers an option to do so.

3. Add defaultserverargs="-dpi 96" to your /usr/bin/startx

4. Preset the DPI in ~/.Xdefaults or ~/.Xresources via "Xft.dpi:     130"

5. Try using xrandr --dpi 118, and if it works, use it in an apropriate start-up script.

I found one possible clue, although no solution yet. I tried everything you suggested, and it seems that the dpi is getting set correctly. At least as reported by xdpyinfo. However, Xft.dpi is stuck at 96, as reported by xrdb -query.

I tried creating both ~/.Xdefaults and ~/.Xresources and setting Xft.dpi: 128, and also setting "xft-dpi" in /etc/lightdm/lightdm.conf. Neither of those had any effect though. Other changes in lightdm.conf did have an effect: I'm able to set the dpi via "xserver-command=X -dpi 128"

Any thoughts on what might be overriding the setting of Xft.dpi?

---

### Post by sauferkel on 2013-03-04
How does it look with the changed dpi value? 

Would someone mind uploading a screenshot?

Sounds great.. :)

---

### Post by MikeBraxner on 2013-03-04
>  it seems that the dpi is getting set correctly. At least as reported by xdpyinfo.
Yeah, I don't get this ... If it has been **SET**, it has been **SET**. This is not a font dpi preset we're talking about, which Unity and/or Gnome might well ignore, but the *X Server* one.

> However, Xft.dpi is stuck at 96, as reported by xrdb -query. ... Any thoughts on what might be overriding the setting of Xft.dpi
Now ***this*** is the font dpi, and you should be able to change that anytime with UbuntuTweak or the like, though there enough prog's around which will *blithely* ignore this. As far as I remember, there were actually some bug reports wrt Unity ignoring this, but I'm not entirely sure.

> I'm able to set the dpi via "xserver-command=X -dpi 128"
OK. So the cli option at least makes it through, might not be the most elegant, but ... [IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG]

More importantly, if you *can* push an altered dpi setting through via cli, then I'd say the problem *DOES* apparently lie with Unity, and *not* with 13.04.

Incidentally, I forgot to confirm earlier that---at least under KDE---the forced DisplaySize setting in xorg.conf also works for the **fbdev** driver, i.e. it will work for everyone who switched of their GT 650.

---

### Post by MikeBraxner on 2013-03-04
> **longint said:**
> 3finger-midle click in Unity, one of the annoying things left...

While Unity is known to hijack the gesture-recognition to some degree (3&4 finger gestures), you should be able to to influence it via synclient, i.e. switch of recognition for 3 finger tap via ...
```

synclient TapButton3=0 
synclient ClickFinger3=0 

```
... or [disable it completely]("http://askubuntu.com/questions/57586/how-can-i-disable-arbitrary-default-multitouch-gestures-in-unity/90383#90383"). You might also want to have a look at [TouchEgg]("https://code.google.com/p/touchegg/wiki/Main").

---

### Post by raccoonone on 2013-03-04
> **MikeBraxner said:**
> 


OK. So the cli option at least makes it through, might not be the most elegant, but ... [IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG]

More importantly, if you *can* push an altered dpi setting through via cli, then I'd say the problem *DOES* apparently lie with Unity, and *not* with 13.04.

Incidentally, I forgot to confirm earlier that---at least under KDE---the forced DisplaySize setting in xorg.conf also works for the **fbdev** driver, i.e. it will work for everyone who switched of their GT 650.

I mean that I can set it via cli, but the value is still ignored :/ (the display doesn't change, just the value reported by xdpyinfo).

About the Xft.dpi, ya that doesn't seem like it would effect anything, but that's the only clue I've been able to find so far.

---

### Post by MikeBraxner on 2013-03-04
Well, that's me out of rope then. I know it works under KDE (12.04, as well as 12.10) with the NVidia proprietary drivers (304, 310), as well as with the fbdev. Maybe someone out there using gnome, gnome 3, bee::shell, ... could give this a try and provide some feedback? Would be nice to know what we have to work with to help narrow down the possible gaffs, and maybe find a solution.

---

### Post by MikeBraxner on 2013-03-04
sauferkel --- Here's a quick desktop snapshot, running on fbdev, at 128 dpi, forced in /etc/xorg.conf within the Monitor Section via "DisplaySize     571.5 357.2"

edit: 2nd try ... since a full-scale screenshot exceeds the upload limit, this is now a *cropped* version of a 1-to-1 screenshot. Settings used are pretty much KDE standard throughout, excepts that the BBC site in chromium is shown at 125%.

---

### Post by Sc0rian on 2013-03-04
has anyone got the sd card working?

it detects but wont work.

---

### Post by longint on 2013-03-05
When runnung Fedora18 I had the SD Card working with a single SD Card, but any other card also gave errors. I've that card not available anymore and did not find any card so far working with Ubuntu. One of the bigger issues left with Linux on MBPr...

---

### Post by MikeBraxner on 2013-03-05
racoonone ... it seems that 'X DPI settings is being ignored' on a Gnome base, and thus Unity, has been an old hat for YEARS! The developers' position appears two-fold, i.e. ...


[LIST=1]
[*]Too many hardware units report 'wrong' information to/through X, which should thus be ignored for 'the good of the user' ... a perfect symbioses of MS and Apple: It really *IS* a feature, and anyway 'poor, dim-witted users' cannot be exposed something as dangerous as an *option* to adjust an X-DPI setting.
[*]This is part of a 'work-around' for the introduction of something 'wonderful and new', and just as there were some 'minor issues' with the introduction of [take your pick], people will get used to it. Anyway, 'only a handful of old programs' still honor X-Settings, stuff 'like xterm and maybe emacs' ... or KDE, I guess.
[/LIST]

In discussions ranging at least 2006-13 the same problem has been flagged, discussed, and had bug reports issued over and again ... in at least one case the bug report was *sequentially* graded as fixed, fixed in release, unconfirmed, solved, invalid, fixed in release, invalid, solved, confirmed, unconfirmed, and critical. More informed discussions clarify that the Gnome base does indeed 'use the X server DPI value. It does not override it', obviously implying that it 'does not have a DPI setting anymore'.

Anyway, I dug up **five claims** of resolving the issue (the last one being my own) ...


[LIST=1]
[*]The DPI can be set, but only on a *per session* basis via "[COLOR=#000000]xrandr --dpi 130".[/COLOR]
[*]The DPI value can be set, but only via a *direct* call a la "startx --dpi 130", i.e. options don't make it through.
[*]You cannot set the DPI value anymore, you can *only* adjust the *text-scaling* factor /org/gnome/desktop/interface/text-scaling-factor, which should be calculated as (scale factor = monitor dpi / 96), and set through dconf, or "gsettings set org.gnome.desktop.interface text-scaling-factor [scale factor]".
[*]The problem lies with 'display-properties', but *can* be resolved by removing '~/.gnome2/monitor.xml'.
[*]"Welcome to KDE".
[/LIST]
&#8203;
If none of these work for you, there's always Wayland ... nope, hang on ... Ries just culled that one for Ubuntu/Ubuntu Next in favor of the 'wonderful and new Mir' (eta 2014), so that your desktop can easier resemble a phone or TV.

---

### Post by raccoonone on 2013-03-05
> **MikeBraxner said:**
> racoonone ... it seems that 'X DPI settings is being ignored' on a Gnome base, and thus Unity, has been an old hat for YEARS! The developers' position appears two-fold, i.e. ...


[LIST=1]
[*]Too many hardware units report 'wrong' information to/through X, which should thus be ignored for 'the good of the user' ... a perfect symbioses of MS and Apple: It really *IS* a feature, and anyway 'poor, dim-witted users' cannot be exposed something as dangerous as an *option* to adjust an X-DPI setting.
[*]This is part of a 'work-around' for the introduction of something 'wonderful and new', and just as there were some 'minor issues' with the introduction of [take your pick], people will get used to it. Anyway, 'only a handful of old programs' still honor X-Settings, stuff 'like xterm and maybe emacs' ... or KDE, I guess.
[/LIST]

In discussions ranging at least 2006-13 the same problem has been flagged, discussed, and had bug reports issued over and again ... in at least one case the bug report was *sequentially* graded as fixed, fixed in release, unconfirmed, solved, invalid, fixed in release, invalid, solved, confirmed, unconfirmed, and critical. More informed discussions clarify that the Gnome base does indeed 'use the X server DPI value. It does not override it', obviously implying that it 'does not have a DPI setting anymore'.

Anyway, I dug up **five claims** of resolving the issue (the last one being my own) ...


[LIST=1]
[*]The DPI can be set, but only on a *per session* basis via "[COLOR=#000000]xrandr --dpi 130".[/COLOR]
[*]The DPI value can be set, but only via a *direct* call a la "startx --dpi 130", i.e. options don't make it through.
[*]You cannot set the DPI value anymore, you can *only* adjust the *text-scaling* factor /org/gnome/desktop/interface/text-scaling-factor, which should be calculated as (scale factor = monitor dpi / 96), and set through dconf, or "gsettings set org.gnome.desktop.interface text-scaling-factor [scale factor]".
[*]The problem lies with 'display-properties', but *can* be resolved by removing '~/.gnome2/monitor.xml'.
[*]"Welcome to KDE".
[/LIST]
&#8203;
If none of these work for you, there's always Wayland ... nope, hang on ... Ries just culled that one for Ubuntu/Ubuntu Next in favor of the 'wonderful and new Mir' (eta 2014), so that your desktop can easier resemble a phone or TV.


Wow, thanks for all the research!! The latest kernel (3.8.0-10) in raring just broken my install, so I'm waiting for that to be fixed :/

I've tried most of those already, and the text-scaling does work for text, unfortunately it's only for text and only some text. Chrome, for example, seems to ignore it. I haven't tried the .gnome2/monitor.xml thing, so I'll try that once this kernel issue is fixed. Thanks again!

---

### Post by Sc0rian on 2013-03-06
it broke it?

How? What does it say, have you submitted a bug?

---

### Post by raccoonone on 2013-03-06
It hangs shortly after booting the kernel from grub, with a purple screen. Seems a number of people are effected by it. There's a thread about it here: [http://ubuntuforums.org/showthread.php?t=2122586&p=12543190](http://ubuntuforums.org/showthread.php?t=2122586&p=12543190)

---

### Post by longint on 2013-03-06
3.8.0.11 worls fine over here.

Why do you use grub btw? you should switch to rEFInd,  I find it sooo much easier and smarter, no bootloader anymore...

---

### Post by Sc0rian on 2013-03-06
does anyone else have a laggy brightness control?

On one of the recent updates the screen brightness control has became extremely laggy. When adjusting with the FN keys, it will lag out the laptop... Not too sure on how to fix it or diagnosis it.

---

### Post by raccoonone on 2013-03-06
> **longint said:**
> 3.8.0.11 worls fine over here.

Why do you use grub btw? you should switch to rEFInd,  I find it sooo much easier and smarter, no bootloader anymore...

Huh, interesting. I'll have to look into it a bit more then.

How does booting without grub work, where do you set kernel options and such? Never heard of booting rEFInd straight to Ubuntu, without grub in between

---

### Post by longint on 2013-03-07
Yeah, just read the rEFInd notes on their homepage and ignore the part saying you should not install from within Linux (but OSX, I did the manual installation in Linux). There is a refind_linux.conf where you can define your kernel options to boot. It only seems to accept FAT (and HFS) partitions to scan for bootable kernels though...

---

### Post by Sc0rian on 2013-03-13
I'm on 3.8.0.12 now.

I have one bug that has came about, maybe from a package update? If I have screen resolution set to anything other than the max, the screen will half load with lines and all messed up. I'm able to just work it out and restore it to max res and its okay. I can then set any other res and it works, something breaks it on bootup?

[http://www.lwfinger.com/b43-firmware/](http://www.lwfinger.com/b43-firmware/)

I noticed on this site there is a newer firmware broadcom-wl-5.10.144.3.tar.bz2, it worked fine on 3.8.0.9,, but it wouldn't work on 3.8.0.12 I had to load in broadcom-wl-5.100.138.tar.bz2 and personally was experience wifi drops on this one.

---

### Post by longint on 2013-03-13
Do yourself a favour and bin the b43 stuff. Switch to the bcmwl drivers - much more stable and performant.

---

### Post by MikeBraxner on 2013-03-13
I agree that bcmwl is a good deal more stable, and provides better performance, but I keep getting the impression that it is rather miserable regarding power-management. More specifically, it seems that it's using between 0.6 and 1.1 W more than the b43 driver ... could anyone else confirm this, please?

---

### Post by longint on 2013-03-13
Interesting Mike, never thought about this. But after toggling the Powermanagement state for this device in powertop I got 3W less!?
Anyway, I'm not that unhappy regarding the battery runtime, even running nvidia drivers. I get several more hours than my Lenove T410 had before...

---

### Post by Sc0rian on 2013-03-14
latest update broke wifi, installed bcmwl which fixed it.

I have some odd issues on my MBPr 13" which I cannot work out.

1. I cannot select 1920 screen res anymore i get lines
2. If I have a mini-dp cable connected for a external monitor, when I login it will go black. Then I unplug it and I normally get lines(same as selecting 1920) or just wont work and I have to reboot. I have to make sure I'm logged in before I plug it in. 
3. I get random 3 or so second hangs for no reason, and if I reboot sometimes it goes away. 
4. Logitech unify device does not work from boot!!!! I have to unplug and plug it back in 5 times or more, so annoying.
5. bluetooth lags big time when wifi traffic is high. if i do a speedtest or something, the bluetooth will break and lag out. Youtube videos are pointless. If running Ethernet i have no problems. 
6. I notice on the external monitor I get some flickering. I cannot see it on a white background, but I just saw a image with lines on it, which caused the external monitor to flicker loads, but not the laptop. :/

---

### Post by Sc0rian on 2013-03-18
wireless drivers are a lot better on the bcmwl drivers although I agree with others, it does now eat my battery.

---

### Post by longint on 2013-03-25
Using 13.04 on a MBPr:
- suspend is broken again (for about a week now)
- DHCP/Name resolution is broken (for about a week)
- kernel is still 3.8.0 while 3.8.4 is out for some time now (not to mention 3.8.1..3)

General:
- many other software packages not up to date, no way to get new software in using an official way 
- way too much stuff where Ubuntu means to patronize the user 

Sorry, but I'll leave Ubuntu soon, Arch on a USB stick is doing quite well...

---

### Post by ksatta1 on 2013-03-25
I created a thread for a "GPU switching"-campaign. It seems the problem is with nVidia's proprietary drivers. More info:
[http://ubuntuforums.org/showthread.php?t=2129158](http://ubuntuforums.org/showthread.php?t=2129158)

---

### Post by rmorr on 2013-03-25
Regarding using rEFINd as the main boot loader instead of grub:

If follow his directions on this page to boot from the kernel (under the test configuration heading because I have not had luck booting from a kernel on my root partition & have things working well enough that I don't want to reinstall with a new partition scheme):
[http://www.rodsbooks.com/refind/linux.html](http://www.rodsbooks.com/refind/linux.html)

The main thing with the Retina is to make sure you get your arguments right in the refind_linux.conf file to avoid issues with the video drivers. I follow some directions provided on this guide for the NVIDIA drivers because I've gotten the most stable performance this way:
[http://cberner.com/2013/03/01/installing-ubuntu-13-04-on-macbook-pro-retina/](http://cberner.com/2013/03/01/installing-ubuntu-13-04-on-macbook-pro-retina/)

The only minor annoyance is copying the kernel and image files to the EFI partition every time they're upgraded. Otherwise everything runs without too many hitches.

---

### Post by longint on 2013-03-26
Just to make sure: You skipped grub completely? (The guide you're refering to is doing some complicated things using grub.)

Why do you copy the kernels to the EFI partition? In my case they are installed automatically to /boot on my ext4 root-partition on dev/sda5 where all of them get recognized by rEFInd automagically, no need for manual interaction.
For some reason I still need my sda1 formatted to vfat. It contains the efi stuff and is mounted to /boot/efi - I'm wondering if there is really a need for this. You can at least skip the mounting for sure, but booting EFI/rEFInd from /dev/sda5 containing my ext4 root partition directly seems not to work for some reason (yet).

---

### Post by rmorr on 2013-03-26
> **longint said:**
> Just to make sure: You skipped grub completely? (The guide you're refering to is doing some complicated things using grub.)

Why do you copy the kernels to the EFI partition? In my case they are installed automatically to /boot on my ext4 root-partition on dev/sda5 where all of them get recognized by rEFInd automagically, no need for manual interaction.
For some reason I still need my sda1 formatted to vfat. It contains the efi stuff and is mounted to /boot/efi - I'm wondering if there is really a need for this. You can at least skip the mounting for sure, but booting EFI/rEFInd from /dev/sda5 containing my ext4 root partition directly seems not to work for some reason (yet).

Yes, no grub. I forced the installer to ignore the normal setup. I'm only referring to the part of the rEFInd guide that talks about copying your kernel to the EFI and booting from there. My sda1 partition is formatted in the way that OS X normally does it when you first set up a GPT scheme and the reason I use the copying the kernel method is that, like you, I experience problems trying to boot directly from the ubuntu root partition even with a refind_linux.conf in the /boot directory.

I haven't invested a lot of time trying to see if I can fix this yet because I went through so many re-installs trying to force Windows 8 to EFI boot without issues (ended up going back and doing my own hybrid MBR scheme with gpt fdisk) that once I got a reasonably snappy triple boot working I decided to leave it be for now so I can get reacquainted with linux.

---

### Post by sauferkel on 2013-03-27
Same for me. 
Refind shows a lot of entries comming from the ubuntu /root partition (sda7 in my case) , but i am not able to boot them.
Had to copy it to sda1, just like you. 
Also using the osx formatting, no problems with that.

How is windows booting from efi? Was it the /boot folder on the efi partition? ( /dev/sda1/efi/EFI/Boot) ? I erased it , but i still can boot windows....

---

### Post by longint on 2013-03-27
Which kernels are you using (not able to boot directly from non sda1)?

---

### Post by sauferkel on 2013-03-27
Wait, i guess i have to correct myself. I just tried booting again from the sda7 (root partition) and it was not working, but i saw that the parameters, i set when booting from sda1, are not set there.

Does anybody know how to do this? 

I am using 
"Boot using standard options" "root=UUID=***myUUID*** ro quite nouveau.modeset=1 i915.lvds_use_ssc=0 i915.lvds_channel_mode=2 i915.modeset=1 splash $vt_handoff"
in the refind_linux.conf file....

I am booting the kernel 3.8.0.14 i guess. The latest one (3 days ago)

---

### Post by rmorr on 2013-03-27
> **sauferkel said:**
> How is windows booting from efi? Was it the /boot folder on the efi partition? ( /dev/sda1/efi/EFI/Boot) ? I erased it , but i still can boot windows....

I stopped EFI booting Windows & went back to the BIOS emulation/bootcamp method. You can get EFI booting to work, but the intel drivers cause blackscreen on boot so you end up having to remove those during the install process and and use some generic microsoft ones ... but you lose onboard sound. After installing the latest NVIDIA drivers I had sound over USB & HDMI but startup was incredibly slow. I decided it wasn't worth it yet.

---

### Post by longint on 2013-03-28
> **sauferkel said:**
> 
I am booting the kernel 3.8.0.14 i guess. The latest one (3 days ago)


OK, just to make sure it is 3.8 - as to my knowledge older kernels are not be bootable directly by EFI.

---

### Post by sauferkel on 2013-03-31
I got my system booting directly from the root partition. For me the problem was the missing boot parameters , to make all this graphic stuff working. I found the solution somewhere here: 
[http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/)

Just copy the refind_linux.conf file (covering the boot parameters) into your boot folder ;).

---

### Post by sauferkel on 2013-03-31
Hey guys.
wanted to upgrade right now ( kernel 3.8.0.15 is out ) but if i run apt-get upgrade he says "kept back..." for several updates. However, if i run dist-upgrade he wants to install grub-pc and -common and stuff like this.

Do you know a way to update without installing grub?

---

### Post by Sc0rian on 2013-04-05
on my 13" mbpr if I select 1920x1050 I get lines through the screen when logging in. :(. Does anyone else have this or a way to fix it?

It only happens at the res, and only when logging in.

---

### Post by bfroemel on 2013-04-08
Better skip efi/firmeware updates for now; concerns the 15'' model.

[https://plus.google.com/111049168280159033135/posts/WCpFxFLJ5sV](https://plus.google.com/111049168280159033135/posts/WCpFxFLJ5sV)
[quote="Greg Kroah-Hartman"]
Argh, I seem to have hosed my Macbook Pro retina by doing the latest EFI update that Apple pushed to it.  No more graphics modes from Arch, or the openSUSE installer. [...]
[/quote]

---

### Post by Sc0rian on 2013-04-08
nice find bfroemel. I follow him but missed that post

---

### Post by sauferkel on 2013-04-09
I just found this, sounds pretty nice. 
[h=1][[SIZE=3]NVIDIA Has Major New Linux Driver: Optimus, RandR 1.4[/SIZE]]("http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE")[/h]

Any comment on it?

---

### Post by Umbra Diaboli on 2013-04-09
Raring Beta 2 is out [http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

Has anyone tried it on the rMBP? 

Does it come with the wireless drivers by default? Or we still have to install the flaky broadcom drivers (this is the main reason I don't use Ubuntu on my retina, the connection is lost every 10-15 min).

Also, how easy is it to install the current nvidia drivers on beta 2? Any problems? Suggestions?

Thanks!!

---

### Post by chenxiaolong on 2013-04-09
It seems that there's no need to boot into OS X to set the Intel card as default anymore. Just run this in the EFI shell (or save it in startup.nsh) before booting:

```
echo Switch select
mm 7C2 1 ;IO :1
stall 100000
mm 7D4 1 ;IO :28

echo Switch display 
mm 7C2 1 ;IO :2
stall 100000
mm 7D4 1 ;IO :10

echo Switch DDC
0x750 0 mm 7C2 1 ;IO :2
stall 100000
mm 7D4 1 ;IO :40

echo Power down discrete graphics
mm 7C2 1 ;IO :1
stall 100000
mm 7D4 1 ;IO :50

mm 7C2 1 ;IO :0
stall 100000
mm 7D4 1 ;IO :50
```

Source: [http://forum.techinferno.com/diy-e-gpu-projects/2367-macbook-pro-retina-15-gtx-560-ti-%40-th05.html](http://forum.techinferno.com/diy-e-gpu-projects/2367-macbook-pro-retina-15-gtx-560-ti-%40-th05.html)

(Note: I don't own a RMBP, so I can't test this)

EDIT: Those commands are based on [https://github.com/ah-](https://github.com/ah-) (which is a Linux kernel module). It should be possible to enable the iGPU in Linux.

EDIT2: [https://www.youtube.com/watch?v=0FYP3nMyxcQ](https://www.youtube.com/watch?v=0FYP3nMyxcQ)

EDIT3: Nevermind, this was already covered earlier in this thread. It won't work.

---

### Post by gschwind on 2013-04-13
Hello,

For those which are very experienced linux user I send the following mail:

[http://permalink.gmane.org/gmane.linux.drivers.platform.x86.devel/4189](http://permalink.gmane.org/gmane.linux.drivers.platform.x86.devel/4189)

I'm able to select intel or nvidia at boot time, without the help of MacOS.

As as said it's a very complicated setup and it need another computer to be setup without trouble, so don't try it without knowing what you are doing. As usual the use of this information are at your own risk.

But it show that there is room for improvement in the support of mac book pro 15" on linux.

I currently run this setup on kernel 3.8.7. I choosed to use nvidia proprietary driver instead of nouveau when I boot with nvidia, when I boot on intel I use nouveau driver to turn off nvidia video card.

Have fun

---

### Post by ksatta1 on 2013-04-14
I had forgotten about your post, I think I read it a while back :) I'll test it one day, and maybe also post scripts for everything etc :) Also, nice job.

---

### Post by ksatta1 on 2013-04-14
With Xubuntu 13.04 and nvidia driver 310.44 my MacBook is idling at 13W, without WiFi. With Xubuntu 12.10 and nouveau driver I can't get below 24W. Both with the Nvidia display adapter in use. Still have to do some testing, but it looks like this is usable with Nvidia now, and I have external outputs working etc :) I haven't updated to the new Apple firmware, not sure what's going on, I'm suspecting the new Nvidia driver.

You can check power consumption with "sudo powertop".

---

### Post by sauferkel on 2013-04-15
Started a new thread covering the power consumption of this device. 
[URL="http://ubuntuforums.org/showthread.php?t=2135782"]
http://ubuntuforums.org/showthread.php?t=2135782[/URL]

---

### Post by lukeco11 on 2013-04-20
I am curious about what most people are doing about the resolution. Are folks running it at full res? with large fonts? Or at lower res back but less crisp? It seems to me that until there is better high resolution support we are stuck with small icons and strange GUI situations. Anyone have any tips or tricks that help with these issues?

---

### Post by sauferkel on 2013-04-20
Just can speak for me , but i'm using ubuntu with full res, text scaling on 1.3 (in gnome-tweak-tool) and the setting (in about:config) layout.css.devPixelsPerPx  set on 1,7 in Firefox......
quite nice and usable like this.

hope this helps...

but i've quite good eyes, and i want to have much place to work with so its still relativly small....

---

### Post by ksatta1 on 2013-04-21
I'm using XFCE (Xubuntu) at full res. More info: [http://ubuntuforums.org/showthread.php?t=2099498](http://ubuntuforums.org/showthread.php?t=2099498) .
Latest tweak was getting the checkboxes in webpages etc to the correct size (last post in the other thread).

The main problem is that almost all applications have hard-coded icon sizes etc. Some use SVG graphics (which could be scaled to any size), but for some reason pretty much all sizes are hard-coded. I think one day I might try to mod separate apps (Eclipse first in line :)), or even better, GTK itself. Although there's probably not much that can be done in GTK itself.

---

### Post by MikeBraxner on 2013-04-21
lukeco11 --- A while back (from [here]("http://ubuntuforums.org/showthread.php?t=2006475&p=12537546#post12537546") to [about here]("http://ubuntuforums.org/showthread.php?t=2006475&p=12543051#post12543051")) we had a brief discussion concerning a simple remedy that actually WORKS just fine under KDE, regardless of which GPU your using, i.e. adjusting the X-Server used DPI/Display Size setting. This way, you can freely scale your DE to whatever size you prefer, with decorations, fonts and icon sizes matching at all times, with minimum hassle. You might want to review those posts. 

However, be advised that this WILL NOT WORK on a Gnome basis, i.e. using Unity (and probably not for Gnome-3 either), since [these DEs forcibly ignore any such user-settings]("http://ubuntuforums.org/showthread.php?t=2006475&p=12543051#post12543051").

---

### Post by philcolbourn on 2013-04-21
> **MikeBraxner said:**
> longint --- Switching off the NVidia GPU is done via [vga_switcheroo]("https://help.ubuntu.com/community/HybridGraphics"), so ensure that your /etc/fstab contains ...
```
# /debug --- required for vgaswitcheroo
none                    /sys/kernel/debug debugfs defaults 0 0
```
... and mind that the vga_switcheroo mechanism will only be active when the kernel is booted with either the "modeset=1" kernel option *set*, and/or the "nomodeset" option being *absent*.

Now boot into OS X and use an **OLD** version of Cody Krieger's gfxCardStatus (2.2.1 works for me) to force the Integrated GPU ... mind, you might have to boot OS X twice to get gfxCardStatus to work properly (i.e. respond to a GPU switch with an on-screen status information). Once you're back in Linux, three simple commands suffice ...
```
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

The first ensures that *both* GPU's are powered up. The second forces the integrated GPU to be used, and the third powers the NVidia OFF. You can (and should) cross-check, i.e. ...
```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0
2:DIS-Audio:+:Off:0000:01:00.1 
```


I think the first ensures that the idle GPU is powered up (which is NVidia in your case) and the third powers the idle GPU off (which again is NVidia).

---

### Post by MikeBraxner on 2013-04-22
> **philcolbourn said:**
> I think the first ensures that the idle GPU is powered up (which is NVidia in your case) and the third powers the idle GPU off (which again is NVidia).

You're quite right, it seems ridiculously overdone, since the preceding OS X Boot should ensure that the NVidia is inactive anyhow. *Should* be ... I've been burnt too many times by assuming that something was the way it was *'supposed to be'*, instead of making sure it **was** the way I ***presumed*** it to be. 

More explicitly, I **don't *know*** that the NVidia is idle, i.e. that the integrated GPU is the active one, so the first call makes sure that **both** GPUs **are** powered up. The second call then ensures that the integrated GPU takes over, ***regardless*** of which GPU claimed that status incoming. The third call finally, as you pointed out, powers the NVidia down. The explained pattern thus simplifies the step further down the [original post]("http://ubuntuforums.org/showthread.php?t=2006475&p=12537799#post12537799"), suggesting to 'automate the lot via /etc/rc.local' for future boots ... when it is also **not** guaranteed that the NVidia will be compliantly inactive.

As I said, I've been burnt too many times to take something that is 'supposed to be' for granted ... an attitude that helps to avoid almost a third of all major screw-ups during the average day. ;-)

---

### Post by philcolbourn on 2013-04-23
But you still need gfxcardstatus 2.2.1 in OS-X to get this to work, right?

I think you also need nouveau kernel module loaded to get vgaswitcheroo/switch.

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by MikeBraxner on 2013-04-23
As far as I'm aware, yes, although the new NVidia driver ([COLOR=#000000][FONT=verdana]319.12 Beta) sounds promising, and [/FONT][/COLOR][chenxiaolong]("http://ubuntuforums.org/showthread.php?t=2006475&p=12596333#post12596333") pointed out a route I haven't tried myself.

---

### Post by gschwind on 2013-04-24
> **philcolbourn said:**
> But you still need gfxcardstatus 2.2.1 in OS-X to get this to work, right?


in fact, you don't need gfxcardstatus 2.2.1 see :
[http://ubuntuforums.org/showthread.php?t=2006475&page=37&p=12601823#post12601823](http://ubuntuforums.org/showthread.php?t=2006475&page=37&p=12601823#post12601823) 

Cold swith (switch at boot time), can be done with kernel 3.8 but it's tricky for commun user.

In most case you will need gfxcardstatus 2.2.1.

---

### Post by philcolbourn on 2013-04-24
I have read your post recently, and I agree that most people will not be able to use your method.

I found your post a little hard to follow and your modified apple-gmux.c file was not commented to indicate what changes you have made.

It would also be helpful to describe how to compile it and install it - or perhaps send your changes to seth forshee or Andreas Heider - unless you are one of these fine examples of humanity... (in which case I withdraw my comments and humbly beg forgiveness).

However, I appreciate you helping us stupid Apple Mac buyers to get their beautiful but proprietary machines to behave under Linux.

Thanks!

---

### Post by gschwind on 2013-04-24
> **philcolbourn said:**
> I have read your post recently, and I agree that most people will not be able to use your method.

I found your post a little hard to follow and your modified apple-gmux.c file was not commented to indicate what changes you have made.

It would also be helpful to describe how to compile it and install it - or perhaps send your changes to seth forshee or Andreas Heider - unless you are one of these fine examples of humanity... (in which case I withdraw my comments and humbly beg forgiveness).

However, I appreciate you helping us stupid Apple Mac buyers to get their beautiful but proprietary machines to behave under Linux.

Thanks!

I agree my post is quite complicated, but it's time consuming to explain everything in detail. with 3 drivers there is a lot of setup possible.

For apple-gmux.c, mains modification are : remove of kernel mutex (this make this executable quite unsafe with kernel), change kernel sleep by user space sleep, remove all unneeded feature (I only need gmux switch, brightness control is removed) and I put it in main() with unsafe args.

compilation of apple-gmux.c is quite usual:
gcc -o apple-gmux apple-gmux.c

I already send it to the related mailing list, I hope this is in the pipe for some switcheroo/gmux maintainers (airlie if you ear me). Maybe I will spend time to include this feature to kernel, currently switcheroo and gmux depend on the load of i915 and nouveau modules, that why I created this executable, which allow to switch without gmux driver loaded.

I'm an Apple hardware user, for PC only (I work with my macbook pro retina) so I am probably stupid as all other users.

Best regards

---

### Post by ksatta1 on 2013-04-24
I tested with your apple-gmux the other day, I got it to switch to intel only (following the instructions in your post). I had some problems getting it to switch to nvidia and don't have another puter right now at home to test over SSH :)
One thing that might confuse people is that the apple-gmux.c is a separate program. You don't have to change the kernel source, but you have to disable EFI framebuffer from "make menuconfig".

In any case nice work. I personally think I'm gonna give up with the nvidia on linux and stick to intel only, maybe I'll buy a USB display adapter to attach an external monitor LOL :)

If someone wants to play around with it, or even better, improve it, it goes something like this (these are additions to the original post):
- When compiling kernel: in menuconfig disable EFI framebuffer, it was somewhere ... / graphics foo / something.
- In /etc/default/grub: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash fbcon=map:01 text" (This disables X autostart, so it boots to text-only mode). fbcon makes half the terminals visible on nvidia, the other half on intel.
- After boot: modprobe foo, apple-gmux foo, etc (like in the original post).

---

### Post by gschwind on 2013-04-25
Thank you for your feed back.

I read my post again, and it seems that I forgot to mention that you need to blacklist nouveau, i915 and nvidia module, because the load order is important so :

in /etc/modprobe.d/blacklist.conf you can add : 

blacklist i915
blacklist nouveau
blacklist nvidia

I will spend time to create a more precise tutorial about case that I use daily.

---

### Post by ksatta1 on 2013-04-25
Ahh yes, I forgot to mention that too :) I might try to get it working with nvidia too one day, I'm sure it works, I was just testing it "blind", without another puter and ssh. The intel switching worked just by putting the commands in /etc/rc.local, then sleep 3s or something, then sudo /etc/init.d/lightdm start.

EDIT: and after getting the switching automated there would be just one hurdle: Switching between nvidia GLX and intel GLX. glx-alternative-nvidia package is currently broken in the repos, has been for a long time apparently (it's designed for just that). The only way I can get intel GLX working with nvidia proprietary installed, is to uninstall nvidia proprietary. Should also be possible by moving /lib/somefiles.

---

### Post by MikeBraxner on 2013-04-25
According to some chatter, the new NVidia Driver 319.12, together with randr1.4 and a 3.9 kernel, *might* (????) allow integrated Optimus support *without* Bumblebee ... and I have *such* a hard time believing that. Has anyone actually tried any of this???

---

### Post by gschwind on 2013-04-26
> **ksatta1 said:**
> Ahh yes, I forgot to mention that too :) I might try to get it working with nvidia too one day, I'm sure it works, I was just testing it "blind", without another puter and ssh. The intel switching worked just by putting the commands in /etc/rc.local, then sleep 3s or something, then sudo /etc/init.d/lightdm start.

EDIT: and after getting the switching automated there would be just one hurdle: Switching between nvidia GLX and intel GLX. glx-alternative-nvidia package is currently broken in the repos, has been for a long time apparently (it's designed for just that). The only way I can get intel GLX working with nvidia proprietary installed, is to uninstall nvidia proprietary. Should also be possible by moving /lib/somefiles.

do you switch xorg.conf depending on your select video cards?

for nvidia I have :

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    Option "UseDPLib" "no"
    BusID          "PCI:01:00:0"
    VendorName     "NVIDIA Corporation"
EndSection

for intel, I just leave an empty file.

---

### Post by gw280 on 2013-04-26
> **MikeBraxner said:**
> According to some chatter, the new NVidia Driver 319.12, together with randr1.4 and a 3.9 kernel, *might* (????) allow integrated Optimus support *without* Bumblebee ... and I have *such* a hard time believing that. Has anyone actually tried any of this???

The MBP doesn't use Optimus for its switchable graphics solution.

---

### Post by tehsu on 2013-04-27
I was having issues with fan control with high temperature where the fan wouldn't change RPM as the temp increased, installing and running macfanctld fixed this issue, if anyone is having issues with that, i installed that and applesmc-dkms on 13.04

---

### Post by ksatta1 on 2013-04-27
> **gschwind said:**
> do you switch xorg.conf depending on your select video cards?

for nvidia I have :

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    Option "UseDPLib" "no"
    BusID          "PCI:01:00:0"
    VendorName     "NVIDIA Corporation"
EndSection

for intel, I just leave an empty file.

I have the same setup. Now I'm using only Intel because of the GLX switching problems.

EDIT: another reply
> **MikeBraxner said:**
> According to some chatter, the new NVidia Driver 319.12, together with randr1.4 and a 3.9 kernel, *might* (????) allow integrated Optimus support *without* Bumblebee ... and I have *such* a hard time believing that. Has anyone actually tried any of this???

Like it was already mentioned here, I think the MBP uses a custom solution for switching. Also, unless there's new info, the 319.12 makes it possible to use nvidia to render and then output the rendered video via integrated adapter. It doesn't have any power management (to turn off nvidia when not used for example), and nvidia doesn't support vgaswitcheroo, so in essence it would be the same as using nvidia all the time. That's the info I found when googling about it a few weeks back.

---

### Post by zackiv31 on 2013-05-05
Has anyone here had issues with the rMBP (10,1 if it matters) and a fresh install of xubuntu 13.04?

Specifically I get kicked out to login at random times.  Sometimes after a couple minutes, sometimes after an hour.

I have no idea why it's happening, or even if it's graphics related.  I see some of you mention random GLX issues... so curious if this was something others are seeing?

I haven't quite figured out how to just do intel only, or nouveau only... as the 2.21 gfxstatus doesn't seem to be sticking.

---

### Post by MikeBraxner on 2013-05-06
> **zackiv31 said:**
> I haven't quite figured out how to just do intel only, or nouveau only... as the 2.21 gfxstatus *doesn't seem to be sticking*.

On selecting an option in Cody Krieger's gfxCardStatus (2.2.1), did you see an On Screen acknowledgment of the switch having been enacted, i.e. did you see a little 'bubble' with "Nvidia ..blabla now active" ( or something of the sort)? 

If you didn't see it, then the GPU was ***not*** forced, which tends to happen if your last boot was into Linux. If that happens, just reboot OS X, and on this *second* boot gfxCardStatus usually works just fine, i.e. you get the on screen confirmation, the GPU was properly forced, and you can cleanly boot into linux.

---

### Post by sauferkel on 2013-05-06
Hey guys,
well, i did a clean installation of 13.04 in order to get rid of some problems i still had from the alpha.
What i recognized during this installation, ....we really need a better knowledge base! kind of sucks to search in all these posts and blogs ( and some of the posts were even my own!) ....

In order to help ( a bit) , i wrote down what i did so far. Just forced to the intel gpu, as nvidia does not seem to work nice nowadays, right? 


**** GUIDE **** 

   [COLOR=#000000][FONT=Helvetica][SIZE=3]First install Refind, make sure it is running. For me it automatically looks for the linux kernels, so no further problems here. [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Helvetica][SIZE=3]
However I used &#8220;default_selection vmlinuz-3.8&#8221; in the * refindpartition * /boot/efi/EFI/refind/refind.conf file in order to make ubuntu the  primary system.[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Helvetica][SIZE=3]Use gfxCardStatus 2.2.1 (!! - its an older version - the new one does not work) in OSX to switch graphic cards.[/SIZE][/FONT][/COLOR]
 
[COLOR=#000000][FONT=Helvetica][SIZE=3]Then install Ubuntu. Start from the Usb-stick, choose testing (not direct install!). Use a terminal to install ubuntu via "ubiquity -b". This makes sure that no boot loader (grub) is installed. We will just use EFI for this. D[SIZE=3]o not reboot yet![/SIZE][/SIZE][/FONT][/COLOR]
 
[COLOR=#000000][FONT=Helvetica][SIZE=3]Mount your root partition ( exactly, you need your /boot folder) and create a file there called "refind_linux.conf" [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Helvetica][SIZE=3]Put the following lines inside:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Helvetica][SIZE=3]"Boot using standard options" "root=UUID=****YOUR UUID**** ro quite nouveau.modeset=1 i915.modeset=1 splash $vt_handoff"[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Helvetica][SIZE=3](find out your uuid of the partition with : sudo blkid ) 
It looks like [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Helvetica][SIZE=3] these two [SIZE=3]arguments are not needed (anymore) ... [/SIZE]i915.lvds_use_ssc=0 i915.lvds_channel_mode=2[/SIZE][/FONT][/COLOR]
 
[COLOR=#000000][FONT=Helvetica][SIZE=3]Now you should be able to boot if you forced the GPU to the internal (intel) in OSX.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Helvetica][SIZE=3]But now the nvidia card is still running and consuming power. To switch it off I needed to add the following lines to the /etc/rc.local file, in order to make it work: [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Helvetica][SIZE=3]chmod -R 705 /sys/kernel/debug/ [/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Helvetica][SIZE=3]chown USERNAME:USERNAME /sys/kernel/debug/vgaswitcheroo/switch[/SIZE][/FONT][/COLOR]
 
[COLOR=#000000][FONT=Helvetica][SIZE=3][SIZE=3]After a reboot [/SIZE]you should be able to switch the card off via: [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Helvetica][SIZE=3]echo IGD > /sys/kernel/debug/vgaswitcheroo/switch [/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Helvetica][SIZE=3](first ensures to make use of the internal graphics card) &#8230; and: [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Helvetica][SIZE=3]echo OFF > /sys/kernel/debug/vgaswitcheroo/switch[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Helvetica][SIZE=3](which switches the nvidia off) [/SIZE][/FONT][/COLOR] 
 
[COLOR=#000000][FONT=Helvetica][SIZE=3][SIZE=3]Y[/SIZE]ou can add these lines to rc.local, but I had problems with this, so I just copied these lines into two files (called on / off) , made them executable ( sudo chmod +x /path/to/file )  and put them on the F3/F4 buttons.[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Helvetica][SIZE=3]This allows you to switch the card easily off, when not needed, but enable it , if several monitors are needed.[/SIZE][/FONT][/COLOR]


*** EDIT ***
Finetuning for make better usage of the full resolution: 
As pointed out by lukeco11 , the plugins do nearly the same, without breaking the context menus:

[LIST]
[*]Deafult Zoom Level - I set this to 180% 
[*]Tab Mix Plus - I use this to adjust the tab sizes, I set max width to 320 
[/LIST]

Install gnome-tweak-tools and set fontsize to 1.3 or higher.


(Firefox over Chrome - I prefer Chrome normally, but in both Firefox and Thunderbird you can goto about:config  or advanced settings and set layout.css.devPixelsPerPx to a greater value, I have it set at 1.9  - copied from this thread, sorry don't have the name, but thanks!! However, this breaks the context menus, which is quite annoying...)


**** END OF GUIDE ****


Please have a look at it , comment, or correct me where i am wrong. 
For example: Do we still need all these bootparameters? Without them i was unable to boot. But i don't know if all of them are really needed.
Someone wrote that power consumtion with nvidia is fine now, is it true? Is it usable? Comparable to OSX ? If so, please tell me (and the others ;) ) how to do it.


Have fun! ;)

cheers,
Sauferkel

---

### Post by zackiv31 on 2013-05-06
> **MikeBraxner said:**
> On selecting an option in Cody Krieger's gfxCardStatus (2.2.1), did you see an On Screen acknowledgment of the switch having been enacted, i.e. did you see a little 'bubble' with "Nvidia ..blabla now active" ( or something of the sort)? 

If you didn't see it, then the GPU was ***not*** forced, which tends to happen if your last boot was into Linux. If that happens, just reboot OS X, and on this *second* boot gfxCardStatus usually works just fine, i.e. you get the on screen confirmation, the GPU was properly forced, and you can cleanly boot into linux.

Yes it sets, and displays the notification... On reboot, it still shows "Dynamic Switching" as the selected choice.  I've restarted a couple times, selecting "Integrated Only" which shows the confirmation.

The one thing that is different between my setup and others, is that I installed grub to the '/' directory of the Ubuntu parition.  reFind picked up the install on it's own, and it boots fine (I select ubuntu from the reFind menu, and than ubuntu from the  grub menu).  I don't see how this would change anything.. but thought I'd make note of it.


EDIT: It may be working now?  I booted with the GRUB options outlined by sauferkel, namely: nouveau.modeset=1 i915.lvds_use_ssc=0 i915.lvds_channel_mode=2 i915.modeset=1.  I also had to manually echo "OFF" into "switch" after login.  I booted into Xubuntu this time and ran glxgears with:

```

vblank_mode=0 glxgears

```

This gives me about 3000~4500 FPS on a 10,1 Macbook.  Is that about right for the intel card?  powertop, with brightness on low, and wifi on shows ~20W while running glxgears.

When I turn off glxgears (idling with wifi on), I'm now getting **~10W**.  Does that seem about right?

EDIT2: I'm also seeing a bunch of nouveau errors when I attempt to shut down.  I have to manually hold the power button to turn it off.

EDIT3: Actually... I don't think the grub options were necessary to get it down to ~10W... what do those lines do? :-/

---

### Post by lukeco11 on 2013-05-06
> **sauferkel said:**
> 
Finetuning for make better usage of the full resolution: 
Firefox over Chrome - I prefer Chrome normally, but in both Firefox and Thunderbird you can goto about:config  or advanced settings and set layout.css.devPixelsPerPx to a greater value, I have it set at 1.9  - copied from this thread, sorry don't have the name, but thanks!! However, this breaks the context menus, which is quite annoying...Another solution?
Install gnome-tweak-tools and set fontsize to 1.3 



Changing the pixel setting does indead seem to break context menus. Just in case it helps someone else, I've got Firefox to be totally usable at full resolution with the help of a couple of add-ons:
[LIST]
[*]Deafult Zoom Level - I set this to 180% 
[*]Tab Mix Plus - I use this to adjust the tab sizes, I set max width to 320 
[/LIST]

I've also have my fontsize scaling set to 1.7 in gnome-tweak-tools. I am still on the hunt for an email client that works well, all seem to have really small reply text.

---

### Post by sauferkel on 2013-05-07
@zackiv31:

As far as i understood it, you have to use the EFI boot method in order to switch graphics, but you are writing the opposite, right? 

I get about 6000 / 6500 frames with the command you mentioned, when the glxgears window is unchanged in size (like, tiny). When i maximize it, it goes down to 120...

But my computer (also 10.1) need about 40watts right now (doing the same as you atm while writing this post here..)


Sadly, i don't know what these lines do, however i need them to boot! Without them it does not start at all...
*edit*
I tried with just  [COLOR=#000000][FONT=Helvetica][SIZE=3]  nouveau.modeset=1   i915.modeset=1  $vt_handoff [/SIZE][/FONT][/COLOR]now and it also works.

---

### Post by philcolbourn on 2013-05-07
> **MikeBraxner said:**
> On selecting an option in Cody Krieger's gfxCardStatus (2.2.1), did you see an On Screen acknowledgment of the switch having been enacted, i.e. did you see a little 'bubble' with "Nvidia ..blabla now active" ( or something of the sort)? 

If you didn't see it, then the GPU was ***not*** forced, which tends to happen if your last boot was into Linux. If that happens, just reboot OS X, and on this *second* boot gfxCardStatus usually works just fine, i.e. you get the on screen confirmation, the GPU was properly forced, and you can cleanly boot into linux.

In my case, I had to leave gfxCardStatus running while shutting-down OS-X.

Or, it takes to reboots to make it stick. Not sure which.

---

### Post by philcolbourn on 2013-05-07
> **zackiv31 said:**
> Yes it sets, and displays the notification... On reboot, it still shows "Dynamic Switching" as the selected choice.  I've restarted a couple times, selecting "Integrated Only" which shows the confirmation.

The one thing that is different between my setup and others, is that I installed grub to the '/' directory of the Ubuntu parition.  reFind picked up the install on it's own, and it boots fine (I select ubuntu from the reFind menu, and than ubuntu from the  grub menu).  I don't see how this would change anything.. but thought I'd make note of it.


EDIT: It may be working now?  I booted with the GRUB options outlined by sauferkel, namely: nouveau.modeset=1 i915.lvds_use_ssc=0 i915.lvds_channel_mode=2 i915.modeset=1.  I also had to manually echo "OFF" into "switch" after login.  I booted into Xubuntu this time and ran glxgears with:

```

vblank_mode=0 glxgears

```

This gives me about 3000~4500 FPS on a 10,1 Macbook.  Is that about right for the intel card?  powertop, with brightness on low, and wifi on shows ~20W while running glxgears.

When I turn off glxgears (idling with wifi on), I'm now getting **~10W**.  Does that seem about right?

EDIT2: I'm also seeing a bunch of nouveau errors when I attempt to shut down.  I have to manually hold the power button to turn it off.

EDIT3: Actually... I don't think the grub options were necessary to get it down to ~10W... what do those lines do? :-/

10W is what I get. I still have to echo OFF to power-down discrete (NVidia) GPU.

---

### Post by zackiv31 on 2013-05-07
> **sauferkel said:**
> @zackiv31:
As far as i understood it, you have to use the EFI boot method in order to switch graphics, but you are writing the opposite, right? 

I get about 6000 / 6500 frames with the command you mentioned, when the glxgears window is unchanged in size (like, tiny). When i maximize it, it goes down to 120...

But my computer (also 10.1) need about 40watts right now (doing the same as you atm while writing this post here..)


It's my understanding that EFI is still the method that is booting.  I'm still using ReFind and it's showing up in the boot menu as "Ubuntu EFI".

Boy those frames are high.  Along with the wattage, are you sure you're not using nvidia?  I'll have to see why mine can barely touch 5000.  They should be about equivalent... something is different.

---

### Post by sauferkel on 2013-05-08
Well, but its Efi grub, right? Should also work.


Hehe, yeah, quite sure. Setings/Details shows Intel, vgaswitcheroo shows DIS "off", how to become even more sure ? ;)

Also that it goes down below 10 watts in idle....

---

### Post by MikeBraxner on 2013-05-08
An OpenGL - i915 Question ... I finally decided to spruce up my desktop a bit, i.e. actually look at some desktop effects in KDE (4.10.2). However, I found that XRender was doing all the work, and OpenGL refused to be selected, and glxinfo reported ...

```
direct rendering: Yesserver glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
GLX version: 1.4
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: **Gallium 0.4 on llvmpipe** (LLVM 3.2, 256 bits)
OpenGL version string: 2.1 Mesa 9.2.0
```

So OpenGL runs on *Software*, not on the i915 ... which probably explains glxgears coming in at ~650. As far as I know, OpenGL should run just fine using the i915, but this really isn't my bally-wick. Any ideas what I'm missing, or screwed up?

Edit: I'm such a dunce at times ... for the DPI scaling testing I set the driver to fbdev ... and didn't reset it to intel ... duuhh :-)

---

### Post by Umbra Diaboli on 2013-05-08
Hi everyone,

I'm having terrible problems with the brightness controls, and my screen looks very dark.

Has anyone figured out how to fix the brightness controls?

Thanks very much,

---

### Post by ksatta1 on 2013-05-09
> **sauferkel said:**
> (Firefox over Chrome - I prefer Chrome normally, but in both Firefox and Thunderbird you can goto about:config or advanced settings and set layout.css.devPixelsPerPx to a greater value, I have it set at 1.9 - copied from this thread, sorry don't have the name, but thanks!! However, this breaks the context menus, which is quite annoying...)

The context menus work correctly with devPixelsPerPx setting in Firefox 16 (I think), or the latest Aurora (Alpha). The menus getting messed up is actually a bug, however it's fixed in current Aurora atleast, beta didn't have it fixed last time I tried. ([http://www.mozilla.org/en-US/firefox/channel/#aurora](http://www.mozilla.org/en-US/firefox/channel/#aurora) . I have a PPA installed, probably googled ppa mozilla aurora or something, or maybe that link installs it, don't remember :)).

> **zackiv31 said:**
> ...
EDIT: It may be working now? I booted with the GRUB options outlined by sauferkel, namely: nouveau.modeset=1 i915.lvds_use_ssc=0 i915.lvds_channel_mode=2 i915.modeset=1. I also had to manually echo "OFF" into "switch" after login. I booted into Xubuntu this time and ran glxgears with:
...
EDIT2: I'm also seeing a bunch of nouveau errors when I attempt to shut down. I have to manually hold the power button to turn it off.

You have to add echo ON > vgaswitcheroo before shutting down, or closing X and echo OFF when waking up from sleep etc. I've put them in /etc/pm/sleep.d/vgaswitch_stuff. With the latest kernel I'm having problems shutting down too, the best place would probably be some script which is run always before X exits (on my TODO list :)).

> **philcolbourn said:**
> In my case, I had to leave gfxCardStatus running while shutting-down OS-X. Or, it takes to reboots to make it stick. Not sure which.
It's very quirky. Sometimes I even have to go back to OS X to set it again, even though I've been booting only Win or Linux.

> **Umbra Diaboli said:**
> Hi everyone,
I'm having terrible problems with the brightness controls, and my screen looks very dark.
Has anyone figured out how to fix the brightness controls?
Thanks very much,
In 13.04 they should work out of the box (with intel atleast), it should always be possible to switch brightness from /sys/devices/pnp0/00:07/backlight/gmux_backlight/brightness (or similar, not sure if it's the same with nvidia).


Another thing, has anyone updated to the latest firmware from OS X? I read somewhere it causes problems, haven't dared to try it yet.

---

### Post by MikeBraxner on 2013-05-09
> **ksatta1 said:**
> 
You have to add echo ON > vgaswitcheroo before shutting down, or closing X and echo OFF when waking up from sleep etc. I've put them in /etc/pm/sleep.d/vgaswitch_stuff. With the latest kernel I'm having problems shutting down too, the best place would probably be some script which is run always before X exits (on my TODO list :)).

13.04 with 3.8.8 Kernel works just fine for me without any additional switching on/off (except for the usual switching NVidia off after boot) ... which Kernel were you referring to?  Anyway, expanding on ksatta1's suggestion, you might want to try a user suspend script, say, /etc/pm/sleep.d/00_usercustom along the lines of ...

```
#!/bin/sh#
#
# location: /etc/pm/sleep.d/00_usercustom
#

. "${PM_FUNCTIONS}"

suspend_usercustom()
{
    export DISPLAY=:0.0 
    su -c "echo ON > /sys/kernel/debug/vgaswitcheroo/switch"
    # anything else you need to take care of before the system suspends
}


resume_usercustom()
{
    export DISPLAY=:0.0
    su -c "echo ON > /sys/kernel/debug/vgaswitcheroo/switch"
    su -c "echo IGD > /sys/kernel/debug/vgaswitcheroo/switch"
    su -c "echo OFF > /sys/kernel/debug/vgaswitcheroo/switch"
    # anything else you need to take care of for the system to resume
}


case $1 in
    suspend|hibernate) suspend_usercustom & ;;
    resume|thaw)       resume_usercustom  & ;;
    *) exit $NA ;; 
esac


exit 0  

```

---

### Post by gschwind on 2013-05-11
As promised I made a first draft of my setup, it is uncomplet and for gentoo, but it could help unbutu advanced users:

[http://www.hzog.net/index.php?title=Linux_on_MacBook_Pro_Retina_15%22_%282012%29](http://www.hzog.net/index.php?title=Linux_on_MacBook_Pro_Retina_15%22_%282012%29)

Have fun. I hope to update it, but it is very time consuming.

---

### Post by Umbra Diaboli on 2013-05-12
> **ksatta1 said:**
> In 13.04 they should work out of the box (with intel atleast), it should always be possible to switch brightness from /sys/devices/pnp0/00:07/backlight/gmux_backlight/brightness (or similar, not sure if it's the same with nvidia).


I've read people saying that WiFi works our of the box in 13.04 - for me it doesn't; I have to install the drivers that cberner mentions in his guide.

Brightness is supposed to work out of the box, for me it doesn't either - I believe Ubuntu isn't recognizing my Intel Graphics (I don't care about my Nvidia).

Unfortunately, switching brightness from /sys/devices/pnp0/00:07/backlight/gmux_backlight/brightness didn't work for me, but thanks for the tip.

If anyone has Ubuntu working properly with brightness on a MacBook Pro 10,1 I would be very thankful if they could provide me with some guidance :)

Thanks a lot!

---

### Post by ksatta1 on 2013-05-13
> **Umbra Diaboli said:**
> I've read people saying that WiFi works our of the box in 13.04 - for me it doesn't; I have to install the drivers that cberner mentions in his guide.

Brightness is supposed to work out of the box, for me it doesn't either - I believe Ubuntu isn't recognizing my Intel Graphics (I don't care about my Nvidia).

Unfortunately, switching brightness from /sys/devices/pnp0/00:07/backlight/gmux_backlight/brightness didn't work for me, but thanks for the tip.

If anyone has Ubuntu working properly with brightness on a MacBook Pro 10,1 I would be very thankful if they could provide me with some guidance :)

Thanks a lot!

For the WiFi you have to go to the additional drivers part and enable Broadcom something STA foo. (This works better for me than the firmware extraction method in the older guides. The additional driver was added only in 13.04, so that's why the older guides use a diff method).

If you don't want to do lots of tweaking I think it's best to install nvidia proprietary driver. It uses less power according to my tests (when idling), than the open-source nouveau. Without lots of tweaking nvidia will be used anyway, so it's best to install the nvidia prop driver. Also the brightness might work better.

I think I'll do some testing with gschwind's stuff, nice work BTW :) If I get that far, I can report how the brightness controls work with nvidia.

> **MikeBraxner said:**
> 13.04 with 3.8.8 Kernel works just fine for  me without any additional switching on/off (except for the usual  switching NVidia off after boot) ... which Kernel were you referring to?   Anyway, expanding on ksatta1's suggestion, you might want to try a  user suspend script, say, /etc/pm/sleep.d/00_usercustom along the lines  of ...
Right now I'm running raring's default (3.8.0-19), when it first got updated to -19 I had lots of probs shutting down, sleeping, etc, but now it has worked fine for days, maybe some update fixed it, haven't had time to investigate.

---

### Post by MikeBraxner on 2013-05-13
> **Umbra Diaboli said:**
> 
I believe Ubuntu isn't recognizing my Intel Graphics ...

Unfortunately, switching brightness from /sys/devices/pnp0/00:07/backlight/gmux_backlight/brightness didn't work for me

About the Intel ... check which driver is installed (dpkg -l | grep intel), which driver is loaded (lsmod | grep video), and that OpenGL uses then correct one (glxinfo | grep vendor). You should see something like ...
```

ii  xserver-xorg-video-intel                  2:2.21.6+git20130502.5637c173-0ubuntu0sarvatt
                          amd64        X.Org X server -- Intel i8xx,** i9xx** display driver
...
video                  19467  3 **i915**,nouveau,apple_gmux
...
OpenGL vendor string: **Intel** Open Source Technology Center

```

If you have trouble getting the Integrated GPU recognized, I would expect one of these to foul up ... which will tell you how to correct it ;-)

As for the brightness: Please start by clarifying just what you have a problem with ... automatic backlight adjustment, adjusting via GUI interface, function keys or plain cli?

To cover some basics, please have a look in /sys/class/backlight ... you should see two entries, gmux_backlight and intel_backlight. Try setting the brightness via 'echo ... > brightness' in either, but mind you use appropriate values ( check max_brightness in either ... gmux uses 1023 as max, intel 1808).

---

### Post by Umbra Diaboli on 2013-05-13
> **ksatta1 said:**
> For the WiFi you have to go to the additional drivers part and enable Broadcom something STA foo. (This works better for me than the firmware extraction method in the older guides. The additional driver was added only in 13.04, so that's why the older guides use a diff method).

Nice, that solved my WiFi problems :D Thanks for this tip!
Additional drivers - it reminds me of ubuntu 10.10.

> **ksatta1 said:**
> If you don't want to do lots of tweaking I think it's best to install  nvidia proprietary driver. It uses less power according to my tests  (when idling), than the open-source nouveau. Without lots of tweaking  nvidia will be used anyway, so it's best to install the nvidia prop  driver. Also the brightness might work better.

Brightness still not working with the prop :(

> **MikeBraxner said:**
> About the Intel ... check which driver is  installed (dpkg -l | grep intel), which driver is loaded (lsmod | grep  video), and that OpenGL uses then correct one (glxinfo | grep vendor).  You should see something like ...

```
ii  intel-gpu-tools                           1.3-0ubuntu2                           amd64        tools for debugging the Intel graphics driver
ii  libdrm-intel1:amd64                       2.4.43-0ubuntu1                        amd64        Userspace interface to intel-specific kernel DRM services -- runtime
ii  xserver-xorg-video-intel                  2:2.21.6-0ubuntu4                      amd64        X.Org X server -- Intel i8xx, i9xx display driver

```

> **MikeBraxner said:**
> As for the brightness: Please start by clarifying just what you have a  problem with ... automatic backlight adjustment, adjusting via GUI  interface, function keys or plain cli?

Sorry about this :(
I'm talking about the brightness controls. The Screen is on a very low backlight brightness, the keyboard controls (F1 + F2) dont work and I can't seem to find a preference anywhere to increase the brightness to a suitable level.

> **MikeBraxner said:**
> To cover some basics, please have a look in /sys/class/backlight ... you  should see two entries, gmux_backlight and intel_backlight. Try setting  the brightness via 'echo ... > brightness' in either, but mind you  use appropriate values ( check max_brightness in either ... gmux uses  1023 as max, intel 1808). 

[IMG]http://i.imgur.com/MK5TOR3.png[/IMG]

Tweaking around, nothing works.

[IMG]http://i.imgur.com/YmqTJnz.png[/IMG]

Anyway, thanks for the help :)

---

### Post by zackiv31 on 2013-05-13
> **ksatta1 said:**
> 
If you don't want to do lots of tweaking I think it's best to install nvidia proprietary driver. It uses less power according to my tests (when idling), than the open-source nouveau. Without lots of tweaking nvidia will be used anyway, so it's best to install the nvidia prop driver. Also the brightness might work better.

Which proprietary driver are you using?  What apt-get command should be run?  I tried to get it working initially but I had a corrupt X constantly.


To the guy who was asking about brightness, a fresh install of xubuntu 13.04 on my 10,1 worked out of the box.  Also had to manually install the wireless.

---

### Post by MikeBraxner on 2013-05-13
Briefly ... you reported the dpkg output, but not the other two commands ... not enough info to comment reliably.

brightness issue ... zackiv31 is certainly right, a clean install should work out of the box. However, judging by your screen captures your system may lack the apple-gmux, and does not seem load the i915 driver. That being said, it seems that you might not have payed too close attention to the installation advice given in the posts throughout this forum, or to diverse 'install on MBPr' guides on the web ... you might want to rectify that. 

Finally, and more as an aside, the above advise to 'echo ...' was a CLI based, i.e. was meant to be used on the command line, hence in a terminal, not via a GUI file-manager like nautilus ... which again denies the information required to assist further.

---

### Post by ksatta1 on 2013-05-14
I've been tweaking my method to switch graphics at boot time (intel or nvidia), modified from gschwind's wiki. So far so good (I'll post everything when it's ready), but now I ran into the brightness prob too (with proprietary nvidia driver). I've been googling and it seems that the brightness can't be controlled when the nvidia proprietary driver is in use?

Does anyone have brightness control working with nvidia's proprietary driver? I've tried suspend/resume, with and without acpi_backlight in kernel cmd etc. /sys/class/foobacklight doesn't work (doesn't change the brightness).

---

### Post by MikeBraxner on 2013-05-14
> **ksatta1 said:**
> I've been tweaking my method to switch graphics at boot time (intel or nvidia), modified from gschwind's wiki. ... but now I ran into the brightness prob too (with proprietary nvidia driver). I've been googling and it seems that the brightness can't be controlled when the nvidia proprietary driver is in use?

Does anyone have brightness control working with nvidia's proprietary driver? I've tried suspend/resume, with and without acpi_backlight in kernel cmd etc. /sys/class/foobacklight doesn't work (doesn't change the brightness).

While I haven't tried gschwind's approach, a similar NVidia backlight issue [has crept up before]("http://ubuntuforums.org/showthread.php?p=12309146#post12309146"). 

At the time it turned out to require two adjustments: (i) apple-gmux de-registered the interface, which was not subsequently not picked up bu the desktop environment (KDE in my case), and (ii) the NVidia only adjusted the backlight correctly after a 'sleep-resume' cycle. Have a look at the original posting, it may be helpful ... or not ... you never know ;-)

---

### Post by ksatta1 on 2013-05-14
Yeah, I just found a combo that works: nvidia 310.xx from nvidia.com and kernel 3.8.0-19 (raring default). Then after suspend/resume /sys/foo works :)

In kernel 3.9.2 I don't think it works with any nvidia driver. Anyway, thanks for the other thread, it's most likely related to that. Well, I guess I'll continue tomorrow.. Now I have to compile the 3.8.0-19 kernel (without efifb..) :D It's taking a while but maybe in the end I have a working setup (with boot-time gfx switch), now I'm close :)

---

### Post by MikeBraxner on 2013-05-14
Just curious ... why 3.8.0-anything? Why not 3.8.8 or 3.8.9?

---

### Post by zackiv31 on 2013-05-14
I'm still unable to get proprietary nvidia working.  I tried to install NVIDIA-Linux-x86_64-310.44.run and NVIDIA-Linux-x86_64-319.17.run from nvidia.com... but each time X would flash login, and crash back to a 640x480 screen.  Are you guys doing anything special to get proprietary working?

Also a question about Intel (integrated) only.  Is it possible to do dual screens under it?  I thought I had this working the other day... but it seems I can only get it running dual screens with nouveau.

---

### Post by gschwind on 2013-05-15
Hello, with my method, without efifb, gmux still functional after nvidia driver load and brightness work fine.

---

### Post by Umbra Diaboli on 2013-05-15
How do you guys switch to intel on Ubuntu? You use gfxcardstatus in your Mac partition? Does this work?
After reading around, the backlight controls don't work with nVidia - so this has been my problem. I don't need nVidia's graphics power, so switching to Intel should be the solution :D


Cheers,

---

### Post by MikeBraxner on 2013-05-15
zackiv31 ... You would probably be better off using the [xorg-edgers repository]("https://launchpad.net/~xorg-edgers/+archive/ppa") to get your NVidia driver. Clean out whatever you've done so far, import the PPA, and use an 'apt-get install nvidia-... nvidia-settings-...' to get your driver, after you've locked the discreet GPU via OS X (cody's gfxcardstatus 2.2.1), or follow in gschwind's footsteps.

Umbra Diaboli ... Yep, gfxCardStatus works just fine (2.2.1) though you might have to boot twice into OS X to get it to stick. For the switch, take a look at [the first part of this post]("http://ubuntuforums.org/showthread.php?t=2006475&p=12537799#post12537799"), or at one of the web guides ... you've been on the forum long enough to have referenced them before yourself.

---

### Post by ksatta1 on 2013-05-15
> **Umbra Diaboli said:**
> How do you guys switch to intel on Ubuntu? You use gfxcardstatus in your Mac partition? Does this work?
After reading around, the backlight controls don't work with nVidia - so this has been my problem. I don't need nVidia's graphics power, so switching to Intel should be the solution :D

I wrote a thread about it a while ago, but the link given in earlier post seems to have all the info, and more :) Looks like recent kernels (even the def. raring 3.8.0-x) don't need the echo ON/OFF when suspending etc, just do echo OFF once to turn off nvidia.

> **MikeBraxner said:**
> Just curious ... why 3.8.0-anything? Why not 3.8.8 or 3.8.9?

I started with 3.9.2 from kernel.org, but couldn't get the brightness control to work with nvidia (I'm setting it up so that I can choose nvidia or intel at boot). Also the bcmwl-kernel-source doesn't compile right with 3.9.2, might work with a newer source from outside of the repos or something. Anyway looks like the default 3.8.0-x is the "easiest" way to go.

> **zackiv31 said:**
> I'm still unable to get proprietary nvidia  working.  I tried to install NVIDIA-Linux-x86_64-310.44.run and  NVIDIA-Linux-x86_64-319.17.run from nvidia.com... but each time X would  flash login, and crash back to a 640x480 screen.  Are you guys doing  anything special to get proprietary working?

In xorg.conf Device section: add:
```
Option "UseDPLib" "off"
```

> 
Also a question about Intel (integrated) only.  Is it possible to do  dual screens under it?  I thought I had this working the other day...  but it seems I can only get it running dual screens with  nouveau.

Nope. It's very annoying, the only reason I'm setting up gfx switching at boot time. I need the external outputs at work. I was very disappointed when I tested in OS X and realized it switches to nvidia there too, so probably a hardware issue.

EDIT: It seems Ubuntu's kernel naming convention is a bit misleading. I just compiled kernel 3.8.0-19 from apt-get source linuxfoo, and it seems to be infact 3.8.8.

EDIT2: I didn't know this before.. Ubuntu drops the last num from kernel versions etc.. [http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html](http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html) . Learn something new every day :D

---

### Post by johnluck on 2013-05-15
i tried the retina effect with ubuntu and it's really wonderful specially with video games.

---

### Post by Symbolix on 2013-05-16
Hi,
I have been reading this entire thread for the last couple of days, trying to make my MacBook Pro, 15" Retina (10,1) work with Ubuntu 13.04. Some very useful information here, thanks to all who contributed. Some very technical stuff, especially things tried with old drivers and older kernel versions, prior to page 30, very deep end experimental, did not get most of it. After page 30, it gets more human-readable :)

Anyway, after trying to install the Nvidia drivers and got them working and then got them broken, I would like to check one important thing:

One of the main problems I run into was "Kernel version and Nvidia Driver version mismatch!". How to avoid this? How do I know that the newest NVidia driver out there is compatible with what I have already installed or have?

For example right now, I started fresh with XUbuntu 13.04, Kernel: 3.8.0-21-generic. I know that there is a new NVidia driver for Linux: 319.17. So do I go with the "./*.run" file approach or do I set-up one of those external repositories, for example "xorg-edgers", what should be the correct approach?

Also, one I install them, how do I ensure that the NVidia drivers will not break with a Kernel update?

Thanks.

---

### Post by MikeBraxner on 2013-05-16
> **Symbolix said:**
> "Kernel version and Nvidia Driver version mismatch!". How to avoid this?

You can't avoid this *as long as* you decide to compile the driver yourself, so just recompile the driver module ... or use a 'ready-made' driver from a ppa.

> **Symbolix said:**
> How do I know that the newest NVidia driver out there is compatible with what I have already installed or have?

You don't ... but you can try! ;-)  With 13.04, the nvidia-current is stable, will work, and requires no particular maintenance on your part, since any driver updates are folded into your general updates, i.e. automated. However, newer versions, say 314, can be expected provide better performance and power-management, and are usually just as stable. Any 'recent releases', such as 319, may still be a bit temperamental at times, but might again improve performance and power-management. Take your pick, it's your choice!

> **Symbolix said:**
> So do I go with the "./*.run" file approach or do I set-up one of those external repositories, for example "xorg-edgers"?

Unless you have a *specific reason* why you want to compile the driver yourself, I would recommend using the xorg-edgers repository. Pick the version you want, and simply a run an 'apt-get install ...", just make sure you pull ***both***, the driver and the *matching* settings module.

---

### Post by ksatta1 on 2013-05-16
My working graphics switching in ubuntu: [http://ubuntuforums.org/showthread.php?t=2145821&p=12650682#post12650682](http://ubuntuforums.org/showthread.php?t=2145821&p=12650682#post12650682) .

Thank you gschwind (just realized there's also an 'i' in there, I think I typoed your nick in some places) and also thanks to all others :)

---

### Post by Symbolix on 2013-05-18
Hi,
Thanks for the help. The reason for me trying to go with 319.17 was that I naively believed that it will help me tweak my resolution?! So after a lot of pain (for some reason all the x-swat and edge reps were still serving the 304) I managed to install the 319.17 driver. As one would expect, there is still nothing in there to fix the crazy resolution of 2880x1800.

So, before switching and etc. I need to be sure that I somehow will be able to solve this problem. The question now is:

What is the unified solution on Ubuntu 13.04 that will help a user to overcome the Small Fonts / Icons etc. problem caused by the native resolution?

I know (from this very forum) that there are Firefox cheats, DPI and screen cheats in Xorg, but does that really work?

Thanks.

---

### Post by MikeBraxner on 2013-05-19
Symbolix ... On Gnome-based DE's (Gnome, Unity, ...) you're more or less stuck with what you've got. You *can* adjust the font size with Ubuntu-Tweak, or the like, and fiddle with Firefox and Chrome settings, but a true 'scaling' is out. On QT-based DE's (KDE, be:shell) you can properly scale at will through X, via DPI setting or displaysize.

---

### Post by Symbolix on 2013-05-19
> **MikeBraxner said:**
> Symbolix ... On Gnome-based DE's (Gnome, Unity, ...) you're more or less stuck with what you've got. You *can* adjust the font size with Ubuntu-Tweak, or the like, and fiddle with Firefox and Chrome settings, but a true 'scaling' is out. On QT-based DE's (KDE, be:shell) you can properly scale at will through X, via DPI setting or displaysize.

Hi Mike,
Thanks for the help. I pushed it to some extend, with the firefox tweaks and DPI settings, but never got it clean as you said. There are always things that will aper small or badly proportioned. Unfortunately, I am running out of time. I have decided to stick to OSX, as I was testing things while trying to make Linux works, and I have found out that %99.9 of what I used will work under OSX with the terminal there. So for now, OSX will be the way to go. But for future reference, by KDE, do you mean Kubuntu? or Fedora? Cause I got KDE on Xubuntu, and it still did not help alot with the resolution?

Thanks.

---

### Post by ksatta1 on 2013-05-19
There's no perfect solution yet, one of the problems is GTK-based apps, it'll probably take time before gtk is "fixed", not a really a bug but anyway.

I tried KDE and it worked more "out-of-the-box" with the dpi etc, but I immediately ran into the same problems as in XFCE, mainly gtk-based apps, also the icons in systray were too small I think, etc etc.

---

### Post by ksatta1 on 2013-05-19
Looks like Firefox's menus not working -bug with about:config / devPixelsfoo has been fixed in the current raring-updates official package. Just thought I'd report here if someone's using the alpha / beta versions because of that :)

---

### Post by MikeBraxner on 2013-05-19
Symbolix ... By 'KDE' I mean precisely that - the K Desktop Environment, aka KDE. Kubuntu is nothing more than the Ubuntu distribution, using KDE as the Desktop Environment. Xubuntu is the ubuntu distribution using the Xfce desktop environment. What you most likely saw, where a number of KDE-*Applications* running under Xfce, not the KDE. You might want to give KDE a try, or if you prefer something 'leaner', have a look at be:shell, i.e. 'KDE without the plasma desktop'.

ksata1 ... If the 'systray icons' where not the size you liked, why didn't you just enlarge the systray-*size*? Just hit the little yellow 'bean', take a hold of where it says 'height' and adjust it to whatever you like. 

As to the GTK-based apps being 'fixed' ... I think you can just about forget it. The problem has been around for years, and has been pretty much ignored/denied by developers and users alike. There was some hope with Wayland, but that has since been culled by canonical in favor of Mir, the 'next great step' in making your computer appear more like a TV or 'smartphone' ... i.e. with an interface for idiots ... sorry ... sore subject ... I'm totally prejudiced ... still right, though ... :-)

---

### Post by ksatta1 on 2013-05-22
> **MikeBraxner said:**
> ksata1 ... If the 'systray icons' where not the size you liked, why didn't you just enlarge the systray-*size*? Just hit the little yellow 'bean', take a hold of where it says 'height' and adjust it to whatever you like. 
Thanks for the tip. I might try KDE again one day :)

> As to the GTK-based apps being 'fixed' ... I think you can just about forget it. The problem has been around for years, and has been pretty much ignored/denied by developers and users alike. There was some hope with Wayland, but that has since been culled by canonical in favor of Mir, the 'next great step' in making your computer appear more like a TV or 'smartphone' ... i.e. with an interface for idiots ... sorry ... sore subject ... I'm totally prejudiced ... still right, though ... :-)
Heh, yeah I've been thinking I'll just move to bare X or something, I use the keyboard 99% of the time anyway :)

It's quite surprising that the whole DPI thing has been pretty much ignored so long.. Even in OS X for example Picasa either has "right-size" buttons and low-dpi image, or small buttons and high-dpi image. One would think that it would be possible to just double all the coordinates when Any UI element is drawn, but ofcourse there's a lot more to it. And even Apple is having problems with it. I just use the word "even" because of all the resources they're probably putting into it etc.

EDIT: I know Picasa is not Apple's but what I meant was it's not possible to run application x properly if it doesn't have support for high-dpi.

---

### Post by Supjae on 2013-05-25
Hey guys,

I just got my rMBP and installed Ubuntu, but every time I close the lid I just get black screen and have to hard reboot to get the comp working again. Anyone had this problem as well?

Sorry if it was posted already. I'm a complete novice to Ubuntu and have no real clue what is going on. :(
Oh and also is there a way to find out if my Nvidia is installed or not ?
also I'm running 13.04 

Thanks,

---

### Post by ksatta1 on 2013-05-25
Hmm.. It might work better if you install nvidia proprietary driver from settings / software & updates / additional drivers-tab (atleast in XFCE, might be in a different place in normal Ubuntu).

Also, I think the prop. driver needs efi stuff, like in: [http://cberner.com/2013/03/01/installing-ubuntu-13-04-on-macbook-pro-retina/](http://cberner.com/2013/03/01/installing-ubuntu-13-04-on-macbook-pro-retina/) (step 4 etc..).
EDIT: also needs "Option "UseDPLib" "off"", like in the guide above, step 5.

If you haven't done some serious tweaking, it's using nvidia :)

BTW, if anyone wants to create a wiki for all this stuff it would be great.

---

### Post by Supjae on 2013-05-26
nvm, fixed

---

### Post by Tuminoid on 2013-05-28
Anyone had luck with BCM4331 in MacBookPro 10,1? I cannot get it to work with b43 nor bcmwl for more than couple seconds at random. Most of the time it is unable to get an IP address.

On the list I have tried are latest mainline kernels (up to 3.9.4 for saucy), b43-fwcutter, firmware-b43-installer, linux-firmware-nonfree, lwfinger.com bcm drivers, bmcwl-kernel-source...

Edit: It may have something to do with power management features at your router. Using mobile hotspots you cannot control those, but at home, I set them off, and connection stayed on perfectly and had proper speed.

---

### Post by bcc2 on 2013-08-19
I guess no one has had any luck getting the SD card working yet :(??

---

### Post by Quackers on 2013-08-20
I seem to have most of the everyday use items working now with my 10,1 MBP retina. I can even change resolution. The display is a little fuzzy on the edge of letters etc when not using the full 2880x1800 resolution but it can be lived with.
The wifi adaptor seems to be working well (no problems yet) after installing the bcmwl thingimabob (and its dependencies) so no current problems there.
Don't know about sd card as I don't use it I'm afraid.
Happy so far!

EDIT I've just read this thread from page 1 to here and I really need to thank all of you guys for the amount of work you've put into sorting these problems out. It's all way over my head but I for one appreciate it all! Thanks.

---

### Post by Quackers on 2013-08-21
One question pops into my head.
My install is new and yesterday the installation of nvidia drivers (apt-get install nvidia-current blah blah) resulted in booting to a black screen. I'm on 13-04 and using the 3.8.0-29 generic kernel.
Having removed everything I'm back to using nouveau and all is well. An interesting point is that the additional drivers tab in software sources doesn't actually list  any available proprietary drivers for my card, which seems a bit strange as I'm surely using the nvidia card by default.
Is this normal?
Thanks.

Mine also suffers from failing to resume from suspend.

---

### Post by randarand97 on 2013-08-23
> **JJ said:**
> racoonone ... it seems that 'X DPI settings is being ignored' on a Gnome base, and thus Unity, has been an old hat for YEARS! The developers' position appears two-fold, i.e. ...


[LIST=1]
[*]Too many hardware units report 'wrong' information to/through X, which should thus be ignored for 'the good of the user' ... a perfect symbioses of MS and Apple: It really *IS* a feature, and anyway 'poor, dim-witted users' cannot be exposed something as dangerous as an *option* to adjust an X-DPI setting. 
[*]This is part of a 'work-around' for the introduction of something 'wonderful and new', and just as there were some 'minor issues' with the introduction of [take your pick], people will get used to it. Anyway, 'only a handful of old programs' still honor X-Settings, stuff 'like xterm and maybe emacs' ... or KDE, I guess. 
[/LIST]

In discussions ranging at least 2006-13 the same problem has been flagged, discussed, and had bug reports issued over and again ... in at least one case the bug report was *sequentially* graded as fixed, fixed in release, unconfirmed, solved, invalid, fixed in release, invalid, solved, confirmed, unconfirmed, and critical. More informed discussions clarify that the Gnome base does indeed 'use the X server DPI value. It does not override it', obviously implying that it 'does not have a DPI setting anymore'.

Anyway, I dug up **five claims** of resolving the issue (the last one being my own) ...


[LIST=1]
[*]The DPI can be set, but only on a *per session* basis via "[COLOR=#000000]xrandr --dpi 130".[/COLOR] 
[*]The DPI value can be set, but only via a *direct* call a la "startx --dpi 130", i.e. options don't make it through. 
[*]You cannot set the DPI value anymore, you can *only* adjust the *text-scaling* factor /org/gnome/desktop/interface/text-scaling-factor, which should be calculated as (scale factor = monitor dpi / 96), and set through dconf, or "gsettings set org.gnome.desktop.interface text-scaling-factor [scale factor]". 
[*]The problem lies with 'display-properties', but *can* be resolved by removing '~/.gnome2/monitor.xml'. 
[*]"Welcome to KDE". 
[/LIST]
&#8203;
If none of these work for you, there's always Wayland ... nope, hang on ... Ries just culled that one for Ubuntu/Ubuntu Next in favor of the 'wonderful and new Mir' (eta 2014), so that your desktop can easier resemble a phone or TV.

Wow, thanks for all the research!! The latest kernel (3.8.0-10) in  raring just broken my install, so I'm waiting for that to be fixed :/

I've tried most of those already, and the text-scaling does work for  text, unfortunately it's only for text and only some text. Chrome, for  example, seems to ignore it. I haven't tried the .gnome2/monitor.xml  thing, so I'll try that once this kernel issue is fixed. Thanks again!

---

### Post by ager2 on 2013-09-26
Hey guys,  just installed Ubuntu 13.10 on my 15" macbook_R, and I have to say it runs really nice, especially that the card reader is working now made me quite happy (@bcc2 ;) )

    I am still using the Intel graphics card, but I would like to prefer the Nvidia card, just not sure about the power consumption. Could someone say something about this? 


@ksatta1: you wrote something about creating a wiki regarding this book. I would really appreciate this!  I could just offer a guide for Intel-only setup, maybe you could help to write the "other side" (nvidia) ?  Let me know!

     ( I posted earlier in this thread, as "sauferkel". However I lost the email adress (was on lavabit.com) so I had to create a new account)    

Cheers,  henning

---

### Post by Quackers on 2013-09-27
Unless something drastic has been changed for 13.10 I would imagine you're using the Nouveau driver and therefore the Nvidia graphics card.
The only Nvidia graphics driver I've got to work so far has been the 319.49 driver installed manually from the Nvidia site though others seem to have found the Ubuntu-packaged Nvidia drivers to work (ie 304 or 310). Neither worked on mine though.
The Nvidia card is likely to consume more power than the Intel though I'm not sure that you can choose which you use without outside assistance.

---

### Post by htHNLDT on 2013-10-02
Hi,

How do you guys switch to the Intel card? I have Ubuntu 13.04 Mac Build installed (I do not have dual boot with Mac or anything, just Ubuntu installed on my SSD) and it always uses Nvidia by default :(

Thanks,

---

### Post by ager2 on 2013-10-02
Do you have an OSX installation atleast somewhere? Booting OSX to force to intel (using GfxCardStatus v2.2) is the simplest solution I guess. 
Otherwise, ksatta1 named a guide 2 pages ago, which allows to use intel. but i didn't follow it so I can't help you there, sorry.

---

### Post by steve57 on 2013-10-04
I read a study that said that software enthusiasts tested Retina MacBook Pro and the latest versions of Ubuntu. They have come to the conclusion that Linux users still too early to order new laptops from Apple. :(

In the course of the experiment revealed the following problems:

1. During the installation embedded WiFi-adapter refused to work, which, however, managed to adjust after.

2. Mode suspend-and-resume works only upon condition the installation of proprietary drivers Nvidia.

3. Desktops Unity, GNOME Shell and KDE look ill-suited for use in ultra-high-resolution display Retina.

4. Ubuntu discharges a battery to 20% faster than native Mac OS X. :-\"

---

### Post by bcc2 on 2013-10-04
I don't suppose anyone has had any luck getting MBPR (13") to work on three monitors?

What ever config I use, display ports + hdmi, hdmi + displayport + laptop, as soon as I try and enable more than 2 monitors. X just crashes and won't work. I have given it a try in the latest 13.10 and got same issues :(.

---

### Post by ager2 on 2013-10-09
@steve57

do you have a link to this study?

---

### Post by Cioran_Naroic on 2013-10-09
Hi everyone,

I'm worried about the power consumption of my new MBPR 10,1 15" (early 2013). I did all the tricks recommended by powertop, and I still get 21W with no wifi, bluetooth, ethernet, nvidia or anything (at least, powertop shows à 0.0% usage in front of them...) while running no applications (not even X11) and with screen brightness set to 0... I browsed the entire web for tips, laptop-mode, power management etc. but I can't go below 21W.

I also tried powerstat in a tty. It reports the same value, BUT after some times the screen gets black and it reports 11W. Is the screen consuming 10W ? Why can't I get this score when brightness is set to 0 ?

I'm suprised to see that some of you get a power consumption around 10W.

Any ideas to help me ? Thank you a lot !

EDIT : powertop now gives me the power estimation for each of my process/device. I did a powertop -html with everything disabled. Summing the mW values of the report gives me around 3-4W consumption, but powertop still says :

The battery reports a discharge rate of 15.7 W
 System baseline power is estimated at 15.0 W

```
[TABLE="width: 100%"]
[TR]
[TH="width: 10%"]ower est.
[/TH]
 	[TH="width: 10%"]Usage[/TH]
 	[TH="class: device"]Device name[/TH]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]  692 mW   [/TD]
 	[TD="class: device_util"]  0.3%[/TD]
 	[TD]CPU core[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]  484 mW   [/TD]
 	[TD="class: device_util"] 29.9%[/TD]
 	[TD]Display backlight[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]  299 mW   [/TD]
 	[TD="class: device_util"]  0.3%[/TD]
 	[TD]CPU misc[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]  264 mW   [/TD]
 	[TD="class: device_util"]  0.0 ops/s[/TD]
 	[TD]GPU core[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"] 32.9%[/TD]
 	[TD]USB device: EHCI Host Controller[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"] 22.9%[/TD]
 	[TD]USB device: usb-device-8087-0024[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"] 12.8%[/TD]
 	[TD]USB device: usb-device-0424-2512
[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"]  2.7%[/TD]
 	[TD]USB device: Apple Internal Keyboard / Trackpad (Apple Inc.)[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]Audio codec hwC0D0: Cirrus Logic[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]Display backlight
[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]USB device: usb-device-8087-0024[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]USB device: xHCI Host Controller[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]USB device: xHCI Host Controller[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]USB device: EHCI Host Controller[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]USB device: BRCM20702 Hub (Apple Inc.)[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]USB device: usb-device-05ac-820a[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]USB device: usb-device-05ac-820b[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]USB device: Bluetooth USB Host Controller (Apple Inc.)[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"]  0.0 ops/s[/TD]
 	[TD]GPU misc[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]    0 mW   [/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]USB device: FaceTime HD Camera (Built-in) (Apple Inc.)[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]100.0%[/TD]
 	[TD]PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]100.0%[/TD]
 	[TD]PCI Device: Intel Corporation 3rd Gen Core processor Graphics Controller[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]100.0%[/TD]
 	[TD]PCI Device: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]100.0%[/TD]
 	[TD]PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]100.0%[/TD]
 	[TD]PCI Device: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]100.0%[/TD]
 	[TD]PCI Device: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]100.0%[/TD]
 	[TD]PCI Device: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]100.0%[/TD]
 	[TD]PCI Device: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode][/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]100.0%[/TD]
 	[TD]PCI Device: Intel Corporation HM77 Express Chipset LPC Controller[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]100.0%
[/TD]
 	[TD]PCI Device: NVIDIA Corporation GK107 HDMI Audio Controller[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]100.0%[/TD]
 	[TD]PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]100.0%[/TD]
 	[TD]PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"] 33.0%[/TD]
 	[TD]PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]PCI Device: Broadcom Corporation Device 16a3[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]PCI Device: Broadcom Corporation BCM4331 802.11a/b/g/n[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]PCI Device: NVIDIA Corporation GK107M [GeForce GT 650M Mac Edition][/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2[/TD]
 [/TR]
 [TR="class: device_odd"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller[/TD]
 [/TR]
 [TR="class: device_even"]
 	[TD="class: device_power"]           
[/TD]
 	[TD="class: device_util"]  0.0%[/TD]
 	[TD]PCI Device: Intel Corporation 3rd Gen Core processor DRAM Controller[/TD]
[/TR]
[/TABLE]


```

How is that possible ? It's not a bug : my battery is really discharging very fast (I get about 3 hours).

---

### Post by ager2 on 2013-10-18
@Cioran_Naroic: Well, I personally have the mid 2012 version but this should be the same. As long as you did not switch off the nvidia graphics card, this causes the high consumption values. I guess mine are pretty much the same with the card on, no matter if using it or not. 

So maybe try to switch to the Intel-one using OSX (Gfxcardstatus 2.2.1) and then disable it within ubuntu 

		echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
		echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

The first command makes sure you use the Intel (integrated) , the second one switches the Nvidia off. (guess u need root for that!)

---

### Post by Cioran_Naroic on 2013-10-18
As listed in the table, my graphic card is actually OFF (0%/W power consumption) using bumblebee/bbswitch. I recently discovered that powertop shows a power consumption for "Display Backlight" (I assume this is the Retina Screen) of around 10W ! So basically, the Retina screen is consuming half of the power of my laptop... WTF?

---

### Post by ager2 on 2013-10-18
Well, as far as I know, these values reported by powertop are far from accurate....so I would not rely on them. 

Also, afaiK, bumblebee does not work with this configuration, however this might be wrong or might have changed.

I just assumed that you have the card still on, as this is also the baseline power mine consumes, having the card on.

What driver are you using ? 

The display needs a lot of power, that's right. But having it switched off, or in the darkest settings, this should be less indeed!

---

### Post by rchman on 2013-10-30
**My Experience With Ubuntu 13.10 on an Early 2013 Macbook Pro (10,2)**


I've been having trouble finding information on compatibility between Ubuntu 13.10 and the last gen Macbook. Everything that I've read has either been "it works" or "it's terrible and I hate Apple."


So, needing (or wanting) new hardware, and having a chance to pickup a used Macbook Pro 13" Retina for cheap, I took the plunge and...it works!


I did this last night so have only used it for a few hours. I'll put up a more in depth review this weekend, but for now, here are my brief notes:


-Installed using the standard 64-bit Ubuntu 13.10 Gnome ISO on a thumb drive.
-Shrunk OSX down to 32gb (I despise OSX so have no desire to go back in there)
-Installed rEFInd
-Booted up the installer, check marked the "Install 3rd party" to get the Broadcom drivers (next screen prompted me to connect to a network, hurray!)
-Retina resolution wasn't that small if you have good eyes
-I chose my own partition scheme


Post-Install
-Function keys are defaulted to (need to remember where I saw to change that)
-Sleep works!
-All function keys work (not sure what F3 does or F4 though)
-Power draw. Without tweaking anything, it's hovering around 9 watts. I need to use further to verify if this is accurate. I have a script that got my X220 from 11watts down to 7.5 so I'm hoping that may work here.
-General experience. What can I say? It's made by Apple and is by far the nicest laptop I've used to date (I've had my hands on most of the ultrabooks when we were doing stuff for Microsoft, and they don't really compare as a complete package). Screen is awesome and Gnome is very responsive. No lagginess or other unwanted effects.




That's it for right now, but I'm hoping this will be useful for those that are looking to see if it's compatible. I'm really liking this community, so I hope this can be a way for me to give back. I'll post up more information over the weekend and then a few weeks after that.


Original instructions that I followed were here:
[http://mcaleely.com/jh/ToT/2013/07/04/ubuntu-13-04-macbookpro-10-2/](http://mcaleely.com/jh/ToT/2013/07/04/ubuntu-13-04-macbookpro-10-2/)


P.S. Contrary to what many have stated, at least with the 13" model (due to avoiding all the issues with a discrete card) installing Ubuntu on this machine was as easy (if not easier) than installing on a Windows 8 Thinkpad X220.

---

### Post by unsichtbarkeit on 2013-11-01
dear ryanchallman,
can you please confirm if suspend/resume is working for you.
and which driver do you use? nvidea or nouvou?
thanks alot

---

### Post by rchman on 2013-11-04
Yes, suspend/resume works as expected. Out of the 20 or so times, I've had to restart network-manager twice. Otherwise, stability has been very good, much better than my x220.

Graphics are neither. I purposely got the 13" model since it's using integrated graphics (Intel). I haven't seen any resoundingly successful report of getting the discrete cards working well.

---

### Post by Infra on 2013-11-14
Hello,

I just yesterday installed Ubuntu 13.10 to my MacbookPro Retina (MBP 10,1). Everything went pretty smoothly but now I have a strange problem which i can't figure out.

My ubuntu install works fine, but if I leave my MBP idle for a long time, for example night time. This morning i went to my mbp and the screen was blank (as it should be) but then I could not get the system to wake up again. I had to force shutdown the machine and start it again to get to the desktop.

Anything I could do to get this fixed?

I installed the ubuntu with refind and used the normal 13.10 desktop iso, i couldn't find the mac version of it. Should I have done it with the mac version ISO file or does it matter anymore. I read some tutorials and others sais (they were based on 13.04 though) that you should use the mac iso, and others said to use the normal desktop ISO file.

I have a pretty fresh install so I haven't installed any software or changed any drivers.

If anyone has a solution to this.

---

### Post by rchman on 2013-11-14
Seeing that you have the 15", this may be related to the discrete card (yours has a discrete right). Also, this may sound dumb, but have you checked to make sure it's not a screen brightness issue? Mine, when I lock it, dims the screen until it's off. Maybe try toggling the brightness when the screen is off? Does CTRL+ALT+F1 bring back the screen?

Also, standard ISO is recommended I believe. That's what I used.

---

### Post by Infra on 2013-11-14
> **ryanchallman said:**
> Seeing that you have the 15", this may be related to the discrete card (yours has a discrete right). Also, this may sound dumb, but have you checked to make sure it's not a screen brightness issue? Mine, when I lock it, dims the screen until it's off. Maybe try toggling the brightness when the screen is off? Does CTRL+ALT+F1 bring back the screen?

Also, standard ISO is recommended I believe. That's what I used.

Yes I have the nvidia card too in this lappy. But I haven't installed the nvidia drivers yet, so it's not that either i guess...

Nope not a brightness issue, tested it many times.

---

### Post by bcc2 on 2013-11-26
updated my laptop to 13.10..

My audio jack seems to be red now. Like digital is enabled. Also, my mic is always really low, I have to go and increase the volume. Ontop of this, the default output is never the speakers.....

What can I do? 

Anyone got sd card working yet?!

---

### Post by rchman on 2013-11-26
SD card for me is working out of the box. My audio jack is red, too. I haven't used the Mic so I'm not sure. My default always goes to the speakers. Maybe try doing a clean install? Otherwise, a startup script could probably take care of the mic and default output.

---

### Post by Umbra Diaboli on 2014-01-06
Hello Everyone,

I just want to check of anyone has found a solution on how to disable the Nvidia GPU? I found a suggestion here: [http://askubuntu.com/questions/370857/cant-adjust-screen-brightness-on-macbook-pro-10-1-ubuntu-13-10](http://askubuntu.com/questions/370857/cant-adjust-screen-brightness-on-macbook-pro-10-1-ubuntu-13-10)

Supposedly it can be done with the command line interface ([FONT=Ubuntu Mono]echo 'OFF' > /sys/kernel/debug/vgaswitcheroo/switch)
[/FONT]
Has anyone tried this? Btw, using gfxCardStatus on Mac OS to reboot to Ubuntu never worked for me.

My goal is to be able to adjust my screen backlight brightness.

Cheers!

(I'm using rMBP 10,1 (the 15 inch) - from mid 2012).

---

### Post by rchman on 2014-01-06
Have you followed this thread?

[http://ubuntuforums.org/showthread.php?t=2098304](http://ubuntuforums.org/showthread.php?t=2098304)

People mentioned that you have to use an old version of gfxCardStatus.

---

### Post by Umbra Diaboli on 2014-01-07
> **rchman said:**
> Have you followed this thread?

[http://ubuntuforums.org/showthread.php?t=2098304](http://ubuntuforums.org/showthread.php?t=2098304)

People mentioned that you have to use an old version of gfxCardStatus.

Thanks, I saw that thread a while ago, followed it, but the suggested solutions didn't work for me. I just tried a clean installation using "ubiquity -b". Now for some reason everytime I boot Ubuntu from rEFInd, the Intel card is the one that loads up... no idea why this happens, but it solved my problem! :D The brightness controls finally work :D (I'm not even using gfxCardStatus).

I then deleted my Mac partition, but left rEFInd on a small separate one - it seems rEFInd is necessary for the Intel GPU to load.

TL;DR: I finally have a clean rMBP just running Ubuntu working flawlessly, everything works :D Thanks everyone!

BTW: I've tried hooking up my Mac, w/ my now flawless Ubuntu 13:10, to my 27" Apple Home Cinema Display. Just when boot is about to finish both my Mac and external monitor go black (sometimes the external monitor will show a scramble on the top half). Has anyone encountered && solved this? Thanks a lot to everyone!

---

### Post by Umbra Diaboli on 2014-01-19
So I am “able” to choose GPU at boot after something very weird happened.


First, I would like to clarify I am the biggest noob in Linux - I was very confused by what GRUB & EFI were | and are, although I do get the notion/idea | etc. So please read this keeping in mind that I have no idea, absolutely no idea why the steps I took in the following story led to the outcome of me being able to choose GPU at boot. Maybe one of the gurus here knows the technicalities that led to this outcome :D


Let me first start from the beginning:


I was hoping to run Ubuntu as my only OS, I didn't want to have OSX installed on a separate partition. What I needed up doing was dividing my OSX partition. I gave OSX the minimum amount possible of space possible (33 GB), the rest was left as unallocated.


I then installed rEFInd, booted up into Ubuntu 13.10 using rEFInd, selected try Ubuntu, and installed with ubiquity -b to avoid installing GRUB. I booted into Mac OS, installed an old version of gfxCardStatus, selected Intel Only. Finally rebooted into Ubuntu and deleted my 33 GB OSX partition and just left it as unallocated – I have the feeling the gfxCardStatus step is unnecessary, but I performed it anyway.


This meant that I had a 460something GB – Ubuntu Only install which would always boot into the Intel GPU. rEFInd still showed up at boot, so everything was fine :D


I have a 27” Apple Home Cinema Display from 2010, I was able to use it with my 2011 MacBook Air running Ubuntu 12.04 and 12.10. I wanted to use it with my retina too. However, it isn't possible with the Intel GPU, so I decided to use the unallocated 33GB and make a GRUB installation of Ubuntu to be able to use the Nvidia GPU. This way I would be able to have 2 installs of Ubuntu, and just choose one or the other depending on the GPU I wanted to use.


Once I had it installed, I discovered that the GRUB installation also showed up on rEFInd at boot, and when chosen, Ubuntu would boot up and use the Intel GPU. However, if I rebooted my retina and pressed ALT/option as soon as I heard the tone, that 33GB install of Ubuntu would boot up with the Nvidia GPU.


After realizing this, I decided to delete my 460something install of Ubuntu, left it as unallocated, plugged in the Ubuntu USB, and reinstalled it – Install Ubuntu 13.10 alongside blah blah (from the menu that comes up when pressing the ALT/option at boot). This install of Ubuntu behaved as the 33GB install. I was able to boot into Ubuntu with the Intel GPU if used the rEFInd menu, and if I pressed ALT/option and used Mac's menu, Nvidia's GPU would be used – this mean I could used the same Ubuntu installation on my Apple Home Cinema display, and not have to switch from one installation to another.


Following this discovery, I deleted the 33GB partition and left the space unallocated. Now I have just one install that boots up into either Intel or Nvidia depending on what I choose, and that can be used with Apple's Home Cinema display :D


Note 1: When I installed Ubuntu using ubiquity -b, nothing showed up when booting with ALT/option - obviously :D
Note 2: Maybe this process has already been explained somewhere in the thread before... but like I said, I'm a really big noob when it comes to Linux, and sometimes it's hard to understand what the gurus write down / explain :D
Note 3: rMBP 10,1
Note 4: It's actually 426GB.

Like I said, maybe one of the gurus here knows the technical aspect of the story.

Here is my partition mess:

[IMG]http://i.imgur.com/ow0WDPV.png[/IMG]

---

