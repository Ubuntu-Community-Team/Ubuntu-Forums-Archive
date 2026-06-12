---
title: "Can't now boot"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by DerekBaker on 2008-02-29
Last year I installed Ubuntu (7.04, x86 64) as an emergency OS alongside Win XP and everything was fine.

However now it is impossible to boot. After selecting one of the the two non-recovery options from the GRUB menu, I get two lines of text, then the monitor goes into standby. The power light of the computer is still on, but there is no activity on the HD light.

It's the same hardware as when I first installed. Windows boots fine and Memtest86+ passes.

Can boot from either of the recovery options, but have no idea what to do at the prompt.

Thanks for any help.

---

### Post by kellemes on 2008-02-29
What are the two lines of text?

---

### Post by kaginken on 2008-02-29
Does it still boot, but possibly w/o the monitor?  You can tell by listening for the boot up sound when you log in.  You don't need a monitor to log in, just type your name , enter, then password, you'll hear the ubuntu music if you're logging in.

Also, how long have you waited - sometimes when there's a monitor problem, it can take like 10 minutes then the monitor will finally come on - try letting it sit there for a LOOONG time before giving up, then you can try taking a look at your xorg.conf file once logged in.

Hope that helps!

---

### Post by DerekBaker on 2008-02-29
kellemes.

I get:

"Starting up ..."

Then:

"Kernal alive"
"Kernal direct mapping tables up to 1 [+ several zeroes] @ 8000-d000"

Couldn't get the exact figure as it flashed up briefly.


kaginken

I've given it about 10 minutes, but I'll leave it longer and see what happens.

---

### Post by Hospadar on 2008-02-29
If you havn't really used it since you installed it, you might want to just re-install gutsy.  If you have files on your linux partition(s) that you need to get at, you get get them from windows with the windows ext drivers [http://www.fs-driver.org/](http://www.fs-driver.org/)

Just choose manual partitioning when you get in the installation, and mount the linux partition to / (root) and check the "format" box on the linux partition (but not the windows one!)

---

### Post by Austin_KW on 2008-02-29
Edit the kernel options ine the grub menu (use 'e') and remove quiet and splash from the end of the line, this may allow you to see more output from the  boot

Or use a recovery mode to look at the logs
To look at dmesg for the previous boot
less /var/log/dmesg.0

---

### Post by Austin_KW on 2008-02-29
Also if you are not comfortable with the command line in recovery mode
**startx**    * will start the xserver for root*
or
**telinit 2**    *will boot to multiuser mode*
but both of these require a working x server config which is often where the problems is.

---

### Post by DerekBaker on 2008-02-29
Thanks Austin_KW, startx  got me to the desktop. Typing this from Ubuntu.

Would still like to get it booting normally. How can I get at boot logs from the desktop and what should I look for?

Unless I'm doing something wrong, I don't see splash and brief to delete.

Kaginken, Left the machine for an hour - still the same.

---

### Post by Austin_KW on 2008-03-01
If you can get startx in root then the problem  be something small.

All the logs are located in /var/log. You should be able to get there using any file browser (nautilus etc)
The main one is dmesg, the version for previous boot will be dmesg.0

Rather than startx try **telinit 2**. This will continue the normal boot to run-level 2 but without the splash and quiet so you should see more output.

---

### Post by DerekBaker on 2008-03-01
I am using telinit2.

I've since upgraded to 7.10, but still same problem.

Now I can briefly see a third message in a non-boot, also found in dmesg.0: 'PCI: Cannot allocate resource region 0 of device 0000:00:00.'

---

### Post by Austin_KW on 2008-03-01
Reboot to recovery mode and look at the end of previous dmesg log with
cat /var/log/dmesg.0

It may be some device that is causing a hang, Try disconnecting peripherals and adapters an see if it works, then reconnecting the them to see what is causing the hang. I have a wireless adapter that will hang one of my ubuntu systems so it might be something like this.

Did you upgrade from the CD and can the live CD run?

---

### Post by DerekBaker on 2008-03-01
End of dmesg.0 after normal(failed) boot and recovery mode boot>telinit 2:

```
[   33.891930] usbcore: registered new interface driver xpad
[   33.891972] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   33.903016] input: PC Speaker as /class/input/input4
[   33.916184] Linux video capture interface: v2.00
[   33.931204] pwc: Philips webcam module version 10.0.13 loaded.
[   33.931244] pwc: Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[   33.931291] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[   33.931336] pwc: the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[   33.931412] pwc: Logitech QuickCam 4000 Pro USB webcam detected.
[   33.931482] pwc: Registered as /dev/video0.
[   33.936428] usbcore: registered new interface driver Philips webcam
[   34.048273] gameport: EMU10K1 is pci0000:02:0a.1/gameport0, io 0xbc00, speed 1205kHz
[   34.178555] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 18
[   34.178604] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKA] -> GSI 18 (level, low) -> IRQ 18
[   34.272635] usbcore: registered new interface driver snd-usb-audio
[   34.966943] lp: driver loaded but no devices found
[   35.040205] Adding 2000084k swap on /dev/sda3.  Priority:-1 extents:1 across:2000084k
[   35.233942] EXT3 FS on sda2, internal journal
```

I'm wondering about the sound card - a Creative Audigy - it's my only PCI card (my X800 is AGP) and when I try to play a (speech) CD with RhythmBox I get static over badly distorted speech.

Did a network upgrade over the internet. Will get the LiveCD out.

EDIT: LiveCD (7.04) shows exactly the same problem.

---

### Post by Austin_KW on 2008-03-01
Sound reasonable. Did you add this card since the original linux install.

---

### Post by DerekBaker on 2008-03-01
Hardly. Same card I've been using since Jan 2002.

Where should I look to find information on the sound card?

Thanks.

---

### Post by kaginken on 2008-03-01
Try stripping down to the bare minimum req'd, i.e. hard drive, mouse monitor keyboard.  That's it.  Take the sound card out too.  Don't need that for now either.  This will eliminate all the variables.  Make sure nothing else is plugged in, heck, you can even unplug your cdrom drives and floppy if you have one.

THEN try it - and post the dmesg if you have problems.  If it works, start adding things back, one at a time until you figure out which one is breaking your ubuntu.  I'd start w/ that sound card if it's acting funny...

Hope that helps!  Rock on  :guitar:

---

### Post by DerekBaker on 2008-03-01
Don't really fancy opening the machine up at the moment, given my main Windows installation is okay.

Is there no way to disable hardware from within Ubuntu as I would using Window's Device Manager?

Thanks.

---

### Post by Austin_KW on 2008-03-01
> **DerekBaker said:**
> Don't really fancy opening the machine up at the moment, given my main Windows installation is okay.

Is there no way to disable hardware from within Ubuntu as I would using Window's Device Manager?

Thanks.

Yes you can blacklist the driver and stop it from loading 
add 
```
blacklist ***driverName***
```
to /etc/modprobe.d/blacklist
And it will not load the driver on next boot

You should be able to find the driver from the ids xxxx:yyyy
use **lsusb** and **lspci** or **lspci -nv** to find the ids. If you cant figure it out post the results back and someone should know which driver will be loaded for the given ids.

---

### Post by DerekBaker on 2008-03-01
lspci gives me, among other entries:

```
02:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
02:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

```

What do I put in the blacklist, the part after the colon?

---

### Post by Austin_KW on 2008-03-01
Those numbers 02.x.x are the pci id  (bus, slot etc), you need the device id from 
 lspci -n

I fould the driver for rev 04 here [http://www.mepis.org/docs/en/index.php/Sound_Driver_Database](http://www.mepis.org/docs/en/index.php/Sound_Driver_Database)
It might be the same one; but you might also try blacklisting the other creative labs drivers
```

blacklist snd-ca0106 
blacklist snd-emu10k1 

```

---

### Post by DerekBaker on 2008-03-01
You mean? ```
02:0a.0 0401: 1102:0004 (rev 03)
02:0a.1 0980: 1102:7003 (rev 03)
02:0a.2 0c00: 1102:4001
```

If so, where do I look for the matching names?

---

### Post by DerekBaker on 2008-03-01
> **Hospadar said:**
> If you havn't really used it since you installed it, you might want to just re-install gutsy.  If you have files on your linux partition(s) that you need to get at, you get get them from windows with the windows ext drivers [http://www.fs-driver.org/](http://www.fs-driver.org/)

Just choose manual partitioning when you get in the installation, and mount the linux partition to / (root) and check the "format" box on the linux partition (but not the windows one!)

I don't need to do anything to the swap partition? Hoping a reinstall might solve things.

---

### Post by Austin_KW on 2008-03-01
> **DerekBaker said:**
> You mean? ```
02:0a.0 0401: 1102:0004 (rev 03)
02:0a.1 0980: 1102:7003 (rev 03)
02:0a.2 0c00: 1102:4001
```

If so, where do I look for the matching names?

Yes, those are the device id (manufacturer:device)
Did you try the blacklist; It is likely one of the two drivers (probably snd-emu10k1)

---

### Post by DerekBaker on 2008-03-01
Can't reboot just now - am downloading the LiveCD for 7.10.

I can't see those names, e.g. in Device Manager. The names I need for the blacklist mechanism aren't in Linux?

EDIT: 7.10 LiveCD won't work either; doesn't seem any point installing it.

EDIT: Blacklisting seems to have worked, but still no boot.

---

### Post by DerekBaker on 2008-03-01
> **Austin_KW said:**
> Edit the kernel options ine the grub menu (use 'e') and remove quiet and splash from the end of the line, this may allow you to see more output from the  boot

Should have pursued this option. Using the menu was no good, but, after a suggestion on another forum, I edited GRUB's menu.lst to remove splash, and all is well - at least with the boot.

Thanks for all your efforts.

---

