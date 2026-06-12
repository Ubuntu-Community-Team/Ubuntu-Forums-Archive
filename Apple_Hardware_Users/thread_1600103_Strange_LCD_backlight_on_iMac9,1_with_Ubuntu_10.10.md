---
title: "Strange LCD backlight on iMac9,1 with Ubuntu 10.10"
date: 2010-10-18
forum: Apple Hardware Users
---

### Post by kesiev on 2010-10-18
Hi,

I've recently installed Ubuntu 10.10 on my iMac9,1...

```
kesiev@kesiev-iMac:~$ sudo dmidecode -s system-product-name
[sudo] password for kesiev: 
iMac9,1
kesiev@kesiev-iMac:~$
```

...and I've a strange behaviour of the LCD backlight. Installing the OS without the restricted drivers (obviously) I don't have any HW acceleration but hitting the light up/down buttons (i.e. F1 and F2) the backlight darken and light up accordingly (but just for the first half of the bar - going lower than the half will turn off the LCD definitively).
Installing any of the suggested nVidia drivers (version 173 and current) I've HW acceleration but backlight is no longer working - even buggy as before. Hitting the keys nothing happens.

I've tried to install mactel-support packages from PPA (mbp-nvidia-bl-dkms and nvidia-bl-dkms) and rebooted but nothing happened.

I don't know if is useful but the screen brightness widget on the bars has a no-go symbol and the slider is unclickable (moving that with the scroll wheel does nothing). Also the /sys/class/backlight directory is empty.

```
kesiev@kesiev-iMac:~$ ls /sys/class/backlight/mbp_backlight/brightness
ls: impossibile accedere a /sys/class/backlight/mbp_backlight/brightness: Nessun file o directory
kesiev@kesiev-iMac:~$ 
```

Am I missing something?

PS: the behaviour can be reverted uninstalling/reinstalling the restricted drivers.

---

### Post by kesiev on 2010-10-19
I hope that lspci -vvv output can help...

```

03:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400] (rev b1) (prog-if 00 [VGA controller])
        Subsystem: Apple Computer Inc. Device 00ad
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at 92000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at 80000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at 90000000 (64-bit, prefetchable) [size=32M]
        Region 5: I/O ports at 1000 [size=128]
        [virtual] Expansion ROM at 93000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia-current, nouveau, nvidiafb

```

The little snippet of code that is around [http://wiki.archlinux.org/index.php/IMac_Aluminium]("http://wiki.archlinux.org/index.php/IMac_Aluminium") does nothing too... :(

---

### Post by kesiev on 2010-10-19
Going without nVidia restricted drivers, partially working backlight pops up.

```

kesiev@kesiev-iMac:~$ ls /sys/class/backlight/nv_backlight
actual_brightness  brightness  max_brightness  subsystem
bl_power           device      power           uevent
kesiev@kesiev-iMac:~$ 

```

While values are not echo-able, hitting the light up and down something happens. Starting from max, for the first 6 times the screen actually dims down (the "sun gauge" is filled for its 2/3).
Then the backlight flashes rapidly at the 7th hit and then is totally turned off from the 8th.
Some infos from the 6th step:

```

kesiev@kesiev-iMac:/sys/class/backlight/nv_backlight$ cat actual_brightness 
719
kesiev@kesiev-iMac:/sys/class/backlight/nv_backlight$ cat brightness 
719
kesiev@kesiev-iMac:/sys/class/backlight/nv_backlight$ cat max_brightness 
1025

```

I really don't know if I've to open up a bug and in which tracker - I don't know the "competence" of this bug.
Is probably the last thing I really need for having a full working Ubuntu box (I've still not tested the mic but I'm getting a tan with high backlight!) so I'd like to help solving it as much as I can :)

---

### Post by kesiev on 2010-10-26
Motto of the week: *help by yourself*. I've wrote a patch for the nvidia_bl 0.17 driver for adding support for iMac9,1 backlight.
Its GeForce 9400 Is mainly smartdimmer compatible, with a pair of funny factors:

- the lower backlight value is 00e0 (224) and not 0000, with 800 steps to 0400 (1024) . Going under e0 makes the backlight flashing or turning off.

- everything works adding the infamous

```

 Option "RegistryDwords" "EnableBrightnessControl=1"

```

to the Device section in xorg.conf.

The patch is not probably the best patch you've ever seen, especially because I added a lower threshold to the backlight value, that is not seen outside from the driver...

```

kesiev@kesiev-iMac:/usr/src/nvidia_bl-0.17$ cat /sys/class/backlight/nvidia_backlight/max_brightness 
800 *<-- but the real registry value is 1024, so gnome-power-manager and sons are working well*

```

That means that I've added code here and there and I don't really know if it was the best way for doing this. By the way now the backlight is working also using gnome-power-manager - I'll use the patched driver for a while, since makes my Mac less aggressive with eyes ;)
I really hope that someone will have a look to this patch and eventually merge with the main driver since, as I said, on iMac9,1 Ubuntu works out of the box, except the backlight.

Obviously, the usual advice: since I've tried everything just on my iMac9,1 and any kernel-guru have seen/approved that, the patch can damage hardware, so use with care :)

---

### Post by kesiev on 2010-10-27
Errata: the lower value for backlight is not e0 but f0. e0 is surely lower but the backlight flashes after a bit.
I resend the patch with updated values. I'll keep on testing and then I'll try to submit this patch somewhere.

---

### Post by kesiev on 2011-10-19
New Ubuntu release, new update on this one-man-thread :(
With 10.11 and just adding the

```
Option "RegistryDwords" "EnableBrightnessControl=1"
```

thing on xorg.conf, I can handle backlight in some kind of acceptable way. The only drawback is that if I go under ~2/15 of the maximum brightness, the screen will turn off. I've to go back over ~13/15 to turn the screen on again.
What's more strange is that when the Mac is suspended with any brightness that is under the maximum, the backlight is not turned on when resuming, so I've to unlock the screen in semi-blindness and then restore the display brightness manually over the ~13/15 threshold to turn it on again.
I've done my suspend tests manually using:

```

sudo sh -c "sync; echo 1 > /sys/power/pm_trace; pm-suspend"

```

and waiting for the screen saver and I've the same results. Notice that the same thing happens when switching user from the user indicator, clicking the "Switch User Account..." option, so I'm not entirely sure that is some kind of suspend issue.
Backlight level is not saved when shutting down Ubuntu so I'm starting to think that all of these things are related together.

Any help?

---

### Post by kesiev on 2011-10-19
Little update:

```

kesiev@kesiev-iMac:~$ ls /sys/class/backlight/apple_backlight/
actual_brightness  brightness      power      type
bl_power           max_brightness  subsystem  uevent
kesiev@kesiev-iMac:~$ 

```

So, out of the box, I've backlight values on "apple_backlight" for mac9,1 instead of "nv_backlight".

---

