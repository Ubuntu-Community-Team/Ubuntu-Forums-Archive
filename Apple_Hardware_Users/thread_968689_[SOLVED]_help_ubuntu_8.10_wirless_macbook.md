---
title: "[SOLVED] help ubuntu 8.10 wirless macbook"
date: 2008-11-02
forum: Apple Hardware Users
---

### Post by alwayshere on 2008-11-02
black macbook gen 1 ubuntu os only ! 
wireless does not seem to be working in 7.04 it worked fine it just sorted itself now in 8.10 i have no idea what is going on 

any info please

---

### Post by joonyah on 2008-11-02
alwayshere,

Some more specifics would be helpful.  Some questions I have for you: 
What kind of wireless card are you using?
What version of Ubuntu are you using, and what kernel?
Is your wireless currently working? (I couldn't tell if you meant it wasn't working and it is now, or the opposite.)

I am currently running 8.10 on a MacBook 2,1 with an Atheros AR5008 a/b/g/n Wireless card.  The driver that was installed with 8.10 is ath9k and seems to be working just fine.  It's been doing better on 8.10 than it ever did on 8.04.  

-- jon

---

### Post by alwayshere on 2008-11-02
its a black macbook generation 1 standard in built wirless i realy dont know anymore in the past with ubuntu 7.04 it just worked all buy itself 
yes im a wireless noob :lolflag:

ubuntu 8.10 
2.6.27.7 generic

---

### Post by cyberdork33 on 2008-11-02
> **alwayshere said:**
> its a black macbook generation 1 
Please use the "Before you post" link in my signature to learn how to properly identify your Mac.

---

### Post by alwayshere on 2008-11-02
noooo idea what your on about please dumb it down for me ??

---

### Post by cyberdork33 on 2008-11-02
> **alwayshere said:**
> noooo idea what your on about please dumb it down for me ??
read the info in the link, determine your mac model version.

---

### Post by alwayshere on 2008-11-02
ok i think  got ya now so im ment to call it a 1.1 not a generation 1 is that it ?

---

### Post by hanzomon4 on 2008-11-02
Run this command in the Terminal program located in the Applications > Accessories menu ```
sudo dmidecode -s system-product-name
``` Then post the results...

Don't feel dumb sometimes we forget how strange the terminology can sound to new folks.

---

### Post by cyberdork33 on 2008-11-02
> **alwayshere said:**
> ok i think  got ya now so im ment to call it a 1.1 not a generation 1 is that it ?If that is what you have... many people think they have some certain generation or something, but all that doesn't matter... If it is a MacBook1,1 then I know what hardware you have, no matter if it is black, white, or even aluminum.

The MacBook1,1 should have an older Atheros WiFi card that works without trouble. However, the swtich to using the ath5k and ath9k drivers may have caused an issue for you. Can you post the output of 'ifconfig' and 'lsmod |grep ath'

---

### Post by alwayshere on 2008-11-02
> :~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:cb:cd:86:d9  
          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::216:cbff:fecd:86d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5567798 (5.5 MB)  TX bytes:7162882 (7.1 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)



> :~$ lsmod
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  2 
i915                   38144  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
btusb                  19736  3 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  2 
l2cap                  30464  16 bnep,rfcomm
bluetooth              61924  11 btusb,sco,bnep,rfcomm,l2cap
uinput                 15744  2 
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  2 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       9856  0 
wmi                    14504  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
loop                   23180  0 
joydev                 18368  0 
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
uvcvideo               62728  0 
evdev                  17696  17 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
appletouch             17156  0 
snd_seq_dummy          10884  0 
appleir                12544  0 
tpm_infineon           17064  0 
tpm                    22848  1 tpm_infineon
tpm_bios               14080  1 tpm
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
video                  25104  0 
output                 11008  1 video
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                     12292  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
battery                18436  0 
pcspkr                 10624  0 
button                 14224  0 
soundcore              15328  1 snd
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
intel_agp              33724  1 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
agpgart                42184  3 drm,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  3 
sr_mod                 22212  0 
crc_t10dif              9984  1 sd_mod
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_generic            12932  0 
ata_piix               24580  2 
usbhid                 35840  0 
hid                    50560  1 usbhid
pata_acpi              12160  0 
libata                177312  3 ata_generic,ata_piix,pata_acpi
ohci1394               37936  0 
scsi_mod              155212  5 sbp2,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  8 btusb,uvcvideo,appletouch,appleir,usbhid,ehci_hcd,uhci_hcd
sky2                   53380  0 
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
:~$ 


> lsmod |grep ath 
:~$

Thanks for helping

---

### Post by alwayshere on 2008-11-03
> :~$ sudo dmidecode -s system-product-name
[sudo] password for xxx: 
Macbook1,1
:~$ 


1.1

---

### Post by hanzomon4 on 2008-11-03
> **cyberdork33 said:**
> If that is what you have... many people think they have some certain generation or something, but all that doesn't matter... If it is a MacBook1,1 then I know what hardware you have, no matter if it is black, white, or even aluminum.

The MacBook1,1 should have an older Atheros WiFi card that works without trouble. However, the swtich to using the ath5k and ath9k drivers may have caused an issue for you. Can you post the output of 'ifconfig' and 'lsmod |grep ath'

I believe the ath5k drivers are disabled by default and going from the OPs out put from the commands wireless is not configured. I believe it's recommended that users use the madwifi drivers

---

### Post by alwayshere on 2008-11-03
It seems i do not have any proprietary drivers at all what do you think of that ??

---

### Post by cyberdork33 on 2008-11-03
> **hanzomon4 said:**
> I believe the ath5k drivers are disabled by default and going from the OPs out put from the commands wireless is not configured. I believe it's recommended that users use the madwifi drivers
That seems counter-intuitive to me since Intrepid does include ath9k which is a much more immature driver when compared to ath5k.

Madwifi should be avoided. It is no longer being developed or supported. (because it is being replaced by ath5k and ath9k...

> **alwayshere said:**
> It seems i do not have any proprietary drivers at all what do you think of that ??

Does anything show when you go to System > Admin > Hardware Drivers ?

If not, try 'modprobe ath5k' and see if the wireless works.

---

### Post by alwayshere on 2008-11-04
There are no drivers displayed and says none are in use 
---------------------------------------------------------

Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

above is the wireless that is in this macbook 1.1 if that is any help

---

### Post by alwayshere on 2008-11-04
All is good now wireless is working fine with a how to i found at this address [http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers)

---

### Post by cyberdork33 on 2008-11-04
> **alwayshere said:**
> All is good now wireless is working fine with a how to i found at this address [http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers)
That uses ath5k...

---

### Post by alwayshere on 2008-11-04
yes thanks for all your help

---

