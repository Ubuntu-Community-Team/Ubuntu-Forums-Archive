---
title: "tried to use OSS sound, now i have nO-SS sound"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Sonic Reducer on 2007-11-02
i tried the how-to from ubuntu unleashed [here]("http://tinyurl.com/36p25w") and now i have no sound from firefox, i'm listening to a mp3 right now in Totem with no problem, but youtube doesn't work and those myspace playlist things actually freeze firefox. both of those things are new.

so this can be one of two types of threads, it can be a "help me fix OSS" or it can be a "Help me get back to ALSA". this depends on which is better, sound quality is nice and all, but compatability is the most important thing to me.

i have to get ready for work right now, but i was hoping this is a common problem and someone can give me a quick fix to it, but if you need any information let me know and i'll supply it when i check back here

thanks

---

### Post by Sonic Reducer on 2007-11-05
this is the output of **lsmod**
```
ryan@ryan-desktop:~$ lsmod
Module			Size	Used by
nls_iso8859_1		5120	1
binfmt_misc		12680	1
vmix			14132	0
**ossusb			52360	0**
hdaudio			67856	0
**osscore			564532	3 vmix,ossusb,hdaudio**
ppdev			10116	0
autofs4			21892	0
powernow_k8		16064	1
cpufreq_conservative	8200	0
cpufreq_userspace	5408	0
cpufreq_ondemand	9228	1
cpufreq_stats		7360	0
freq_table		5792	3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave	2688	0
sony_acpi		6284	0
dev_acpi		12292	0
pcc_acpi		13184	0
tc1100_wmi		8068	0
battery			10756	0
video			16388	0
dock			10268	0
asus_acpi		17308	0
sbs			15652	0
i2c_ec			6016	1 sbs
ac			6020	0
container		5248	0
button			8720	0
backlight		7040	1 asus_acpi
nls_utf8		3072	1
nls_cp437		6784	2
vfat			14208	2
fat			53916	1 vfat
ipv6			268960	14
ndiswrapper		193116	0
w83627ehf		19724	0
i2c_isa			6272	1 w83627ehf
eeprom			8336	0
sbp2			23812	0
lp			12452	0
fuse			46612	3
psmouse			38920	0
parport_pc		36388	1
parport			36936	3 ppdev,lp,parport_pc
pcspkr			4224	0
serio_raw		7940	0
ide_cd			32672	0
cdrom			37664	1 ide_cd
k8temp			6656	0
af_packet		23816	2
i2c_nforce2		6784	0
nvidia			6224240	24
shpchp			34324	0
pci_hotplug		32576	1 shpchp
agpgart			35400	1 nvidia
i2c_core		22656	6 i2c_ec,w83627ehf,i2c_isa,eeprom,i2c_nforce2,nvidia
tsdev			8768	0
evdev			11008	3
ext3			133128	1
jbd			59816	1 ext3
mbcache			9604	1 ext3
sg			36252	0
sd_mod			23428	8
amd74xx			15260	0 [permanent]
generic			5124	0 [permanent]
ata_generic		9092	0
usb_storage		72256	1
libusual		17936	1 usb_storage
floppy			59524	0
forcedeth		46728	0
ohci1394		36528	0
ieee1394		299448	2 sbp2,ohci1394
sata_nv			20868	4
libata			125720	2 ata_generic,sata_nv
scsi_mod		142348	5 sbp2,sg,sd_mod,usb_storage,libata
ehci_hcd		34188	0
ohci_hcd		22532	0
**usbcore			134280	7 ossusb,ndiswrapper,usb_storage,libusual,ehci_hcd,ohci_hcd**
thermal			14856	0
processor		31048	2 powernow_k8,thermal
fan			5636	0
fbcon			42656	0
tileblit		3584	1 fbcon
font			9216	1 fbcon
bitblit			6912	1 fbcon
softcursor		3200	1 bitblit
vesafb			9220	0
capability		5896	0
commoncap		8192	1 capability
```

this is the contents of **/etc/modprobe.d/blacklist**
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

# Default RT2500 Driver
blacklist rt2500
```

i didn't get the expected output from **lsmodules | grep snd**, there weren't any *snd* drivers installed. should i blacklist *hdaudio* and *pcspkr* instead?

correct me if i'm wrong, but if i do blacklist these drivers, reboot, and still have no sound, the first thing i should do is **sudo soundoff** then **sudo soundon**, right?

---

