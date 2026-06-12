---
title: "Powerbook 12'' runs hot"
date: 2007-04-22
forum: Apple PPC Users
---

### Post by dbuzi123 on 2007-04-22
Hey All,

I have a 12'' Powerbook which I installed Feisty on.  Everything works pretty well, airport working, sound, things are pretty good, but it runs really hot while doing simple tasks.  The CPU is constantly at 50C and the GPU at 60C.  It is much warmer than in OS X.  One thing I have noticed is the fans don't turn on until the cpu is at 50C, and even then they don't really power up.  If you reboot while it is hot into os x, os x kicks the fans on full blast for a while.  Is there anyway to make them turn on sooner?  Any other tips on making it run colder?  I already have cpu scaling going.

On another note, any tips for getting suspend to disk, or suspend to ram to work?

---

### Post by stmiller on 2007-04-22
I hate to break it to you, but if you have the 12" powerbook that has an nvidia gpu, sleep/suspend will not work. Blame Nvidia for not releasing specs. Sleep/suspend on ppc only withs with ATI hardware.

What is the output of lsmod? It should be running cooler than os x...

---

### Post by dbuzi123 on 2007-04-23
I've been looking at cpu temps in both OS X and Ubuntu, and they seem to be fairly similar, though a little higher in Ubuntu.  It is really the GPU temp that has me worried, it is about 10C higher in Ubuntu.  Perhaps it because of the extra load from not having very good video drivers.

Output of lsmod:

```
Module                  Size  Used by
arc4                    1952  2 
ecb                     4000  2 
blkcipher               7392  1 ecb
ieee80211_crypt_wep     5696  1 
ipv6                  307500  8 
binfmt_misc            13672  1 
ppdev                  11268  0 
lp                     13580  0 
parport                44304  2 ppdev,lp
cpufreq_powersave       2048  0 
cpufreq_stats           6436  0 
cpufreq_userspace       5332  1 
cpufreq_conservative     8096  0 
cpufreq_ondemand        9160  0 
therm_adt746x          13580  0 
sbp2                   25188  0 
scsi_mod              181324  1 sbp2
apm_emu                 8012  1 
snd_powermac           49984  0 
fuse                   52820  0 
snd_aoa_codec_tas      15456  2 
snd_aoa_fabric_layout    14088  1 
snd_aoa                20640  2 snd_aoa_codec_tas,snd_aoa_fabric_layout
snd_aoa_i2sbus         24292  1 
snd_pcm_oss            53984  0 
snd_mixer_oss          20960  1 snd_pcm_oss
snd_pcm                95812  3 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
snd_page_alloc         11368  1 snd_pcm
snd_seq_dummy           4004  0 
snd_seq_oss            40660  0 
joydev                 12032  0 
snd_seq_midi           10016  0 
snd_rawmidi            29632  1 snd_seq_midi
snd_seq_midi_event      8192  2 snd_seq_oss,snd_seq_midi
appletouch             10560  0 
snd_seq                61888  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26404  2 snd_pcm,snd_seq
snd_seq_device          9388  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69812  15 snd_powermac,snd_aoa_codec_tas,snd_aoa_fabric_layout,snd_aoa,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8996  1 snd
pmac_zilog             21140  0 
serial_core            24384  1 pmac_zilog
snd_aoa_soundbus        7812  2 snd_aoa_fabric_layout,snd_aoa_i2sbus
bcm43xx               141620  0 
ieee80211softmac       35008  1 bcm43xx
ieee80211              35653  2 bcm43xx,ieee80211softmac
ieee80211_crypt         6528  2 ieee80211_crypt_wep,ieee80211
uninorth_agp           12012  1 
agpgart                41308  1 uninorth_agp
af_packet              24936  8 
tsdev                   9056  0 
evdev                  12800  13 
ext3                  159048  1 
jbd                    68488  1 ext3
mbcache                 9572  1 ext3
usbhid                 28996  0 
hid                    43968  1 usbhid
ide_cd                 36900  0 
cdrom                  47580  1 ide_cd
ide_disk               18880  3 
ohci1394               43152  0 
ieee1394              430800  2 sbp2,ohci1394
sungem                 35460  0 
sungem_phy             12128  1 sungem
ehci_hcd               38476  0 
ohci_hcd               36100  0 
usbcore               158260  5 appletouch,usbhid,ehci_hcd,ohci_hcd
capability              5256  0 
commoncap               7968  1 capability

```

---

### Post by stmiller on 2007-04-23
Okay it is probably defaulting to a 'cpu performance' sort of designation. This could be sticky, but you can change those values and see if that makes a difference. 

And hibernation could be possibly (write session to disk). But I'm not sure.

---

### Post by dbuzi123 on 2007-04-23
Where do you change those values?

---

### Post by stmiller on 2007-04-23
Hm, after checking, I see that the cpu freq changes only change cpu speed, and not fan speed. So scratch that thought.

Check out this page:

[http://72.14.253.104/search?q=cache:SvLxrH4aUKwJ:www.alessandroronchi.net/wiki/LinuxOnIBookG4%3Fshow_comments%3D1+ibook+linux+change+fan+control&hl=en&ct=clnk&cd=3&gl=us](http://72.14.253.104/search?q=cache:SvLxrH4aUKwJ:www.alessandroronchi.net/wiki/LinuxOnIBookG4%3Fshow_comments%3D1+ibook+linux+change+fan+control&hl=en&ct=clnk&cd=3&gl=us)

This guy says you can load this module for fan control:

modprobe therm_adt746x

(add it to /etc/modules to autoload)

He says he uses fan speed=128

so try specifying
therm-adt746x fan_speed=128

in /etc/modules and rebooting.

I'll have to mess with this later. I'm using a G4 TiBook

---

### Post by neatokino on 2007-04-24
I just wanted to pipe in that I interested in this, too.  I just loaded 7.04 on my 12"powerbook, and even though I am a rank beginner, it seems to be working pretty well (got sound to work, haven made the wireless work y et, but I&#314;l try that later)... the computer does run hot, though, and I haven noticed the fan turning on at all.   Is there anyone who can help walk me through some of these ways to cool it down (and I mean really walk me through it, as I just starting here!)

TIA
Michael

btw, at first blush, it&#347; great to be running this OS on my old powerbook.  Setup has not been difficult so far!

---

### Post by stmiller on 2007-04-24
Okay, after some quick research, I can confirm that the therm-adt746x modules is the one to control fan for iBooks, and Aluminum Powerbooks. (So my TiBook does not use that driver.)

So search for info about that driver, perhaps. That will be the key to controlling the fan speed.

---

### Post by stream303 on 2008-06-08
I am searching for it now, but I vaguely remember something back in 2004 on a debian list about how the fan will eventually come on at very high load without the module, but may come on too early with the module installed as is, without any special temperature arguments.

I wonder if this is still an issue in either Gutsy or Hardy for those machines that need / want it.  Apparently this is not Ubuntu-specific, as neither Debian nor Gentoo include this module by default - afaik.

Anyone have this problem lately?

---

### Post by lesjohn on 2008-06-14
> **stream303 said:**
> I am searching for it now, but I vaguely remember something back in 2004 on a debian list about how the fan will eventually come on at very high load without the module, but may come on too early with the module installed as is, without any special temperature arguments.

I wonder if this is still an issue in either Gutsy or Hardy for those machines that need / want it.  Apparently this is not Ubuntu-specific, as neither Debian nor Gentoo include this module by default - afaik.

Anyone have this problem lately?

I'm running Hardy on an aluminum PowerBook.  It was running very hot but adding the module therm_adt746x seems to have fixed it up.  Thanks!  The fan runs a lot now; how do I adjust the temperature settings?

---

### Post by stream303 on 2008-06-15
That seems to be the most common result is that now the fan comes on too early, and some users say that the system can handle those hotter temps until it automatically kicks in.

There might be a manpage for that module to help out - not sure.

The link stmiller pointed to is interesting as far as that user using hdparm to get some performance out of the hd, and to also keep it cooler.  ymmv.

---

### Post by jtan on 2008-06-26
just a test of ubuntu.

---

### Post by stream303 on 2008-06-29
I think the temperature settings was a big point of contention.  The Mac will run hot, but will save itself automatically.  The thermal module will make it run cooler, but the fan activity and increased battery drain might be a problem for some.  The biggest issue seems to be that nobody wants the end-user setting the temperature wrong accidentally, and totally frying the box.

This is why I think that module was left out of most installations.

I recall some instructions about the temp settings in the Debian PPC mailing list archives - I forgot which month, but I think it was about a year or so ago...

---

