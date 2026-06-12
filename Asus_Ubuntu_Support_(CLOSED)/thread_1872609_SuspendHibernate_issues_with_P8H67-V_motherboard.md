---
title: "Suspend/Hibernate issues with P8H67-V motherboard"
date: 2011-10-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Dr. Guitar on 2011-10-31
Hi everybody,

I built a computer a few days ago using an Asus P8H67-V motherboard, and I am unable to suspend or hibernate with Kubuntu 11.10. If I choose either suspend or hibernate from the panel menu my power cuts off instantly without going through the proper shutdown routine. Has anybody had this problem before or could otherwise guide me towards a fix? I have 8GB of RAM and 8GB of swap.

Much appreciated,
DG

---

### Post by 2F4U on 2011-10-31
There are usually two files related to suspend/hibernat in /var/log:
- pm-powersave.log
- pm-suspend.log

Look into these files, they may contain more information about why it fails.

---

### Post by Dr. Guitar on 2011-10-31
Below is the pm-suspend.log after an attempt to put the computer to sleep through KDE's menu. Do you think there's anything in there that could help me? I really appreciate your help! :-)

```
Initial commandline parameters: 
Mon Oct 31 20:40:06 EDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux cerebro 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
eeepc_wmi              12826  0 
asus_wmi               20035  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
snd_hda_intel          33390  4 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
i915                  566711  4 
wmi                    19256  1 asus_wmi
drm_kms_helper         42558  1 i915
drm                   236330  5 i915,drm_kms_helper
pata_via               13623  0 
atl1c                  41643  0 
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
xhci_hcd               78641  0 
             total       used       free     shared    buffers     cached
Mem:       8104348    1065368    7038980          0      35876     359340
-/+ buffers/cache:     670152    7434196
Swap:      8296444          0    8296444

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

/usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Mon Oct 31 20:40:07 EDT 2011: performing suspend

```

Edit: This is the output of pm-powersave.log after one attempt at suspend and one attempt at hibernation. Anything juicy in here? I grep'd it and couldn't find a single line with 'fail' in it.

```


Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.

```

---

### Post by Dr. Guitar on 2011-11-06
Unfortunately I was not able to find a fix for this problem, however I did find this bug report already open: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760842]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760842")

If anyone who has this problem in the future comes across this thread, I encourage them to view the bug report for a possible future fix and/or contribute to resolving it. 

Thanks, 
DG

---

