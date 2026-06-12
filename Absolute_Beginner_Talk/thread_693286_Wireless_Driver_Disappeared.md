---
title: "Wireless Driver Disappeared"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2008-02-10
Hi all, last night i turned off my laptop and everything was fine. This morning, I seem to have lost my wireless. The light on the front of the laptop is constantly orange instead of blue, and I have no wireless option in my networking window. 

Does anyone know if it was an update that has knocked this out? I dont remember doing any updates yesterday... any ideas on how i can get it back? I am using a Compaq Presario V3000 series with a Broadcom chip. I am pretty sure I had ndiswrapper installed, so maybe something has changed that... 

Any advice would be great. 

Many Thanks

Patrick

---

### Post by mrsteveman1 on 2008-02-10
Check and see what modules are loaded at the moment

```

sudo lsmod
```

Also check the kernel messages for the broadcom driver to see if there are any errors. NDISwrapper should also show any errors in the kernel log

```
sudo dmesg
```

If you don't see any errors relating to the network driver, check the interfaces to see what is loaded at the moment

```
sudo ifconfig -a
```

---

### Post by ozPATT on 2008-02-18
hi mrsteveman, it seems a weird problem, as the following day it worked, then it didnt work at all until the other day when it worked once when i turned my laptop on, and hasnt worked since. i dont know too much about linux, so any help you can give would be great. 

this is the lsmod output:
> Module                  Size  Used by
cdc_acm                17184  0 
nls_iso8859_1           5120  0 
nls_cp437               6784  0 
vfat                   14080  0 
fat                    54300  1 vfat
usb_storage            73024  0 
libusual               18448  1 usb_storage
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ipv6                  273892  10 
nfsd                  220912  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ppdev                  10244  0 
powernow_k8            16960  1 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
video                  18060  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
battery                11012  0 
container               5504  0 
ac                      6148  0 
af_packet              24840  2 
ndiswrapper           185240  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
xpad                    9988  0 
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
i2c_nforce2             7040  0 
nvidia               4716468  26 
agpgart                35016  1 nvidia
pcspkr                  4224  0 
psmouse                39952  0 
serio_raw               8068  0 
shpchp                 34580  0 
sdhci                  18828  0 
mmc_core               28420  1 sdhci
k8temp                  6656  0 
i2c_core               26112  2 i2c_nforce2,nvidia
pci_hotplug            32704  1 shpchp
joydev                 11328  0 
evdev                  11136  7 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
sata_nv                20612  2 
usbhid                 29536  0 
hid                    28928  1 usbhid
ehci_hcd               36492  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
forcedeth              51592  0 
ata_generic             8452  0 
libata                125168  2 sata_nv,ata_generic
scsi_mod              147084  5 usb_storage,sbp2,sg,sd_mod,libata
amd74xx                15260  0 [permanent]
ide_core              116804  3 usb_storage,ide_cd,amd74xx
ohci_hcd               22916  0 
usbcore               138632  9 cdc_acm,usb_storage,libusual,ndiswrapper,xpad,usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


the output of dmesg is too much to put here, but there is a lot - and i mean lot - of the following:
>  sdc: rw=0, want=959338, limit=958999
[43293.288000] Buffer I/O error on device sdc1, logical block 958848


so not sure if that has anything to do with it. what should i be looking for in there? 

and finally this is ifconfig -a
>  sdc: rw=0, want=959338, limit=958999
[43293.288000] Buffer I/O error on device sdc1, logical block 958848


Any thoughts on this? It must still be in the system somewhere, or surely it wouldnt have worked those couple of times... 

Thanks

Patrick

---

### Post by mrsteveman1 on 2008-02-18
Run ```
 sudo ndiswrapper -l
```   (Thats a lowercase L)

That should list a driver for your card etc. 

Might also be worth it to remove the listed driver using ```
sudo ndiswrapper -e <driver>
``` (get the name from the first command). Then reinstall it the way you did before.

Unload and reload ndiswrapper:

```
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

then check the end of dmesg like this:

```
sudo dmesg | tail -n 30
```

There should be messages there showing ndiswrapper loading, what its doing, and any errors.

---

### Post by ozPATT on 2008-02-20
hi steve, I have done as you suggested, and then i restarted my computer but still no joy. when i run the dmesg thing, I get the following after rmmod/modprobe: 

> [  240.360000] usbcore: deregistering interface driver ndiswrapper
[  244.240000] ndiswrapper version 1.45 loaded (smp=yes)
[  244.328000] usbcore: registered new interface driver ndiswrapper


So I am guessing it is loading.. but it doesnt seem to be working at all.. Any further ideas?

Thanks

Patrick

---

### Post by nsimeone2000 on 2008-02-20
Ensure your wireless switch is turned off, reboot the computer, once you are on your desktop, flick your wireless switch on, right click on the connection icon top right of the screen, I noticed when my wireless was working and I don't turn the switch off prior to restart, I no longer have wireless myself.

I didn't read any other posts but the first one, so I hope I am not way off the mark.

---

### Post by mrsteveman1 on 2008-02-20
Did ndiswrapper -l list a driver ?

You don't have to restart the box for this sort of thing, just reloading the module is enough if you change anything.

---

### Post by ozPATT on 2008-02-20
yeah it listed something like bcmlw5 but it doesnt show anything now... did that line above remove it? maybe thats the problem now... i thought you meant i had to reinstall ndiswrapper, but i was only removing the driver wasnt i?

i just looked here and tried the suggested.. 

[http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+chipset+ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+chipset+ndiswrapper+howto)

but to no avail.. still no wireless. ps, i have the driver installed again, as is ndiswrapper.

---

### Post by mrsteveman1 on 2008-02-20
Yea, all you need to do is uninstall the driver from ndiswrapper:

```
sudo ndiswrapper -e bcmwl5
``` 

then redo it by pointing it at the windows driver like you did before:

```
sudo ndiswrapper -i bcmwl5.inf
```

Then you want to unload the ndiswrapper module and load it again:

```
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

then make sure the driver didn't give you any errors in dmesg:

```
sudo dmesg | tail -n 30

```

Then make sure the interface at least exists now:

```
sudo ifconfig -a
```

You might have to bring the interface up like this:

```
sudo ifconfig eth1 up
```

the only steps of these that you need to repeat in all this is to make ndiswrapper load at boot by adding ndiswrapper to the /etc/modules file.

This should work, if it doesn't it means the driver isn't compatible with ndiswrapper for some reason. I've had plenty of trouble with the broadcom driver in ndiswrapper, i had to grab a specific version to get it to work right, and i think it was the one from dell.

---

### Post by ozPATT on 2008-02-20
no joy :( i did what you said. > $ sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device there was no errors int eh dmesg bit, but the eth1 isnt showing at all. It used to work until about a week or so ago when it just stopped. i dont know if there was an update that knocked it out or something, but it should work with ndiswrapper im sure, as it did before...

---

### Post by ozPATT on 2008-02-28
hi again, still no joy. I have done lspci, and there is no mention of broadcom in there at all. I have found a section in System > Admin which is called Windows Drivers. It shows that bcmwl5 is installed, but it says there is no hardware. How can the hardware suddenly disappear? This is pretty frustrating as I use this laptop for work, and at the moment I have to plug it in at work, and at home I dont have a cable long enough so I cant really use it - without sitting on the floor... 

thanks

Patrick

---

### Post by mrsteveman1 on 2008-02-29
So the card disappeared from lspci?

Is there a hardware switch somewhere that disables the card?

Is there a bios option to hide the card from the OS? Some laptops have a bios option to turn the card off for situations where you don't want it being used etc.

---

### Post by ozPATT on 2008-03-02
yep disappeared from there. There is a switch on the front, but that is on. I haven't seen the BIOS yet, but I haven't turned anything off, so it would seem strange for it to suddenly switch off wouldnt it? I will have a lok though...

---

### Post by ozPATT on 2008-03-05
arrrrrgh! stoopid thing... ok i have completely reinstalled ubuntu, decided that a fresh install would maybe do it. and after losing a years worth of emails through the backup not working beforehand, the wireless worked! and i have used it all day. 

came home, turned it on, and now no wireless. I am not using ndiswrapper at the moment. When i did the fresh install, the restricted driver thing came up and told me i needed to install the bcm43xx-fwcutter which i did, and thats when it worked. but why doesnt it work now and how can i get the cutter working again? 

thanks

Patrick

---

### Post by smylie on 2008-03-06
Hi

One thing to check is that you have the restricted modules for your current kernel. (I've noticed sometimes the update managers pulls down a kernel and leaves out the restricted drivers.).
At a terminal type:

```
uname -r
```

and  it should give you a line like:
```

2.6.24-10-generic
```

Then, start synaptic, and check you have the package** linux-restricted-modules-xxx** (where xxx equals your kernel version/type (eg, generic or 386) 
Not having these restricted modules could be the cause of your wireless not working.

Now, of course with your network not working, you may have issues downloading the restricted modules. If thats the case, try some of the older kernels that are present in your grub menu at boot-up. If a kernel upgrade was the cause of your probs, then your original kernel should still be in the list, and should still work.

Good luck =)

Dave Smylie

---

### Post by ozPATT on 2008-03-06
hi Dave, I did as you suggested, and it seems to be installed ok, though I do notice the following... > Non-free Linux 2.6.22 modules on x86/x86_64 
This package provides restricted modules for Linux version 2.6.22 on
x86/x86_64.

Currently the following modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
 - fcdsl, fcdslusba, fcusb, fwlanusb, fxusb (AVM ISDN x86 only)

These modules are "restricted" because they are not available under a
completely Free licence.There is no mention of bcm43xx in there, so perhaps this is why it isnt loading or finding it? If that is the case though, how did it find it the other day immediately after the install? or could it be that having done updates after the install, some different headers were downloaded? 

thanks

patrick

---

