---
title: "Once suspended, P8Z68-M PRO never wakes up"
date: 2011-11-26
forum: Asus Ubuntu Support (CLOSED)
---

### Post by m.suzuki on 2011-11-26
Hi, I'm posting from Japan.
7 days ago I asked this question in the forum of the Japanese site but so far I have got no answer.
So please let me ask here, too.

I'm having trouble when I try to suspend my computer, which I prepared as follows.

Motherboard: ASUS P8Z68-M PRO
CPU&#65306; Intel Core i5 2500K
Startup drive: 120 GB SSD connected to a SATA 6Gb/s port
OS&#65306; Ubuntu 11.10 installed using the "Japanese Remix CD" provided by the Ubuntu Japanese Team
Memory: 8GB (4GBx2)
HDD: none

If I select Suspend in the menu, my computer's power LED turns off, instead of blinking.
And then I'll never be able to wake it up again, until I shut it down by pressing the power button for more than 4 seconds.

I've heard about a similar problem in Windows computers fixed by disabling Internal PLL Overvoltage, but in my case that didn't work.

According to the ASUS website, the BIOS installed in my board is compatible with Core i5 2500K.
Should I do anything in Ubuntu, or should I just try updating BIOS to the latest version?

I'd appreciate your help and sorry for my poor English!

---

### Post by m.suzuki on 2011-11-26
After retrying with all BIOS settings reset to default, the following  lines were added  in /var/log/pm-suspend.log.

----------
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux (my computer name) 3.0.0-13-generic-pae #22-Ubuntu SMP Wed Nov 2 15:17:35 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
snd_hrtimer            12648  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
binfmt_misc            17292  1 
snd_hda_intel          28358  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
usbhid                 41905  0 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
hid                    77367  1 usbhid
snd_seq_midi           13132  0 
i915                  505143  3 
drm_kms_helper         32889  1 i915
mei                    36466  0 
drm                   196322  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
eeepc_wmi              12722  0 
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
asus_wmi               19333  1 eeepc_wmi
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13658  1 asus_wmi
video                  18908  1 i915
snd                    55902  15 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
ppdev                  12849  0 
parport_pc             32114  1 
mxm_wmi                12859  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  2 asus_wmi,mxm_wmi
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
xhci_hcd               77080  0 
r8169                  47200  0 
ahci                   21634  2 
libahci                25761  1 ahci
             total       used       free     shared    buffers     cached
Mem:       8176836     718240    7458596          0      33452     372088
-/+ buffers/cache:     312700    7864136
Swap:      8295420          0    8295420

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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
Sun Nov 27 11:33:18 JST 2011: performing suspend
----------

Is there anything I can do?

---

### Post by m.suzuki on 2011-12-03
I updated BIOS to the latest version, but there seems to be no effect. I'd expect this problem might be fixed in a future version of Ubuntu.

---

### Post by leth on 2012-01-11
I have an ASUS P8Z68-V LX motherboard (same CPU and RAM as OP) and it has the same problem.  When I select "Suspend" the system turns off (light does not flash, system draws no power according to my power bar which has a meter to measure power usage.)

If  I press the power button to resume, sometimes the power light will come back on and the system appears to resume but the display does not return (monitor is in sleep mode.)  I must pull the plug to get the system back.  However most of the time when I press the power button, the power light will come on for 3 or 4 seconds, then turn off for a moment, then back on for another 3 or 4 seconds, and keep repeating until I pull the plug.

I tried "Hibernate" but the screen just goes back for a few seconds, the hard drive clicks a couple times, then the screen comes back on to the "locked" screen and asks me for my password.  It never goes to sleep.

I have tried upgrading to the latest BIOS.   I also went through all of the BIOS settings (in Advanced Mode) but cannot find any settings related to power or sleep setting.

I think my next step will be to dual-boot this computer with Windows 7 and see if the problem occurs there.  I suspect everything will be OK in Windows, but if that is the case then I'm not sure what to do about it.

Any ideas for troubleshooting would be appreciated.

---

### Post by leth on 2012-01-11
FWIW, I installed Windows 7 Pro 64-bit and sleep mode works properly.  This at least tells me it's not the hardware.

Does anyone have any suggestions how to troubleshoot/fix this?

---

### Post by eL_vErDe on 2012-01-15
Hi,

Yes, I know how to fix it ;)

It seems there's an issue with all recent Asus motherboard, based upon P67, H67 or Z68 chipsets. It seems they are using ACPI 5.0 which is not fully working on Linux yet.

However, the patch is already available and fixed the issue for one guy and for me too. Lookg a second page of this thread:
[https://bbs.archlinux.org/viewtopic.php?id=117643&p=2](https://bbs.archlinux.org/viewtopic.php?id=117643&p=2)

Regards, Adam.

---

### Post by m.suzuki on 2012-01-16
Thank you!
It seems difficult for me because I know little about Linux, but I'm going to try it anyhow! O:)

---

### Post by eL_vErDe on 2012-01-17
Could help:

[http://blog.le-vert.net/?p=24](http://blog.le-vert.net/?p=24)

---

