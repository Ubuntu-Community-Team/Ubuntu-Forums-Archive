---
title: "Would anyone be able to create a .deb file for a common driver?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-03-27
I have been having problems installing the driver for an intel ipw3945 wireless card, and I have also noticed that other people have been having similar problems. Would anyone out there be willing to create a .deb file or command prompt script to download and install the driver for us noobs?? Something in the tar file from intel is making it more complicated than it has to be I believe, because I always get an error while attempting to untar it using the command prompt, but the archive manager opens it with no problems. Thanks!!

---

### Post by charles.g.moore on 2007-03-27
What is the exact nature of the error???

I also use that driver and don't recall having too much trouble with it...
As soon as I get home I can send you the links I used

---

### Post by compmodder26 on 2007-03-27
I too use ipw3945 and it has worked out of the box since Dapper for me.

---

### Post by brennydoogles on 2007-03-27
I am not near the laptop that has been having the issues, but I will reply again later when I am near it. The card has not been recognized yet by Ubuntu, but I am going to try NDISwrapper later to see if that works. If not I'll let you know.

---

### Post by Bachstelze on 2007-03-27
Don't try ndiswrapper. There is a native driver and it is fairly easy to install. So easy, in fact, that I never bothered to make a shell script to automate that though if you say it chould help people, I could take a few minutes to make one if I get bored :p

It narrows down to this :

Install required stuff 

```
sudo apt-get install linux-headers-$(uname -r) build-essential
```

Get in a clean dir

```
cd && mkdir ipw3945 && cd ipw3945
```

Get the driver

```
wget http://kent.dl.sourceforge.net/sourceforge/ipw3945/ipw3945-1.2.0.tgz
```

Extract the tarball 

```
tar xzvf ipw3945-1.2.0.tgz
```

Get the firmware 

```
wget http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.14.2.tgz
```

Extract the tarball 

```
tar xzvf ipw3945-ucode-1.14.2.tgz
```

Get the daemon

```
wget http://bughost.org/ipw3945/daemon/ipw3945d-1.7.22.tgz
```

Extract the tarball

```
tar xzvf ipw3945d-1.7.22.tgz
```

Install the firmware

```
sudo cp ipw3945-ucode-1.14.2/ipw3945.ucode /lib/firmware
```

Install the daemon

```
sudo cp ipw3945d-1.7.22/x86/ipw3945d /sbin
```

cd to the driver's dir 

```
cd ipw3945-1.2.0
```

Build it

```
make
```

Load it

```
sudo ./load debug=0
```

Enjoy :)

---

### Post by brennydoogles on 2007-03-27
```
bobby@linux:~/ipw3945/ipw3945-1.2.0$ make
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1

```

This is the error I get when I try to make the driver

---

### Post by Bachstelze on 2007-03-28
```
sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh
```

---

### Post by brennydoogles on 2007-03-28
I did what was recommended in the previous post, and still got this error message```
bobby@linux:~/ipw3945/ipw3945-1.2.0$ make

 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
 Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1

```

Any suggestions?

---

### Post by brennydoogles on 2007-03-28
Latest update:

```
bobby@linux:~$ lsmod
Module                  Size  Used by
ipw3945               124576  0 
ieee80211              35272  1 ipw3945
ieee80211_crypt         7552  1 ieee80211
usbserial              34152  0 
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
af_packet              24584  2 
vfat                   14720  0 
fat                    56348  1 vfat
fuse                   43912  2 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
pcmcia                 40380  0 
8139cp                 24832  0 
joydev                 11200  0 
8139too                29056  0 
mii                     6912  2 8139cp,8139too
tsdev                   9152  0 
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
usbhid                 45152  0 
sg                     37404  0 
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
ath_pci               100000  0 
ath_rate_sample        16512  1 ath_pci
wlan                  207708  2 ath_pci,ath_rate_sample
ath_hal               192976  2 ath_pci,ath_rate_sample
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
psmouse                41352  0 
serio_raw               8452  0 
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ati_agp                10636  0 
agpgart                34888  1 ati_agp
evdev                  11392  4 
pcspkr                  4352  0 
ext3                  142728  1 
jbd                    62228  1 ext3
ohci_hcd               22532  0 
ehci_hcd               34696  0 
usbcore               134912  5 usbserial,usbhid,ohci_hcd,ehci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
atiixp                  7824  1 
sd_mod                 22656  4 
generic                 6276  0 
sata_sil               11016  3 
libata                 74892  1 sata_sil
scsi_mod              144648  3 sg,sd_mod,libata
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

Where do I go from here?

---

### Post by Bachstelze on 2007-03-29
You configure your interface normally. I personnally use *iwconfig* in the CLI but I think you could udse a GUI tool as well.

---

### Post by brennydoogles on 2007-03-31
> **HymnToLife said:**
> You configure your interface normally. I personnally use *iwconfig* in the CLI but I think you could udse a GUI tool as well.

Unable to use the driver still I tried to install it again, and added in the sudo make install step which I have seen everywhere except this thread, and got this from terminal

```
bobby@linux:~/ipw3945$ sudo cp ipw3945d-1.7.22/x86/ipw3945d /sbin
bobby@linux:~/ipw3945$ cd ipw3945-1.2.0
bobby@linux:~/ipw3945/ipw3945-1.2.0$ make
 Using ieee80211 subsystem version API v2 from:

        Base: /lib/modules/2.6.17-10-generic/build/
        Path: /lib/modules/2.6.17-10-generic/build/include/

 EXTRA_CFLAGS = -DIPW3945_COMPAT=2 -g -Wa,-adhlms=check_inc.lst

mkdir -p /home/bobby/ipw3945/ipw3945-1.2.0/tmp/.tmp_versions
make -C /lib/modules/2.6.17-10-generic/build M=/home/bobby/ipw3945/ipw3945-1.2.0 MODVERDIR=/home/bobby/ipw3945/ipw3945-1.2.0/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
bobby@linux:~/ipw3945/ipw3945-1.2.0$ sudo make install 
install -d /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/
install -m 644 -c ipw3945.ko /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.17-10-generic
Don't forget to copy firmware to your hotplug's firmware directory 
and have the hotplug tools in place.
See INSTALL for more information.

NOTE:  This driver is for development and validation purposes only 
and has not been tested for regulatory compliance.  By using this 
driver you assume responsibility for any compliance issues that may 
arise.

Please see the README.ipw3495 for information on regulatory compliance.
bobby@linux:~/ipw3945/ipw3945-1.2.0$ sudo ./load debug=0
No modules unloaded.
insmod: error inserting './ipw3945.ko': -1 Unknown symbol in module
Load failed.
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2007-03-31 15:06:07: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection
..done.
bobby@linux:~/ipw3945/ipw3945-1.2.0$ 


```


What should I do??

---

### Post by brennydoogles on 2007-03-31
by the way, here are the resuls for lsmod 

```
bobby@linux:~$ lsmod
Module                  Size  Used by
ieee80211              35272  0 
ieee80211_crypt         7552  1 ieee80211
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
ipv6                  272288  8 
af_packet              24584  2 
vfat                   14720  0 
fat                    56348  1 vfat
fuse                   43912  2 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
8139cp                 24832  0 
joydev                 11200  0 
sg                     37404  0 
pcmcia                 40380  0 
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
8139too                29056  0 
ath_pci               100000  0 
ath_rate_sample        16512  1 ath_pci
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
mii                     6912  2 8139cp,8139too
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
ati_agp                10636  0 
agpgart                34888  1 ati_agp
psmouse                41352  0 
tsdev                   9152  0 
wlan                  207708  2 ath_pci,ath_rate_sample
usbhid                 45152  0 
evdev                  11392  4 
pcspkr                  4352  0 
serio_raw               8452  0 
ath_hal               192976  2 ath_pci,ath_rate_sample
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142728  1 
jbd                    62228  1 ext3
ohci_hcd               22532  0 
ehci_hcd               34696  0 
usbcore               134912  4 usbhid,ohci_hcd,ehci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
atiixp                  7824  1 
sd_mod                 22656  4 
generic                 6276  0 
sata_sil               11016  3 
libata                 74892  1 sata_sil
scsi_mod              144648  3 sg,sd_mod,libata
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability
bobby@linux:~$ 


```

---

### Post by Bachstelze on 2007-03-31
If I didn't tell you to make install, it's for a reason...

---

### Post by brennydoogles on 2007-03-31
> **HymnToLife said:**
> If I didn't tell you to make install, it's for a reason...

Following the directions exactly as posted did not load the driver, so I combined directions from several threads to attempt to find a working solution. Is there a reason not to make install? any help would be greatly appreciated. I also have AIM, so if it would be easier to give me instructions that way feel free to contact me.

---

### Post by brennydoogles on 2007-04-10
bump

---

### Post by FrostyFlames on 2007-04-10
I am going to assume that you are trying to set up your Intel Wireless 3945ABG card on 6.10 Edgy. I really don't know why everyone wants to compile the drivers when they are already part of Edgy. 

The first thing I would have to suggest is to install network-manager and the gnome GUI frontend. Do this in the Synaptic Package Manager. The packages you want to select are "network-manager" and "network-manager-gnome". Install those and whatever they bug you for dependency wise. I would restart after this point. 

After restarting you may or may not see a new addition to the top right of your screen. The icon should look like two computers one on top of the other, with a possible ! by it, if I remember correctly. If it's there, click on it and select your wireless SSID and it should ask you for the password, keyphrase, or whatever it needs to connect. It is also possible that the network-manager is installed, but your wireless card isn't quite set up.

If you do NOT have that new addition or the wireless part isn't showing up, you need to do some more installing. You should install the latest "linux-restricted-modules" package. When you scroll down to view this area you will see multiple versions of this package. You need to install the right one for your current kernel. To find out what version of the kernel you have, open a terminal and type in:```
uname -a
```
This should print out something like "Linux BrennysBox 2.6.17-10-generic" with some other stuff following it. The only thing we care about is that version number (2.6.17 ...) and what comes after that which should be either 386 or generic. 

Once you know your kernels version, select the corresponding restricted modules package. Since the uname command spat out "Linux BrennysBox 2.6.17-10-generic" I would chose the "linux-restricted-modules-2.6.17-10-generic" package. To my knowledge it doesn't hurt to have the 386 package installed, but if you want you can install that version, it just sucks up more hard drive space. Install and reboot. Check to see if that application is running at the top. If yet again the program isn't running, try installing the latest "linux-image" package and/or the newest "linux-headers" package based on your kernel.

I don't know what to tell you after that if the program isn't running. It's been awhile since I have had to install this device.

---

