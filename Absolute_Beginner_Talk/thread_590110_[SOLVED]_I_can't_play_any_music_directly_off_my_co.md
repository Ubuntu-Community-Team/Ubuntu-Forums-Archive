---
title: "[SOLVED] I can't play any music directly off my computer"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by DutyDuty on 2007-10-24
After I upgraded to Gusty, I lost my ability to play sounds from my hard drive. Banshee, Rhythmbox, Sound Juicer, nothing! They don't play CDs, either. I know my sound is fine since I can hear things on Youtube and such. Any suggestions?

---

### Post by Pumalite on 2007-10-24
This might help:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://ubuntuforums.org/showthread.php?t=503342](http://ubuntuforums.org/showthread.php?t=503342)

---

### Post by DutyDuty on 2007-10-24
According to the new Springsteen CD, those were not the answers.

---

### Post by Pumalite on 2007-10-24
What does the command: aplay -l says.

---

### Post by DutyDuty on 2007-10-25
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

What did that do?

---

### Post by DutyDuty on 2007-10-26
bump

---

### Post by MegaJim on 2007-10-26
that last command just shows us if Ubuntu has detected any audio hardware, which it has

check out this general sound troubleshooter for ubuntu:

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by DutyDuty on 2007-10-27
That was fun to read and all, but no such luck.

---

### Post by argie on 2007-10-27
Hmm, what do the volume sliders show when you run 'alsamixer' in the terminal?

---

### Post by DutyDuty on 2007-10-27
I'm afraid I'm not being clear. The progress through the song, the bar stays at 0:00 forever.

---

### Post by DutyDuty on 2007-10-31
bump 2.0

---

### Post by DutyDuty on 2007-11-01
Lather, rinse, bump.

---

### Post by anatolica on 2007-11-02
Hi:) I am a veeery newbie and I also cannot play any music or movie file.. totem, amarok, atc. all freeze and become dull when I click on a movie or music file... I got the "Sound server fatal error: Error while initializing the sound driver: device: default can't be opened for playback (Operation not permitted)".. Possibly I messed up with somewhere, but I really cannot get any way around this problem, please help:))

---

### Post by Pumalite on 2007-11-02
Try:

sudo apt-get install linux-backports-modules-generic

---

### Post by DutyDuty on 2007-11-03
No such luck, again: the problem is that the song never starts.0:00 is all I see.

---

### Post by Pumalite on 2007-11-03
Post the output of this at the Terminal:
alsamixer

---

### Post by DutyDuty on 2007-11-04
```
alsamixer: function snd_ctl_open failed for default: No such device

```

As I've said, it's not so much the lack of sound, because I can hear Youtube videos, etc. CDs, music stored on my computer, never starts, just remains at 0:00. 
I'm still not sure anyone is receiving that idea.

---

### Post by SunnyRabbiera on 2007-11-04
are you sure this is not a codec issue?

---

### Post by DutyDuty on 2007-11-04
Oh, and according to ```
alsamixer -c 0
``` nothing is muted, except Caller 1, which I un-muted to no avail.

---

### Post by DutyDuty on 2007-11-04
Oops. A what issue?

---

### Post by DutyDuty on 2007-11-05
Yet another bump.

---

### Post by Pumalite on 2007-11-05
What about:

sudo lshw -C sound

---

### Post by Happy_Man on 2007-11-05
Perhaps it's just a problem with your Gstreamer plugins? Go to Add/Remove and search Gstreamer and reinstall/install whatever comes up.

---

### Post by SunnyRabbiera on 2007-11-05
> **DutyDuty said:**
> Oops. A what issue?

Codecs can help you play media, if you use the gstreamer stuff I can understand why you have issues.
Gstreamer is okay but you might want to download an app called automatix to help out.

---

### Post by Pumalite on 2007-11-05
According to prior post by OP, I have the feeling that the kernel is not recognizing the card and therefore, not loading the module. So, another thing to try is this:

sudo apt-get install linux-backports-modules-generic

---

### Post by DutyDuty on 2007-11-05
sudo lshw -C sound yields ```
  *-multimedia            
       description: Audio device
       product: SB450 HDA Audio
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel
```
I already have Automatix, and sudo apt-get install linux-backports-modules-generic was already installed.

I also re-installed all Gstreamer related programs to no avail.

---

### Post by Pumalite on 2007-11-05
I just found this:

[http://ubuntuforums.org/showthread.php?t=604084](http://ubuntuforums.org/showthread.php?t=604084)

---

### Post by DutyDuty on 2007-11-05
How do I say this properly? I have sound, but not off my hard drive. I can hear Firefox/Opera and the startup make sounds, but Banshee and Rhythm-box and other devices are not playing songs. It is not mute. Everything is fine with alsamixer. I have a properly hooked up sound card. I feel like I've been through this one hundred times. I've read other threads. They haven't helped.

---

### Post by DutyDuty on 2007-11-06
*sigh* bump

---

### Post by Happy_Man on 2007-11-06
Maybe it's a problem with ALSA itself? Try the sound off of a LiveCD, and see if it is that which is causing the problem...

---

### Post by DutyDuty on 2007-11-08
I don't have a CD burner...I resent having to order a CD, so can we try something else?

---

### Post by DutyDuty on 2007-11-10
This problem doesn't go away, you know! bump...

---

