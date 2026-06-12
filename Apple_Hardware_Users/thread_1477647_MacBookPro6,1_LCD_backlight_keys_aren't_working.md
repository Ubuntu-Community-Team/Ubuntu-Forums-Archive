---
title: "MacBookPro6,1 LCD backlight keys aren't working?"
date: 2010-05-09
forum: Apple Hardware Users
---

### Post by lael on 2010-05-09
I've installed Lucid on a MacBookPro6,1 (17" i7 / Install & Setup went smoothly) but I haven't been able to adjust the LCD Backlight.  I'm using a current nvidia driver (195.36.15) with the GeForce GT 330M discrete card.

I'm not really sure how I should go about figuring out how to fix this.  Any pointers would be helpful.

How would I manually adjust the LCD backlight?

I also am not able to adjust the keyboard backlight brightness with the fn keys (but am able to do this manually via /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness)

Also, where can I find the repository for pommed?

---

### Post by lael on 2010-05-09
> **lael said:**
> Also, where can I find the repository for pommed?

I've found [http://www.technologeek.org/projects/pommed/](http://www.technologeek.org/projects/pommed/) which references git://git.debian.org/pommed/pommed.git  So that answers that question.


Upon further review, it looks like pommed isn't running and dies :-(
```
sudo pommed -d
I: pommed v1.33git Apple laptops hotkeys handler
I: Copyright (C) 2006-2009 Julien BLACHE <jb@jblache.org>
pommed configuration:
 + General settings:
    fnmode: 1
 + sysfs backlight control:
    initial level: -1
    step: 1
    on_batt: 6
 + ATI X1600 backlight control:
    initial level: -1
    step: 10
    on_batt: 80
 + Intel GMA950 backlight control:
    initial level: 0xffffffff
    step: 0xf
    on_batt: 0x40
 + nVidia GeForce 8600M GT backlight control:
    initial level: -1
    step: 1
    on_batt: 6
 + Audio volume control:
    card: default
    initial volume: -1
    step: 10%
    beep: yes
    volume element: PCM
    speaker element: Front
    headphones element: Headphone
 + Keyboard backlight control:
    default level: 100
    step: 10
    auto on threshold: 20
    auto off threshold: 40
    auto enable: yes
    idle timer: 60s
    idle tickms: 2000ms
 + CD eject:
    enabled: yes
    device: /dev/dvd
 + Beep:
    enabled: no
    beepfile: /usr/share/pommed/goutte.wav
 + Apple Remote IR Receiver:
    enabled: no
DMI vendor name: [Apple Inc.]
DMI product name: [MacBookPro6,1]
[B]E: Unknown Apple machine: MacBookPro6,1
E: Unknown Apple machine[/B]

```

So how can I manually manipulate the backlight?

---

### Post by lael on 2010-05-10
> **lael said:**
> So how can I manually manipulate the backlight?

Following the rabbit trail, I've found that mbp-nvidia-bl-dkms && nvidia-bl-dkms don't support the MacBookPro6,1 yet and die when trying to insert the kernel modules, it fails with a 
```
FATAL: Error inserting nvidia_bl (/lib/modules/2.6.32-22-generic/updates/dkms/nvidia_bl.ko): No such device
```

I've seen the source code for each and they don't support the MacBookPro6,1 yet (working on getting them up to snuff).

Once it does support it I assume that I'll be able to control the brightness manually via something in this directory: /sys/class/backlight

Nvidia GeForce GT 330M is coming up with a PCI Device ID: 0x0a29
Graphics card appears to be working great: (glxgears runs @ 21680 fps)

I think I'll have to whip up a bug in launchpad for pommed, mbp-nvidia-bl-dkms and nvidia-bl-dkms when I get a little free time.

---

### Post by abel_bcn on 2010-05-10
I'm having the exact same issues with the 6,2, although my screen brightness hotkeys are working fine.

---

### Post by newbie80 on 2010-05-10
This may be of help - I followed the instructions posted below by [bfroemel]("http://ubuntuforums.org/member.php?u=217880") and they work on my mbp 6.2

[https://help.ubuntu.com/community/MacBookPro6-2/Lucid#LCD](https://help.ubuntu.com/community/MacBookPro6-2/Lucid#LCD)

---

### Post by lael on 2010-05-11
Mario Schwalbe updated mbp-nvidia-bl-dkms 0.24.3~lucid 
[https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=lucid)

This works great :-) 

Noteably the intel chip is responsible for the backlight adjustment.

---

### Post by abel_bcn on 2010-05-11
> **lael said:**
> Mario Schwalbe updated mbp-nvidia-bl-dkms 0.24.3~lucid 
[https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=lucid)

This works great :-) 

Noteably the intel chip is responsible for the backlight adjustment.

Installed flawlessly. I'll be trying it out tomorrow and report back, as I was having issues with high temperatures.

---

