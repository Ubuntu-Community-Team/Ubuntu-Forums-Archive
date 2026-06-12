---
title: "Default backlight brightness settings"
date: 2011-07-08
forum: Apple Hardware Users
---

### Post by pygo on 2011-07-08
I've just reinstalled ubuntu 10.04 LTS on my macbook pro 5.5

I've forgotten where to go to change the backlight settings. The keys and everything else works out of the box. Just the step level is way too low, and when I switch to battery power the backlight goes very dark. Unusably dark if not used at night time.

The ambient light sensors appears to work OK as when I turn down the keyboard backlight all the way and then cover the sensor, it comes back on.

Making changes to pommed.conf don't seem to have an affect. I've tried doing a full restart and confirming my changes weren't undone. Both the on_batt setting and the step settings have no affect. I've also tried larger values with the assumption that the range is not 0-15 and is instead 0-254)

Power Management also doesn't seem to have any affect on disabling the auto-diming feature. Again, after restart there is no affect.

I've googled around for a few hours now and haven't come up with anything useful. I must be overlooking something as I feel I'm going in circles now. Any help is appreciated! I hope it's something simple and easy like a different config file I'd forgotten about.

---

### Post by johnmurrayvi on 2011-07-10
Did you try 'gconf-editor'? Under apps > gnome-power-manager > backlight it should have options for brightness with AC vs. battery.

---

### Post by pygo on 2011-07-11
Thanks for the tip, but still no success.

I should mention that the settings to do with display in the "Power Management" app don't have any affect.

I'm thinking it's something to do with nvidia drivers I added, or a configuration file somewhere. F1 and F2 do work for changing brightness nicely.

---

### Post by frc.gabriel on 2011-07-11
I install dkms and nvidia-bl-dkms and this works for me on my macbookpro 7,1:



root@MacBookPro:~# add-apt-repository ppa:mactel-support && sudo apt-get update


root@MacBookPro:~# apt-get install dkms nvidia-bl-dkms

(maybe be another name like "*mbp*-*nvidia*-bl")

and then load module:

root@MacBookPro:~# modprobe nvidia_bl

or reboot,
after this, when remove the power the backlight continues on same


sorry for the bad english. :D

---

### Post by pygo on 2011-07-12
No worries about the bad english. It really wasn't that bad, and much better than most of what's out there! :)


I did install those two packages from those repositories. I double checked to make sure it was running, as seen below. Along with a few others.
[INDENT]root@macbuntu:~# modprobe -l | grep nvidia
kernel/drivers/video/backlight/mbp_nvidia_bl.ko
kernel/drivers/video/nvidia/nvidiafb.ko
updates/dkms/nvidia_bl.ko
updates/dkms/nvidia-current.ko
root@macbuntu:~#
[/INDENT]I tried removing "mbp_nvidia_bl", but it did not unload. Even with the -f option specified. I assume this is because it may be in use? Sorry, not much of a newbie, but I've not worked with kernal compiles in some time so I've forgotten some things. hehe.

In addition, I found these other backlight modules running. I haven't tried removing any of them however. Perhaps I should give them a try?[INDENT]root@macbuntu:~# modprobe -l | grep backlight
kernel/drivers/video/backlight/lcd.ko
kernel/drivers/video/backlight/lms283gf05.ko
kernel/drivers/video/backlight/ltv350qv.ko
kernel/drivers/video/backlight/ili9320.ko
kernel/drivers/video/backlight/platform_lcd.ko
kernel/drivers/video/backlight/vgg2432a4.ko
kernel/drivers/video/backlight/tdo24m.ko
kernel/drivers/video/backlight/generic_bl.ko
kernel/drivers/video/backlight/progear_bl.ko
kernel/drivers/video/backlight/cr_bllcd.ko
kernel/drivers/video/backlight/da903x_bl.ko
kernel/drivers/video/backlight/mbp_nvidia_bl.ko
kernel/drivers/video/backlight/kb3886_bl.ko
kernel/drivers/video/backlight/wm831x_bl.ko
kernel/drivers/leds/ledtrig-backlight.ko
root@macbuntu:~#
[/INDENT]

---

### Post by johnmurrayvi on 2011-07-12
> **pygo said:**
> No worries about the bad english. It really wasn't that bad, and much better than most of what's out there! :)


I did install those two packages from those repositories. I double checked to make sure it was running, as seen below. Along with a few others.
[INDENT]root@macbuntu:~# modprobe -l | grep nvidia
kernel/drivers/video/backlight/mbp_nvidia_bl.ko
kernel/drivers/video/nvidia/nvidiafb.ko
updates/dkms/nvidia_bl.ko
updates/dkms/nvidia-current.ko
root@macbuntu:~#
[/INDENT]I tried removing "mbp_nvidia_bl", but it did not unload. Even with the -f option specified. I assume this is because it may be in use? Sorry, not much of a newbie, but I've not worked with kernal compiles in some time so I've forgotten some things. hehe.

In addition, I found these other backlight modules running. I haven't tried removing any of them however. Perhaps I should give them a try?[INDENT]root@macbuntu:~# modprobe -l | grep backlight
kernel/drivers/video/backlight/lcd.ko
kernel/drivers/video/backlight/lms283gf05.ko
kernel/drivers/video/backlight/ltv350qv.ko
kernel/drivers/video/backlight/ili9320.ko
kernel/drivers/video/backlight/platform_lcd.ko
kernel/drivers/video/backlight/vgg2432a4.ko
kernel/drivers/video/backlight/tdo24m.ko
kernel/drivers/video/backlight/generic_bl.ko
kernel/drivers/video/backlight/progear_bl.ko
kernel/drivers/video/backlight/cr_bllcd.ko
kernel/drivers/video/backlight/da903x_bl.ko
kernel/drivers/video/backlight/mbp_nvidia_bl.ko
kernel/drivers/video/backlight/kb3886_bl.ko
kernel/drivers/video/backlight/wm831x_bl.ko
kernel/drivers/leds/ledtrig-backlight.ko
root@macbuntu:~#
[/INDENT]

Does the file '/etc/modprobe.d/nvidia-bl-dkms.conf' exist? It should have been generated automatically when you installed nvidia-bl-dkms. Anyways, here's the file contents:
```
jmurray@jjmvi-mbp-ubuntu:~$ cat /etc/modprobe.d/nvidia-bl-dkms.conf
#
# This file has been automatically installed by nvidia-bl-dkms. Do not edit.
# If you do, don't forget to run `update-initramfs -k all -u` after updating.
#

# blacklist mbp_nvidia_bl in favor of nvidia_bl
blacklist mbp_nvidia_bl

```

---

### Post by pygo on 2011-07-12
It does exist, and is the same as yours.

I was also playing around with the idea of forcing the GPU to always run at 100mhz instead of throttling up. (compiz runs perfectly fine at 100mhz, so no need to throttle up to 450mhz). So I added in the coolbits 1 setting into xorg.conf. Voila my screen no longer darkens when I unplug the power cable!

Though I did try enabling the dim when on battery options again, to no affect. Not a big deal. I did get what I originally wanted. What would be even better is if it only dimmed a small amount, enough to know it's switched to battery power.

Here's what I added to xorg.conf in the Device section:
[INDENT]Option "Coolbits"   "1"
[/INDENT]
Then I rebooted and then ran the following command:
[INDENT]nvclock -nf 100
[/INDENT]

---

