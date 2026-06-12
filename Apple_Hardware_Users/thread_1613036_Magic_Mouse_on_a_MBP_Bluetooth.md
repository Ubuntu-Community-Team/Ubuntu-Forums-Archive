---
title: "Magic Mouse on a MBP Bluetooth??"
date: 2010-11-04
forum: Apple Hardware Users
---

### Post by lael on 2010-11-04
I installed Ubuntu 10.10 on my MacbookPro6,1 and the Magic mouse worked OOTB.

but now that I'm trying to get scrolling (and more?) to work with the Magic Mouse, but I noticed that my machine isn't recognizing a bluetooth device.

When I start Bluetooth Preferences, it tells me that there are no bluetooth adapters present.  My bluetooth magic mouse is definitely working.

Any ideas on why the bluetooth device wasn't shown and how I get it to show up?  It works even when the 'bluetooth' service is stopped.
```

$ xinput list 
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; HID 05ac:820b                           	id=10	[slave  pointer  (2)]
&#9116;   &#8627; bcm5974                                 	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; HID 05ac:820a                           	id=9	[slave  keyboard (3)]
    &#8627; Apple Inc. Apple Internal Keyboard / Trackpad	id=11	[slave  keyboard (3)]
    &#8627; Built-in iSight                         	id=13	[slave  keyboard (3)]
```

```
$ sudo lsmod
Module                  Size  Used by
bluetooth              59213  0 
ipheth                  7214  0 
michael_mic             2188  0 
arc4                    1497  0 
snd_hda_codec_nvhdmi    14587  4 
binfmt_misc             7984  1 
ppdev                   6804  0 
parport_pc             30086  0 
snd_hda_codec_cirrus    12144  1 
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_nvhdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
nvidia              10221046  41 
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     8732  0 
joydev                 11363  0 
snd_timer              23850  2 snd_pcm,snd_seq
uvcvideo               62379  0 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               49359  1 uvcvideo
bcm5974                 8573  0 
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12486  1 videodev
applesmc               12872  0 
led_class               3393  1 applesmc
snd                    64117  13 snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   1965231  0 
intel_agp              32080  0 
input_polldev           4527  1 applesmc
intel_ips              13252  0 
lib80211                6175  2 lib80211_crypt_tkip,wl
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
video                  22176  0 
output                  2527  1 video
coretemp                6203  0 
lp                     10201  0 
parport                37032  3 ppdev,parport_pc,lp
hid_apple               5695  0 
usbhid                 42062  0 
hid                    84678  2 hid_apple,usbhid
firewire_ohci          24679  0 
firewire_core          54327  1 firewire_ohci
tg3                   135768  0 
crc_itu_t               1739  1 firewire_core
```

---

