---
title: "no sound"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Mumbutu on 2007-09-03
Hello all,
I am new to the Forum.
I am new to Linux.
WindowsXP is installed on the main HD (primary drive).
Ubuntu is just  installed on another HD(slave).
My goal is to use Ubuntu, in a graphical mode, as my main OS. It implies to bring all my Microsoft Office 2003 files to Ubuntu. But it is another story.

Installation went fine. 
Only issue so far: no sound.
Under WindowsXP sound is there and DVD, and CD play as requested.
Under Ubuntu no sound and therefore nothing coming out of a DVD or CD even if it shows it's playing.
Master set up properly.
Sound card is SBLive Value (from Sound Blaster)- EMU10k1 and it is recognized by Ubuntu.
If anyone has the patience to guide me, step by step, to fix this issue I'll be very grateful.

---

### Post by ggaaron on 2007-09-03
Please paste results of following commands:
lspci
lsmod
sudo /etc/init.d/alsasound restart && dmesg | tail

This may prove valuable information, and hopefully someone will be able to help you=)

---

### Post by Mumbutu on 2007-09-03
andre@andre-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
Here are the answers:

00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
02:08.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:0b.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
andre@andre-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
xt_limit                3584  8 
xt_tcpudp               4224  23 
iptable_mangle          3712  0 
ipt_LOG                 7680  8 
ipt_MASQUERADE          4608  0 
nf_nat                 19372  1 ipt_MASQUERADE
ipt_TOS                 3200  0 
ipt_REJECT              5632  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11008  0 
nf_conntrack_ipv4      19468  7 
xt_state                3456  6 
nf_conntrack           62600  6 ipt_MASQUERADE,nf_nat,nf_conntrack_irc,nf_conntrack_ftp,nf_conntrack_ipv4,xt_state
nfnetlink               7704  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_filter          3968  1 
ip_tables              13796  2 iptable_mangle,iptable_filter
x_tables               16388  8 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,ip_tables
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
dock                   10268  0 
button                  8720  0 
battery                10756  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ipv6                  268960  8 
lp                     12452  0 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           121248  2 snd_emu10k1_synth
snd_ac97_codec         98464  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd                    54020  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
emu10k1_gp              4736  0 
gameport               16520  2 emu10k1_gp
intel_agp              26140  1 
agpgart                35400  1 intel_agp
i2c_core               22656  1 i2c_ec
intel_rng               6528  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
evdev                  11008  3 
tsdev                   8768  0 
usbhid                 26592  0 
hid                    27392  1 usbhid
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
floppy                 59524  0 
3c59x                  46632  0 
mii                     6528  1 3c59x
uhci_hcd               25360  0 
usbcore               134280  3 usbhid,uhci_hcd
ata_piix               15492  2 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
generic                 5124  0 [permanent]
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
andre@andre-desktop:~$ sudo /etc/init.d/alsasound restart && dmesg | tail
Password:
Sorry, try again.
Password:
sudo: /etc/init.d/alsasound: command not found
andre@andre-desktop:~$ sudo /etc/init.d/alsasound restart && dmesg | tail
sudo: /etc/init.d/alsasound: command not found

---

### Post by ggaaron on 2007-09-03
Strange, all is set up and should work as you've said. Are you sure that some of the channels aren't muted? Only thing that comes to my mind is to restart alsa and watch for warning messages, unfortunately it seems that ubuntu uses different script than /etc/init.d/alsasound, but I'm sure that someone actually using ubuntu will help you with this, or you can find it yourself, for sure it is in /etc/init.d/ and has alsa in name. Restart it and run dmesg - on the bottom should be something related to alsa and your audio card.

---

