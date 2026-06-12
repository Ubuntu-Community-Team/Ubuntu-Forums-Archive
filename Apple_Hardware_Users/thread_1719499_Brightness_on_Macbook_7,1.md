---
title: "Brightness on Macbook 7,1"
date: 2011-04-01
forum: Apple Hardware Users
---

### Post by Pierre Lourens on 2011-04-01
Hello!

I have a white Macbook 7,1 and am running 11.04 beta 1.

I have worked out almost everything, sound being the main thing that didn't work.  The one thing I don't have working is my brightness control -- my laptop always displays at 100%.

I tried installing pommed and the dkms package from the Mactel PPA, but nothing works yet.  The wiki hasn't been updated to 7,1 for Maverick, let alone Natty.

Thanks for any help!

---

### Post by navaburo on 2011-05-14
I also have this problem.

Prior to enabling the nvidia driver, I could adjust the brightness while on battery, but not while on AC. Furthermore, while on battery the range was limited (could not go very bright) and re-plugging in the AC had no effect.

Now, with the nvidia drivers installed, the screen brightness is STUCK at 100%. This is killing my eyes and my battery. I literally need to squint to use the screen.

I have tried using some other solution suggested, but, nvclock tells me that my card is not supported. I tried "handy"'s C code, which returns "15" as my brightness but does not change the brightness. I have also tried pommed, but I get the following error:

cmerck@Hades:~/backlight$ sudo pommed -f -d
I: pommed v1.37 Apple laptops hotkeys handler
I: Copyright (C) 2006-2011 Julien BLACHE <jb@jblache.org>
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
    idle level: 0
 + CD eject:
    enabled: yes
    device: /dev/dvd
 + Beep:
    enabled: no
    beepfile: /usr/share/pommed/goutte.wav
 + Apple Remote IR Receiver:
    enabled: no
DMI vendor name: [Apple Inc.]
DMI product name: [MacBookPro7,1]
I: DMI machine check: running on a MacBookPro7,1
System: Linux 2.6.38-8-generic i686
[B]Failed to access brightness node: No such file or directory
Failed to access brightness node: No such file or directory
Failed to access brightness node: No such file or directory
E: sysfs backlight probe failed, no fallback for this machine
E: LCD backlight probe failed, check debug output[/B]
cmerck@Hades:~/backlight$ 


Any help would be greatly appreciated!

-Chris

---

### Post by samuaz on 2011-05-14
sudo apt-get install pommed work for my macbook 4,1 

but you can try this [http://ubuntuforums.org/showthread.php?p=10583183#6](http://ubuntuforums.org/showthread.php?p=10583183#6)

---

### Post by Pierre Lourens on 2011-06-01
Whoops, forgot to update this thread.  This fix worked for me:

[https://help.ubuntu.com/community/MacBookPro7-1/Natty#Screen](https://help.ubuntu.com/community/MacBookPro7-1/Natty#Screen)

---

