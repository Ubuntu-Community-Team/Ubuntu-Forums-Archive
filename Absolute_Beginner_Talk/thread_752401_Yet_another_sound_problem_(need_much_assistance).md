---
title: "Yet another sound problem (need much assistance)"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by bharatpatel89 on 2008-04-11
So I've been searching the boards and guides for a few hours now, but honestly after trying a few things in them I've had little luck. Hopefully I can get some specalized assistance from some nice folks here ^_^. I'm basically getting no sound from my laptop's speakers or headphone jack or anything. I have a Toshiba Satellite P100-ST9772.I'm using the 1.10 Gutsy Gibbon release of Ubuntu.

aplay -l brings up the following
> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

sudo lshw -C multimedia brings up
>   *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
bharat@bharat-laptop:~$ 

alsamixer brings up the sound options and everything is turned up, same thing for the volume controls on the pannel
> &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: Conexant CX20549 (Venice)                                              &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master                                                                 &#9474;
&#9474;                                                                              &#9474;
&#9474;         &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;                        &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;         &#9500;&#9472;&#9472;&#9508;          &#9492;&#9472;&#9472;&#9496;          &#9484;&#9472;&#9472;&#9488;          &#9500;&#9472;&#9472;&#9508;          &#9500;&#9472;&#9472;&#9508;         &#9474;
&#9474;         &#9474;OO&#9474;                        &#9474;MM&#9474;          &#9474;OO&#9474;          &#9474;OO&#9474;         &#9474;
&#9474;         &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;         &#9474;
&#9474;       100<>100      100<>100                    100<>100      100<>100       &#9474;
&#9474;      < Master >       PCM          IEC958       Ext Mic       Int Mic        &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;



I've also tried doing what "Getting the ALSA drivers from a *fresh* kernel" in the Sound Troubleshooting guide said 

I'm sort of confused as to what to do, and how to get drivers and trying things on the Sound Troubleshooting guide is semi-difficut when I don't know what I'm really doing. I'm pretty much a total newbie to Linux this is my first attempt at trying it out. Anyway hopefully someone can help me out, thanks in advance for any assistance.

---

### Post by annda on 2008-04-11
if i can see right, alsamixer shows that your PCM output is turned up, but **muted!**

i really hope that you just missed it and that changing this setting will solve the problem.

---

### Post by bharatpatel89 on 2008-04-11
really? how do you unmute it?

---

### Post by annda on 2008-04-11
in alsamixer, use the --> key to go from Master to PCM and hit the M key. now you should see OO instead of MM for PCM and hopefully you will be able to hear sound.

---

### Post by bharatpatel89 on 2008-04-11
Its unable to unmute it, like pressing m changes nothing, though i was able to unmute the IEC958 next to it...though there seems to be no way to increase that sound. I added a screen shot of what I'm seeing

---

### Post by mgmiller on 2008-04-11
If you double click the speaker icon in the top panel, or right click it and select "Open Volume Control", you should see the slider for PCM.  At the bottom of that slider is the mute/unmute button.  It looks like a little speaker icon.  Click it to unmute it.  If the PCM slider is not visible, click  Edit > Preferences and then put a check next to the PCM entry.  It should appear in the volume control window.

If you don't have the speaker icon in the top panel, open a terminal and type:
```
gnome-volume-control
```
That should pop up the gui interface.

---

### Post by bharatpatel89 on 2008-04-11
Aright when I opened it up this is what I see, and thus far it looks unmuted to me....I toggled with it anyway but no luck. Any other ideas? Thanks so for the help btw.

---

### Post by annda on 2008-04-11
iit may be a reported [kernel bug]("http://bugzilla.kernel.org/show_bug.cgi?id=7228"). it seems that the IRQ of your sound card is hijacked by the power management system.

the easiest way to fix this is boot without ACPI support.

when you get to GRUB after starting the computer, select the boot option hit E and add the following in the line that starts with 'kernel':
acpi=off

then boot. if it works, add the option permanently:
[http://ubuntuforums.org/showpost.php?p=2772325&postcount=6](http://ubuntuforums.org/showpost.php?p=2772325&postcount=6)

also, it seems that a BIOS upgrade from Toshiba can solve your problem, too.

---

### Post by mgmiller on 2008-04-11
In that window, what do you get if you hit, File > Change device?

---

### Post by mgmiller on 2008-04-11
annda's comment seems more relevant to me.  I would follow his suggestions, especially the BIOS update part.  If that fixes it, then you don't need to disable ACPI.  I would think ACPI would be especially useful on a laptop.

---

### Post by bharatpatel89 on 2008-04-11
Cheers, I'll try updating the BIOS first, and then try disabling it, though could I ask what problems might happen if i disable it? I'm currently running a dual  boot of Ubuntu and Vista

---

### Post by annda on 2008-04-11
disabling ACPI the way i mentioned will have absolutely no effect on vista. 

to the best of my knowledge, when running Ubuntu your CPU fans will not react to CPU temperature and battery status will not be read. many users report fans working all the time, with moderate speed, so it can be relatively loud.

usually BIOS takes care of CPU overheating and switches the computer off when it gets too hot, but i wouldn't leave it on overnight before you make sure it doesm't overheat. other than that you are safe.

---

### Post by bharatpatel89 on 2008-04-11
no luck with both the update and disabling the support T_T, anymore ideas by chance?:(

---

