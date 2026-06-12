---
title: "No Sound in Kubuntu 7.04"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Pepp on 2007-05-13
I recently installed Ubuntu KDE 3 days ago and since then still haven't got my sound to work. I haven't heard a single sound come from the system while in Ubuntu, going to System Settings > Sound System and testing sound still has no effect. I have checked other threads and online sources but they haven't been able to help me, also my sound worked perfectly in Windows XP.

I'm using an onboard sound card, my motherboard is a P4G8X.

I hope someone can help! :(

---

### Post by nightstalker76 on 2007-05-13
Hello 

did you check if you use the right driver? Wich Soundcard di you use ? 

And do you use a Dolby Surround system?

---

### Post by nightstalker76 on 2007-05-13
sorry i typed spme words wrong.My English iss not so well. I have to practise I know. I hope I'll be better in the future.

---

### Post by Pepp on 2007-05-13
I don't use Dolby surround sound, both my headphones / desktop speakers result in no sound. I don't know if I'm using the right driver either, in the hardware tab its on Autodetect, Ive gone through all the audio devices it lists and none have sound.

---

### Post by nightstalker76 on 2007-05-13
Did you install a Mixer ? And do you know which Soundcard xou use the I can look what iss to do that it work.

---

### Post by Pepp on 2007-05-13
I installed Alsamixer, but I get this error if I try and open it: "alsamixer: function snd_ctl_open failed for default: No such device"

I don't have a sound card, its built into the motherboard.

---

### Post by nightstalker76 on 2007-05-13
You use the onboard Sound that can cause trouble.
Please macke sure that the onboardsound iss enabelt.!

---

### Post by nightstalker76 on 2007-05-13
after this please type @ the Terminal -----> lspci | grep -i audio and then post what the command line gives out! 

take care

---

### Post by nightstalker76 on 2007-05-13
you can copy the command and paste into the Terminal . Sorry I've forgotten that

---

### Post by nightstalker76 on 2007-05-13
If you want you can contact me ICQ my Numerber iss 254889453

---

### Post by Pepp on 2007-05-14
Putting the lspci | grep -i audio command in terminal puts out no information.

---

### Post by Freezerburn on 2007-05-21
I'm having the exact same problem. I've tried to fix sound but to no avail. I'm using a laptop with onboard sound. aplay -l says I have a HDA Intel. I've tried alsamixer, kmix, qmix, gnome-volume-control, etc.

When I use gnome-volume-control, the terminal gives me a BadDevice error. Does this help?

I really like Kubuntu. I just wish getting sound was a lot easier.

---

### Post by apienk01 on 2007-05-21
Please post full output of the following command:

```
lspci
```

On your mobo it should contain a line saying something like:

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
```

---

### Post by Freezerburn on 2007-05-21
This is what I get when I run lspci.

```
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
```

If it's any help, the -v extension gives this result,

```
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
        Subsystem: LG Electronics, Inc. Unknown device 000e
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at b8000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

---

### Post by Freezerburn on 2007-05-21
Bumping for some help. I've scoured the internet but I (still) can't find the solution.

---

### Post by apienk01 on 2007-05-22
According to ALSA documentation, your soundcard is supported in Feisty.

Check the output of:
```
lsmod | grep snd
```
if it contains snd-hda-intel.
If it does, run kmix and un-mute and maximize all volume. Also uncheck 'external amplifier' setting if you have one.

If it doesn't help, edit the file /etc/modprobe.d/alsa-base and add this line at the end:
```
options snd-hda-intel model=ref
```
Save and reboot, or type:
```
sudo /etc/init.d/alsasound reload
```

If it still doesn't help you last option is to compile the newest alsa drivers. Use the instructions on [this]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#ALSA_driver_Compilation") page.

---

### Post by Freezerburn on 2007-07-17
Is there a chance that Kubuntu has detected my sound card incorrectly? I think I've tried every solution on these forums to no avail.

---

### Post by Freezerburn on 2007-07-18
Replying to myself because I'm so alone.

According to [this website]("http://www.ryanheise.com/LW60/"), I need snd-azx (my laptop is the LG LW60 Express and the lspci result is the exact same). 

Apparently, alsa has renamed the driver to snd-hda-intel, which is what I've been trying to install to no avail. Is there a way for me to try snd-azx instead?

---

### Post by ubanchaos on 2007-07-18
well im with  the guy .....u might need to go to the synaptic package manager and download the correct drivers

---

