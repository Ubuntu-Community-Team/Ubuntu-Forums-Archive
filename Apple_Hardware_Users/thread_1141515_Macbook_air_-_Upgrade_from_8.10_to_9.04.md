---
title: "Macbook air - Upgrade from 8.10 to 9.04"
date: 2009-04-28
forum: Apple Hardware Users
---

### Post by peakperformance on 2009-04-28
I had to do a few updates :

network :
Deactivate and activate hardware driver from System->Administration->Hardware Drivers GUI , then reboot.
Check 'Available to all Users' in System->Preferences->Network Connections for each wifi connection.

Keyboard : change FN key behavior
Create /etc/modprobe.d/options
Add options hid_apple fnmode=2
Run update-initramfs -u -v -k `uname -r`

Sound :
Add options snd_hda_intel model=mbp3 in /etc/modprobe.d/alsa-base.conf

---

### Post by peakperformance on 2009-04-28
adobe flash plugin does work in firefox 3.0.9
I installed the i386 version and I run jaunty 9.04 amd64.

---

### Post by benniboi on 2009-04-28
I made that change to the options file and my FN key is still not functioning.

I have found that under Jaunty my keyboard and mouse are a bit off. They worked fine under Intrepid.

Right click now seems to be three fingers and a click and it is ultra sensitive. As soon as I click it selects one of the options from the menu. It is extremely frustrating and renders the right click useless.

Attaching an external wireless keyboard I find that I can't use the arrow keys, I have to disable the num lock and use the keypad. The del, home, end, pg up and pg down also don't work, I have to use the del button on the keypad to delete. Really frustrating and it used to work fine without any modifications in Intrepid.

What setup do you have for your keyboard? And are you having any similar problems? Thanks.

---

### Post by terryroe on 2009-05-01
peakperformance,

I used your keyboard fix for my Apple keyboard and it worked perfectly, after I rebooted.  Others that try this may need to reboot after for the changes to take effect.

Thanks for the fix!

TR

---

