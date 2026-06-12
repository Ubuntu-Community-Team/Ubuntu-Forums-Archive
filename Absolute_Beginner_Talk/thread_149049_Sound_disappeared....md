---
title: "Sound disappeared..."
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by Pelham123 on 2006-03-23
Hi

Bear with me please...

Over the last week I have installed Ub5.10 and am gradually getting my head around this new OS (which means doing a lot of things I don't know much about :p ). Played a CD directly from the CD drive, but the sound was distorted at medium volume. So, I thought I'd download some audio/media codecs from Automatix, also the Gstreamer codecs/libraries from SPM. Don't seem to have any sound now...

From poking around the GUI:

Configuration editor-System-Gstreamer-Audio-Profiles = all profiles ticked/active
Speaker Icon in tray is muted, clicking icon  = no control volume devices/elements found
System-Preferences-Sound = blank entry in default sound card box.

I did register the Gstreamer plugins, but I have changed a few startup entries with BUM, but as far as I can tell only the ALSA & Utilities should affect the sound, they are both enabled.

Any ideas please?

---

### Post by akiro.yamamoto on 2006-03-23
What do the outputs of :
```
lsmod
lspci | grep -i audio

``` Show ??
See my pic...

---

### Post by Pelham123 on 2006-03-23
Thanks for the reply:

lspci | grep -i audio:
0000:00:04.0 Multimedia audio controller: nVidia Corporation: Unknown device 0059 (rev a2)

(I should have AC97 Audio)

-------------------------------------

lsmod:
Module                  Size  Used by
ipv6                  217408  6
ipt_limit               2432  8
iptable_mangle          2816  0
ipt_LOG                 6400  8
ipt_MASQUERADE          3328  0
iptable_nat            21076  1 ipt_MASQUERADE
ipt_TOS                 2432  0
ipt_REJECT              5248  1
ip_conntrack_irc       71824  0
ip_conntrack_ftp       72336  0
ipt_state               2048  6
ip_conntrack           39864  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2944  1
ip_tables              18176  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
af_packet              20232  2
nls_iso8859_1           4224  1
vfat                   12288  1
fat                    46492  1 vfat
nls_cp437               5888  2
ntfs                   92016  1
dm_mod                 50364  0
evdev                   9088  0
nvidia               3711364  12
agpgart                32328  1 nvidia
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  1 sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
ext3                  115976  5
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
usbhid                 30688  0
forcedeth              19072  0
ehci_hcd               29448  0
ohci_hcd               18564  0
usbcore               104316  4 usbhid,ehci_hcd,ohci_hcd
sd_mod                 17424  0
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  9
ide_generic             1664  0
sata_nv                 9092  0
libata                 47876  1 sata_nv
scsi_mod              124872  4 sr_mod,sbp2,sd_mod,libata
amd74xx                12828  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   24624  518
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon


Sorry, didnt know how to paste (small) screenshots

---

### Post by Pelham123 on 2006-04-04
I posted this problem a while back (been away for some time) and I got the above reply from Akiro (thanks for that). From looking at Akiro's screenshots, I'm thinking we both have Nvidia setups (with AC97 audio) and if you compare the two, you can see I have a few(!) snd_ entries missing from the lsmod printout. Am guessing this is where my sound has disappeared to??

Any ideas please?

edit: installed and ran alsamixer = "function snd_ctl_open failed for default"

---

