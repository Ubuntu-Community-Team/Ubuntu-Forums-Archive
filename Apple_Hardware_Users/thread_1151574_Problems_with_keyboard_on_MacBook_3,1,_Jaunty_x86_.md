---
title: "Problems with keyboard on MacBook 3,1, Jaunty x86_64"
date: 2009-05-07
forum: Apple Hardware Users
---

### Post by smaffulli on 2009-05-07
Hello

I've finally installed Ubuntu Jaunty on my MacBook 3.1. Wi-fi works, video effects don't (but I don't care, for now). The main problem I have is that the internal keyboard of the laptop doesn't work. The sympton is that most of the keys don't send any code. Pressing all the keys of the first row, the numbers, only 789 work and pressing 0 sends /

This is the result of xev:

```
KeyRelease event, serial 33, synthetic NO, window 0x3a00001,
    root 0xac, subw 0x0, time 969114, (672,449), root:(677,518),
    state 0x10, keycode 81 (keysym 0xffb9, KP_9), same_screen YES,
    XLookupString gives 1 bytes: (39) "9"
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x3a00001,
    root 0xac, subw 0x0, time 970066, (672,449), root:(677,518),
    state 0x10, keycode 80 (keysym 0xffb8, KP_8), same_screen YES,
    XLookupString gives 1 bytes: (38) "8"
    XmbLookupString gives 1 bytes: (38) "8"
    XFilterEvent returns: False
```Other keys send nothing. Output of lsmod:

```
Module                  Size  Used by
tun                    20868  1 
i915                   75272  2 
drm                   123232  3 i915
binfmt_misc            18572  1 
ppdev                  16904  0 
btusb                  21784  2 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
uinput                 17408  2 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557364  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
joydev                 20864  0 
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
applesmc               37700  0 
hid_apple              15872  0 
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  29204  0 
appleir                13440  0 
led_class              13064  1 applesmc
ieee80211_crypt_tkip    17920  0 
iTCO_wdt               21712  0 
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
usbhid                 47040  0 
appletouch             19972  0 
input_polldev          12688  1 applesmc
wl                   1496016  0 
ieee80211_crypt        14596  2 ieee80211_crypt_tkip,wl
isight_firmware        11520  0 
output                 11648  1 video
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
pcspkr                 11136  0 
iTCO_vendor_support    12420  1 iTCO_wdt
intel_agp              39408  1 
ohci1394               42036  0 
ieee1394              108288  1 ohci1394
sky2                   63236  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```In lsusb I see:

```
Bus 007 Device 003: ID 05ac:022a Apple, Inc. Internal Keyboard/Trackpad (MacBook Pro) (ISO)
```My macbook is not pro, though. Maybe the kernel doesn't recognize the keyboard correctly? Am I the only one with this problem? Do you have any suggestion besides re-installing the 32bit?

thanks, stef

---

### Post by cyberdork33 on 2009-05-07
what selection did you make for the keyboard in your install?

---

### Post by smaffulli on 2009-05-08
> **cyberdork33 said:**
> what selection did you make for the keyboard in your install?

I don't remember what I selected at install time and I don't know if it worked during install because I installed using an external USB keybard. From Gnome I've tried to select many other layouts but the issue is that no signal is sent when pressing keys (see the xev output). I sense the error is lower than a layout issue.

Any other ideas?
stef

---

### Post by cyberdork33 on 2009-05-08
> **smaffulli said:**
> I don't remember what I selected at install time and I don't know if it worked during install because I installed using an external USB keybard. From Gnome I've tried to select many other layouts but the issue is that no signal is sent when pressing keys (see the xev output). I sense the error is lower than a layout issue.

Any other ideas?
stef
the only thing I can think of is if you tried the fixes posted for getting the touchpad to work properly, it might have messed things up for your keyboard, but then the whole thing wouldn't work I don't think... You seem to be the first encountering this strange issue and I am tempting to ask that you try a reinstall...

---

### Post by smaffulli on 2009-05-09
Reinstalling is not a GNU thing, that's for Windows :)

I tracked the culprit: not surprisingly it's all Broadcom's fault. I got the hint because I managed to login into gnome with the internal keyboard, but once the desktop loaded I couldn't type anything anymore.

I deactivated the proprietary driver and, happiness, the keyboard works well. Thanks everybody for the help, I'm filing a bug on launchpad now.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/374012](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/374012)

---

