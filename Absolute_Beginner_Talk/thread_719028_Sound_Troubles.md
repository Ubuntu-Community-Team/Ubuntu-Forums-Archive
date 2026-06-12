---
title: "Sound Troubles"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by heyniceaddress on 2008-03-08
I have installed Ubuntu on both my desktop (three years old from Dell) and my new laptop, also from Dell. I have no sound on either. I believe the problem is that I have sound blaster x-fi on my desktop. I don't know what i have on my laptop, though. But both of them tell me that i have no gstreamer plugins and/or devices available, which I do, because I installed them all with Synoptic. I've another post on here regarding the same thing and did everything that people told me to no avail. I've looked at many other links and sites that discuss it, but I have not yet fixed it. 

I found this, though, and am wondering whether this would help me out:

[http://www.opensound.com/index.html](http://www.opensound.com/index.html)

If so, does anybody know whether it can be installed in Ubuntu 7.10; if so, which download do I choose; also, how do I go about installing it?

Thank you for your time in advance, I appreciate it.

---

### Post by LuisGMarine on 2008-03-08
Type this command into your terminal and post the output:
```

sudo lshw -C multimedia
```

This command is going to display the type of audio card that your dell PC has, this is going to help the community determine what kind of troubleshooting we need to start.

---

### Post by heyniceaddress on 2008-03-08
Thanks...here's what came up:

*-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: SB X-Fi
       vendor: Creative Labs
       physical id: 4
       bus info: pci@0000:05:04.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=64 maxlatency=5 mingnt=4

---

### Post by LuisGMarine on 2008-03-08
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

according to alsa your card isn't supported.  Although from googling there are some people that say the beta drivers from creative labs work, the problem is that they only released it for 64-bit Linux, and not 32-bit.

If you want you can compile the latest drivers from alsa, and see if that works.  

First paste the output of this command:
```

gksu gedit /etc/modprobe.d/alsa-base

```

We can try to change some options in that file, if nothign works then I will give you the guide compile the alsa drivers and hopefully that will work if not, I'm not sure what to do.  Sorry :\

---

### Post by heyniceaddress on 2008-03-08
Here were the results:

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=auto

Thanks for the responses, I appreciate your helpfulness. It will be nice once I become more accustomed to Ubuntu/Linux and am able to understand code for myself.

---

### Post by LuisGMarine on 2008-03-08
run this command again :
```

gksu gedit /etc/modprobe.d/alsa-base
```

edit the line at the end of the file,

```
options snd-hda-intel model=auto
```

so it reads 

```
options snd-hda-intel model=dell
```

save it and reboot and test sound, if that doesn't work do the same steps and rename it so it reads

```
options snd-hda-intel model=3stack
```

and reboot again and try sound.  Hopefully one of these two settings will work.

---

### Post by LuisGMarine on 2008-03-08
Here is the guide to compile the latest ALSA source

[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

try this and then retry the modifcations I suggested in the earlier post and test sound.  I hope it works!

---

### Post by heyniceaddress on 2008-03-08
I tried both, but neither of them worked; thank you regardlessly.

I'll take a look at that site you sent me.

---

### Post by heyniceaddress on 2008-03-08
I went through that site and followed it exactly, and then I re-tried both of your edits, but it had no effect. My computer's volume always has a slash through it (and its not muted), and when I click on it it says: 

No volume control GStreamer plugins and/or devices found.

And

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

---

### Post by superprash2003 on 2008-03-10
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by heyniceaddress on 2008-03-10
I tried the other options with rebooting in between and every time I tested the sound I got this error box: 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

---

### Post by cmnorton on 2008-03-13
> **LuisGMarine said:**
> Type this command into your terminal and post the output:
```

sudo lshw -C multimedia
```This command is going to display the type of audio card that your dell PC has, this is going to help the community determine what kind of troubleshooting we need to start.

Thanks for posting this. I too have no sound. Here is the output of the command:

 sudo lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by cmnorton on 2008-03-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/122560](https://bugs.launchpad.net/ubuntu/+bug/122560) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 I got my Thinkpad T61p's sound working by adding the following to the end of /etc/modprobe.d/alsa-base

options snd-hda-intel model=thinkpad-t61p

There was no magic list containing my model number. Someone else had a problem with their Dell; and added this line

options snd-hda-intel model=dell-m26

Basically, I put a dash in between the brand and the model and took a guess. I now have sound.

---

