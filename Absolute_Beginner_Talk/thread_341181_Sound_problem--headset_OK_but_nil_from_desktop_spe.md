---
title: "Sound problem--headset OK but nil from desktop speakers"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2007-01-18
I'd like to fix this but couldn't last time I tried.
Using Dapper on older Dell desktop and sound via speakers was fine until I bought and used Logitech USB 350 headset.  Now, sound via headset works but can't get sound through desktop speakers. (both work under XP)
I assumed (naively!?) that I could switch back & forth as with XP.
Sound preferences shows:  Intel 82801BA-ICH2 sound card and Logitech USB headset and both can be selected but only the headset works for system sounds or Amarok and I can lose headset sound in Amarok by trying to switch back/forth but can restore by reboot (tedious!).

So..any help or pointing to guides would be appreciated!

---

### Post by deadgobby on 2007-01-18
I am kinda Dumbfounded here. But lets try this. reboot the system with out the head set and with the speakers plugged in and see if Ubie picks the speakers by default. I am wounder if Ubie is seeing the USB head set and not going to the speaker out put. Or it is the BIOS.
Gobby

---

### Post by flyingsolo on 2007-01-18
Thanks for picking up my thread.
However, I've tried that before without luck.  Today I restarted in XP just to make sure the speakers still work on it and they do; I can also plug/unplug the USB headset to switch audio back/forth on XP but in Ubuntu, no way.  Most of the time I boot to dapper without headset in if I don't need audio.
Strange right?

---

### Post by deadgobby on 2007-01-18
I wounder if you need to make your head set as a 2cd drive? Here is a link that may give you a idea. Different type of head set, but it may be the same in basic.
[https://help.ubuntu.com/community/PlantronicsUSBHeadsetControls](https://help.ubuntu.com/community/PlantronicsUSBHeadsetControls)
Gobby

---

### Post by flyingsolo on 2007-01-18
Thanks again but I must say, I'm wary of messing with the headset functionality because it currently is my only sound output.  I just don't understand whatever happened to the regular sound output to speakers.

---

### Post by deadgobby on 2007-01-18
Ubie may be seeing as a drive. Like when I use a USB Flash. The drive icon pops up and ready to go. I do not have a head set to play with or I will be more useful engine. Darn my kids and Thomas the Tank Engine vids. ](*,)

---

### Post by flyingsolo on 2007-01-23
OK--I'd like to pick someone's brain if you please!
When I go: Preference-->Sound I see the Intel 82801BA-ICH2 on board sound card.  If I plug in the headset, the Intel card and Logitech Headset appear in same place with a drop down to select one or other.
When I do alsamixer in Terminal I get the following:

alsamixer: function snd_ctl_open failed for default: No such device

So this seems to perhaps be a source of problem but I don't really know what I should do to correct this!
Thanks.

---

### Post by flyingsolo on 2007-02-18
Still trying!  I've been following the sticky above: Comprehensive sound solution guide [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)
but no success yet...looking for help out there!
For aplay, I see the intel sound card and the USB headset:
```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

but alsamixer only shows the headset.
From lslpci -v, I get:
```
0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
        Subsystem: Dell: Unknown device 0145
        Flags: medium devsel, IRQ 11
        I/O ports at dcf0 [size=16]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Au dio (rev 04)
        Subsystem: Dell: Unknown device 0145
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at d800 [size=256]
        I/O ports at dc80 [size=64]
```

So it would seem Dapper sees the intel card but alsamixer doesn't?  Following the tutorial, I have:
```
~$ cat /proc/asound/modules
0 snd_intel8x0
1 snd_usb_audio
```

so I know the sound modules are present.
This is all very frustrating but hopefully some bright light out there can spot the problem for, alas, I am still but a noob after 2 years on Ubuntu!
Thanks.

---

### Post by flyingsolo on 2007-02-18
OK--one small thing fixed; I can get alsamixer to see the intel sound card by System-->Pref-->Sound and selecting intel card from drop down of default sound cards.  So I can adjust the settings for the sound card but it   
DOESN'T work--ie:  still no sound from desktop speakers!  (nothing muted in alsa settings)

---

### Post by flyingsolo on 2007-02-27
Just a BUMP.  I'm still trying but was hoping for an audio angel of mercy to guide me!

From what I can tell, my sound card is recognized and levels are turned up in alsamixer but still it just doesn't work!  Arrgh!

---

### Post by flyingsolo on 2007-03-01
I experimented by running my system from the original CD of Dapper & I can get sound through desktop speakers or USB headset just by switching which card is default in System-->Pref-->Sound but the same process doesn't work in my installed Dapper which has been present for one year.

Clearly, the Dapper run in RAM from CD is a bare-bones Ubuntu compared to my hard drive install which includes many other programs like Amarok, Audacity, Java and Flash for Firefox and lots more.  This leads me to think one of these programs is somehow altering how the sound is configured but I really don't know how to further troubleshoot this.  Does anyone have an idea?  Would be much appreciated.

---

### Post by ubromtoo on 2007-03-01
Flyingsolo:

     maybe you could help this noob:  when I go into Terminal and type alsamixer

and then hit enter, some of the sound levels are turned completely down. 

     How do I turn them up/down? and what do the different colors mean?

     The reason I ask is because the little built-in speakers of my monitor work, but

the speakers which plug-in to my comp. tower do not work.(in windows xp they work)

              Sincere thanks from a Newbie,

                ubromtoo         :)

---

### Post by flyingsolo on 2007-03-02
In alsamixer you select the different columns by TAB repeatedly which moves from one to the next.  If the item you want to change has MM at the bottom of it, it is muted--just type 'm' to toggle mute on/off.  Once it is on, use your up/down arrows to adjust the volume level for the device.  Once all is set as you wish, ESC will exit alsamixer.

---

### Post by ubromtoo on 2007-03-02
Flyingsolo

     thanks for the help...although whatever iec958 is, the up/down arrows do

nothing, even after i turned it on with the "m" key.  any ideas?

     btw, found out by trial-and-error that the "h" key gives me a small Help 

screen.

               thanks for the help!   :)

---

### Post by freebird54 on 2007-03-02
Not sure if it is relevant - but I was SURE I had everyhting relevant turned on/unmuted/loud enough in alsamixer - but not until I turned EVERYTHING up (from the first to the last) did I get any sound.  Revisit alsamixer just for the fun....

---

### Post by ubromtoo on 2007-03-02
freebird54


       did what you said, but iec958 still won't budge, and still no sound.

   Thank you for the suggestion, though   :)

---

