---
title: "Can't suspend or hibernate - Asus k42j"
date: 2012-02-17
forum: Asus Ubuntu Support (CLOSED)
---

### Post by FariAzz on 2012-02-17
When going to suspend or hibernate I get a blank screen and the laptop overheats, then I have to do a hard reset.

-Ubuntu 11.10

My pm-suspend file:

[HTML]Initial commandline parameters: 
Thu Feb 16 13:26:11 CLST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux wayashash 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
snd_seq_dummy          12798  0 
ppp_deflate            13038  0 
zlib_deflate           27139  1 ppp_deflate
bsd_comp               12994  0 
ppp_async              17539  0 
crc_ccitt              12667  1 ppp_async
option                 25849  2 
usb_wwan               20491  1 option
cdc_ether              13536  0 
usbnet                 26212  1 cdc_ether
usbserial              47107  7 option,usb_wwan
usb_storage            57901  0 
uas                    18027  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  1 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
bbswitch               13355  0 
binfmt_misc            17540  1 
joydev                 17693  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  5 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
psmouse                73882  0 
serio_raw              13166  0 
snd_rawmidi            30547  1 snd_seq_midi
intel_ips              18089  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_laptop            19722  0 
sparse_keymap          13890  1 asus_laptop
ath9k                 127538  0 
mac80211              462092  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
mei                    41480  0 
soundcore              12680  1 snd
cfg80211              199630  3 ath9k,mac80211,ath
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
mxm_wmi                12979  0 
i915                  567092  8 
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
wmi                    19256  1 mxm_wmi
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
ahci                   26002  2 
libahci                26861  1 ahci
jme                    41301  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
             total       used       free     shared    buffers     cached
Mem:       7977064    5157096    2819968          0     218356    2786824
-/+ buffers/cache:    2151916    5825148
Swap:      3976188          0    3976188

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Feb 16 13:26:13 CLST 2012: performing suspend
Initial commandline parameters: 
Fri Feb 17 09:56:34 CLST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux wayashash 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
option                 25849  0 
cdc_ether              13536  0 
usb_wwan               20491  1 option
usbnet                 26212  1 cdc_ether
usbserial              47107  2 option,usb_wwan
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
bbswitch               13355  0 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
dm_crypt               23199  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
usb_storage            57901  0 
uas                    18027  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
arc4                   12529  2 
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
intel_ips              18089  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k                 127538  0 
mac80211              462092  1 ath9k
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ath9k_common           13839  1 ath9k
asus_laptop            19722  0 
sparse_keymap          13890  1 asus_laptop
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
mei                    41480  0 
cfg80211              199630  3 ath9k,mac80211,ath
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
mxm_wmi                12979  0 
ahci                   26002  2 
libahci                26861  1 ahci
wmi                    19256  1 mxm_wmi
i915                  567092  8 
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
jme                    41301  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
             total       used       free     shared    buffers     cached
Mem:       7977064    3018436    4958628          0     167512    1521676
-/+ buffers/cache:    1329248    6647816
Swap:      3976188          0    3976188

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Feb 17 09:56:36 CLST 2012: performing suspend[/HTML]

****

The line "/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed."

draws my attention of course. I read there is an issue with this, but don't know which actions I need to carry out in order to make it suspend. Also I'm not sure if that is what is causing the problem.

[http://lists.debian.org/debian-kernel/2011/08/msg00900.html](http://lists.debian.org/debian-kernel/2011/08/msg00900.html)

[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2316](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2316)

---

### Post by FariAzz on 2012-02-17
I tried this:

sudo service network-manager stop

and it doesn't work.

I'm focusing on Suspend first as it's the one I need the most.

---

### Post by Toz on 2012-02-17
Have a look at this fix: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug"). According to comments section, seems to work on similar systems.

---

### Post by FariAzz on 2012-02-17
Thanks that solved the suspend! :D

When hibernating it doesn't freeze, it just turns off, then when I turn it on it's just like a new session, it doesn't restore the previously open programs, windows, etc.

---

### Post by Toz on 2012-02-17
Is your swap partition encrypted? If so, hibernate will not work. What does the following return (enter command in a terminal window and post back results):
```

cat /etc/fstab

```

Also, swap partition needs to be at least as large as total memory.

---

### Post by FariAzz on 2012-02-17
I have my home directory encrypted.

The result of cat /etc/fstab is:


[HTML]
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=dbcc7c9b-9237-4f4d-b19a-d808c91a99d0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=8d0f65df-91f1-4a99-8035-247b3d723dd5 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
[/HTML]

---

### Post by FariAzz on 2012-02-17
Oh.. I have 4 GB of swap but recently upgraded to 8 GB of ram... 

If I increase the swap, do you think the fact that my home folder is encrypted will be a problem?

---

### Post by Toz on 2012-02-17
> **FariAzz said:**
> Oh.. I have 4 GB of swap but recently upgraded to 8 GB of ram... 

If I increase the swap, do you think the fact that my home folder is encrypted will be a problem?

Your swap partition is encrypted. When the system hibernates, it saves an image of the current state of the memory in the swap partition. When you resume, the system needs to retrieve that image but can't because its encrypted. The codes to decrypt it are in the encrypted partition. You need to have/use an unencrypted swap partition.

---

### Post by ayesha14 on 2012-02-18
Thanks for information

---

### Post by FariAzz on 2012-02-18
I'm sorry about my ignorance here but does the fact that my home folder is encrypted also mean that the swap partition is encrypted? is the swap partition located inside the home folder??

---

### Post by Toz on 2012-02-18
No, the swap is _not_ located inside your home folder. When you install ubuntu and select the "Encrypt my home folder" (or something like that) option, it also encrypts your swap file.

Here is a link to a blog entry that talks about turning on and off swap file encryption: [http://www.logilab.org/blogentry/29155]("http://www.logilab.org/blogentry/29155").

EDIT: An btw, as with any system work that you do, make sure your important data is backed up.

---

