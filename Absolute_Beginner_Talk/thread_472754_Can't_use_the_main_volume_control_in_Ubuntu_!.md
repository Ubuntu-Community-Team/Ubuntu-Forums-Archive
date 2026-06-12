---
title: "Can't use the main volume control in Ubuntu !"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Najmudin on 2007-06-13
The sound in my system is working but i can't use the main volume control , is there something missing or what  should i do to make work with me.:!::roll:

---

### Post by dannyboy79 on 2007-06-13
when requesting help, you should really be specific as I am not sure what you mean by this, you mean you don't see the volume control? you mean that you see it but when you go up and down it doesn't affect the sound that's coming from the speakers? please be very specific. also, pleaser post the results of the following commands that you enter in a terminal session.

lspci

aplay -l

---

### Post by Najmudin on 2007-06-13
> **dannyboy79 said:**
> when requesting help, you should really be specific as I am not sure what you mean by this, you mean you don't see the volume control? you mean that you see it but when you go up and down it doesn't affect the sound that's coming from the speakers? please be very specific. also, pleaser post the results of the following commands that you enter in a terminal session.

lspci

aplay -l

I'm sorry for that , i can see the volume control but it dose not effect when i go up and down , i put the command in the terminal and i got this result:
[PHP]najmudin@najmudin-desktop:~$ 
najmudin@najmudin-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:01.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
02:03.0 Multimedia audio controller: Creative Labs SB Audigy LS
02:05.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
najmudin@najmudin-desktop:~$ 
najmudin@najmudin-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
najmudin@najmudin-desktop:~$ [/PHP]

---

### Post by dannyboy79 on 2007-06-13
the volume control is most likely controlling the OTHER sound card as you have a built in one and a PCI one. you should be able to double click the volume control, once it comes up with a dialog, then you should be able to go somwhere witin the menu's and choose hte card you want it to control. If I were you, I woiuld disable the onbaord sound int he bios so there's no confliction. linux in my experience doesn't handle multiple devices well BUT that could just be my experience only and some1 will probably chime in and say otherwise which is again, only THEIR experience and not everyones. good luck. you could always gogle it also, just type in
multiple sound cards and ubuntu
and you should get some good returns.

---

### Post by Najmudin on 2007-06-14
> **dannyboy79 said:**
> the volume control is most likely controlling the OTHER sound card as you have a built in one and a PCI one. you should be able to double click the volume control, once it comes up with a dialog, then you should be able to go somwhere witin the menu's and choose hte card you want it to control. If I were you, I woiuld disable the onbaord sound int he bios so there's no confliction. linux in my experience doesn't handle multiple devices well BUT that could just be my experience only and some1 will probably chime in and say otherwise which is again, only THEIR experience and not everyones. good luck. you could always gogle it also, just type in
multiple sound cards and ubuntu
and you should get some good returns.

I goggled like you advised me, i found a site with instruction on how to control my sound cards , i followed the instruction , using this :

sudo gedit /etc/asound.conf

a file apeared i entered this:

 pcm.!default { type hw card 1 } ctl.!default { type hw card 1 }

Then save and close it.
after that i entered this to restart alsa:

sudo /etc/init.d/alsa-utils restart

After that i get problems with my sound, its not working with some parts in my system, for example the sound in Firefox is not working when i try to run a video from (youtube)  it dose not work ,at the same time  when trying to run a sound file from a media player like audacious it works, strange ???
I tried to change the card numbers again , for example the first one to {0} the second one to {1} 
When i did this the opposite happened  the youtube.com video worked, but the media player did not ???!!! then i tried to change it again & again , but each time something wrong happen and some times i cant hear anything at all.
I'm getting frustrated , i just want to get back to the default sound setting that was working well , but i don't know how to do that ???
Sorry for my English
Please some one help :(

---

### Post by dannyboy79 on 2007-06-14
well what you're doing is changing your sound cards around within alsa and it appears that each of the programs are calling for the different cards instead of ALL programs calling for the same one, it's got to be a setting within each of the programs I may guess.
do you have this file:
/etc/modprobe.d/alsa-base
does it have this at the bottom which basically index's each of the modules to a certain card?
# My own options, combined with the solution for Ubuntu bug #62691
options snd-cmipci mpu_port=0x330 fm_port=0x388 index=0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

OR


you could always try to reinstall alsa-base or maybe just reconfigure it by issueing: 
dpkg-reconfigure alsa-base

---

### Post by Najmudin on 2007-06-14
I have the file and here is what is there:

[HTML]# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388[/HTML]

but what i have to change there , should i copy - paste your setting in the file or what .
I tried to reinstall alsa but it said you have to be root to make changes,how can i be root ??

---

### Post by dannyboy79 on 2007-06-14
> **Najmudin said:**
> I have the file and here is what is there:

[HTML]# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388[/HTML]

but what i have to change there , should i copy - paste your setting in the file or what .
I tried to reinstall alsa but it said you have to be root to make changes,how can i be root ??

NO, don't just copy what I posted, that was a hint at what to do and probably doesn't have your sound driver so it wouldn't work. You would have to apply this line, "# My own options, combined with the solution for Ubuntu bug #62691
options snd-cmipci mpu_port=0x330 fm_port=0x388 index=0" and adjust it to fit your needs.
OH, you're that new that you aren't aware of sudo? well you need to use sudo before any commands that require admin rights. just open your package manager within System, Admin, Synaptic, when it asks for a password, it's the same as what you made whne you installed ubuntu. it's the sudo password. then do a search for alsa-base, then right click and do reinstall. or do the reconfigure command like I suggested just using sudo.
sudo dpkg-reconfigure alsa-base 
BUT this will ask you a bunch of questions that you may not be able answer. Normally the defaults will work though.
You should really read up on some basic linux knowledge if I were you. read a beginner's guide to ubuntu webpage or something.

---

### Post by Najmudin on 2007-06-14
> **dannyboy79 said:**
> NO, don't just copy what I posted, that was a hint at what to do and probably doesn't have your sound driver so it wouldn't work. You would have to apply this line, "# My own options, combined with the solution for Ubuntu bug #62691
options snd-cmipci mpu_port=0x330 fm_port=0x388 index=0" and adjust it to fit your needs.
OH, you're that new that you aren't aware of sudo? well you need to use sudo before any commands that require admin rights. just open your package manager within System, Admin, Synaptic, when it asks for a password, it's the same as what you made whne you installed ubuntu. it's the sudo password. then do a search for alsa-base, then right click and do reinstall. or do the reconfigure command like I suggested just using sudo.
sudo dpkg-reconfigure alsa-base 
BUT this will ask you a bunch of questions that you may not be able answer. Normally the defaults will work though.
You should really read up on some basic linux knowledge if I were you. read a beginner's guide to ubuntu webpage or something.

First of all i have to thank for your help and follow up on the issue .
as you can see i'm still a beginner, i agree with you that i have to read more about Linux or Ubuntu , but for now I'm just asking for simple way or instruction to solve the problem i have ( this also will give me more experience and learning).
I decided to use Ubuntu for its user friendly interface and many great things it has above other Linux distributions and windows, for me i can be patient on these problems , but for those people like my sister my friends , other people whom i asked to use Ubuntu over windows if they face these problems they will just simply return back to windows , what i want to say is that there should be an easier way to do that instead of searching for system files or using orders in terminal ( maybe using an option in the system sound to do these things , i think many people who are using windows and wants to change to Ubuntu will not like it that way.:)

Return to the problem      

[HTML]
You would have to apply this line, "# My own options, combined with the solution for Ubuntu bug #62691
options snd-cmipci mpu_port=0x330 fm_port=0x388 index=0" and adjust it to fit your needs.[/HTML]

Where should i apply the above line because i did not get it at all.:D

---

### Post by drs305 on 2007-06-14
By any chance did you do a windows xp update today? I did and lost my sound. It's the first time I've ever had an ubuntu sound problem. All I had to to was go to system, preferences, sound and deselect and reselect my mixers and everything returned to normal. Prior to that, all the sound volume sliders were selected and moved but still didn't allow any sounds, including the test sounds.

---

### Post by dannyboy79 on 2007-06-14
> **Najmudin said:**
> First of all i have to thank for your help and follow up on the issue .
as you can see i'm still a beginner, i agree with you that i have to read more about Linux or Ubuntu , but for now I'm just asking for simple way or instruction to solve the problem i have ( this also will give me more experience and learning).
I decided to use Ubuntu for its user friendly interface and many great things it has above other Linux distributions and windows, for me i can be patient on these problems , but for those people like my sister my friends , other people whom i asked to use Ubuntu over windows if they face these problems they will just simply return back to windows , what i want to say is that there should be an easier way to do that instead of searching for system files or using orders in terminal ( maybe using an option in the system sound to do these things , i think many people who are using windows and wants to change to Ubuntu will not like it that way.:)

Return to the problem      

[HTML]
You would have to apply this line, "# My own options, combined with the solution for Ubuntu bug #62691
options snd-cmipci mpu_port=0x330 fm_port=0x388 index=0" and adjust it to fit your needs.[/HTML]

Where should i apply the above line because i did not get it at all.:D
I don't disagree with you regarding this quote unquote simple issue, it should be easier to fix it, BUT it's not. I don't have 2 sound cards, and don't have this problem.I have 1.5 years of linux experience and a strong desire to help others IF I CAN. All I haev been doing is gogling stuff and presenting you with the soliutions I have found!
OK, as far as editing this file I mentioned, you're way underqualified to do this and I really don't have the time to invetigate what module your sound card is using and the rest that is required with adding this option to that file. SO.........

Either you read the thread above mine and see if this XP update thingy and suggested fix works, or you gogle around or you wait for other's to come to help or you try the sudo reconfigure command I gave or you try to reinstall alsa-base. Other than those suggestions, I can't help ya anymore. good luck

---

### Post by mercals on 2007-06-14
All of my sound problems came from having 3 sound devices listed. I disabled the onboard sound device in BIOS and then the fun begain. I searched high and low for a way to enable sound through my SB Live! card. There was lots of information out there on sound problems in Ubuntu. I finally found the answer deep in the replies to a post on the Ubuntu forums. A simple fix compared to all the othere information I had encountered. In terminal simply do the following.

asoundconf - This will list commands to use with asoundconf.

asoundconf list - This will list your cards by name.
                  (my output was)
		  Names of available sound cards:
		  rev20
                  Live
                  
asoundconf set-default-card CARD - Card being the name of the sound card      you wish to use. In my case it was Live.

Then right click on the volume controller on the taskbar and select prefrences. Selecte your card from the drop down list and select master.

This worked for me and I hope it does for you!

---

### Post by Najmudin on 2007-06-14
> **mercals said:**
> All of my sound problems came from having 3 sound devices listed. I disabled the onboard sound device in BIOS and then the fun begain. I searched high and low for a way to enable sound through my SB Live! card. There was lots of information out there on sound problems in Ubuntu. I finally found the answer deep in the replies to a post on the Ubuntu forums. A simple fix compared to all the othere information I had encountered. In terminal simply do the following.

asoundconf - This will list commands to use with asoundconf.

asoundconf list - This will list your cards by name.
                  (my output was)
		  Names of available sound cards:
		  rev20
                  Live
                  
asoundconf set-default-card CARD - Card being the name of the sound card      you wish to use. In my case it was Live.

Then right click on the volume controller on the taskbar and select prefrences. Selecte your card from the drop down list and select master.

This worked for me and I hope it does for you!

I followed you tips , and every thing is fine now :p
I'm using now my on board sound , i tried to disable the on board sound card and use my sound blaster but failed , doesn't matter .
Thanks too much to you mate for your help.;)

---

### Post by dannyboy79 on 2007-06-14
> **Najmudin said:**
> I followed you tips , and every thing is fine now :p
I'm using now my on board sound , i tried to disable the on board sound card and use my sound blaster but failed , doesn't matter .
Thanks too much to you mate for your help.;)

I am glad some1 has helped you.

---

### Post by aquamammal on 2007-11-13
I don't know if the problem has been fixed, but right click on the sound control icon and choose preferences, then PCM. That might help.

---

