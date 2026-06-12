---
title: "Intel Macbook 64-bit: Upgraded to 4GB, 3GB shows up; Video very laggy"
date: 2009-09-26
forum: Apple Hardware Users
---

### Post by frikker on 2009-09-26
Hey everyone,
  I have a Macbook 2,1 Core 2 Duo running 64-bit Ubuntu.  I just bought 4GB PC5300 (2x2GB) and popped it in (I had 2GB prior).  These are my symptoms:
[LIST]
[*] I am dual booting OS X 10.5.  OS X shows 4GB of ram
[*] MemFree86 (I assume is 32-bit) shows 3GB of ram
[*] Ubuntu only shows 3GB of ram
[*] My video is very poor now.  Compiz is laggy, dragging windows is not good.  Before it was very snappy and quite impressive
[*] Not sure if this is connected or not, but my backlight appeared to be flickering in OS X.  Not the case on bootup or in Ubuntu.
[/LIST]

So... I am running a 64-bit kernel and seeing 32-bit memory limitations.  And why the video problems? I have not changed any drivers or anything else, other than swap hardware and boot up.  I imagine if I swap back to 2GB, my performance will come back. Is this related intel's PAE, which I thought was only for 32-bit hardware?

Thanks!
Blaine
  
```

10$ uname -a
Linux macbook 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

$ free -m
             total       used       free     shared    buffers     cached
Mem:          2953       1031       1921          0        114        427
-/+ buffers/cache:        489       2463
Swap:         7812          0       7812

9$ lsmod
Module                  Size  Used by
i915                   77960  2 
drm                   123232  3 i915
binfmt_misc            18572  1 
ppdev                  16904  0 
btusb                  21784  2 
bridge                 63776  0 
stp                    11140  1 bridge
bnep                   22912  2 
vboxnetadp            109356  0 
vboxnetflt            116972  0 
vboxdrv              1721612  1 vboxnetflt
uvcvideo               69640  0 
compat_ioctl32         18304  1 uvcvideo
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557492  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99464  2 snd_hda_intel,snd_pcm_oss
arc4                   10240  2 
snd_seq_dummy          11524  0 
ecb                    11392  2 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath9k                 310584  0 
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              251528  1 ath9k
iTCO_wdt               21712  0 
iTCO_vendor_support    12420  1 iTCO_wdt
joydev                 20992  0 
video                  29204  0 
snd                    78920  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
applesmc               37700  0 
output                 11648  1 video
soundcore              16800  1 snd
pcspkr                 11136  0 
cfg80211               43680  1 mac80211
appletouch             19972  0 
isight_firmware        11520  0 
input_polldev          12688  1 applesmc
intel_agp              39408  1 
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
led_class              13064  2 ath9k,applesmc
hid_apple              15872  0 
usbhid                 47040  0 
ohci1394               42164  0 
ieee1394              108288  1 ohci1394
sky2                   63364  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```

---

### Post by frikker on 2009-09-26
Update... my compiz benchmark test went from FULL (80fps or so) before the upgrade, to 22fps (1/4 full) now.

edit:
Also, I'm seeing this now in my dmesg:
[   18.890528] [drm:i915_setparam] *ERROR* unknown parameter 4
[   18.890550] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  795.820163] ACPI: EC: GPE storm detected, transactions will use polling mode
[ 2362.760889] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 2416.352084] ACPI: EC: missing confirmations, switch off interrupt mode.
[ 4318.773266] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 9513.813066] CE: hpet increasing min_delta_ns to 15000 nsec
[ 9693.815684] npviewer.bin[6736]: segfault at ff99cd48 ip 00000000ff99cd48 sp 00000000ff80339c error 14

Man.  My kernel seems to be choking on something.

---

### Post by frikker on 2009-09-27
I figured out whats up.  Basically, my macbook has the Intel 945 chipset (lucky me...).  The CPU is 64-bit, the OS is 64-bit, but the northbridge can only allocate 32-bit :(. OS X ignores the extra amount.  But here's the kicker: When you have more than 3GB, I guess there is some hardware memory allocation overlap, and that extra 1GB starts screwing with hardware interfacing.  This is why my video is laggy, and probably why the screen flickers in OS X.  In fact, **every time I reboot something different is messed up, sometimes wireless wont work, sometimes trackpad wont work, etc.**

Solution: Go to 3GB of ram, not 4GB of ram.  Thats it. :(

Either way, the performance of my video card when its not crippled is pretty phenomenal for being integrated, so I should be happy.  I'm just a little bit disappointed in Intel (and Apple) for letting this slip by...

Sources:
[http://superuser.com/questions/47327/64-bit-linux-kernel-only-seeing-3-of-4gb-after-upgrade/47563#47563](http://superuser.com/questions/47327/64-bit-linux-kernel-only-seeing-3-of-4gb-after-upgrade/47563#47563)
[http://www.ifrankie.com/?p=70](http://www.ifrankie.com/?p=70)
[http://forum.tabletpcreview.com/showthread.php?t=6809](http://forum.tabletpcreview.com/showthread.php?t=6809)

---

### Post by Cochise on 2009-10-20
Great information, just deciding weather to visit 64-bit again, I have decided I shall since I only have 2GB RAM.

---

### Post by Ravernomina on 2009-10-21
Try Running Apple Hardware diagnostics. On Boot up of the computer hold the D key down for about 10 seconds and it should boot up. Run the extended testing it will test the Memory VERY throughly and also will go through the Logic board. If nothing went wrong. Try reinstalling 64bit with a new ubuntu CD. Also check to see if your EFI is 64bit as well as this can cause problems with the Kernel.... And if all else fails one of your RAM DIMMS might of had a short. Also try swapping them (move on stick into the other slot and vise versa)


Run this Command in Terminal in Mac OSX

```
ioreg -l -p IODeviceTree | grep firmware-abi
```

Good Luck, Ravernomina

---

