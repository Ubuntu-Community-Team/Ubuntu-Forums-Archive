---
title: "Does 6.06 work on OldWorld Macs?"
date: 2006-06-19
forum: Apple PPC Users
---

### Post by rexbinary on 2006-06-19
I have a OldWorld PowerMac G3 MiniTower (Beige) that is running Ubuntu 5.10 with no issues.

I'd like to install Xubuntu 6.06 on it, but the system requirements state it requires a NewWorld Mac, and I can't seem to find any confirmation that anyone has any distribution of Ubuntu 6.06 running on a OldWorld machine.

So if anyone has Ubuntu, Kubuntu, or especially Xubuntu 6.06 working properly on a OldWorld Mac could you please reply?

Thanks!

---

### Post by nkbj on 2006-06-19
I'm running Ubuntu 6.06 on a beige G3 (300 MHz MT) without any problems. You should use the alternate install CD to avoid a installer crash when it cannot find a newworld boot partition. SCSI will not work before you upgrade the kernel to 2.6.15-25.

Regards,
Niels Kristian

---

### Post by rexbinary on 2006-06-19
Great! Thank You for replying.

Is there anything different or special I need to do for installing 6.06 other then using the alternate CD?

For 5.10 I copied the kernel files to BootX, started installing 5.10 and when it got to the boot loader warning, I opened a console and copied the installed kernel files to BootX, rebooted and finished the install. Should that still work the same for 6.10?

Thanks again, and thanks for the heads-up on the SCSI.

---

### Post by nkbj on 2006-06-19
It's the same method as with 5.10 - using BootX and copying the files to the Mac OS partition.

---

### Post by rexbinary on 2006-06-19
Great, Thank You very much for your help. :)

---

### Post by rexbinary on 2006-06-20
Well I got Ubuntu 6.06 installed without a problem, but Xubuntu 6.06 is a different story.

During the install of Xubuntu 6.06, when it gets to the 'Select and Install Software' stage of the install, it installs 1 of 2 files, skips to 89% done, then installs 1 of 11 files. Basically nothing but the base system and some language files get installed, no X11, Xfce, etc.

When I install Ubuntu 6.06, at the 'Select and Install Software' stage of the install, it installs 1 of 2 files, 1 of 847 files, then 1 of 11 files.

Seems Xubuntu is not installing a few hundred files. ](*,)  

I re-downloaded the iso file and made a new CD just in case I had bad media, same result.

So has anyone successfully installed Xubuntu 6.06 on a OldWorld Mac?

---

### Post by Uta on 2006-06-22
I have a question in terms of what hardware will work and where to get "howto" instructions. I have a Tower Power Pro running Mac OS 9.2.2/memory is 472 MB /Video 16mb/ Processor PowerPC G3 300MHz. It has a usb card installed and a funky CR-W drive. All drives are scsi
The main HD is 6Gigs and the 2nd HD is 8 GIGs. It has been sitting around collecting dust but if there is a chance I can get it going with Linux, I certainly would like to try.
Is it possible? If so I don't mind reformatting the 2nd HD or the main HD for that matter. How does one get a terminal going in OS 9? I don't think the system came with a terminal? Thanks for any useful direction!

---

### Post by Niftium on 2006-06-22
[QUOTE=nkbj]It's the same method as with 5.10 - using BootX and copying the files to the Mac OS partition.[/QUOTE]

Same method, although beware of following some of the old 5.10 walkthroughs.  I've been trying to install 6.06 on my beige G3 desktop for a couple of days now.  It was a lot easier to find the kernel you needed to switch over to the Mac OS in 5.10.  But I eventually got Breezy, so I'm sure I'll get Dapper.

Has anyone attempted to use quik with any success?

---

### Post by Uta on 2006-06-23
I am in the middle of installing Dapper PPC on my Power Tower Pro and I am as far along as the cdrom is not being recognized, I need to load the right scsi driver, but which one? I had read before about "modprode mesh" well in 6.0.6 there isn't a "mesh" What have other's used? Thank you!

OK, I couldn't figure out the scsi driver to use for my internal cdrom so I am using an external firewire cdrom which is recognizes and I get as far as the partitioning section and it stops. Referring to this "You should use the alternate install CD to avoid a installer crash when it cannot find a newworld boot partition" 
I am using the 6.0.6 Alternate install and I am staring at a blue screen? It's crashed. Any help would be appreciated, thank you.
Hours later.
I decided to switch to 5.10, that seems to be more "old world mac" friendly. The first time I tried installing it stopped at about 80% "bug#3196", second time the same. The message is:
"No installable kernel was found in the defined APT sources. The current default kernel package is  'kernel-image'. You may try to continue though this rather strange error is probably fatal"

I would really appreciate some help with this, how do I install without this "bug" fatally ending my install. Thank you.

---

### Post by rexbinary on 2006-06-25
[QUOTE=rexbinary]Well I got Ubuntu 6.06 installed without a problem, but Xubuntu 6.06 is a different story.

During the install of Xubuntu 6.06, when it gets to the 'Select and Install Software' stage of the install, it installs 1 of 2 files, skips to 89% done, then installs 1 of 11 files. Basically nothing but the base system and some language files get installed, no X11, Xfce, etc.

When I install Ubuntu 6.06, at the 'Select and Install Software' stage of the install, it installs 1 of 2 files, 1 of 847 files, then 1 of 11 files.

Seems Xubuntu is not installing a few hundred files. ](*,)  

I re-downloaded the iso file and made a new CD just in case I had bad media, same result.

So has anyone successfully installed Xubuntu 6.06 on a OldWorld Mac?[/QUOTE]

UPDATE: I got Xubuntu 6.06 installed on my OldWorld PowerMac G3 MiniTower (Beige)

It seems something is wrong with the installer as it defaults to a server install rather then a standard desktop installation. Put the following line in the 'More kernel arguments :' field in BootX to instruct Xubuntu to perform a standard install:

```
preseed/file=/cdrom/preseed/xubuntu.seed quiet --
```

Ubuntu 6.06 does not seem to have this problem, it will install the standard desktop installation without adding anything to the 'More kernel arguments :' field in BootX. I have not tried Kubuntu 6.06, so I don't know if it requires kernel arguments or not to install properly.

---

### Post by Uta on 2006-06-25
[Rexbinary] did you install to a scsi drive, and is your processor a G3  from Apple  or is it an upgrade card?
The scsi install is key for me because although I was able to install to an IDE drive via an adapter card, Breezy freezes a lot. If I click on something and the system call hasn't completed and I click on something else everything crashes  and nothing to do but reboot. In my case I think it's a combination of booting from an IDE drive and the upgrade card. 
a dmesg message:
_________________________________________________________________________
[ 1473.972848] ide: failed opcode was: unknown
[ 1549.136462] hdg: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 1549.136522] hdg: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 1549.136548] ide: failed opcode was: unknown
[ 1549.146767] hdg: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 1549.146798] hdg: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 1549.146819] ide: failed opcode was: unknown
[ 1549.333487] hdg: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 1549.333535] hdg: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 1549.333560] ide: failed opcode was: unknown
_________________________________________________________________________
I'd really like to know if you installed your system to your main scsi drive and the 'details' Thanks!

---

### Post by rexbinary on 2006-06-25
I installed to a IDE drive on the built-in IDE controller, I don't have any SCSI devices on the system.

---

### Post by jmertic on 2006-06-27
I upgrade my 6500 from breezy to dapper via apt-get dist-upgrade; apt-get update. However, the kernel will not let me access my serial port modem ( on /dev/ttyS0 in breezy ). Any ideas on what could have happened?

---

### Post by rexbinary on 2006-06-28
[QUOTE=jmertic]I upgrade my 6500 from breezy to dapper via apt-get dist-upgrade; apt-get update. However, the kernel will not let me access my serial port modem ( on /dev/ttyS0 in breezy ). Any ideas on what could have happened?[/QUOTE]

They are not officially supporting OldWorld Macs anymore, so now it's a crap-shoot as to what OldWorld support is compiled in the kernel. My guess is OldWorld serial port modem support was not included in the kernel.

---

### Post by Tommy on 2006-10-21
> **jmertic said:**
> I upgrade my 6500 from breezy to dapper via apt-get dist-upgrade; apt-get update. However, the kernel will not let me access my serial port modem ( on /dev/ttyS0 in breezy ). Any ideas on what could have happened?

I'm replying to this old thread hoping you subscribed to it. I just upgraded my Wallstreet II from Breezy to Dapper (sorry I'm so late -- almost Edgy time!).

One of the changes in the Dapper kernel was to move the pmac_zilog driver to a module rather than compiling it in. I'm not sure why the kernel doesn't detect it and load it automatically, but you can load the driver and your serial port will work. (Mine does -- I just sync'ed my Palm using it.)

```
# sudo modprobe pmac_zilog
```

[edit] I tried the following and it works...

I just added this line to /etc/modules:

```
pmac_zilog
```

When I rebooted the module loaded just fine.  So that's what I recommend unless someone says otherwise. (If there's a newer/better way to load modules under newer kernels, let me know.)

---

