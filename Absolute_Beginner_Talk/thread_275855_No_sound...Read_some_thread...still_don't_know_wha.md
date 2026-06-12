---
title: "No sound...Read some thread...still don't know what to do."
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by hyby on 2006-10-12
Howdy,

I have searched the ubuntu forums for configuring my sound card, ICH6 sound cards, to be exact : 82801FB/FBM/FR/FW/FRW (ICH6 Family). However, i am still confused in how to configure the sound. I have been told that im required to update the kern. and replace the ALSA drivers, is this correct?

If so, can someone kind of guide me through the process as i have never upgraded the kern. before. Also, i do not have a connection for my laptop, is there i a way where i can carry out the upgrade by downloading the .rpms?

Thank you!

---

### Post by hyby on 2006-10-12
quiet *bump*

---

### Post by petri on 2006-10-12
Have you checked this link? [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)
I hope that will help you, otherwise post the output of ```
lspci
``` here. Just highlight the code above with your left mousebutton (copy) and paste it in terminal with the click of your scrollwheel.

EDIT: ooops, that wasn't quite an answer to your problem, paste ```
alsamixer
``` in your terminal and see if you can adjust some levels there.

And BTW that Intels chips should work, see [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)

---

### Post by hyby on 2006-10-12
Thanks for your reply, i have tried what you have suggested, however it still doesnt work. 

i toggle the mute with m, and the 00 light on and off, i turned them all on *i.e. all green*... still no avail. 

The mixer recognises the sound drivers as ICH6, would this be correct?

---

### Post by petri on 2006-10-12
So alsa should be installed in your machine :)

Leftclick the speaker icon to the left from clock and play with Preferences* and Open volumecontroll. That is the I succeeded as I didn't had sound. And BTW do check the applications volumecontroll too.

"I have been told that im required to update the kern. and replace the ALSA drivers, is this correct?" - Where or how did you get this message?



*EDIT: You choose Preferences in Popup-menu and pick your soundchip and then choose PCM, does that work?

---

### Post by hyby on 2006-10-12
thanks looks like no avail.

I looked at my head phone jack and in the past it would light up in windows, however it doesnt seem to light up in dapper

---

### Post by cacharreo on 2006-10-12
Run ***gstreamer-properties*** and play with the options

---

### Post by petri on 2006-10-12
Cordless headphones?

Anyway, here is a sound troubleshooting guide [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

I hope you find something there.

---

### Post by xyz on 2006-10-12
This one is good too:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by hyby on 2006-10-12
my apologise, what i mean is that i realised that the digital output light observed with my headphone jack is not on. Could that be an indication of anything?

---

### Post by hyby on 2006-10-13
howdy guys, thanks for the feedback and assistance and the links

i tried the aplay -v as listed in the guides and this is what i got;
hyby@hyby:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Therefore, by the guides it means that the drivers are there, however when i go to alsamixer it doesnt want to work when i mute and unmute it i dont get sound

---

### Post by hyby on 2006-10-14
Hi guys,

i have reinstalled alsa from the guide using apt-get. I realised when i mute and unmute in alsamixer i get a clicking sound. Can that mean anything?

I thought i'd post extra details of my system. 
here is my lspci data:

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:01.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:06:01.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

and my lsmod

Module Size Used by
af_packet 22920 4
ipv6 265728 6
rfcomm 40216 0
l2cap 26244 5 rfcomm
bluetooth 49892 4 rfcomm,l2cap
ppdev 9220 0
i915 20608 1
drm 73236 2 i915
speedstep_centrino 8400 1
cpufreq_userspace 4696 1
cpufreq_stats 5636 0
freq_table 4740 2 speedstep_centrino,cpufreq_stats
cpufreq_powersave 1920 0
cpufreq_ondemand 6428 0
cpufreq_conservative 7332 0
video 16260 0
tc1100_wmi 6916 0
sony_acpi 5644 0
pcc_acpi 12416 0
hotkey 11556 0
dev_acpi 11140 0
container 4608 0
button 6672 0
acpi_sbs 19980 0
battery 9988 1 acpi_sbs
ac 5252 1 acpi_sbs
i2c_acpi_ec 5120 1 acpi_sbs
i2c_core 21904 1 i2c_acpi_ec
nls_iso8859_1 4224 1
nls_cp437 5888 1
vfat 13440 1
fat 53020 1 vfat
nls_utf8 2176 2
ntfs 103536 2
dm_mod 58936 1
md_mod 72532 0
sr_mod 16932 0
sbp2 24196 0
scsi_mod 139496 2 sr_mod,sbp2
lp 11844 0
pcmcia 40508 0
yenta_socket 28428 1
joydev 10048 0
tsdev 8000 0
rsrc_nonstatic 13440 1 yenta_socket
parport_pc 35780 1
parport 36296 3 ppdev,lp,parport_pc
pcmcia_core 42640 3 pcmcia,yenta_socket,rsrc_nonstatic
8139cp 22528 0
ipw2200 107308 0
ieee80211 37064 1 ipw2200
ieee80211_crypt 6272 1 ieee80211
ieee80211_1_1_13 38216 0
ieee80211_1_1_13_crypt 6784 1 ieee80211_1_1_13
psmouse 36100 0
8139too 26880 0
mii 5888 2 8139cp,8139too
serio_raw 7300 0
snd_intel8x0 33692 1
snd_ac97_codec 93088 1 snd_intel8x0
snd_ac97_bus 2304 1 snd_ac97_codec
snd_pcm_oss 53664 0
snd_mixer_oss 18688 1 snd_pcm_oss
snd_pcm 89864 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer 25220 1 snd_pcm
snd 55268 8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_ oss,snd_pcm,snd_timer
soundcore 10208 1 snd
snd_page_alloc 10632 2 snd_intel8x0,snd_pcm
hw_random 5652 0
rtc 13492 0
shpchp 45632 0
pci_hotplug 29236 1 shpchp
intel_agp 22940 1
agpgart 34888 3 drm,intel_agp
evdev 9856 2
ext3 135688 1
jbd 58772 1 ext3
ide_generic 1536 0
ehci_hcd 34184 0
ohci1394 35124 0
ieee1394 299832 2 sbp2,ohci1394
uhci_hcd 33680 0
usbcore 130692 3 ehci_hcd,uhci_hcd
ide_cd 33028 0
cdrom 38560 2 sr_mod,ide_cd
ide_disk 17664 6
piix 11012 1
generic 5124 0
thermal 13576 0
processor 23360 2 speedstep_centrino,thermal
fan 4868 0
capability 5000 0
commoncap 7296 1 capability
vga16fb 13704 1
vgastate 10368 1 vga16fb
fbcon 42784 72
tileblit 2816 1 fbcon
font 8320 1 fbcon
bitblit 6272 1 fbcon
softcursor 2304 1 bitblit

My specs of my laptop are here : [http://benq-eu.com/products/joybook...=specifications](http://benq-eu.com/products/joybook...=specifications)

it is the S53W G01 specs.

I really hope you guys can help me out, cause for me to ditch windows i need sound for my work! My life is in your hands!

---

### Post by xyz on 2006-10-14
Hi hyby,

You probably already did this but just in case...have you ckecked Applications > Sound & Video > Volume Control and fiddle in there, see what's marked with a red x and so forth.

---

### Post by hyby on 2006-10-14
hi xyz,
thanks for the reply, yes i have...tried it countless times in many distros. I guess i have sound curse in linux

---

### Post by xpod on 2006-10-14
What about the "multimedia system selector"...if it`s not in your pref`s menu you can enable it in the "Alacarte menu editor"....scroll down to prefs and check the MSS box..

It`s good for checking sound and what devices are being used.....or not

---

### Post by hyby on 2006-10-16
Hi Guys,

Just an update, i have searched near and far for solutions however i have had no sucess

Things tried:
- alsamixer muting and unmutin
- external amplifier on/off - off by default
- updated my kernal
- synaptics says my alsa drivers are updated with the latest
- enabled mixers settings in menu and altered the output settings with OSS and ALSA
- tried headphones

New observation:

When i mute and unmute in alsamixer or with the desktop mixer settings, i hear a clicking sound

---

### Post by Sef on 2006-10-16
Try this, I couldn't get my sound working until I did this:

sudo gedit /etc/modprobe.d/alsa-base

This is what I got

```
# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
```

I commented out the next to last line and changed to last line from 2 to 0.

```
# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
# options snd-intel8x0m index=-2
options snd-via82xx-modem index=-0
```

---

### Post by junglepeanut on 2006-10-16
Have you tried using default? Mine does not work when I choose ICH6, but I am sure that is what I have, but it is fine under default. Also do you have external amplifier checked in gnome-volume-manager? I think it should be unchecked.

Just posting from old methods of fixing sound.

---

### Post by hyby on 2006-10-16
junglepeanut: i was wondering what do you mean by default? I was wondering where did you select default from?

When i checked for external amplfier it was already unchecked in the gnome-volume-manager

---

### Post by junglepeanut on 2006-10-16
If I open gnome-volume-manager and select options from the drop down. It has like a list bar with default and ICH6, of which only default works.

Maybe you are on default and yours is opposite who knows, just hoping to help out.

---

### Post by hyby on 2006-10-16
junglepeanut: cheers thanks for your help...ill give it a shot!

God! i love this community...i have this warm and fuzzy feeling.

---

### Post by junglepeanut on 2006-10-16
Apparently the external amplifier thing is an old fix, as mine does not seem to care whether it is checked or not (Edgy). 

The default issue occurs for me in both Edgy and Dapper.

Also what are we using as a test for sound? Maybe this will help?

i.e. beep does not work for me from the terminal but I have sound fine everywhere else.

---

### Post by hyby on 2006-10-16
i run the nelson mandela click to test for sound. I was wondering when you had your problems, when you muted and unmuted did you get a clicking sound?

---

### Post by junglepeanut on 2006-10-16
I don't recall if I had this issue when muting or unmuting before, but I do not have it now. But I get it and still get clicking when raising or lowering the volume while listening to sound in certain gnome environments. Not in KDE or XFCE.

---

### Post by junglepeanut on 2006-10-16
Well, hopefully some linux guru will step up to bat and cure you ails, because if the other tutorials did not work and this is not either I am out of ideas.

Hmm. I will keep looking. Maybe it is something fixed in Edgy? 

What application does it use? As there is a Nautilus bug for .ogg files for some individuals. 

Have you tried from killing esd and restarting it?

What does this say?

/proc/asound/cards

And how about your config

/etc/asound.conf

I don't really know what to look for in these but maybe they are blank or have no device etc, and we can then cut and paste from a working one. 

Mine are blank.

But I have this in 

/etc/esound/esd.conf

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=


And in 

/usr/share/alsa/pcm/iec958.conf


I have this 


#
#  Hardware output from iec958
#

pcm.!iec958 {
	@args [ CARD DEV AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
		default {
			@func getenv
			vars [
				ALSA_IEC958_CARD
				ALSA_PCM_CARD
				ALSA_CARD
			]
			default {
				@func refer
				name defaults.pcm.iec958.card
			}
		}
	}
	@args.DEV {
		type integer
		default {
			@func igetenv
			vars [
				ALSA_IEC958_DEVICE
			]
			default {
				@func refer
				name defaults.pcm.iec958.device
			}
		}
	}
	@args.AES0 {
		type integer
		# consumer, not-copyright, emphasis-none, mode=0
		default 0x04
	}
	@args.AES1 {
		type integer
		# original, PCM coder
		default 0x82
	}
	@args.AES2 {
		type integer
		# source and channel
		default 0x00
	}
	@args.AES3 {
		type integer
		# fs=48000Hz, clock accuracy=1000ppm
		default 0x02
	}
	@func refer
	name {
		@func concat
		strings [
			"cards."
			{
				@func card_driver
				card $CARD
			}
			".pcm.iec958." $DEV ":"
			"CARD=" $CARD ","
			"AES0=" $AES0 ","
			"AES1=" $AES1 ","
			"AES2=" $AES2 ","
			"AES3=" $AES3
		]
	}
}

---

### Post by junglepeanut on 2006-10-16
I did not use the code thing as I tend to have java off so it looks weird, but I think tabbing is not an issue for this as the brackets are used...

Hope this helps, let me know if you need additional .conf to compare

---

### Post by hyby on 2006-10-16
thanks junglepeanut for your assistance, i am gonna step away from trying to fix my sound for a 2-3 days as i have to edit my thesis and hand it in.

I appreciate your assistance, and would enjoy it when i begin to battle it in a few days

---

### Post by junglepeanut on 2006-10-16
I was just about to write I need to crash so I can work on my thesis in the morning, (4 hrs from now my adviser will walk into my office wanting to see what I have so far.) And I need a nap so I can whip up something quick before he arrives. 

Hope this gets worked out.

Jp

---

### Post by junglepeanut on 2006-10-16
Good luck on handing yours in.

---

### Post by hyby on 2006-10-22
Im back...back and fighting to get sound through my speakers!!!

Anybody with ICH6 soundcards get sound? of fixed their problems?

---

### Post by xyz on 2006-10-22
Oh man still no sound...after all this time!
You may already have read these but just incase:
[http://ubuntuforums.org/showthread.php?t=120070](http://ubuntuforums.org/showthread.php?t=120070)
[http://ubuntuforums.org/showthread.php?t=87849&highlight=ICH6](http://ubuntuforums.org/showthread.php?t=87849&highlight=ICH6)
Sorry if these links have already been suggested to you.

---

### Post by hyby on 2006-10-22
hahahahaha...

thanks for your links xyz...if you have some time could you check whether some of my config are correct. However, i am enjoying this troubleshooting game

---

### Post by hyby on 2006-10-28
*Bump*

I installed Edgy, and still no sound!!! 
ill post my .confs in a few days. 

Please help!

---

