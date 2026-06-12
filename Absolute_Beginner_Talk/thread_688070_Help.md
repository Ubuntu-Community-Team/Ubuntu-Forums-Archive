---
title: "Help"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by N6e6r6o on 2008-02-05
so i got gutsy to install on my dell laptop and i cant figure out how to get connected to my wireless network and it doesnt pick up my sound card please help

---

### Post by LaRoza on 2008-02-05
Giving your wireless adapter and sound card would help.

---

### Post by N6e6r6o on 2008-02-05
o sorry, the sound is a sigmatel 9205 and all the wireless says is dell wireless and i have a netgear router

---

### Post by N6e6r6o on 2008-02-05
i know im not very tech savy but any help would be greatly appreciated

---

### Post by erginemr on 2008-02-05
Maybe I am not the one to answer this question, since I am not using any wireless modem either, but AFAIK, there is a tool "ndisgtk", which can be installed via:
```
sudo aptitude install ndisgtk
```
which will install "ndiswrapper" tools alongside, the technology which allows wireless modem owners to use their windows (*.inf) drivers from under Linux. The following site discusses this issue in depth:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Also follow anewguy's post from:
[http://ubuntuforums.org/showthread.php?t=688034](http://ubuntuforums.org/showthread.php?t=688034)

---

### Post by erginemr on 2008-02-05
Regarding your sound card problem, can you please post the output of:
```
cat /etc/modprobe.d/alsa-base
```
and that of the following command:
```
lspci | grep audio
```
(both commands to be run from a console) here?

---

### Post by N6e6r6o on 2008-02-05
i know i sound like a total noob but uh... how do i do that?

---

### Post by Cypher on 2008-02-05
Open up a terminal under Applications->Accessories->Terminal and then type in the commands that **erginemr** suggested.

---

### Post by N6e6r6o on 2008-02-05
i cant really post the outputs because they are on a different computer and i'd be a pain to type all that but i did do both of the ones for the sound card

---

### Post by N6e6r6o on 2008-02-05
actually i dont think that second one worked right

---

### Post by seventhc on 2008-02-05
if the wireless isn't working, why don't you plug it in for now so you can connect and post the output. Otherwise it's going to be near impossible to help..or very difficult. ;)
Or maybe if you have a flash drive you can save the output and then open it from the connected computer.

---

### Post by erginemr on 2008-02-05
To save the output as indicated by **seventhc** above, you need to copy the output of the terminal by selecting the text in the terminal and paste it to Accessories -> Gnome Editor (gedit) by middle-clicking in it.

You can then save the file to a floppy or a pen drive.

For the wireless, you can also refer to the following Wireless Howto:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by N6e6r6o on 2008-02-07
ner0@ner0-laptop:~$ cat /etc/modprobe.d/alsa-base
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

and when i type the second command nothing happens
appreciate the help guys

---

### Post by erginemr on 2008-02-07
My alsa-base file is precisely the same as yours:
```
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
```

and I have sound. So, there is nothing wrong in it. Meanwhile, the second command "lspci | grep audio" yielding no feedback meand your sound card -surprise- hasn't been detected. 

I believe to have seen threads with similar problems involving "HDA Intel" sound cards, which should have been solved by adding an appropriate line to the "/etc/modprobe.d/alsa-base" file. So, you should do a Google research and focus on these keywords. I am also on it...

I also hope that my thread will work as a big BUMP! (bring up my post), so that other users will notice your post and give us a hand...

---

### Post by erginemr on 2008-02-07
Here are my findings:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

[http://mrtrick.org/2007/10/15/gutsy-now-with-sound-again-finally/](http://mrtrick.org/2007/10/15/gutsy-now-with-sound-again-finally/)

Given the fact that you have a DELL laptop and a Sigmatel 9205 sound chipset, I believe we are on the right track. I suggest you to read all of them thoroughly first before taking any action, and try first editing only the alsa-base config file:
```
gksu gedit /etc/modprobe.d/alsa-base
```
and add the following line:
```
options snd-hda-intel model=MODEL
```
Replace MODEL with first auto, dell-3stack, laptop and so on as suggested by the above threads, such as:
```
options snd-hda-intel model=auto
```
Reboot and see if you have sound (also do not forget to check out the sound volume control while doing this). 

If there still is no sound, then you will have to download and reinstall the Alsa sound driver following the steps given in the above posts.

---

### Post by erginemr on 2008-02-07
Here is another one:

[http://chriseckman.com/?p=3](http://chriseckman.com/?p=3)

Look for the section _**Audio**_. Good Luck!

---

### Post by N6e6r6o on 2008-02-07
thanks alot i'll let you know tonight

---

