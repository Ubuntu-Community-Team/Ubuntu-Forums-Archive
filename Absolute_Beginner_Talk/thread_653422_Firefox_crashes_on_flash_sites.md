---
title: "Firefox crashes on flash sites"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Meizulo on 2007-12-29
Everytime I go onto any site with flash the browser crashes.

---

### Post by taurus on 2007-12-29
Do you have flash plugin for firefox?

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by JoshuaRL on 2007-12-29
What's your system?  And what addons do you have installed?

---

### Post by Meizulo on 2007-12-30
I'm pretty sure that I have flash already installed because flash sites load, but crash after a short time.

---

### Post by Meizulo on 2007-12-30
Anyone out there?

---

### Post by Sef on 2007-12-30
How did you install flash?

---

### Post by Meizulo on 2007-12-30
through synaptic... I think?

---

### Post by ^rooker on 2007-12-30
Just my 2 cents:
The latest version of flash from Adobe's site (v9.0.115.0) seems to be a bit "unstable".

---

### Post by Meizulo on 2007-12-31
I've checked and checked again and I am 99.9% sure that flash is installed properly, but Firefox Keeps crashing. Is there anyone out there who can help, this is really annoying. Perhaps there is an alternative that I do not know about?

---

### Post by zabien1970 on 2007-12-31
What  are you system specs and which version of ubuntu are you using?
 Also are you running compiz?

---

### Post by Meizulo on 2007-12-31
I am using Kubuntu 7.04. And I do not know what compiz is???

Here are my swpecs:

Module                  Size  Used by
nls_iso8859_1           5120  0
nls_cp437               6784  0
vfat                   14208  0
fat                    53916  1 vfat
radeon                124576  2
drm                    81044  3 radeon
rfcomm                 40856  0
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0
acpi_cpufreq           10056  1
speedstep_lib           6148  0
cpufreq_userspace       5408  0
cpufreq_ondemand        9228  1
cpufreq_powersave       2688  0
cpufreq_conservative     8200  0
cpufreq_stats           7360  0
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
tc1100_wmi              8068  0
sony_acpi               6284  0
pcc_acpi               13184  0
dev_acpi               12292  0
button                  8720  0
asus_acpi              17308  0
backlight               7040  1 asus_acpi
ac                      6020  0
sbs                    15652  0
dock                   10268  0
container               5248  0
battery                10756  0
video                  16388  0
i2c_ec                  6016  1 sbs
ipv6                  269088  8
sbp2                   23812  0
lp                     12452  0
fuse                   46612  0
joydev                 10816  0
sg                     36252  0
snd_atiixp_modem       17160  1
wlan_scan_sta          14976  1
sd_mod                 23428  0
irda                  201276  0
snd_atiixp             20620  4
ath_rate_sample        14080  1
pcmcia                 39212  0
parport_pc             36388  1
crc_ccitt               3072  1 irda
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
sdhci                  18700  0
snd_ac97_codec         98464  2 snd_atiixp_modem,snd_atiixp
ath_pci                97312  0
parport                36936  3 ppdev,lp,parport_pc
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
mmc_core               26756  1 sdhci
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
pcspkr                  4224  0
psmouse                38920  0
serio_raw               7940  0
wlan                  204868  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                79876  5 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
yenta_socket           27532  1
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_timer              23684  3 snd_seq,snd_pcm
ati_agp                10124  1
snd                    54020  19 snd_atiixp_modem,snd_atiixp,snd_seq_oss,snd_ac97_codec,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore               8672  1 snd
snd_page_alloc         10888  3 snd_atiixp_modem,snd_atiixp,snd_pcm
agpgart                35400  2 drm,ati_agp
i2c_piix4               9740  0
i2c_core               22656  2 i2c_ec,i2c_piix4
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
af_packet              23816  6
tsdev                   8768  0
evdev                  11008  4
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0
cdrom                  37664  1 ide_cd
ide_disk               17024  3
8139cp                 25088  0
ata_generic             9092  0
libata                125720  1 ata_generic
generic                 5124  0 [permanent]
usb_storage            72256  0
scsi_mod              142348  5 sbp2,sg,sd_mod,libata,usb_storage
libusual               17936  1 usb_storage
8139too                27648  0
mii                     6528  2 8139cp,8139too
ohci1394               36528  0
ieee1394              299448  2 sbp2,ohci1394
atiixp                  7440  0 [permanent]
ehci_hcd               34188  0
ohci_hcd               22532  0
usbcore               134280  5 usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                14856  0
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability

---

### Post by taurus on 2007-12-31
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by Meizulo on 2007-12-31
The code is no good. I get bad command when I try to install compiz through that link.

---

### Post by taurus on 2007-12-31
Which command did you run?

---

### Post by niglch on 2007-12-31
I have trouble with flash sometimes too. Whenever I try to go on to the Ubuntu Gamers' Arena homepage (which uses flash videos), my processor use jumps close to 100% and Firefox often freezes for a few seconds. When Ubuntu's visual effects (Compiz) are enabled, things get way worse and Firefox usually stops responding after a few seconds. The flash plugin itself may just be bad, especially for older systems like mine. My advice is to make sure Compiz is **not** enabled if you want nice flash playback.

---

### Post by Irony on 2007-12-31
Don't install compiz! Get flash working.

Uninstall flashplugin from synaptic - now go to;

~/.mozilla

rename the plugins folder - then follow the instructions I issued earlier.

---

### Post by Meizulo on 2007-12-31
OK... I checked to see if compiz is installed and it looks like its not. So, flash is installed, but Firefox still crashes on flash sites. Please can anyone shed some light. I have been trying to get this to work for the past week?

---

### Post by Meizulo on 2008-01-01
Can anyone shed some light???

---

### Post by kleo skywalker on 2008-01-01
I've had problems with Firefox crashing a lot in Gutsy. At first I thought it had to do with Flash or another plugin, but later figured out it had to do with Google Toolbar. (See [this thread]("http://ubuntuforums.org/showthread.php?t=620153") for details.) Are you using Google Toolbar?

---

### Post by markyb86 on 2008-01-01
> **Irony said:**
> Don't install compiz! Get flash working.

Uninstall flashplugin from synaptic - now go to;

~/.mozilla

rename the plugins folder - then follow the instructions I issued earlier.
what was said earlier?

---

### Post by Meizulo on 2008-01-01
I'm about to give up on the idea of having a browser that will not crash on flash sites. There must be someone out there that can help me figure out why Firefox crashes when I am on sites that use flash???

---

### Post by markyb86 on 2008-01-01
how about i just started using opera.. I hate opera in gnome btw.. it crashed the same way (where it just dissapears) I used the one in the repos AND the 9.50b version. I cant understand. My browsers didnt crash in crappy sabayon linux or in suse linux enterprise 10.3 or opensuse 10.2

I just dont understand I may have to try a new distro?

---

### Post by Nuggs on 2008-01-25
Hi Meizulo,

I had the same problem a week ago.  I finally figured it out after a lot of playing around... (maybe the same is happening to you?)

First step: using Synaptic Package Manager, uninstall the adobe flash plugin, and the "gnash" flash plugin (if they are installed).  

DO NOT use Synaptic Package Manager to install flash:  It didn't work for me.  If you press on the detail button when the flash plugin is installing, you'll notice that the installation aborts when the checksum of the archive doesn't match (unknown why).  Unfortunately, Synaptic Package Manager will say that the package has been installed!

Next, go to the macromedia/adobe webpage ([http://www.adobe.com/products/flash](http://www.adobe.com/products/flash)) and download flash package.  Take the first one (I can't remember what it is called, but I know it is not the RPM, or the YUM installer).  Follow the instruction on how to install.

Basically, download the file onto your computer, uncompress it (i.e. right-click on the file and select "extract here").  Go to the flash installer directory, and double-click on the file called "flashplayer-installer".  A window will popup to ask if you really want to run the file, click on "run in terminal".  Follow the prompt, and make sure your browser is closed, and it should install...

With any luck, that should fix your problem!

---

### Post by kokuryu on 2008-01-25
Hey Nuggs!

Thank you very much for posting your advice or steps wutever you call it. My firefox was crashing everytime i went on youtube to watch videos and on a good day it would play but i couldnt click any buttons to stop or rewind. I just had to create a account on Ubuntu to tell you this.

p.s. Dont think im crazy...just very happy its working. Oh one more thing i seen you posted it 32 min ago if i was 32 min early i would of prolly never fixed this problem! Almost lost hope...Thanks again.

---

