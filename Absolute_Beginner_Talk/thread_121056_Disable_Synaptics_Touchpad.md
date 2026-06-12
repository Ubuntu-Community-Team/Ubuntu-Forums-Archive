---
title: "Disable Synaptics Touchpad"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by javierga on 2006-01-24
I'm trying to get this since my laptop (an averatech 5500) has a very sensinble touchpad that is very near the keyboard and whenever I try to type, it always minimizes the windows or focuses other porgrmas.
This is not an Ubuntu problem, since the same happened under windows and I've always used a USB mouse.
I've looked here:

[https://wiki.ubuntu.com/SynapticsTouchpadHowto?highlight=%28touchpad%29](https://wiki.ubuntu.com/SynapticsTouchpadHowto?highlight=%28touchpad%29)

but I can't find the answer to my problem

My lsmod:
```

magellan@estragon:~$ lsmod
Module                  Size  Used by
thermal                13576  0
fan                     4868  0
button                  6672  0
battery                 9732  0
ac                      4996  0
ehci_hcd               32520  0
ohci_hcd               21892  0
rt2500                173540  1
sis900                 22784  0
uinput                  9088  0
binfmt_misc            12296  1
powernow_k8            12680  0
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11136  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
ipv6                  265600  6
af_packet              22920  4
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   23940  0
scsi_mod              138856  2 sr_mod,sbp2
parport_pc             35780  0
lp                     11844  0
parport                36296  2 parport_pc,lp
pcmcia                 40508  0
i2c_sis96x              5764  0
snd_intel8x0           33436  1
snd_ac97_codec         92448  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
usbhid                 38624  0
psmouse                36100  0
pcspkr                  2180  0
serio_raw               7300  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
rtc                    13492  0
mii                     5888  1 sis900
yenta_socket           27916  2
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               21904  1 i2c_sis96x
ohci1394               35124  0
ieee1394              299576  2 sbp2,ohci1394
snd_pcm                89736  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
amd64_agp              12356  0
sis_agp                 8708  1
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
agpgart                34888  2 amd64_agp,sis_agp
evdev                   9856  0
ext3                  135688  4
jbd                    58772  1 ext3
usbcore               129668  4 ehci_hcd,ohci_hcd,usbhid
ide_generic             1536  0
ide_cd                 41348  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  6
sis5513                17032  1
generic                 5124  0
processor              23360  2 thermal,powernow_k8
capability              5000  0
commoncap               7296  1 capability
vga16fb                13448  1
cfbcopyarea             3968  1 vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               3200  1 vga16fb
cfbfillrect             4352  1 vga16fb
fbcon                  42784  74
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

I'm guessing it's something with the ps/2 mouse, but I'd like to confirm before messing my system up again.

Thanks,
Javier

PD. I'm using Dapper if it's any help

---

### Post by Razorback on 2006-01-24
I believe you can disable the touchpad in your bios.  My work laptop has a flaky touchpad and that is how I disabled mine.

---

### Post by javierga on 2006-01-25
O.K. Ill try it as soon as I'm back home.
I'll keep you posted

---

### Post by javierga on 2006-01-26
I tried disabling it from bios, but nothing, still doesn't work.  
Any more ideas are welcome...
Thanks.
Javier

---

### Post by nik on 2006-01-26
How about trying to make it work with the synaptics driver, and then setting options to make it less sensitive and/or disabling some features (like tapping)?

---

### Post by mikkelwe on 2006-02-06
To disable it in X, you can edit your xorg.conf and comment out the appriopiate sections. In the VT you can fiddle with gpm if you use it.

---

### Post by Eversmann on 2006-02-14
I do this:

En etc/X11/xorg.con on this place:

> Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "False"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Just change  Option          "SendCoreEvents"        "True" -----> "False"

On running, just ctrl+alt+backspace and restart gdm and changes will be done.

Just another solution ;-)

---

### Post by javierga on 2006-08-29
Yep, worked, thanks
Sorry for posting so late, but i've had a bit of problems lately with my hard drives (burnt 4 in 6 months!!!), so I've had to keep restoring and re'installing os, etc

---

### Post by kwalo on 2006-08-29
Yet another sollution: To disable the tap function in touchpad, edit synaptics section in /etc/X11/xorg.conf as follows:```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
[COLOR="Red"]        Option          "SendCoreEvents"        "true"[/COLOR]
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"

[COLOR="Red"]        Option          "SHMConfig"             "on"
        Option          "MaxTapTime"            "0"[/COLOR]
EndSection
```This will only disable tapping, but you can tweak other options. See synaptics(5) manpage for full list of options.

---

### Post by javierga on 2006-08-30
@Kwalo:
Thanks, I don't think I'll be using this much right now, but it seems like a good idea when for the run.  I've included it to my xorg.conf just in case my other mice stop working.
Thanks a mill!!!:D

---

### Post by jimmysz on 2006-08-31
Once again there was no need to start a new thread to fix my problem.
Awesome! Tapping was driving me crazy.

Thanks for the fix!:D

Now if only someone can provide me with an xorg.conf line option that will remove the dead pixel on my screen ;)

---

### Post by Frank Golden on 2006-08-31
> **jimmysz said:**
> Once again there was no need to start a new thread to fix my problem.
Awesome! Tapping was driving me crazy.

Thanks for the fix!:D

Now if only someone can provide me with an xorg.conf line option that will remove the dead pixel on my screen ;)
On my machine an Acer Aspire 5672 Fn+F7 toggles touchpad on and off regardless of OS.
Bet you have similar setup.
My old laptop a HP pavilion had a switch next to touchpad.

---

### Post by mssever on 2006-08-31
> **kwalo said:**
> This will only disable tapping, but you can tweak other options. See synaptics(5) manpage for full list of options.

Thanks for the pointer! I asked about configuring my touchpad some time ago and didn't get a response. This was just what the doctor ordered. Now my touchpad works almost the way I want. :D One more question, though, that I didn't find the answer for in synaptics(5): I want my left button to send middle button (is that button 2 or 3 in X?) clicks. This way I don't have to mess with emulating the middle button--and the there's no need for the left button to send button 1 when I can tap.

---

### Post by XaeroDegreaz on 2006-08-31
Hey, I tried to edit the xorg.conf but I cannot get it to save. How can I open and edit the file as root? I tried using "sudo /ect/X11/xorg.comf" and it says invalid command hehe, it was a good try though, no?

---

### Post by XaeroDegreaz on 2006-08-31
Nevermind, I fount out how. I was reading another post on the forum and found the gksudo command to run Nautilus as root :)

---

