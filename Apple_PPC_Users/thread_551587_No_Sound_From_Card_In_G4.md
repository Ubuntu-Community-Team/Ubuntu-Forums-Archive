---
title: "No Sound From Card In G4"
date: 2007-09-15
forum: Apple PPC Users
---

### Post by mac0s9user on 2007-09-15
My G4 (digital audio edition) has no sound from the built in motherboard sound. It works on the small speaker in the front but not on the audio out. This is on a Fedora 7 Linux Distro, however I had the same problem on ubuntu. The initial boot sound plays but then once it enters yaboot  it quits. Any Ideas would be great. That little speaker doesn't cut it for movies.:)

---

### Post by frog_pilot on 2007-09-16
I mentioned  similar problems on my G4 MDD. 
The Problem on my machine was the DRC-level in the alsamixer-app

I'm using the snd-powermac driver for sound ( /etc/modules ) and the alsa-app. for sound. If you do so start the alsamixer-app. in a maximized terminal:```
alsamixer
```the take a look to the rigt side of the controllers. There is one for "drc" and one for "DRC Rang". Make sure that the "DRC" is muted ( M ) or that the "DRC Rang" is on the maximum-level.

For me this is working. But the sound is not as loud as on OS X. I'm working on this problem, but did not yet find the right solution... :confused:

---

### Post by mac0s9user on 2007-09-16
Sadly this did not work. It doesnt even see my sound card. Although that little speaker inside is still working. Thanks for your help! I may have to abandon Linux until all the bugs get worked out.

---

### Post by frog_pilot on 2007-09-16
If your small speaker in the cage is working, your sound-card was successfully detected.

What means > It doesnt even see my sound card.?

What's happening when you type ```
alsamixer
``` in a terminal?

Show us the output of ```
lsmode
``` and ```
sudo modprobe snd-powermac
```

---

### Post by mac0s9user on 2007-09-17
I noticed that  get an error on boot that says HIDD Failed: Address is already in use. May be unrelated.
When I type Alsa mixer I get the program With the volume control and all of that. 

When I type ls mode I get

bash: lsmode: command not found

Anything to with fedora? I'll go back to ubuntu if so

sudo modprobe snd-powermac   yields   

sudo: modprobe: command not found



weird... Any Ideas? Mybe a fresh install?

---

### Post by frog_pilot on 2007-09-17
> **mac0s9user said:**
> Anything to with fedora? I'll go back to ubuntu if so
I think this is the point. I didn't read this before. my fault :oops:

that's why the commands may not work for you.

But didn't you see here > **mac0s9user said:**
> When I type Alsa mixer I get the program With the volume control and all of that.
a volume control labeled "DRC"? make sure that it is on highest level. on my g4 this was the problem. I also didn't hear anything with the internal soundcard until I fixed this.

---

### Post by mac0s9user on 2007-09-19
DRC level is maxed out in alsa mixer. Oh well, myabe I should go back to ubuntu. Thanks for your help.

---

### Post by stmiller on 2007-09-19
> **mac0s9user said:**
> I noticed that  get an error on boot that says HIDD Failed: Address is already in use. May be unrelated.
When I type Alsa mixer I get the program With the volume control and all of that. 

When I type ls mode I get

bash: lsmode: command not found

Anything to with fedora? I'll go back to ubuntu if so

sudo modprobe snd-powermac   yields   

sudo: modprobe: command not found



weird... Any Ideas? Mybe a fresh install?

Fedora is different, no sudo. ;)

So do:

```

lsmod

```
not lsmod**e**
and see if snd-powermac is listed as a loaded module (driver). "list modules"

If it is not, then type
```

su -
```
to become root
then
```

modprobe snd-powermac

```
or possibly
```

/usr/sbin/modprobe snd-powermac

```
if needed to get that to work.

Then if snd-powermac loads, you can type alsamixer in a terminal and turn up your volume levels.

---

### Post by mac0s9user on 2007-10-11
I did ls mod and got this in ubuntu now

Module                  Size  Used by
binfmt_misc            13896  1 
rfcomm                 45400  0 
l2cap                  26244  5 rfcomm
ppdev                  11268  0 
lp                     13612  0 
parport                44624  2 ppdev,lp
cpufreq_userspace       5588  0 
cpufreq_stats           6532  0 
cpufreq_powersave       2176  0 
cpufreq_ondemand        8128  0 
cpufreq_conservative     8448  0 
ipv6                  302796  8 
sbp2                   26440  0 
scsi_mod              175824  1 sbp2
apm_emu                 8140  1 
af_packet              25192  2 
snd_powermac           49916  3 
rt2570                202640  0 
snd_usb_audio          92364  0 
snd_usb_lib            19776  1 snd_usb_audio
snd_rawmidi            30144  1 snd_usb_lib
snd_seq_device          9740  1 snd_rawmidi
usbhid                 52132  0 
hci_usb                17748  2 
bluetooth              59044  7 rfcomm,l2cap,hci_usb
snd_hwdep              10980  1 snd_usb_audio
ide_floppy             22784  0 
snd_aoa_i2sbus         24516  0 
uninorth_agp           11144  1 
snd_pcm_oss            54048  0 
snd_mixer_oss          22144  1 snd_pcm_oss
agpgart                38204  1 uninorth_agp
snd_pcm                95556  5 snd_powermac,snd_usb_audio,snd_aoa_i2sbus,snd_pcm_oss
snd_timer              26980  2 snd_pcm
snd_page_alloc         11368  1 snd_pcm
evdev                  12736  7 
tsdev                   9120  0 
pmac_zilog             21060  0 
serial_core            24896  1 pmac_zilog
sungem                 35492  0 
sungem_phy             10720  1 sungem
snd                    69940  14 snd_powermac,snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11396  1 snd
snd_aoa_soundbus        7972  1 snd_aoa_i2sbus
ext3                  161544  1 
jbd                    69556  1 ext3
ohci1394               41840  0 
ieee1394              431440  2 sbp2,ohci1394
ehci_hcd               37288  0 
ohci_hcd               24228  0 
usbcore               151676  8 rt2570,snd_usb_audio,snd_usb_lib,usbhid,hci_usb,ehci_hcd,ohci_hcd
ide_cd                 36420  1 
cdrom                  47932  1 ide_cd
ide_disk               19296  3 
capability              5320  0 
commoncap               8064  1 capability


unmuted all of alsa mixer and it still doesnt help

---

### Post by frog_pilot on 2007-10-12
output of lsmod | grep snd:
```
snd_powermac           50944  2 
snd_aoa_i2sbus         25028  0 
snd_pcm_oss            54560  0 
snd_mixer_oss          21088  1 snd_pcm_oss
snd_pcm                98888  3 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
snd_page_alloc         11464  1 snd_pcm
snd_seq_dummy           4100  0 
snd_seq_oss            42300  0 
snd_seq_midi           10112  0 
snd_rawmidi            30432  1 snd_seq_midi
snd_seq_midi_event      8672  2 snd_seq_oss,snd_seq_midi
snd_seq                67112  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27464  2 snd_pcm,snd_seq
snd_seq_device          9484  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71896  14 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9416  1 snd
snd_aoa_soundbus        7940  1 snd_aoa_i2sbus

```

the difference I can see is here:
```
snd_usb_audio 92364 0
snd_usb_lib 19776 1 snd_usb_audio
snd_rawmidi 30144 1 snd_usb_lib
```

Do you use an usb sound card? Which modules are listed in /etc/modules?

Look here [PMG4DA]("http://www.apple-history.com/?page=gallery&model=g4da")
> The G4 (Digital Audio) was so-named because of a new Built-in Amplifier, designed to drive USB speakers, along with the conventional minijack line output. Maybe with these usb-modules you could run only usb-speakers and there is no signal on the normal sound card output.

Maybe unloading these usb-modules could solve the problem.

---

### Post by mac0s9user on 2007-10-12
I noticed USB was thrown in there a lot when I entered lsmod.While it does have the setup for a USB sound card I currently do not use and and really don't plan too. Im up for disabling the modules. How do I go about it?Also do you thing Gutsy will solve this problem and that I should just wait?

Thanks for all your help frog_pilot & stmiller. I do appreciate it.

---

### Post by frog_pilot on 2007-10-12
If you have usb-speakers you could test if they will work. But I really don't know at all, what this means > new Built-in Amplifier, designed to drive USB speakers.

First of all, check your /etc/modules. It should look like this:```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

snd-powermac
apm_emu
sbp2
therm_windtunnel
fuse
```
If there are any other entry's, comment them out and try again. If it's the same, you have to unload modules by hand.


To unload the dispensable modules you need first the output of```
lsmod | grep snd
```. As G4MDD and G4DA only differ in processor speed, my settings should also work for you. That's why you have to unload these modules, you don't find in my listing above.
```
sudo modprobe -r <module>
``` this will unload the module and any dependencies with no further relevance.

If you are not shure what to do, post again the output of lsmod | grep snd. Then I can assist you. To search this output in the whole lsmod-listing would take to much time... ;)

---

### Post by mac0s9user on 2007-10-12
lsmod | grep snd outputs the following

root@jeff-desktop:/home/jeff# lsmod | grep snd
snd_powermac           49916  1 
snd_usb_audio          92364  0 
snd_usb_lib            19776  1 snd_usb_audio
snd_rawmidi            30144  1 snd_usb_lib
snd_seq_device          9740  1 snd_rawmidi
snd_hwdep              10980  1 snd_usb_audio
snd_aoa_i2sbus         24516  0 
snd_pcm_oss            54048  0 
snd_mixer_oss          22144  1 snd_pcm_oss
snd_pcm                95556  4 snd_powermac,snd_usb_audio,snd_aoa_i2sbus,snd_pcm_oss
snd_timer              26980  1 snd_pcm
snd_page_alloc         11368  1 snd_pcm
snd                    69940  12 snd_powermac,snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11396  1 snd
snd_aoa_soundbus        7972  1 snd_aoa_i2sbus
usbcore               151676  8 snd_usb_audio,snd_usb_lib,rt2570,usbhid,hci_usb,ehci_hcd,ohci_hcd



If I tried to enter just /etc/modules I would get a permission denied message even though I am logged in as root

---

### Post by frog_pilot on 2007-10-13
to enter /etc/modules you need the sudo-command. e.g. ```
sudo gedit /etc/modules
```. It would be better to first have a look to your /etc/modules prior to start unloading any modules.

---

### Post by mac0s9user on 2007-10-13
Cool I will give it a shot. Yeah I dont use the USB speaker port and have no plans too. Thanks I'll let you know how it turns out!

---

### Post by Jason-X on 2007-10-14
> **frog_pilot said:**
> If you have usb-speakers you could test if they will work. But I really don't know at all, what this means .

First of all, check your /etc/modules. It should look like this:```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

snd-powermac
apm_emu
sbp2
therm_windtunnel
fuse
```
If there are any other entry's, comment them out and try again. If it's the same, you have to unload modules by hand.


To unload the dispensable modules you need first the output of```
lsmod | grep snd
```. As G4MDD and G4DA only differ in processor speed, my settings should also work for you. That's why you have to unload these modules, you don't find in my listing above.
```
sudo modprobe -r <module>
``` this will unload the module and any dependencies with no further relevance.

If you are not shure what to do, post again the output of lsmod | grep snd. Then I can assist you. To search this output in the whole lsmod-listing would take to much time... ;)

Thanks for this. My sound now works in Gutsy.:)

"snd-powermac" was missing from my module file

---

