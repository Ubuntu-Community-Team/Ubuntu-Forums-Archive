---
title: "Unable to complete hibernation"
date: 2014-07-15
forum: Any Other OS
---

### Post by Marcelo Ruiz on 2014-07-15
Hi All!
I am using linux mint 17 (based on Ubuntu 14.04) x64.
In previous editions my laptop (Toshiba Qosmio X500) hibernated with no problems, and now the hibernation process is somehow blocked with 100% CPU usage and the laptop never shuts down. Is anyone experiencing this behavior?
The suspend log (/var/log/pm-suspend.log) does show the hibernation finished:

```

Linux marcelo-qosmio 3.15.4-031504-generic #201407062345 SMP Mon Jul 7 03:46:19 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13193  2 
ccm                    17856  2 
bnep                   19884  2 
rfcomm                 75078  8 
binfmt_misc            17508  1 
nvidia              10527419  63 
snd_hda_codec_hdmi     48290  4 
snd_hda_codec_conexant    23005  1 
arc4                   12573  2 
snd_hda_codec_generic    70087  1 snd_hda_codec_conexant
snd_hda_intel          30608  5 
btusb                  32555  0 
snd_hda_controller     35518  1 snd_hda_intel
snd_hda_codec         144671  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              13613  1 snd_hda_codec
bluetooth             461855  22 bnep,btusb,rfcomm
uvcvideo               82299  0 
snd_pcm               113863  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
rtl8192se              64772  0 
videobuf2_vmalloc      13216  1 uvcvideo
snd_seq_midi           13564  0 
rtl_pci                27257  1 rtl8192se
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_seq_midi_event     14899  1 snd_seq_midi
6lowpan_iphc           18968  1 bluetooth
rtlwifi                69157  2 rtl_pci,rtl8192se
videobuf2_core         45435  1 uvcvideo
snd_rawmidi            30865  1 snd_seq_midi
mac80211              663788  3 rtl_pci,rtlwifi,rtl8192se
videodev              149504  2 uvcvideo,videobuf2_core
snd_seq                67636  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              30118  2 snd_pcm,snd_seq
coretemp               13638  0 
snd                    74235  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
kvm_intel             148919  0 
soundcore              12680  2 snd,snd_hda_codec
cfg80211              514187  2 mac80211,rtlwifi
kvm                   463855  1 kvm_intel
drm                   310655  3 nvidia
dm_multipath           23188  0 
toshiba_acpi           28280  0 
joydev                 17587  0 
scsi_dh                14873  1 dm_multipath
serio_raw              13483  0 
i7core_edac            24581  0 
lpc_ich                21176  0 
edac_core              63001  1 i7core_edac
sparse_keymap          13890  1 toshiba_acpi
toshiba_bluetooth      12867  0 
wmi                    19379  1 toshiba_acpi
mac_hid                13275  0 
parport_pc             32906  0 
ppdev                  17711  0 
lp                     17799  0 
parport                42481  3 lp,ppdev,parport_pc
dm_mirror              22356  0 
dm_region_hash         21010  1 dm_mirror
dm_log                 18527  2 dm_region_hash,dm_mirror
hid_logitech_dj        18647  0 
usbhid                 53121  0 
hid                   106436  3 usbhid,hid_logitech_dj
psmouse               113095  0 
firewire_ohci          45300  0 
ahci                   30167  5 
firewire_core          69403  1 firewire_ohci
sdhci_pci              23347  0 
libahci                32191  1 ahci
atl1c                  47016  0 
sdhci                  43409  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
video                  19932  0 
             total       used       free     shared    buffers     cached
Mem:       8164340    5443284    2721056      94588     445136    1717204
-/+ buffers/cache:    3280944    4883396
Swap:     16852148          0   16852148
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

Tue Jul 15 00:03:39 EDT 2014: performing suspend
Tue Jul 15 09:48:03 EDT 2014: Awake.
Tue Jul 15 09:48:03 EDT 2014: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Tue Jul 15 09:48:06 EDT 2014: Finished.


```

I even tried downloading an Ubuntu kernel compiled with Tux On Ice but the behavior repeats.
Any ideas on how to solve this? It is driving me nuts! ](*,)
Thanks!

---

### Post by ibjsb4 on 2014-07-16
This any help?

[http://ubuntuforums.org/showthread.php?t=2219403&p=13003320#post13003320](http://ubuntuforums.org/showthread.php?t=2219403&p=13003320#post13003320)

---

### Post by Marcelo Ruiz on 2014-07-18
Thanks for the answer, but it does not solve my problem. My computer already has hibernation activated. The problem is that it does not shutdown at the end of the process...
The weird thing is that it used to work!

---

### Post by Toz on 2014-07-18
> My computer already has hibernation activated.
The log snippet from your first post shows a suspend attempt, not a hibernate attempt. Are you sure that hibernate is enabled on your computer and that it is being executed? You can try:
```
sudo pm-hibernate
```
...from the command line to start the hibernate process manually.

Also helpful would be:
```
cat /var/log/syslog | grep PM:
```

*Since you are using Linux Mint, I'm going to move this thread to **Other OS/Distro Support***.

---

### Post by Marcelo Ruiz on 2014-07-19
@Toz:

Thanks for the answer. In a topic in the forum they were mentioning that file...
Anyway, I tried the command you gave me and hibernate now kind-of-worked: it turned off the computer. When I turned on the computer again, it started normally.
The log you requested after that attempt is:

```

Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880237600000-ffff88023f5fffff] on node 0
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009cfff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dbfff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000fffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf27c000-0xbf281fff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf3ec000-0xbf40efff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf46f000-0xbf46ffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf470000-0xbf4f0fff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf4f1000-0xbf70efff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf718000-0xbf71efff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf782000-0xbf79efff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf7cc000-0xbf7fefff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf800000-0xbfffffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafefff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfeaff000-0xfeafffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfebfffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec0ffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfecfffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed1bfff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed8ffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfedfffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.604324] Performance Events: PEBS fmt1+, 16-deep LBR, Nehalem events, Intel PMU driver.
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.619812] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.713004] PM: Registering ACPI NVS region [mem 0xbf470000-0xbf4f0fff] (528384 bytes)
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.713015] PM: Registering ACPI NVS region [mem 0xbf782000-0xbf79efff] (118784 bytes)
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.836087] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.836139] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.837523] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.838573] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.838840] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.839052] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.839262] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.839479] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.839701] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.839976] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.840681] pci 0000:00:1f.2: PME# supported from D3hot
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.841763] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.842026] pci 0000:07:00.1: PME# supported from D0 D1 D2 D3hot D3cold
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.842295] pci 0000:07:00.2: PME# supported from D0 D1 D2 D3hot D3cold
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.850701] pci 0000:0a:00.0: PME# supported from D0 D1 D2 D3hot
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.858678] pci 0000:0b:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.867685] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.867690] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
Jul 19 17:27:35 marcelo-qosmio kernel: [    1.655398] ima: No TPM chip found, activating TPM-bypass!
Jul 19 17:27:35 marcelo-qosmio kernel: [    1.660446] PM: Hibernation image not present or could not be loaded.
Jul 19 17:27:35 marcelo-qosmio kernel: [   17.952212] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140214/utaddress-258)

```

Any ideas?
Thanks!

---

### Post by Toz on 2014-07-19
Can you also post back the last attempt from /var/log/pm-suspend.log (or the whole file if its easier).

Maybe related:
> Jul 19 17:27:35 marcelo-qosmio kernel: [    1.660446] PM: Hibernation image not present or could not be loaded.
Do you have a swap file?
```
swapon -s
```
...and how much memory?
```
free -m
```

---

### Post by Marcelo Ruiz on 2014-07-19
Hi, yes I have a swap partition with big enouth: 16Gb (my computer has 8 Gb of RAM)

The info you requested is here:

```

marcelo@marcelo-qosmio ~ $ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda7                               partition	16852148	0	-1

marcelo@marcelo-qosmio ~ $ free -m
             total       used       free     shared    buffers     cached
Mem:          7972       2620       5352         63        112        888
-/+ buffers/cache:       1619       6353
Swap:        16457          0      16457


```

---

### Post by Marcelo Ruiz on 2014-07-19
Ok, I tried hibernating again and the problem I reported first happened: The computer won't shutdown and the CPU usage spiked.

The relevant info follows:


```
marcelo@marcelo-qosmio ~ $ cat /var/log/syslog | grep PM:
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009cfff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dbfff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000fffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf27c000-0xbf281fff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf3ec000-0xbf40efff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf46f000-0xbf46ffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf470000-0xbf4f0fff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf4f1000-0xbf70efff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf718000-0xbf71efff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf782000-0xbf79efff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf7cc000-0xbf7fefff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf800000-0xbfffffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafefff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfeaff000-0xfeafffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfebfffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec0ffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfecfffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed1bfff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed8ffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfedfffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.713004] PM: Registering ACPI NVS region [mem 0xbf470000-0xbf4f0fff] (528384 bytes)
Jul 19 17:27:35 marcelo-qosmio kernel: [    0.713015] PM: Registering ACPI NVS region [mem 0xbf782000-0xbf79efff] (118784 bytes)
Jul 19 17:27:35 marcelo-qosmio kernel: [    1.660446] PM: Hibernation image not present or could not be loaded.
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009cfff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dbfff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000fffff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf27c000-0xbf281fff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf3ec000-0xbf40efff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf46f000-0xbf46ffff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf470000-0xbf4f0fff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf4f1000-0xbf70efff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf718000-0xbf71efff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf782000-0xbf79efff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf7cc000-0xbf7fefff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf800000-0xbfffffff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafefff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfeaff000-0xfeafffff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfebfffff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec0ffff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfecfffff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed1bfff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed8ffff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfedfffff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.712693] PM: Registering ACPI NVS region [mem 0xbf470000-0xbf4f0fff] (528384 bytes)
Jul 19 18:24:44 marcelo-qosmio kernel: [    0.712704] PM: Registering ACPI NVS region [mem 0xbf782000-0xbf79efff] (118784 bytes)
Jul 19 18:24:44 marcelo-qosmio kernel: [    1.664836] PM: Hibernation image not present or could not be loaded.
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009cfff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dbfff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000fffff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf27c000-0xbf281fff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf3ec000-0xbf40efff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf46f000-0xbf46ffff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf470000-0xbf4f0fff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf4f1000-0xbf70efff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf718000-0xbf71efff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf782000-0xbf79efff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf7cc000-0xbf7fefff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf800000-0xbfffffff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafefff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfeaff000-0xfeafffff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfebfffff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec0ffff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfecfffff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed1bfff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed8ffff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfedfffff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.712905] PM: Registering ACPI NVS region [mem 0xbf470000-0xbf4f0fff] (528384 bytes)
Jul 19 18:29:30 marcelo-qosmio kernel: [    0.712916] PM: Registering ACPI NVS region [mem 0xbf782000-0xbf79efff] (118784 bytes)
Jul 19 18:29:30 marcelo-qosmio kernel: [    1.664021] PM: Hibernation image not present or could not be loaded.

```

One thing I noticed is that the log file is relevant to the resume part, not to the hibernation process. I wish I could read a log that describes what's going on during it...

---

### Post by Marcelo Ruiz on 2014-07-19
Also, from the following boot:

dmesg output:

```

marcelo@marcelo-qosmio ~ $ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.15.4-031504-generic (apw@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201407062345 SMP Mon Jul 7 03:46:19 UTC 2014
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.15.4-031504-generic root=UUID=8f793fc9-739e-4010-8744-27eec5e35496 ro persistent quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009c3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009c400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000dc000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bf27bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf27c000-0x00000000bf281fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf282000-0x00000000bf3ebfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf3ec000-0x00000000bf40efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf40f000-0x00000000bf46efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf46f000-0x00000000bf46ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf470000-0x00000000bf4f0fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf4f1000-0x00000000bf70efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf70f000-0x00000000bf717fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf718000-0x00000000bf71efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf71f000-0x00000000bf781fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf782000-0x00000000bf79efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf79f000-0x00000000bf7cbfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf7cc000-0x00000000bf7fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bf7ff000-0x00000000bf7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf800000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feaff000-0x00000000feafffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: TOSHIBA Qosmio X500/Qosmio X500, BIOS V2.90    12/10/2010
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x240000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 disabled
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 100000000 mask F00000000 write-back
[    0.000000]   4 base 200000000 mask FC0000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: update [mem 0xc0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbf800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f62f0-0x000f62ff] mapped at [ffff8800000f62f0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fed000, 0x01fedfff] PGTABLE
[    0.000000] BRK [0x01fee000, 0x01feefff] PGTABLE
[    0.000000] BRK [0x01fef000, 0x01feffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23fe00000-0x23fffffff]
[    0.000000]  [mem 0x23fe00000-0x23fffffff] page 2M
[    0.000000] BRK [0x01ff0000, 0x01ff0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23c000000-0x23fdfffff]
[    0.000000]  [mem 0x23c000000-0x23fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x23bffffff]
[    0.000000]  [mem 0x200000000-0x23bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbf27bfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbf1fffff] page 2M
[    0.000000]  [mem 0xbf200000-0xbf27bfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbf282000-0xbf3ebfff]
[    0.000000]  [mem 0xbf282000-0xbf3ebfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbf40f000-0xbf46efff]
[    0.000000]  [mem 0xbf40f000-0xbf46efff] page 4k
[    0.000000] BRK [0x01ff1000, 0x01ff1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xbf70f000-0xbf717fff]
[    0.000000]  [mem 0xbf70f000-0xbf717fff] page 4k
[    0.000000] BRK [0x01ff2000, 0x01ff2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xbf71f000-0xbf781fff]
[    0.000000]  [mem 0xbf71f000-0xbf781fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbf79f000-0xbf7cbfff]
[    0.000000]  [mem 0xbf79f000-0xbf7cbfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbf7ff000-0xbf7fffff]
[    0.000000]  [mem 0xbf7ff000-0xbf7fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] RAMDISK: [mem 0x349d8000-0x364e3fff]
[    0.000000] ACPI: RSDP 0x00000000000F6220 000024 (v02 TOSQCI)
[    0.000000] ACPI: XSDT 0x00000000BF7EEF64 000064 (v01 TOSQCI TOSQCI00 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 0x00000000BF7CE000 0000F4 (v03 INTEL  CALPELLA 06040000 PTEC 00000001)
[    0.000000] ACPI: DSDT 0x00000000BF7CF000 00FBD2 (v02 TOSQCI CALPELLA 06040000 INTL 20060912)
[    0.000000] ACPI: FACS 0x00000000BF79BFC0 000040
[    0.000000] ACPI: HPET 0x00000000BF7FED32 000038 (v01 INTEL  CALPELLA 06040000 PTEC 00000001)
[    0.000000] ACPI: MCFG 0x00000000BF7FED6A 00003C (v01 INTEL  CALPELLA 06040000 PTEC 00000001)
[    0.000000] ACPI: APIC 0x00000000BF7FEDA6 0000BC (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 0x00000000BF7FEE62 000028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 0x00000000BF7FEE8A 000176 (v01 TOSQCI TOSQCI00 06040000  LTP 00000000)
[    0.000000] ACPI: DMAR 0x00000000BF7DF000 000068 (v01 INTEL  CP_FIELD 00000001 INTL 00000001)
[    0.000000] ACPI: SSDT 0x00000000BF7CD000 0009F1 (v01 PmRef  CpuPm    00003000 INTL 20060912)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x23fffffff]
[    0.000000]   NODE_DATA [mem 0x23fff4000-0x23fff8fff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880237600000-ffff88023f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009bfff]
[    0.000000]   node   0: [mem 0x00100000-0xbf27bfff]
[    0.000000]   node   0: [mem 0xbf282000-0xbf3ebfff]
[    0.000000]   node   0: [mem 0xbf40f000-0xbf46efff]
[    0.000000]   node   0: [mem 0xbf70f000-0xbf717fff]
[    0.000000]   node   0: [mem 0xbf71f000-0xbf781fff]
[    0.000000]   node   0: [mem 0xbf79f000-0xbf7cbfff]
[    0.000000]   node   0: [mem 0xbf7ff000-0xbf7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x23fffffff]
[    0.000000] On node 0 totalpages: 2094203
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3995 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12180 pages used for memmap
[    0.000000]   DMA32 zone: 779488 pages, LIFO batch:31
[    0.000000]   Normal zone: 20480 pages used for memmap
[    0.000000]   Normal zone: 1310720 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dbfff]
[    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf27c000-0xbf281fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf3ec000-0xbf40efff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf46f000-0xbf46ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf470000-0xbf4f0fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf4f1000-0xbf70efff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf718000-0xbf71efff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf782000-0xbf79efff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf7cc000-0xbf7fefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf800000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafefff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeaff000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed8ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88023fc00000 s86592 r8192 d24000 u262144
[    0.000000] pcpu-alloc: s86592 r8192 d24000 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2061458
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.15.4-031504-generic root=UUID=8f793fc9-739e-4010-8744-27eec5e35496 ro persistent quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8134348K/8376812K available (7717K kernel code, 1177K rwdata, 3652K rodata, 1360K init, 1440K bss, 242464K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-7.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1728.998 MHz processor
[    0.000048] Calibrating delay loop (skipped), value calculated using timer frequency.. 3457.99 BogoMIPS (lpj=6915992)
[    0.000052] pid_max: default: 32768 minimum: 301
[    0.000062] ACPI: Core revision 20140214
[    0.014590] ACPI: All ACPI Tables successfully acquired
[    0.431483] Security Framework initialized
[    0.431499] AppArmor: AppArmor initialized
[    0.431501] Yama: becoming mindful.
[    0.432322] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.434463] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.435336] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.435351] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.435620] Initializing cgroup subsys memory
[    0.435627] Initializing cgroup subsys devices
[    0.435629] Initializing cgroup subsys freezer
[    0.435631] Initializing cgroup subsys net_cls
[    0.435633] Initializing cgroup subsys blkio
[    0.435635] Initializing cgroup subsys perf_event
[    0.435637] Initializing cgroup subsys net_prio
[    0.435639] Initializing cgroup subsys hugetlb
[    0.435660] CPU: Physical Processor ID: 0
[    0.435661] CPU: Processor Core ID: 0
[    0.435667] mce: CPU supports 9 MCE banks
[    0.435677] CPU0: Thermal monitoring handled by SMI
[    0.435689] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.435689] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.435689] tlb_flushall_shift: 6
[    0.435801] Freeing SMP alternatives memory: 28K (ffffffff81e7c000 - ffffffff81e83000)
[    0.437343] ftrace: allocating 32038 entries in 126 pages
[    0.457506] dmar: Host address width 36
[    0.457510] dmar: DRHD base: 0x000000fed90000 flags: 0x1
[    0.457519] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c90780106f0462 ecap f020e2
[    0.457521] dmar: RMRR base: 0x000000bf6e9000 end: 0x000000bf6fefff
[    0.458071] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.497739] smpboot: CPU0: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz (fam: 06, model: 1e, stepping: 05)
[    0.604320] Performance Events: PEBS fmt1+, 16-deep LBR, Nehalem events, Intel PMU driver.
[    0.604326] perf_event_intel: CPU erratum AAJ80 worked around
[    0.604328] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.604330] ... version:                3
[    0.604332] ... bit width:              48
[    0.604333] ... generic registers:      4
[    0.604334] ... value mask:             0000ffffffffffff
[    0.604336] ... max period:             000000007fffffff
[    0.604337] ... fixed-purpose events:   3
[    0.604338] ... event mask:             000000070000000f
[    0.606556] x86: Booting SMP configuration:
[    0.606558] .... node  #0, CPUs:      #1
[    0.617505] CPU1: Thermal monitoring handled by SMI
[    0.619716] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.619826]  #2
[    0.630870] CPU2: Thermal monitoring handled by SMI
[    0.633093]  #3<7>[    0.644140] CPU3: Thermal monitoring handled by SMI
[    0.657406]  #4
[    0.657407] CPU4: Thermal monitoring handled by SMI
[    0.670677]  #5
[    0.670677] CPU5: Thermal monitoring handled by SMI
[    0.683946]  #6
[    0.683946] CPU6: Thermal monitoring handled by SMI
[    0.697210]  #7
[    0.697210] CPU7: Thermal monitoring handled by SMI
[    0.699328] x86: Booted up 1 node, 8 CPUs
[    0.699333] smpboot: Total of 8 processors activated (27663.96 BogoMIPS)
[    0.705862] devtmpfs: initialized
[    0.712838] evm: security.selinux
[    0.712840] evm: security.SMACK64
[    0.712842] evm: security.ima
[    0.712843] evm: security.capability
[    0.712905] PM: Registering ACPI NVS region [mem 0xbf470000-0xbf4f0fff] (528384 bytes)
[    0.712916] PM: Registering ACPI NVS region [mem 0xbf782000-0xbf79efff] (118784 bytes)
[    0.714207] pinctrl core: initialized pinctrl subsystem
[    0.714292] regulator-dummy: no parameters
[    0.714331] RTC time: 18:28:12, date: 07/19/14
[    0.714383] NET: Registered protocol family 16
[    0.714546] cpuidle: using governor ladder
[    0.714548] cpuidle: using governor menu
[    0.714598] ACPI: bus type PCI registered
[    0.714600] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.714686] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.714689] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.751448] PCI: Using configuration type 1 for base access
[    0.751885] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.751887] mtrr: probably your BIOS does not setup all CPUs.
[    0.751888] mtrr: corrected configuration.
[    0.753570] ACPI: Added _OSI(Module Device)
[    0.753573] ACPI: Added _OSI(Processor Device)
[    0.753574] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.753576] ACPI: Added _OSI(Processor Aggregator Device)
[    0.757775] ACPI: Executed 1 blocks of module-level executable AML code
[    0.763220] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.763681] ACPI: SSDT 0x00000000BF71AA98 00032A (v01 PmRef  Cpu0Ist  00003000 INTL 20060912)
[    0.764228] ACPI: Dynamic OEM Table Load:
[    0.764231] ACPI: SSDT 0x0000000000000000 00032A (v01 PmRef  Cpu0Ist  00003000 INTL 20060912)
[    0.764388] ACPI: SSDT 0x00000000BF719018 000891 (v01 PmRef  Cpu0Cst  00003001 INTL 20060912)
[    0.765127] ACPI: Dynamic OEM Table Load:
[    0.765130] ACPI: SSDT 0x0000000000000000 000891 (v01 PmRef  Cpu0Cst  00003001 INTL 20060912)
[    0.772573] ACPI: SSDT 0x00000000BF71A718 000303 (v01 PmRef  ApIst    00003000 INTL 20060912)
[    0.773191] ACPI: Dynamic OEM Table Load:
[    0.773194] ACPI: SSDT 0x0000000000000000 000303 (v01 PmRef  ApIst    00003000 INTL 20060912)
[    0.776370] ACPI: SSDT 0x00000000BF718D98 000119 (v01 PmRef  ApCst    00003000 INTL 20060912)
[    0.776911] ACPI: Dynamic OEM Table Load:
[    0.776914] ACPI: SSDT 0x0000000000000000 000119 (v01 PmRef  ApCst    00003000 INTL 20060912)
[    0.828311] ACPI: Interpreter enabled
[    0.828319] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140214/hwxface-580)
[    0.828325] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140214/hwxface-580)
[    0.828344] ACPI: (supports S0 S3 S4 S5)
[    0.828346] ACPI: Using IOAPIC for interrupt routing
[    0.828387] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.835991] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.835998] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.836044] \_SB_.PCI0:_OSC invalid UUID
[    0.836046] _OSC request data:1 1f 0 
[    0.836051] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.837202] PCI host bridge to bus 0000:00
[    0.837206] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.837208] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.837211] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.837213] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.837216] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.837218] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.837220] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.837223] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfebfffff]
[    0.837234] pci 0000:00:00.0: [8086:d132] type 00 class 0x060000
[    0.837377] pci 0000:00:03.0: [8086:d138] type 01 class 0x060400
[    0.837438] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.837552] pci 0000:00:08.0: [8086:d155] type 00 class 0x088000
[    0.837686] pci 0000:00:08.1: [8086:d156] type 00 class 0x088000
[    0.837817] pci 0000:00:08.2: [8086:d157] type 00 class 0x088000
[    0.837943] pci 0000:00:08.3: [8086:d158] type 00 class 0x088000
[    0.838073] pci 0000:00:10.0: [8086:d150] type 00 class 0x088000
[    0.838185] pci 0000:00:10.1: [8086:d151] type 00 class 0x088000
[    0.838343] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.838379] pci 0000:00:1a.0: reg 0x10: [mem 0xf0906000-0xf09063ff]
[    0.838486] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.838572] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.838636] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.838666] pci 0000:00:1b.0: reg 0x10: [mem 0xf0900000-0xf0903fff 64bit]
[    0.838758] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.838823] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.838882] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.838966] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.839093] pci 0000:00:1c.3: [8086:3b48] type 01 class 0x060400
[    0.839176] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.839301] pci 0000:00:1c.4: [8086:3b4a] type 01 class 0x060400
[    0.839390] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.839457] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.839523] pci 0000:00:1c.6: [8086:3b4e] type 01 class 0x060400
[    0.839611] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.839677] pci 0000:00:1c.6: System wakeup disabled by ACPI
[    0.839746] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.839782] pci 0000:00:1d.0: reg 0x10: [mem 0xf0907000-0xf09073ff]
[    0.839888] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.839973] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.840028] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.840198] pci 0000:00:1f.0: [8086:3b03] type 00 class 0x060100
[    0.840427] pci 0000:00:1f.2: [8086:3b2f] type 00 class 0x010601
[    0.840461] pci 0000:00:1f.2: reg 0x10: [io  0x1830-0x1837]
[    0.840474] pci 0000:00:1f.2: reg 0x14: [io  0x1824-0x1827]
[    0.840487] pci 0000:00:1f.2: reg 0x18: [io  0x1828-0x182f]
[    0.840500] pci 0000:00:1f.2: reg 0x1c: [io  0x1820-0x1823]
[    0.840513] pci 0000:00:1f.2: reg 0x20: [io  0x1800-0x181f]
[    0.840526] pci 0000:00:1f.2: reg 0x24: [mem 0xf0908000-0xf09087ff]
[    0.840589] pci 0000:00:1f.2: PME# supported from D3hot
[    0.840709] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.840735] pci 0000:00:1f.3: reg 0x10: [mem 0xf0909000-0xf09090ff 64bit]
[    0.840761] pci 0000:00:1f.3: reg 0x20: [io  0x1840-0x185f]
[    0.840956] pci 0000:01:00.0: [10de:0cb1] type 00 class 0x030000
[    0.840969] pci 0000:01:00.0: reg 0x10: [mem 0xcc000000-0xccffffff]
[    0.840981] pci 0000:01:00.0: reg 0x14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.840993] pci 0000:01:00.0: reg 0x1c: [mem 0xce000000-0xcfffffff 64bit pref]
[    0.841002] pci 0000:01:00.0: reg 0x24: [io  0x2000-0x207f]
[    0.841012] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0007ffff pref]
[    0.841120] pci 0000:01:00.1: [10de:0be4] type 00 class 0x040300
[    0.841132] pci 0000:01:00.1: reg 0x10: [mem 0xcdefc000-0xcdefffff]
[    0.841269] pci 0000:00:03.0: PCI bridge to [bus 01]
[    0.841273] pci 0000:00:03.0:   bridge window [io  0x2000-0x2fff]
[    0.841277] pci 0000:00:03.0:   bridge window [mem 0xcc000000-0xcdefffff]
[    0.841282] pci 0000:00:03.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.841377] acpiphp: Slot [1] registered
[    0.841392] pci 0000:00:1c.0: PCI bridge to [bus 02-04]
[    0.841401] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.841410] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf03fffff]
[    0.841421] pci 0000:00:1c.0:   bridge window [mem 0xf0a00000-0xf0bfffff 64bit pref]
[    0.841532] pci 0000:07:00.0: [1217:10f7] type 00 class 0x0c0010
[    0.841552] pci 0000:07:00.0: reg 0x10: [mem 0x00000000-0x00000fff]
[    0.841680] pci 0000:07:00.0: supports D1 D2
[    0.841682] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.841784] pci 0000:07:00.1: [1217:8120] type 00 class 0x080501
[    0.841806] pci 0000:07:00.1: reg 0x10: [mem 0xf0501000-0xf05010ff]
[    0.841948] pci 0000:07:00.1: supports D1 D2
[    0.841950] pci 0000:07:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.842048] pci 0000:07:00.2: [1217:8130] type 00 class 0x018000
[    0.842070] pci 0000:07:00.2: reg 0x10: [mem 0xf0503000-0xf0503fff]
[    0.842098] pci 0000:07:00.2: reg 0x18: [mem 0xf0502000-0xf05027ff]
[    0.842227] pci 0000:07:00.2: supports D1 D2
[    0.842229] pci 0000:07:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.850280] pci 0000:00:1c.3: PCI bridge to [bus 07]
[    0.850291] pci 0000:00:1c.3:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.850414] pci 0000:0a:00.0: [10ec:8172] type 00 class 0x028000
[    0.850436] pci 0000:0a:00.0: reg 0x10: [io  0x4000-0x40ff]
[    0.850453] pci 0000:0a:00.0: reg 0x14: [mem 0xf0600000-0xf0603fff]
[    0.850591] pci 0000:0a:00.0: supports D1 D2
[    0.850593] pci 0000:0a:00.0: PME# supported from D0 D1 D2 D3hot
[    0.850650] pci 0000:0a:00.0: System wakeup disabled by ACPI
[    0.858239] pci 0000:00:1c.4: PCI bridge to [bus 0a]
[    0.858252] pci 0000:00:1c.4:   bridge window [io  0x4000-0x4fff]
[    0.858270] pci 0000:00:1c.4:   bridge window [mem 0xf0600000-0xf06fffff]
[    0.858394] pci 0000:0b:00.0: [1969:1063] type 00 class 0x020000
[    0.858423] pci 0000:0b:00.0: reg 0x10: [mem 0xf0400000-0xf043ffff 64bit]
[    0.858440] pci 0000:0b:00.0: reg 0x18: [io  0x5000-0x507f]
[    0.858568] pci 0000:0b:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.858605] pci 0000:0b:00.0: System wakeup disabled by ACPI
[    0.866243] pci 0000:00:1c.6: PCI bridge to [bus 0b]
[    0.866260] pci 0000:00:1c.6:   bridge window [io  0x5000-0x5fff]
[    0.866273] pci 0000:00:1c.6:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.866378] pci 0000:00:1e.0: PCI bridge to [bus 0c] (subtractive decode)
[    0.866393] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.866396] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.866398] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.866401] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.866403] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.866405] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.866408] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.866992] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.867073] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.867152] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.867230] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.867312] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.867392] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.867471] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.867549] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.867582] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    0.867588] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.867593] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.867655] PCI host bridge to bus 0000:ff
[    0.867658] pci_bus 0000:ff: root bus resource [bus ff]
[    0.867665] pci 0000:ff:00.0: [8086:2c52] type 00 class 0x060000
[    0.867725] pci 0000:ff:00.1: [8086:2c81] type 00 class 0x060000
[    0.867789] pci 0000:ff:02.0: [8086:2c90] type 00 class 0x060000
[    0.867846] pci 0000:ff:02.1: [8086:2c91] type 00 class 0x060000
[    0.867904] pci 0000:ff:03.0: [8086:2c98] type 00 class 0x060000
[    0.867959] pci 0000:ff:03.1: [8086:2c99] type 00 class 0x060000
[    0.868016] pci 0000:ff:03.4: [8086:2c9c] type 00 class 0x060000
[    0.868072] pci 0000:ff:04.0: [8086:2ca0] type 00 class 0x060000
[    0.868128] pci 0000:ff:04.1: [8086:2ca1] type 00 class 0x060000
[    0.868183] pci 0000:ff:04.2: [8086:2ca2] type 00 class 0x060000
[    0.868238] pci 0000:ff:04.3: [8086:2ca3] type 00 class 0x060000
[    0.868297] pci 0000:ff:05.0: [8086:2ca8] type 00 class 0x060000
[    0.868354] pci 0000:ff:05.1: [8086:2ca9] type 00 class 0x060000
[    0.868410] pci 0000:ff:05.2: [8086:2caa] type 00 class 0x060000
[    0.868467] pci 0000:ff:05.3: [8086:2cab] type 00 class 0x060000
[    0.868696] ACPI: Enabled 14 GPEs in block 00 to 3F
[    0.868788] ACPI : EC: GPE = 0x1e, I/O: command/status = 0x66, data = 0x62
[    0.868935] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.868941] vgaarb: loaded
[    0.868942] vgaarb: bridge control possible 0000:01:00.0
[    0.869192] SCSI subsystem initialized
[    0.869249] libata version 3.00 loaded.
[    0.869277] ACPI: bus type USB registered
[    0.869304] usbcore: registered new interface driver usbfs
[    0.869315] usbcore: registered new interface driver hub
[    0.869345] usbcore: registered new device driver usb
[    0.869498] PCI: Using ACPI for IRQ routing
[    0.876099] PCI: pci_cache_line_size set to 64 bytes
[    0.876218] e820: reserve RAM buffer [mem 0x0009c400-0x0009ffff]
[    0.876220] e820: reserve RAM buffer [mem 0xbf27c000-0xbfffffff]
[    0.876223] e820: reserve RAM buffer [mem 0xbf3ec000-0xbfffffff]
[    0.876226] e820: reserve RAM buffer [mem 0xbf46f000-0xbfffffff]
[    0.876228] e820: reserve RAM buffer [mem 0xbf718000-0xbfffffff]
[    0.876231] e820: reserve RAM buffer [mem 0xbf782000-0xbfffffff]
[    0.876233] e820: reserve RAM buffer [mem 0xbf7cc000-0xbfffffff]
[    0.876235] e820: reserve RAM buffer [mem 0xbf800000-0xbfffffff]
[    0.876348] NetLabel: Initializing
[    0.876350] NetLabel:  domain hash size = 128
[    0.876351] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.876367] NetLabel:  unlabeled traffic allowed by default
[    0.876485] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.876495] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 40, 41, 42, 43, 44, 0
[    0.876502] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.878563] hpet: hpet2 irq 40 for MSI
[    0.878637] hpet: hpet3 irq 41 for MSI
[    0.878712] hpet: hpet4 irq 42 for MSI
[    0.878780] hpet: hpet5 irq 43 for MSI
[    0.878851] hpet: hpet6 irq 44 for MSI
[    0.879022] Switched to clocksource hpet
[    0.885885] AppArmor: AppArmor Filesystem Enabled
[    0.885915] pnp: PnP ACPI init
[    0.885934] ACPI: bus type PNP registered
[    0.886168] pnp 00:00: [dma 4]
[    0.886206] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.886360] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.886410] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.886502] system 00:03: [io  0x03e0-0x03e1] has been reserved
[    0.886505] system 00:03: [io  0x0680-0x069f] has been reserved
[    0.886508] system 00:03: [io  0x0500-0x050f] has been reserved
[    0.886510] system 00:03: [io  0x0600-0x0603] has been reserved
[    0.886513] system 00:03: [io  0xffff] has been reserved
[    0.886516] system 00:03: [io  0x0400-0x047f] could not be reserved
[    0.886519] system 00:03: [io  0x1180-0x11ff] has been reserved
[    0.886521] system 00:03: [io  0x164e-0x164f] has been reserved
[    0.886524] system 00:03: [io  0xfe00] has been reserved
[    0.886528] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.886601] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.886850] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.886902] pnp 00:06: Plug and Play ACPI device, IDs SYN102f SYN1000 SYN0002 PNP0f13 (active)
[    0.887014] pnp 00:07: disabling [mem 0xf0501100-0xf05013ff] because it overlaps 0000:00:1c.3 BAR 14 [mem 0xf0500000-0xf05fffff]
[    0.887089] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.887496] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.887499] system 00:08: [mem 0xfed1b000-0xfed1bfff] has been reserved
[    0.887502] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
[    0.887505] system 00:08: [mem 0xf090a000-0xf090afff] has been reserved
[    0.887508] system 00:08: [mem 0xc0000000-0xc0000fff] has been reserved
[    0.887511] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.887514] system 00:08: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.887516] system 00:08: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.887519] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.887522] system 00:08: [mem 0xff808000-0xff8080ff] has been reserved
[    0.887525] system 00:08: [mem 0xff000000-0xffffffff] could not be reserved
[    0.887527] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.887531] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.887773] pnp: PnP ACPI: found 9 devices
[    0.887775] ACPI: bus type PNP unregistered
[    0.895393] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 07] add_size 1000
[    0.895398] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 07] add_size 200000
[    0.895412] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0a] add_size 200000
[    0.895425] pci 0000:00:1c.6: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0b] add_size 200000
[    0.895442] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.895445] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.895448] pci 0000:00:1c.6: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.895451] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.895460] pci 0000:00:1c.3: BAR 15: assigned [mem 0xc0100000-0xc02fffff 64bit pref]
[    0.895467] pci 0000:00:1c.4: BAR 15: assigned [mem 0xc0300000-0xc04fffff 64bit pref]
[    0.895474] pci 0000:00:1c.6: BAR 15: assigned [mem 0xc0500000-0xc06fffff 64bit pref]
[    0.895477] pci 0000:00:1c.3: BAR 13: assigned [io  0x6000-0x6fff]
[    0.895482] pci 0000:01:00.0: BAR 6: assigned [mem 0xcd000000-0xcd07ffff pref]
[    0.895485] pci 0000:00:03.0: PCI bridge to [bus 01]
[    0.895488] pci 0000:00:03.0:   bridge window [io  0x2000-0x2fff]
[    0.895493] pci 0000:00:03.0:   bridge window [mem 0xcc000000-0xcdefffff]
[    0.895496] pci 0000:00:03.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.895502] pci 0000:00:1c.0: PCI bridge to [bus 02-04]
[    0.895509] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.895518] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf03fffff]
[    0.895527] pci 0000:00:1c.0:   bridge window [mem 0xf0a00000-0xf0bfffff 64bit pref]
[    0.895539] pci 0000:07:00.0: BAR 0: assigned [mem 0xf0500000-0xf0500fff]
[    0.895549] pci 0000:00:1c.3: PCI bridge to [bus 07]
[    0.895556] pci 0000:00:1c.3:   bridge window [io  0x6000-0x6fff]
[    0.895565] pci 0000:00:1c.3:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.895574] pci 0000:00:1c.3:   bridge window [mem 0xc0100000-0xc02fffff 64bit pref]
[    0.895585] pci 0000:00:1c.4: PCI bridge to [bus 0a]
[    0.895593] pci 0000:00:1c.4:   bridge window [io  0x4000-0x4fff]
[    0.895602] pci 0000:00:1c.4:   bridge window [mem 0xf0600000-0xf06fffff]
[    0.895611] pci 0000:00:1c.4:   bridge window [mem 0xc0300000-0xc04fffff 64bit pref]
[    0.895622] pci 0000:00:1c.6: PCI bridge to [bus 0b]
[    0.895630] pci 0000:00:1c.6:   bridge window [io  0x5000-0x5fff]
[    0.895639] pci 0000:00:1c.6:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.895648] pci 0000:00:1c.6:   bridge window [mem 0xc0500000-0xc06fffff 64bit pref]
[    0.895658] pci 0000:00:1e.0: PCI bridge to [bus 0c]
[    0.895674] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.895677] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.895679] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.895681] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.895684] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.895686] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.895688] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xfebfffff]
[    0.895691] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.895693] pci_bus 0000:01: resource 1 [mem 0xcc000000-0xcdefffff]
[    0.895695] pci_bus 0000:01: resource 2 [mem 0xce000000-0xdfffffff 64bit pref]
[    0.895698] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.895700] pci_bus 0000:02: resource 1 [mem 0xf0000000-0xf03fffff]
[    0.895703] pci_bus 0000:02: resource 2 [mem 0xf0a00000-0xf0bfffff 64bit pref]
[    0.895705] pci_bus 0000:07: resource 0 [io  0x6000-0x6fff]
[    0.895707] pci_bus 0000:07: resource 1 [mem 0xf0500000-0xf05fffff]
[    0.895710] pci_bus 0000:07: resource 2 [mem 0xc0100000-0xc02fffff 64bit pref]
[    0.895712] pci_bus 0000:0a: resource 0 [io  0x4000-0x4fff]
[    0.895715] pci_bus 0000:0a: resource 1 [mem 0xf0600000-0xf06fffff]
[    0.895717] pci_bus 0000:0a: resource 2 [mem 0xc0300000-0xc04fffff 64bit pref]
[    0.895719] pci_bus 0000:0b: resource 0 [io  0x5000-0x5fff]
[    0.895722] pci_bus 0000:0b: resource 1 [mem 0xf0400000-0xf04fffff]
[    0.895724] pci_bus 0000:0b: resource 2 [mem 0xc0500000-0xc06fffff 64bit pref]
[    0.895727] pci_bus 0000:0c: resource 4 [io  0x0000-0x0cf7]
[    0.895729] pci_bus 0000:0c: resource 5 [io  0x0d00-0xffff]
[    0.895731] pci_bus 0000:0c: resource 6 [mem 0x000a0000-0x000bffff]
[    0.895734] pci_bus 0000:0c: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.895736] pci_bus 0000:0c: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.895738] pci_bus 0000:0c: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.895741] pci_bus 0000:0c: resource 10 [mem 0xc0000000-0xfebfffff]
[    0.895770] NET: Registered protocol family 2
[    0.895967] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.896270] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.896668] TCP: Hash tables configured (established 65536 bind 65536)
[    0.896693] TCP: reno registered
[    0.896707] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.896791] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.896912] NET: Registered protocol family 1
[    0.897586] pci 0000:01:00.0: Boot video device
[    0.897654] PCI: CLS 64 bytes, default 64
[    0.897714] Trying to unpack rootfs image as initramfs...
[    1.532638] Freeing initrd memory: 27696K (ffff8800349d8000 - ffff8800364e4000)
[    1.532721] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.532724] software IO TLB [mem 0xbb27c000-0xbf27c000] (64MB) mapped at [ffff8800bb27c000-ffff8800bf27bfff]
[    1.532777] Simple Boot Flag at 0x36 set to 0x1
[    1.533205] microcode: CPU0 sig=0x106e5, pf=0x10, revision=0x3
[    1.533217] microcode: CPU1 sig=0x106e5, pf=0x10, revision=0x3
[    1.533228] microcode: CPU2 sig=0x106e5, pf=0x10, revision=0x3
[    1.533238] microcode: CPU3 sig=0x106e5, pf=0x10, revision=0x3
[    1.533248] microcode: CPU4 sig=0x106e5, pf=0x10, revision=0x3
[    1.533263] microcode: CPU5 sig=0x106e5, pf=0x10, revision=0x3
[    1.533273] microcode: CPU6 sig=0x106e5, pf=0x10, revision=0x3
[    1.533282] microcode: CPU7 sig=0x106e5, pf=0x10, revision=0x3
[    1.533349] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.533371] Scanning for low memory corruption every 60 seconds
[    1.533825] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    1.533854] Initialise system trusted keyring
[    1.533875] audit: initializing netlink subsys (disabled)
[    1.533893] audit: type=2000 audit(1405794493.000:1): initialized
[    1.571862] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.573864] zbud: loaded
[    1.574108] VFS: Disk quotas dquot_6.5.2
[    1.574157] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.574865] fuse init (API version 7.23)
[    1.574988] msgmni has been set to 15941
[    1.575057] Key type big_key registered
[    1.575821] Key type asymmetric registered
[    1.575823] Asymmetric key parser 'x509' registered
[    1.575870] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.575943] io scheduler noop registered
[    1.575945] io scheduler deadline registered (default)
[    1.575985] io scheduler cfq registered
[    1.577018] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.577037] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.577106] intel_idle: MWAIT substates: 0x1120
[    1.577122] intel_idle: v0.4 model 0x1E
[    1.577124] intel_idle: lapic_timer_reliable_states 0x2
[    1.577612] ipmi message handler version 39.2
[    1.579715] ACPI: AC Adapter [ACAD] (on-line)
[    1.579879] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.579888] ACPI: Power Button [PWRB]
[    1.579990] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    1.580392] ACPI: Lid Switch [LID]
[    1.580502] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.580509] ACPI: Power Button [PWRF]
[    1.582882] thermal LNXTHERM:00: registered as thermal_zone0
[    1.582888] ACPI: Thermal Zone [THRM] (74 C)
[    1.582961] GHES: HEST is not enabled!
[    1.583042] ACPI: Battery Slot [BAT1] (battery absent)
[    1.583234] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.587550] Linux agpgart interface v0.103
[    1.591151] brd: module loaded
[    1.592976] loop: module loaded
[    1.594007] libphy: Fixed MDIO Bus: probed
[    1.594268] tun: Universal TUN/TAP device driver, 1.6
[    1.594272] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.594476] PPP generic driver version 2.4.2
[    1.594687] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.594696] ehci-pci: EHCI PCI platform driver
[    1.595155] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.595171] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.595212] ehci-pci 0000:00:1a.0: debug port 2
[    1.599261] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.599309] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf0906000
[    1.610759] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.610862] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.610868] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.610872] usb usb1: Product: EHCI Host Controller
[    1.610877] usb usb1: Manufacturer: Linux 3.15.4-031504-generic ehci_hcd
[    1.610881] usb usb1: SerialNumber: 0000:00:1a.0
[    1.611330] hub 1-0:1.0: USB hub found
[    1.611350] hub 1-0:1.0: 3 ports detected
[    1.611967] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.611982] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.612022] ehci-pci 0000:00:1d.0: debug port 2
[    1.616052] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.616102] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf0907000
[    1.626855] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.626953] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.626960] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.626965] usb usb2: Product: EHCI Host Controller
[    1.626969] usb usb2: Manufacturer: Linux 3.15.4-031504-generic ehci_hcd
[    1.626974] usb usb2: SerialNumber: 0000:00:1d.0
[    1.627459] hub 2-0:1.0: USB hub found
[    1.627477] hub 2-0:1.0: 3 ports detected
[    1.627785] ehci-platform: EHCI generic platform driver
[    1.627805] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.627814] ohci-pci: OHCI PCI platform driver
[    1.627841] ohci-platform: OHCI generic platform driver
[    1.627856] uhci_hcd: USB Universal Host Controller Interface driver
[    1.627982] usbcore: registered new interface driver usb-storage
[    1.628061] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.631188] i8042: Detected active multiplexing controller, rev 1.1
[    1.632832] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.632837] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.632862] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.632923] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.632983] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.633632] mousedev: PS/2 mouse device common for all mice
[    1.634575] rtc_cmos 00:04: RTC can wake from S4
[    1.635061] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.635114] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.635225] device-mapper: uevent: version 1.0.3
[    1.635625] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.635646] ledtrig-cpu: registered to indicate activity on CPUs
[    1.635846] TCP: cubic registered
[    1.636112] NET: Registered protocol family 10
[    1.636813] NET: Registered protocol family 17
[    1.636834] Key type dns_resolver registered
[    1.638351] Loading compiled-in X.509 certificates
[    1.639273] Loaded X.509 cert 'Magrathea: Glacier signing key: d119329066fe4be59d0c7cd84062003d6cf15b30'
[    1.639282] registered taskstats version 1
[    1.646291] Key type trusted registered
[    1.652948] Key type encrypted registered
[    1.659363] AppArmor: AppArmor sha1 policy hashing enabled
[    1.659370] ima: No TPM chip found, activating TPM-bypass!
[    1.661028]   Magic number: 6:270:494
[    1.661265] rtc_cmos 00:04: setting system clock to 2014-07-19 18:28:13 UTC (1405794493)
[    1.663934] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.663935] EDD information not available.
[    1.664021] PM: Hibernation image not present or could not be loaded.
[    1.665484] Freeing unused kernel memory: 1360K (ffffffff81d28000 - ffffffff81e7c000)
[    1.665486] Write protecting the kernel read-only data: 12288k
[    1.667094] Freeing unused kernel memory: 464K (ffff88000178c000 - ffff880001800000)
[    1.668252] Freeing unused kernel memory: 444K (ffff880001b91000 - ffff880001c00000)
[    1.668472] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.685587] systemd-udevd[152]: starting version 204
[    1.807181] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.807990] acpi device:01: registered as cooling_device8
[    1.808121] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input8
[    1.819944] sdhci: Secure Digital Host Controller Interface driver
[    1.819948] sdhci: Copyright(c) Pierre Ossman
[    1.822687] sdhci-pci 0000:07:00.1: SDHCI controller found [1217:8120] (rev 1)
[    1.822846] mmc0: no vqmmc regulator found
[    1.822849] mmc0: no vmmc regulator found
[    1.822981] mmc0: SDHCI controller on PCI [0000:07:00.1] using DMA
[    1.824058] ahci 0000:00:1f.2: version 3.0
[    1.824323] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.824360] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    1.826384] firewire_ohci 0000:07:00.0: enabling device (0104 -> 0106)
[    1.838683] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x3b impl SATA mode
[    1.838692] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    1.847152] atl1c 0000:0b:00.0: version 1.0.1.1-NAPI
[    1.872000] scsi0 : ahci
[    1.872943] scsi1 : ahci
[    1.873437] scsi2 : ahci
[    1.874023] scsi3 : ahci
[    1.874662] scsi4 : ahci
[    1.875008] scsi5 : ahci
[    1.875158] ata1: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908100 irq 45
[    1.875164] ata2: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908180 irq 45
[    1.875165] ata3: DUMMY
[    1.875171] ata4: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908280 irq 45
[    1.875177] ata5: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908300 irq 45
[    1.875184] ata6: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908380 irq 45
[    1.878850] firewire_ohci 0000:07:00.0: added OHCI v1.10 device as card 0, 8 IR + 8 IT contexts, quirks 0x10
[    1.926824] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.059402] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    2.059410] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.059948] hub 1-1:1.0: USB hub found
[    2.060146] hub 1-1:1.0: 6 ports detected
[    2.170762] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.194705] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.195918] ata1.00: ATA-8: Hitachi HTS725050A9A360, PC4OC71E, max UDMA/133
[    2.195926] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.197408] ata1.00: configured for UDMA/133
[    2.197837] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72505 PC4O PQ: 0 ANSI: 5
[    2.198665] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.198728] sd 0:0:0:0: [sda] Write Protect is off
[    2.198734] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.198760] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.198903] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.275060]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    2.277806] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.303285] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    2.303293] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.303928] hub 2-1:1.0: USB hub found
[    2.304059] hub 2-1:1.0: 8 ports detected
[    2.374672] usb 1-1.3: new full-speed USB device number 3 using ehci-pci
[    2.378513] firewire_core 0000:07:00.0: created device fw0: GUID 01cee4ea00000700, S400
[    2.470818] usb 1-1.3: New USB device found, idVendor=046d, idProduct=c52b
[    2.470828] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.470837] usb 1-1.3: Product: USB Receiver
[    2.470845] usb 1-1.3: Manufacturer: Logitech
[    2.475767] hidraw: raw HID events driver (C) Jiri Kosina
[    2.482656] usbcore: registered new interface driver usbhid
[    2.482659] usbhid: USB HID core driver
[    2.486599] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1.3/input2
[    2.518428] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.519514] ata2.00: ATA-8: Hitachi HTS725050A9A360, PC4OC71E, max UDMA/133
[    2.519522] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.520952] ata2.00: configured for UDMA/133
[    2.521351] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HTS72505 PC4O PQ: 0 ANSI: 5
[    2.521986] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.522024] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.522070] sd 1:0:0:0: [sdb] Write Protect is off
[    2.522075] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.522103] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.530512] tsc: Refined TSC clocksource calibration: 1728.988 MHz
[    2.543367] input: Logitech Unifying Device. Wireless PID:101a as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.2/0003:046D:C52B.0003/0003:046D:C52B.0004/input/input13
[    2.543780] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101a] on usb-0000:00:1a.0-1.3:1
[    2.549220]  sdb: sdb1 sdb2 < sdb5 >
[    2.550086] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.574638] usb 2-1.1: new high-speed USB device number 3 using ehci-pci
[    2.672378] usb 2-1.1: New USB device found, idVendor=04f2, idProduct=b130
[    2.672382] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.672384] usb 2-1.1: Product: USB2.0 UVC WebCam
[    2.672385] usb 2-1.1: Manufacturer: Chicony
[    2.672387] usb 2-1.1: SerialNumber: CNA8155-000001
[    2.725004] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1e0b1, caps: 0xd04733/0xa40000/0xa0000, board id: 3655, fw id: 583639
[    2.742411] usb 2-1.3: new full-speed USB device number 4 using ehci-pci
[    2.785158] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input12
[    2.838308] ata4: SATA link down (SStatus 0 SControl 300)
[    2.839120] usb 2-1.3: New USB device found, idVendor=0930, idProduct=020f
[    2.839128] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.839133] usb 2-1.3: Product: Askey for Toshiba
[    2.839138] usb 2-1.3: Manufacturer: Broadcom Corp
[    2.839143] usb 2-1.3: SerialNumber: E839DF26117A
[    3.158208] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.159461] ata5.00: ATAPI: MATSHITABD-CMB UJ141ES, 1.00, max UDMA/100
[    3.161664] ata5.00: configured for UDMA/100
[    3.167039] scsi 4:0:0:0: CD-ROM            MATSHITA BD-CMB UJ141ES   1.00 PQ: 0 ANSI: 5
[    3.186004] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.186010] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.186423] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    3.186573] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    3.506062] ata6: SATA link down (SStatus 0 SControl 300)
[    3.530438] Switched to clocksource tsc
[    3.934113] random: nonblocking pool is initialized
[   10.908331] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
[   10.908334] EXT4-fs (sdb1): write access will be enabled during recovery
[   11.678163] EXT4-fs (sdb1): orphan cleanup on readonly fs
[   11.678303] EXT4-fs (sdb1): 9 orphan inodes deleted
[   11.678305] EXT4-fs (sdb1): recovery complete
[   11.743914] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   12.831310] init: ureadahead main process (338) terminated with status 5
[   13.618839] Adding 16852148k swap on /dev/sda7.  Priority:-1 extents:1 across:16852148k FS
[   14.674929] systemd-udevd[446]: starting version 204
[   15.495660] lp: driver loaded but no devices found
[   15.552961] ppdev: user-space parallel port driver
[   17.243098] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140214/utaddress-258)
[   17.243106] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.243114] ACPI Warning: SystemIO range 0x00000000000011c0-0x00000000000011cf conflicts with OpRegion 0x0000000000001180-0x00000000000011e3 (\GPIO) (20140214/utaddress-258)
[   17.243118] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.243120] ACPI Warning: SystemIO range 0x00000000000011b0-0x00000000000011bf conflicts with OpRegion 0x0000000000001180-0x00000000000011e3 (\GPIO) (20140214/utaddress-258)
[   17.243124] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.243125] ACPI Warning: SystemIO range 0x0000000000001180-0x00000000000011af conflicts with OpRegion 0x0000000000001180-0x00000000000011e3 (\GPIO) (20140214/utaddress-258)
[   17.243129] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.243131] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   17.257031] EDAC MC: Ver: 3.0.0
[   17.285265] EDAC i7core: Device not found: dev 00.0 PCI ID 8086:2c50
[   17.724254] wmi: Mapper loaded
[   17.749961] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler
[   17.751830] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[   17.839310] [drm] Initialized drm 1.1.0 20060810
[   17.916495] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   17.916666] snd_hda_intel 0000:01:00.1: Disabling MSI
[   17.916675] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   17.996453] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.20
[   17.997594] input: Toshiba input device as /devices/virtual/input/input14
[   18.208033] sound hdaudioC0D0: CX20583 (Pebble HSF): BIOS auto-probing.
[   18.208646] sound hdaudioC0D0: autoconfig: line_outs=1 (0x1f/0x0/0x0/0x0/0x0) type:speaker
[   18.208651] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.208656] sound hdaudioC0D0:    hp_outs=1 (0x19/0x0/0x0/0x0/0x0)
[   18.208659] sound hdaudioC0D0:    mono: mono_out=0x0
[   18.208662] sound hdaudioC0D0:    dig-out=0x20/0x0
[   18.208665] sound hdaudioC0D0:    inputs:
[   18.208669] sound hdaudioC0D0:      Internal Mic=0x1e
[   18.208673] sound hdaudioC0D0:      Mic=0x1a
[   18.209946] sound hdaudioC0D0: Enable sync_write for stable communication
[   18.212725] device-mapper: multipath: version 1.7.0 loaded
[   18.213302] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   18.213444] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   18.246186] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   18.446773] cfg80211: Calling CRDA to update world regulatory domain
[   18.721704] Bluetooth: Core ver 2.19
[   18.721726] NET: Registered protocol family 31
[   18.721728] Bluetooth: HCI device and connection manager initialized
[   18.721736] Bluetooth: HCI socket layer initialized
[   18.721739] Bluetooth: L2CAP socket layer initialized
[   18.721748] Bluetooth: SCO socket layer initialized
[   18.810399] usbcore: registered new interface driver btusb
[   18.904479] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input17
[   18.904634] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input18
[   18.904785] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input19
[   18.904933] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input20
[   19.189416] rtl8192se: FW Power Save off (module option)
[   19.189453] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   19.189453] Loading firmware rtlwifi/rtl8192sefw.bin
[   19.269514] Linux video capture interface: v2.00
[   19.725678] uvcvideo: Found UVC 1.00 device USB2.0 UVC WebCam (04f2:b130)
[   19.748383] input: USB2.0 UVC WebCam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input21
[   19.748629] usbcore: registered new interface driver uvcvideo
[   19.748631] USB Video Class driver (1.1.1)
[   20.046716] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   20.587176] cfg80211: World regulatory domain updated:
[   20.587181] cfg80211:  DFS Master region: unset
[   20.587182] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   20.587186] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   20.587188] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   20.587191] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   20.587193] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   20.587196] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   22.111073] nvidia: module license 'NVIDIA' taints kernel.
[   22.111081] Disabling lock debugging due to kernel taint
[   22.115146] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   22.120444] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   22.120945] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   22.120957] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  340.24  Wed Jul  2 14:24:20 PDT 2014
[   26.644186] init: udev-fallback-graphics main process (1935) terminated with status 1
[   68.554896] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[   68.692907] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   68.755631] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   77.652855] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[   78.060395] init: failsafe main process (2024) killed by TERM signal
[   80.469407] Bluetooth: RFCOMM TTY layer initialized
[   80.469427] Bluetooth: RFCOMM socket layer initialized
[   80.469440] Bluetooth: RFCOMM ver 1.11
[   80.527965] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   80.527969] Bluetooth: BNEP filters: protocol multicast
[   80.527976] Bluetooth: BNEP socket layer initialized
[   80.859153] init: cups main process (2295) killed by HUP signal
[   80.859170] init: cups main process ended, respawning
[   84.248174] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   84.264009] atl1c 0000:0b:00.0: irq 47 for MSI/MSI-X
[   84.280704] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   84.302891] init: samba-ad-dc main process (2317) terminated with status 1
[   86.163020] wlan0: authenticate with c8:d7:19:97:fb:55
[   86.182554] wlan0: send auth to c8:d7:19:97:fb:55 (try 1/3)
[   86.184126] wlan0: authenticated
[   86.186616] wlan0: associate with c8:d7:19:97:fb:55 (try 1/3)
[   86.189121] wlan0: RX AssocResp from c8:d7:19:97:fb:55 (capab=0x431 status=0 aid=2)
[   86.191292] wlan0: associated
[   86.191338] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   86.368989] wlan0: deauthenticating from c8:d7:19:97:fb:55 by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   86.400880] cfg80211: Calling CRDA to update world regulatory domain
[   86.400949] wlan0: authenticate with c8:d7:19:97:fb:55
[   86.411041] wlan0: send auth to c8:d7:19:97:fb:55 (try 1/3)
[   86.411330] cfg80211: World regulatory domain updated:
[   86.411334] cfg80211:  DFS Master region: unset
[   86.411336] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   86.411341] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   86.411346] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   86.411348] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   86.411351] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   86.411353] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   86.414072] wlan0: authenticated
[   86.422453] wlan0: associate with c8:d7:19:97:fb:55 (try 1/3)
[   86.426637] wlan0: RX AssocResp from c8:d7:19:97:fb:55 (capab=0x431 status=0 aid=2)
[   86.428807] wlan0: associated
[   87.795242] init: plymouth-upstart-bridge main process ended, respawning
[   87.806155] init: plymouth-upstart-bridge main process (2861) terminated with status 1
[   87.806187] init: plymouth-upstart-bridge main process ended, respawning
[   92.414326] nvidia 0000:01:00.0: irq 48 for MSI/MSI-X
[   92.689574] perf interrupt took too long (4213 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[   96.785821] init: plymouth-stop pre-start process (3341) terminated with status 1
[ 5493.092722] wlan0: deauthenticated from c8:d7:19:97:fb:55 (Reason: 16=GROUP_KEY_HANDSHAKE_TIMEOUT)
[ 5493.122242] cfg80211: Calling CRDA to update world regulatory domain
[ 5493.127758] cfg80211: World regulatory domain updated:
[ 5493.127765] cfg80211:  DFS Master region: unset
[ 5493.127768] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 5493.127774] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 5493.127780] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 5493.127784] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 5493.127789] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 5493.127794] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 5494.182081] wlan0: authenticate with c8:d7:19:97:fb:55
[ 5494.201278] wlan0: send auth to c8:d7:19:97:fb:55 (try 1/3)
[ 5494.202878] wlan0: authenticated
[ 5494.205250] wlan0: associate with c8:d7:19:97:fb:55 (try 1/3)
[ 5494.207842] wlan0: RX AssocResp from c8:d7:19:97:fb:55 (capab=0x431 status=0 aid=2)
[ 5494.209479] wlan0: associated

```

cat /proc/cmdline

```
marcelo@marcelo-qosmio ~ $ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.15.4-031504-generic root=UUID=8f793fc9-739e-4010-8744-27eec5e35496 ro persistent quiet splash

```

cat /etc/initramfs-tools/conf.d/resume

```
marcelo@marcelo-qosmio ~ $ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=0bac7284-9e90-4112-81ab-41ad69fea206

```

---

### Post by Toz on 2014-07-19
> cat /proc/cmdline
```
marcelo@marcelo-qosmio ~ $ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.15.4-031504-generic root=UUID=8f793fc9-739e-4010-8744-27eec5e35496 ro persistent quiet splash

```
Out of curiosity, why is the word "persistent" in your kernel boot line? I can't find any reference to such a kernel parameter.

-----

> cat /etc/initramfs-tools/conf.d/resume
```
marcelo@marcelo-qosmio ~ $ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=0bac7284-9e90-4112-81ab-41ad69fea206

```
Does the UUID line up with what is reported via:
```
sudo blkid
```

-----

> One thing I noticed is that the log file is relevant to the resume part, not to the hibernation process. I wish I could read a log that describes what's going on during it...
Can you try another hibernate attempt by running:
```
sudo pm-hibernate
```
...then when you recover the system, post back the contents of your /var/log/pm-suspend.log file via:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated. There is a difference in entries specific for suspend and those specific to hibernate.

---

### Post by Marcelo Ruiz on 2014-07-20
Thanks again for your message.
I don't know why the 'persistent' word is at the kernel boot parameters... this is a clean Mint 17 install and it was there... 
The requested log after a new failed attempt to hibernate is here:

[http://pastebin.com/4X6bFjjN](http://pastebin.com/4X6bFjjN)

Also the swap partition is correct:

```
marcelo@marcelo-qosmio ~ $ sudo blkid
/dev/sda1: LABEL="System" UUID="94A2504AA250334A" TYPE="ntfs" 
/dev/sda2: LABEL="Win7" UUID="469C75FD9C75E7B7" TYPE="ntfs" 
/dev/sda3: LABEL="HDDRECOVERY" UUID="96F69BD0F69BAF4D" TYPE="ntfs" 
/dev/sda5: LABEL="Home" UUID="6cba833a-79e4-4c47-af09-5c48ef094683" TYPE="ext4" 
/dev/sda6: LABEL="Backup" UUID="1a36d1d6-590e-4b6e-95e2-dd347ad24a4d" TYPE="ext4" 
/dev/sda7: UUID="0bac7284-9e90-4112-81ab-41ad69fea206" TYPE="swap" 
/dev/sdb1: LABEL="Linux" UUID="8f793fc9-739e-4010-8744-27eec5e35496" TYPE="ext4" 
/dev/sdb5: LABEL="Media" UUID="d602f9f1-0d9c-4cf8-88ec-1d6856738502" TYPE="ext4"
```

I am starting to think that the hibernation problem is related to the nVidia driver...
I will post back after doing some experimenting...

---

### Post by Marcelo Ruiz on 2014-07-20
Well, I think the problem is related to the nVidia graphics driver, so I opened a thread there:

[HTML]https://devtalk.nvidia.com/default/topic/762644/linux/nvidia-340-24-problems-with-hibernation-and-suspend/?offset=2#4264346[/HTML]

The description of the problem that I posted there follows:

[FONT=Arial Black]
This is a bug related to both hibernation and suspend on linux Mint 17 x64, X server version 1.15.1 (11501000), NV-CONTROL Version 1.29 with a GeForce GTS 360M video card. 
When trying to hibernate my computer the hibernation never completes. A green screen is shown for a fraction of a second and the CPU spikes and the computer never turns off.
When suspending the computer things work partially: the computers suspends and resumes fine but the powermizer performance level is forever stuck at level 1 (my card has level 0, level 1 and level 2).
The interesting thing is that after suspending and resuming, forcing the powermizer level to be stuck at level 1, hibernation and thaw work with no problem.
This problem is reproducible 100% of the time so far.
[/FONT]

and the link to linux mint forum reporting the problem is:

[HTML]http://forums.linuxmint.com/viewtopic.php?f=49&t=173531[/HTML]

the other only thing that I can think of is the output of 'inxi -Fxz' to give more information about my hardware:

```

marcelo@marcelo-qosmio ~ $ inxi -Fxz
System:    Host: marcelo-qosmio Kernel: 3.15.4-031504-generic x86_64 (64 bit, gcc: 4.6.3) 
           Desktop: Gnome  (Gtk 3.10.8) Distro: Linux Mint 17 Qiana
Machine:   System: TOSHIBA product: Qosmio X500 version: PQX33U-03Q022
           Mobo: TOSHIBA model: Qosmio X500 Bios: TOSHIBA version: V2.90 date: 12/10/2010
CPU:       Quad core Intel Core i7 CPU Q 740 (-HT-MCP-) cache: 6144 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 13831.2 
           Clock Speeds: 1: 933.00 MHz 2: 1199.00 MHz 3: 1734.00 MHz 4: 933.00 MHz 5: 933.00 MHz 6: 933.00 MHz 7: 933.00 MHz 8: 933.00 MHz
Graphics:  Card: NVIDIA GT215M [GeForce GTS 360M] bus-ID: 01:00.0 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1920x1080@60.0hz 
           GLX Renderer: GeForce GTS 360M/PCIe/SSE2 GLX Version: 3.3.0 NVIDIA 340.24 Direct Rendering: Yes
Audio:     Card-1: Intel 5 Series/3400 Series Chipset High Definition Audio driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2: NVIDIA High Definition Audio Controller driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture ver: k3.15.4-031504-generic
Network:   Card-1: Realtek RTL8191SEvB Wireless LAN Controller driver: rtl8192se port: 4000 bus-ID: 0a:00.0
           IF: wlan0 state: up mac: <filter>
           Card-2: Qualcomm Atheros AR8131 Gigabit Ethernet driver: atl1c ver: 1.0.1.1-NAPI port: 5000 bus-ID: 0b:00.0
           IF: eth0 state: down mac: <filter>
Drives:    HDD Total Size: 1000.2GB (71.7% used) 1: id: /dev/sda model: Hitachi_HTS72505 size: 500.1GB 
           2: id: /dev/sdb model: Hitachi_HTS72505 size: 500.1GB 
Partition: ID: / size: 50G used: 11G (22%) fs: ext4 ID: /home size: 292G used: 235G (85%) fs: ext4 
           ID: swap-1 size: 17.26GB used: 0.09GB (1%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 63.0C mobo: N/A gpu: 0.0:38C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 309 Uptime: 1 day Memory: 5216.6/7973.0MB Runlevel: 2 Gcc sys: 4.8.2 Client: Shell inxi: 1.8.4 
```

Anyway, I will try any suggestions...
Thanks again!

---

