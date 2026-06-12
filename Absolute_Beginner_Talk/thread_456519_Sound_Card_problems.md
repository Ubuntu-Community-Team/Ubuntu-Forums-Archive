---
title: "Sound Card problems"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by MikeJ112 on 2007-05-27
Hi, have installed ubuntu 6.10, but I am not getting any sound. Have checked in device manager, its showing up as "82801BA/BAM AC'97 Audio" but not working. HELP!

---

### Post by cymen on 2007-05-27
Open up alsamixer in a terminal and have a play with the sliders. It might help.

---

### Post by MikeJ112 on 2007-05-27
Just attempted to do this, and I was given this error message.

```
alsamixer: function snd_ctl_open failed for default: No such device
```

---

### Post by cymen on 2007-05-27
That sounds as if something's going amiss with the detection/drivers. I'd advise you to follow this excellent troubleshooting thread: [Comprehensive Sound Guide]("http://ubuntuforums.org/showthread.php?t=205449"). Hopefully something on there will help you to at least further diagnose the problem, if not solve it.

---

### Post by MikeJ112 on 2007-05-27
OK I have managed to find out that the chipset is Intel 815, where do I now go from here. Have tried following the Tutorial but when I press TAB in the terminal the screen just flashes

Cheers

---

### Post by MikeJ112 on 2007-05-28
I'm upgrading to v7.04 now, would this resolve the problem?

---

### Post by cymen on 2007-05-28
Right, so the Intel 815 uses the intel8x0 driver by the looks of things. So you'll want to do this:

```
sudo modprobe snd-intel8x0
```

But don't press enter - instead press tab *twice*. You should see one or two drivers listed - including snd-intel8x0. Then press enter. You should then be fine to follow the rest of the guide. 

Upgrading might solve this all automatically, though!

---

### Post by MikeJ112 on 2007-05-28
> **cymen said:**
> Right, so the Intel 815 uses the intel8x0 driver by the looks of things. So you'll want to do this:

```
sudo modprobe snd-intel8x0
```

But don't press enter - instead press tab *twice*. You should see one or two drivers listed - including snd-intel8x0. Then press enter. You should then be fine to follow the rest of the guide. 

Upgrading might solve this all automatically, though!

Sorry to keep dragging this up guys, when I press enter it just goes back to command line, have pressed tabs and it displays the drivers, but when i run;

```
sudo modprobe snd-intel8x0
```

then type alsamixer it says no such device

I'm now on 7.04

I've got admin rights as well :)

:???:

---

### Post by MikeJ112 on 2007-05-28
Any ideas guys?

---

### Post by MikeJ112 on 2007-05-28
Also, its an ASUS mobo. Would this be another reason why it wont work?

---

### Post by MikeJ112 on 2007-05-29
Does anyone else know what could be causing this?

---

### Post by BobLand on 2007-05-29
Mike,
I've had similar problems.  I also have an ASUS board.  You must be certain that your driver is found in /proc/asound/modules.  Make a number of the position.  It should be either 0 or 1 (or other numbers if more sound cards--but that's a whole different matter).

Run
```
cat /etc/modprobe.d/alsa-base
```

Look for your driver.  If it's not there then add it much like the other drivers.   On my system it looks like this:
```
options snd-ca0106 index=-1
```

If you don't find it, add it.  Make sure it is the lowest index number.  The other drivers should be 2.  Use the index number found in alsa-base.

When I reboot I usually loose sound.  To fix this (works so far but keeping fingers crossed), I ran 
```
sudo apt-get install libxine-extracodecs
reboot
```

There is an intertwining relationship with sound and audio.  Sometimes changing an audio setting will fix a video problem and visa versa.

If it still doesn't work open /etc/modules and comment out everything except your driver.
Run
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
reboot
```

On some reboots or when reinstalling these drivers /etc/modprobe.d/alsa-base may be overwritten so if you don't have sound after a reboot, check this file for your driver and re-add if necessary.  Probably a good idea to reboot after this addition.

This worked for me.  Hopefully, it will work for you or at least give you some clues.
Bobland

---

### Post by MikeJ112 on 2007-05-29
> **BobLand said:**
> Mike,
I've had similar problems.  I also have an ASUS board.  You must be certain that your driver is found in /proc/asound/modules.  Make a number of the position.  It should be either 0 or 1 (or other numbers if more sound cards--but that's a whole different matter).

Run
```
cat /etc/modprobe.d/alsa-base
```

Look for your driver.  If it's not there then add it much like the other drivers.   On my system it looks like this:
```
options snd-ca0106 index=-1
```

If you don't find it, add it.  Make sure it is the lowest index number.  The other drivers should be 2.  Use the index number found in alsa-base.

When I reboot I usually loose sound.  To fix this (works so far but keeping fingers crossed), I ran 
```
sudo apt-get install libxine-extracodecs
reboot
```

There is an intertwining relationship with sound and audio.  Sometimes changing an audio setting will fix a video problem and visa versa.

If it still doesn't work open /etc/modules and comment out everything except your driver.
Run
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
reboot
```

On some reboots or when reinstalling these drivers /etc/modprobe.d/alsa-base may be overwritten so if you don't have sound after a reboot, check this file for your driver and re-add if necessary.  Probably a good idea to reboot after this addition.

This worked for me.  Hopefully, it will work for you or at least give you some clues.
Bobland

Thanks for your response Bobland; on typing the first command line I am presented with

```
mike@ubuntu:~$ cat /etc/modprobe.d/alsa-base
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
options snd-cmipci mpu_port=0x330 fm_port=0x388
mike@ubuntu:~$ 

```

My chipset (815) is intel8x0.... There is 8x0m on there but thats for modem, how do I add 8x0 and what do I need to change with any of these?

Thanks

---

### Post by MikeJ112 on 2007-05-29
Not too worry now, got fed up and bought a PCI soundcard!

---

### Post by davver on 2007-12-15
I'm getting problems too. I have Ubuntu (Gutsy) 7.10 installed, but had the same problem with a previous version too. I'm very new to the Linux world but I'm not too shabby with PC Hardware. Setup:

AMD64 3000+
Audigy 2 Sound Board
Onboard sound (Realtek)
1024 Meg RAM

I have disabled the onboard sound through the BIOS so it shouldn't be detected but IS being detected??? Therefore both sound sources are being detected and obviously there's a clash. I want to use the Audigy 2 due to my Ubuntu being partitioned on the same disk as Windows XP *cough There are no issues so far with this btw.

SO main problem peeps is that both cards are being detected and Ubuntu keeps changing its mind. One minute it will use the Audigy Drivers, then next reboot, it'll decide to use the Realtek drivers??? See my confusion. I know I could simply take out the Audigy 2 card, but I would rather not as it's a damn good card.

I have also checked using the ALSAMIXER command in the Terminal and it sees only the card/driver that it has loaded. Am I doing something wrong?:confused:

Thank for your help!

Dave

---

### Post by bobpur on 2007-12-15
What CPU are you running on that ASUS Mobo? I have two Socket 939 A8N-32 SLI Deluxe mobo's that definitely do not like Linux in any form. I have two other ASUS mobo's that dualboot Windows and Ubuntu like a champ. One is an AM2 with a 5600+ AMD dualcore CPU and the other is a 775 Intel Core 2 duo 2.66 ghz.

---

