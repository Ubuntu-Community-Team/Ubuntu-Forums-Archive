---
title: "no sound...no errors... went through the guide...help!"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Tsadkiel on 2007-07-25
hello everyone,

so, i tried to install Ubuntu as a double boot and in trying to resize my vista partition for some swap space i encountered an error, which resulted in my hard drive being completely wiped out... yay for me!  luckily i still had said Ubuntu installer CD and now I'm all Linux (which probably isn't a bad thing).  the full installation went almost without error (almost...)

my sound wouldn't work! i kept getting errors saying things along the lines of "you either don't have the proper GStreamer plugins or your audio device is not configured".   so i went online, found the comprehensive guide and started to follow along.  i made it to step two...

my sound card is a Creative Labs Sound Blaster X-Fi ... lo and behold, the alsa project wiki shot me down faster then i could blink.

> Sound Blaster X-Fi
	
UNKNOWN
		
    [Unsupported] [PCI] Card delivered to developers. Completely new architecture. Creative actively preventing support due to no datasheets being released to ALSA developers. Reverse engineering work not started due to lack of time.

so, i figured i could simply load my basic on board Intell sound card.  i restarted my system, went to the setup menu and activated both the analog and digital intell HD sound cards.

just to be safe i went back to the guide and tried step one.  here are the results.

```
tsadkiel@Raziel:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

so, continuing with the guide i opened the alsa mixer without any problems.  i activated all channels and maxed out all volume settings...

no sound...

the file i am trying to play is an .mp3.  when i first tried to play it i got an error message saying i didn't have the right codec.  i promptly downloaded and installed all codecs listed after the error and now when i load the .mp3 i get no error messages... but i also get no sound...

if this helps any, i tried step 4 of the guide just to see if the modules were there... here are the results

```
root@Raziel:/home/tsadkiel# sudo modprobe snd-
FATAL: Module snd_ not found.
```

which is unsettling...


any help with this would be greatly appreciated.
Thanks!
Tsadkiel

---

### Post by Timmy66 on 2007-07-25
Believe me brother I know what you are thru.Dealing with the same problem no sound at all.Install went flawlessly just no [SIZE="5"]sound[/SIZE]

---

### Post by DBStevens on 2007-07-25
Could you provide the output from:

lspci

and 

lsmod

As for the above Fatal error there is in fact no module named snd-  maybe you ment to run a lsmod to list the loaded modules or you didn't finish the module name.

---

### Post by Tsadkiel on 2007-07-25
assume i know nothing about Ubuntu or Linux...

```
root@Raziel:/home/tsadkiel# ispci
bash: ispci: command not found
root@Raziel:/home/tsadkiel# ismod
bash: ismod: command not found
```

i really hope that this isn't what you meant... (i couldn't find any manuals on ispci or ismod either)

edit:
thats an "L" there and not an "i" isn't it...

```
root@Raziel:/home/tsadkiel# lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7183
01:00.1 Display controller: ATI Technologies Inc Unknown device 71a3
04:04.0 Multimedia audio controller: Creative Labs SB X-Fi
04:05.0 Communication controller: Conexant HSF 56k Data/Fax Modem
```

```
root@Raziel:/home/tsadkiel# lsmod
Module                  Size  Used by
ipv6                  307456  22 
binfmt_misc            14604  1 
rfcomm                 45352  0 
l2cap                  28160  5 rfcomm
bluetooth              62468  4 rfcomm,l2cap
ppdev                  11272  0 
fglrx                 623096  45 
cpufreq_powersave       3072  0 
cpufreq_userspace       6176  0 
cpufreq_ondemand       10640  0 
cpufreq_conservative     9736  0 
cpufreq_stats           8416  0 
freq_table              6336  2 cpufreq_ondemand,cpufreq_stats
sony_acpi               7064  0 
dev_acpi               17028  0 
pcc_acpi               15616  0 
tc1100_wmi              9224  0 
video                  19080  0 
ac                      6920  0 
asus_acpi              19756  0 
container               6144  0 
battery                12040  0 
sbs                    17856  0 
i2c_ec                  6912  1 sbs
i2c_core               26496  1 i2c_ec
backlight               8448  1 asus_acpi
dock                   11992  0 
button                 10016  0 
parport_pc             40104  0 
lp                     15048  0 
parport                43404  3 ppdev,parport_pc,lp
fuse                   51888  0 
af_packet              27020  4 
snd_hda_intel          24224  1 
snd_hda_codec         262528  1 snd_hda_intel
snd_pcm_oss            49536  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 29088  0 
pcspkr                  4736  0 
iTCO_wdt               13648  0 
hid                    34048  1 usbhid
iTCO_vendor_support     5636  1 iTCO_wdt
intel_agp              29504  1 
snd                    68904  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
psmouse                43536  0 
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm
serio_raw               9092  0 
tsdev                  10112  0 
evdev                  13056  3 
ext3                  143760  1 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sg                     40616  0 
sr_mod                 18980  0 
sd_mod                 25092  3 
cdrom                  40744  1 sr_mod
ehci_hcd               37004  0 
uhci_hcd               28320  0 
usbcore               154416  4 usbhid,ehci_hcd,uhci_hcd
ahci                   25348  2 
libata                137000  1 ahci
scsi_mod              166968  4 sg,sr_mod,sd_mod,libata
e1000                 133696  0 
thermal                16912  0 
processor              34952  1 thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability

```

much better i think


Tsadkiel

---

### Post by DBStevens on 2007-07-26
That's the small letter L not the small letter  I  ;-)

---

### Post by DBStevens on 2007-07-26
I'm finding several issues with that sound system as well.

I'll look at it some more later.  I'm out of here for some shut eye.

---

### Post by Tsadkiel on 2007-07-26
could this be a result of installing the wrong version?  i installed the AMD Intell version, but there is also the basic desktop, and sun versions (i definitely don't have a sun machine).

i have noticed that FLASH is not supported with this version (or it appears like it isn't.  i certainly cant install it, and when i download the .tar.gz version from the flash website and try to install i get a "not supported by current architecture" error).

is flash supported on the desktop version? DBStevens, what version are you running?

---

### Post by Tsadkiel on 2007-07-26
this is a shameless bump.  i would really like some help

thanks

---

### Post by DBStevens on 2007-07-26
You might want to read this:

[http://forums.gentoo.org/viewtopic-t-567773-highlight-.html?sid=6e96da0e414aa8f7d09f4dd14f3f81ec](http://forums.gentoo.org/viewtopic-t-567773-highlight-.html?sid=6e96da0e414aa8f7d09f4dd14f3f81ec)

---

### Post by Tsadkiel on 2007-07-26
i read through your link... i hardly understood any of it =(

so many abbreviations...

i downloaded the script they mentioned near the end and i can't get it to run.

i followed the link to the methods listed in the second to last reply and it made even less sense.

can't anyone tell me whats going on with my sound and help me fix it? I'm new to Linux and this is starting to get very frustrating.

---

### Post by DBStevens on 2007-07-26
To put it bluntly it looks like your onboard audio isn't exactly supported in the current alsa package provided by Ubuntu.

This is showing up as issues with several distributions.   Like I said late last night and I haven't seen anything yet that looks all that promising. The alsa subsystem appears  (I am still seeing issues here as well) to support it in the latest builds.  Even the Alsa Wiki  entry for Intel is missing the entry for the ICH8 (00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)) class of device.

I haven't looked at the currently being tested Ubuntu (Gutsy Gibbon) release to see if it is supported there.

---

### Post by Tsadkiel on 2007-07-26
do you know if it's possible to acquire the latest build of the alsa subsystem?  if so, do you recommend it, or is it purely a test phase or something like that...


from what it sounds like, there is no current, real solution to this problem...  is this the case?

---

### Post by DBStevens on 2007-07-26
I can't say if a solution does or doesn't exist out there that'll work for your current system, however it is not currently something that is a single mouse click from doing.   

I'd check with the Alsa folks about it.  After all the current kernel is almost three releases ahead of the one in Fiesty and there are tons of Alsa fixes and updates  along with various ICH8 fixes and even ICH9 additions.

---

### Post by DBStevens on 2007-07-26
Here is something to try, I don't know if it will fix your issue or not:

sudo gedit /etc/modprobe.d/alsa-base

and add:

options snd-hda-intel position_fix=1

at the end of the file save and reboot.

if that doesn't work 

edit the same file and change that line to:

options snd-hda-intel position_fix=1 model=laptop-eapd

save and reboot.

if these two don't do it remove the line you added save and reboot.   That should put you back where you currently are.

---

### Post by Tsadkiel on 2007-07-27
nope... didn't work...

i also found this guide on the HDA intel sound cards

[URL="http://help.ubuntu.com/community/HdaIntelSoundHowto"]

and followed it to the letter, also without success...

thanks for working with me on this.  i really appreciate it.  i'm going to continue working on it tomorrow after i get some sleep.

on a lighter note, i DID get wine working so i have some basic windows functionality again.

which raises an interesting question... i know my sound cards worked in windows vista.  would it be possible to get the windows drivers, intsall them via wine, and run my sound through that system instead?

---

### Post by DBStevens on 2007-07-27
I don't think that wine has that kind of functionality .  I've never used it, my understanding is that wine is more of a set of function wrappers windows function  >>>  to linux functions so all of your hardware support is still that of the operating system you are actually running which is Linux.  As for Vista you can deal with that, if I'm lucky I'll never have to install or maintain it.  It will never be on any of my systems.

As for the ICH8 and higher chip sets the current Ubuntu kernel for Fiesty is now several levels behind and there are a lot of changes in that area.   

Maybe one of these days I'll try a stock kernel.org kernel install.  I've done that with other distros but keeping distro specific additions is not a trivial thing to maintain when doing that.

---

