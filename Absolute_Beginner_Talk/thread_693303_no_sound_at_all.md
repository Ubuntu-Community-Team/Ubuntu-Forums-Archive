---
title: "no sound at all"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by marie-p on 2008-02-10
I just installed Ubuntu 7.10 on my hp pavilion dv2000 laptop and I have no sound at all. I tried with mp3 and with system sounds and my computer remains completely silent.

I here's what lspci gives me:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


I checked the restricted drivers manager and there was nothing there about the sound card. From the list above, it seems like the sound card is there... but why no sound? 

(yes, I did check to make sure the computer wasn't on mute)

---

### Post by peterff on 2008-02-10
Hi,

I believe you may have a similar sound card to mine, an Intel High Definition Audio. As I understand it, the kernel provides the support for this sound card with the module snd-hda-intel, and in Ubuntu 7.10's kernel that module doesn't work properly with this sound card. What worked for me was to install the package linux-backports-modules-generic, which contains updated modules which happen to work with my sound card.

---

### Post by marie-p on 2008-02-10
> **peterff said:**
> Hi,

I believe you may have a similar sound card to mine, an Intel High Definition Audio. As I understand it, the kernel provides the support for this sound card with the module snd-hda-intel, and in Ubuntu 7.10's kernel that module doesn't work properly with this sound card. What worked for me was to install the package linux-backports-modules-generic, which contains updated modules which happen to work with my sound card.

How do I install this package?

---

### Post by peterff on 2008-02-10
Are you familiar with apt-get and aptitude? They're systems for managing packages. They're two different programs used for the same set of tasks, but people say not to use both on the same system--so, if you haven't used aptitude before, here's how to do it with apt-get, the system you've been using:
sudo apt-get update
sudo apt-get install linux-backports-modules-generic

If you've used aptitude before and would like to use it for this:
sudo aptitude update
sudo aptitude install linux-backports-modules-generic

I believe I had to restart afterwards before I had sound.

---

### Post by marie-p on 2008-02-11
I tried that and still no luck

But I think with all the things I tried, I might have messed things up. The computer now sees two sound cards :confused: 

Tonight I'll try to just re-install Ubuntu completely and then try what you said.

---

### Post by peterff on 2008-02-11
Argh. :( Sorry it didn't work. If you want to undo my instructions, just run sudo apt-get purge linux-backports-modules-generic (replace apt-get with aptitude if that's what you used to install it).

Regarding the two sound cards, have you tried selecting each one in the GNOME volume manager? You might also look at the different "items" you can control--e.g., I have Front, Master, and Surround, all of which control volume. Make sure they're all unmuted and turned up.

---

### Post by marie-p on 2008-02-11
> **peterff said:**
> Argh. :( Sorry it didn't work. If you want to undo my instructions, just run sudo apt-get purge linux-backports-modules-generic (replace apt-get with aptitude if that's what you used to install it).

Regarding the two sound cards, have you tried selecting each one in the GNOME volume manager? You might also look at the different "items" you can control--e.g., I have Front, Master, and Surround, all of which control volume. Make sure they're all unmuted and turned up.

What happened is earlier I tried another set of instructions to try to fix the problem, and I think by doing that I added an extra identical soundcard.

I had also tried yet another set of instructions, but halfway through, I realized it didn't really apply so I stopped. Maybe I messed things up.

Anyways, my installation is still fresh, I didn't customize anything or move my files over (that's another problem altogether) so I might as well just reinstall Ubuntu and try again from scratch, beginning with the instructions you gave me, since they seem to make sense. I'll see how it goes.

---

### Post by amvella on 2008-02-11
Hey there i had the same problem with my sound card. I have a HP dv9500t and i found a fix for this problem. Do these step by step.

Okay, so install these five, (e.g. using Synaptic Package Manager).

    po-debconf
    debhelper
    quilt
    alsa-base
    libc6-dev
 
  Then download the Alsa Driver 
   [Download]("http://alsa.cybermirror.org/driver/alsa-driver-1.0.15.tar.bz2")

Extract it to a folder in your home directory
 make yourself root with the sudo command

3) go to the folder with the "cd" command

4) Run these commands in this order:

    ./configure
    make
    make install

Note: Yes, this process can take like 3 minutes.

When its installed, add this line to/etc/modprobe.d/alsa-base [use command "gedit /etc/modprobe.d/alsa-base" under "su" priveleges]:


    options snd-hda-intel model=hp

If your sound isn't working at startup (e.g. you cannot hear the ubuntu login noise, then do this:

gedit /etc/modules

Add these lines to the bottom:
> 
snd-hwdep
snd-hda-intel

Restart your computer, and bam. It should be working.
[B]
If your sound doesnt work after you update your kernal here is a fix for it.[/b]

To solve this problem, run these commands in the a terminal under "sudo" privileges

> rm /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
ln -s /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko

Restart the computer and Hell yea its working for ever.. lemme know if it worked ...
Oh yea you have to do this every time you do a complete install of Ubuntu 7.10

Hope it works for you

---

### Post by marie-p on 2008-02-11
> **peterff said:**
> Are you familiar with apt-get and aptitude? They're systems for managing packages. They're two different programs used for the same set of tasks, but people say not to use both on the same system--so, if you haven't used aptitude before, here's how to do it with apt-get, the system you've been using:
sudo apt-get update
sudo apt-get install linux-backports-modules-generic

If you've used aptitude before and would like to use it for this:
sudo aptitude update
sudo aptitude install linux-backports-modules-generic

I believe I had to restart afterwards before I had sound.

I'm trying that but I can't connect to ca.archive.ubuntu.com :confused:

---

### Post by rkd on 2008-02-11
I checked and that archive site is having some sort of problem.

You could wait a while and try again, or you could switch to use a different archive site.  If you want to switch, go to the System menu, select Administration, then Software Sources.

In the window that opens, make sure you are on the "Ubuntu Software" tab. In the middle of the window, you should see a selection box labeled "Download from". Click on the arrows at the right end of the selection box, from the selections that pop up, select "Other...". 

I expect it will open a set of selections for Canada. If it doesn't scroll through the list until you find the ones for Canada. If the Canada list is not open, click on the triangle to the left of the name "Canada". Click on any of the names in the list except the one that has uwaterloo in its name (that's the one that name you gave converted to). Click Choose Server, then click Close, then click Reload and wait for it to refresh. When it has closed, retry what you were trying to do.

---

### Post by DoubleR on 2008-02-11
I just fixed my sound a few minutes ago by deselecting headphone jack sense in GNOME Alsa Mixer.  This is after going through several rounds of trouble shooting and purging and installing sound and ALSA.  Just saying to play around with your settings if you think the drivers are installed.

good luck

---

### Post by marie-p on 2008-02-12
I managed to download the updates and install them, but there's still no sound.

I also noticed that when I reboot the computer, it "mutes" itself. There's a light on my keyboard that is blue when the sound is on, and red when I press mute. That light turns red by itself when I reboot (until Ubuntu is almost finished loading)
Could something be set to mute somewhere in the system? If so... how do I fix it?

---

### Post by amvella on 2008-02-12
You can fix the automatic muting problem by doing the second part of my fix. Did u do that? It should work. because i just installed a fresh version of ubuntu 7.10 and did all the steps. And its working like a charm for me.Just make sure u did all the steps and yea make sure to do the last two steps too...

---

### Post by marie-p on 2008-02-12
> **amvella said:**
> You can fix the automatic muting problem by doing the second part of my fix. Did u do that? It should work. because i just installed a fresh version of ubuntu 7.10 and did all the steps. And its working like a charm for me.Just make sure u did all the steps and yea make sure to do the last two steps too...

Hmmm... I'll try that. 
Unfortunately I am very new to linux and I don't know how to run the commands. I usually just re-type what other people give me. Can someone translate these instructions for me? 

I guess the install is done with sudo apt-get install followed by the name of the program. Right?

:oops: yes, I'll go learn the codes some day :oops:

---

### Post by bump_ on 2008-02-12
Hi,

I have a dv6500t with a similar audio card. Try Method B on this site:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
and see if it helps. It works like a charm for me.

---

### Post by marie-p on 2008-02-12
> **bump_ said:**
> Hi,

I have a dv6500t with a similar audio card. Try Method B on this site:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
and see if it helps. It works like a charm for me.

when I get to the step:[COLOR="SandyBrown"]
./configure --with-cards=hda-intel[/COLOR]
it gives me the following error:
[COLOR="SandyBrown"]checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.[/COLOR]

What do I do? :confused:

---

### Post by stevescripts on 2008-02-12
You need to install build-essential.

From the terminal:

```

sudo aptitude install build-essential

```

Hope this helps a bit.

Steve

---

### Post by marie-p on 2008-02-12
> **stevescripts said:**
> You need to install build-essential.

From the terminal:

```

sudo aptitude install build-essential

```

Hope this helps a bit.

Steve

Ok, I was able to go through the instructions and at the end, it gave me a big warning saying that the mixer channels for the ALSA driver are muted by default.

How do I un-mute them?

---

### Post by stevescripts on 2008-02-12
I'm *reasonably* sure that it is somewhere in the settings, but dont
have an Ubuntu box here to look at ...

Again, from a terminal:
```

 alsamixer

```

Navigation is with the arrow keys.

Will check an Ubuntu box in the morning...

Meanwhile, I hope this might help (or somebody else chime in here)

Steve

---

### Post by marie-p on 2008-02-12
> **amvella said:**
> Hey there i had the same problem with my sound card. I have a HP dv9500t and i found a fix for this problem. Do these step by step.

Okay, so install these five, (e.g. using Synaptic Package Manager).

    po-debconf
    debhelper
    quilt
    alsa-base
    libc6-dev
 
  Then download the Alsa Driver 
   [Download]("http://alsa.cybermirror.org/driver/alsa-driver-1.0.15.tar.bz2")

Extract it to a folder in your home directory
 make yourself root with the sudo command

3) go to the folder with the "cd" command

4) Run these commands in this order:

    ./configure
    make
    make install

Note: Yes, this process can take like 3 minutes.

When its installed, add this line to/etc/modprobe.d/alsa-base [use command "gedit /etc/modprobe.d/alsa-base" under "su" priveleges]:


    options snd-hda-intel model=hp

If your sound isn't working at startup (e.g. you cannot hear the ubuntu login noise, then do this:

gedit /etc/modules

Add these lines to the bottom:


Restart your computer, and bam. It should be working.
[B]
If your sound doesnt work after you update your kernal here is a fix for it.[/b]

To solve this problem, run these commands in the a terminal under "sudo" privileges



Restart the computer and Hell yea its working for ever.. lemme know if it worked ...
Oh yea you have to do this every time you do a complete install of Ubuntu 7.10

Hope it works for you

Ok, I think I understand these instructions now, but when I try to add lines under su privilege, my password doesn't work. I have only used one password when setting up Ubuntu... why isn't it working?

---

### Post by marie-p on 2008-02-12
> **stevescripts said:**
> I'm *reasonably* sure that it is somewhere in the settings, but dont
have an Ubuntu box here to look at ...

Again, from a terminal:
```

 alsamixer

```

Navigation is with the arrow keys.

Will check an Ubuntu box in the morning...

Meanwhile, I hope this might help (or somebody else chime in here)

Steve

Ok, I found it but it doesn't seem to be on mute. 

Still no sound though. :(

---

### Post by stevescripts on 2008-02-13
Click on System>Preferences>Sound

Then check device - to see if the correct sound device settings are selected ?

Steve

---

### Post by marie-p on 2008-02-13
> **stevescripts said:**
> Click on System>Preferences>Sound

Then check device - to see if the correct sound device settings are selected ?

Steve

I don't have my computer with me right now, but if I remember correctly, those settings are set to "automatic"
Or maybe I'm thinking of the wrong section. I'll look at it when I get home from work.

---

### Post by marie-p on 2008-02-13
> **stevescripts said:**
> Click on System>Preferences>Sound

Then check device - to see if the correct sound device settings are selected ?

Steve

All the "Sound Playback" are set at "autodetect" (I tried them on ALSA too, still nothing)
"Sound Capture" is set on ALSA


I tried a few solutions already, all of which involved updating the ALSA driver, but when I look at the Synaptic Package Manager, alsa-base is still at version 1.0.14 :confused:

](*,)

---

### Post by spiderbatdad on 2008-02-13
can you post the result of ```
asoundconf list
```

---

### Post by marie-p on 2008-02-13
> **spiderbatdad said:**
> can you post the result of ```
asoundconf list
```

Names of available sound cards:
NVidia

---

### Post by spiderbatdad on 2008-02-13
not really what I was hoping to see. Was hoping for a series of numbers.

maybe ```
lsmod
``` then compare the soundcard shown there to 

/etc/modprobe.d/blacklist  just to make sure it isn't blacklisted. Sorry i couldn't be of more help. It seems like there are a number of guides posted by others with the same soundcard, who have gotten it working.   

Regards.

---

### Post by marie-p on 2008-02-13
Module                  Size  Used by
ipv6                  317192  10 
af_packet              28172  2 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
powernow_k8            16608  1 
cpufreq_userspace       6048  0 
cpufreq_powersave       3072  0 
cpufreq_conservative     9608  0 
cpufreq_ondemand       10896  1 
cpufreq_stats           8160  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
container               6400  0 
battery                12424  0 
sbs                    21520  0 
button                 10400  0 
ac                      7304  0 
video                  21140  0 
dock                   12264  0 
sbp2                   27144  0 
parport_pc             41896  0 
lp                     15048  0 
parport                44172  3 ppdev,parport_pc,lp
snd_hda_intel         375848  4 
snd_pcm_oss            47488  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                93832  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
snd_hwdep              12168  1 snd_hda_intel
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
joydev                 13440  0 
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62624  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27400  3 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bcm43xx               140392  0 
ide_cd                 35488  0 
uvcvideo               52228  0 
ieee80211softmac       34944  1 bcm43xx
cdrom                  41768  1 ide_cd
compat_ioctl32         11136  1 uvcvideo
usblp                  16896  0 
videodev               31360  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
ieee80211              38472  2 bcm43xx,ieee80211softmac
ieee80211_crypt         8192  1 ieee80211
i2c_nforce2             7808  0 
snd                    69544  16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci                  21004  0 
soundcore              10272  1 snd
pcspkr                  4608  0 
mmc_core               33416  1 sdhci
k8temp                  7680  0 
psmouse                45596  0 
serio_raw               9092  0 
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
i2c_core               30208  1 i2c_nforce2
evdev                  13056  6 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sg                     41384  0 
sd_mod                 32512  3 
amd74xx                17328  0 [permanent]
ide_core              141200  2 ide_cd,amd74xx
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
sata_nv                24068  2 
forcedeth              55048  0 
ehci_hcd               40076  0 
ata_generic             9988  0 
libata                138928  2 sata_nv,ata_generic
scsi_mod              172856  4 sbp2,sg,sd_mod,libata
ohci_hcd               25092  0 
usbcore               161584  5 uvcvideo,usblp,ehci_hcd,ohci_hcd
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor

-------------------------------------------------------------------

I can't seem to get to the blacklist though.

---

### Post by marie-p on 2008-02-13
Ok, I found the blacklist. The only part that seems to be about the sound card is:

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

---

### Post by spiderbatdad on 2008-02-13
what I dont see is a line like this: snd_ac97_codec        100644  1 snd_intel8x0


but you say none are blacklisted other than snd_intel8x0m

not sure what to suggest for you...you've made a lot of changes already. You said your installation is fairly clean. Personally, I would start over. You seem to have been half way through 3-4 different fixes and adjustments. A clean install and then updates may fix your problem. If not, you can start with the fix provided in a previous post that seems most likely to work for you.

---

### Post by marie-p on 2008-02-13
> **spiderbatdad said:**
> seems to be a lot of modules:
snd 69544 16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,sn d_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer, snd_seq_device

but you say none are blacklisted other than snd_intel8x0m

not sure what to suggest for you...you've made a lot of changes already. You said your installation is fairly clean. Personally, I would start over. You seem to have been half way through 3-4 different fixes and adjustments. A clean install and then updates may fix your problem. If not, you can start with the fix provided in a previous post that seems most likely to work for you.

Alright, I'll try re-installing again.

---

### Post by spiderbatdad on 2008-02-13
if you run ```
alsamixer
```

in a terminal, do you see a line like this at the top?  Intel 82801CA-ICH3

---

### Post by marie-p on 2008-02-13
> **spiderbatdad said:**
> if you run ```
alsamixer
```

in a terminal, do you see a line like this at the top?  Intel 82801CA-ICH3

No, I see:

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA NVidia                                                             &#9474;
&#9474; Chip: Conexant CX20549 (Venice)                                              &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master        


(that's after I re-installed Ubuntu)

---

### Post by spiderbatdad on 2008-02-13
I'm reading through the previous instructions others posted to see what looks reasonable

---

### Post by spiderbatdad on 2008-02-13
meanwhile make sure Master and PCM are both up in alsamixer. And you might as well go ahead and run ```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by spiderbatdad on 2008-02-13
Try this: ```
asoundconf set-default-card NVidia
```  then reboot.

---

### Post by littletinman on 2008-02-13
what does that do?

---

### Post by spiderbatdad on 2008-02-13
Probably not much.

The key seems to be in loading the proper Modules...possibly "linux-restricted-modules-386," or "linux-ubuntu-modules-2.6.22-1"  or even the "linux-image-2.6.22-14-386"

but I really don't know. I'm reading bug reports, and how others claim to have fixed the issue. The consensus seems to be in the linux modules. Unfortunately, folks tend to mix the titles up a little when listing the packages, so they end up being combinations of the above packages... those listed here actually appear in synaptic.

---

### Post by littletinman on 2008-02-13
So which modules do i want and what do i not need for ubuntu?

---

### Post by marie-p on 2008-02-13
Ok, after I reinstalled Ubuntu, I tried amvella's solution (on page 1 of this thread) but it didn't work.

I did those too, and still no luck

> **spiderbatdad said:**
> meanwhile make sure Master and PCM are both up in alsamixer. And you might as well go ahead and run ```
sudo apt-get update
sudo apt-get install build-essential
```

> **spiderbatdad said:**
> Try this: ```
asoundconf set-default-card NVidia
```  then reboot.

I'll keep trying other solutions.

---

### Post by littletinman on 2008-02-13
how long did it take you to re-install?

---

### Post by marie-p on 2008-02-13
> **littletinman said:**
> how long did it take you to re-install?

not long, 15-20 minutes at the most.

---

### Post by littletinman on 2008-02-13
are you running 64bit or 32?

---

### Post by marie-p on 2008-02-13
> **littletinman said:**
> are you running 64bit or 32?

64

---

### Post by littletinman on 2008-02-13
is it any better than 32? cause that's what i'm running. With dual core AMD 64x2

---

### Post by Chris555 on 2008-02-13
This has apparently been a long running problem with your nVidia chipset. I chased down forums from over a year ago about the chipset. Here might be some help for you
[http://forums.fedoraforum.org/showthread.php?p=868053](http://forums.fedoraforum.org/showthread.php?p=868053)
I see that someone with an HP dv9500t got his working. There is also a how to link by another person on that forum page. At least this may give some other people some ideas how to help you out, as I am also very new to linux.

---

### Post by littletinman on 2008-02-14
thanks, i'll check it out.

---

### Post by Linked713 on 2008-02-14
I am having a problem with the sound. Laptop with ubuntu 7.10
Installed realtek-linux-audiopack-4.07b for Intel 82801G (ICH7 Family).
Sound works fine with headphone but won't get out of the speakers.
It works fine on windows.
I installed alsa and updated it.. even unchecked "headphones" but no sound.
Did every of the things said on this thread.

Can you help?

thanks

---

### Post by littletinman on 2008-02-14
I have no sound anywhere. Can you explain in a VERY detailed way how you installed that realtek package?

---

### Post by marie-p on 2008-02-16
Well, I still don't have any sound on my computer. I tried all the instructions given here, re-installed Ubuntu 5-6 times already and no change. I don't know what to do anymore! :(

A few things I am wondering about...

I have tried to install more recent versions of alsa (1.0.16 or 1.0.15). I downloaded the driver, utils and lib files, extracted them, went to that folder and rand "./configure", "make" and "make install" The thing is, even after I reboot, if I go into the synaptic package manager, the alsa-utils (and all other alsa packages) are still at the 1.0.14 version. :confused:
I tried: removing the alsa-utils package and rebooting, but removing alsa-utils also removes ubuntu-desktop and ubuntu-minimal (among other things) so when I rebooted, I couldn't get back to Ubuntu and I had to reinstall
So then I tried to remove alsa-utils, install the new version and then re-install ubuntu-desktop and all the other packages that had been removed before rebooting. However, that just re-installed the old 1.0.14 package. 

Second mystery... the mute/unmute indicator on my computer.
On top of my keyboard, I have a light that is blue when the sound is on, and red when the computer is on mute. Since I installed Ubuntu, that light automatically turns red every time I reboot and turns blue again shortly after Ubuntu starts loading. It never did that with Windows. 
Also, when I removed alsa-utils and rebooted, the light stayed blue. So it seems that alsa might be somehow muting the computer. Alsa itself isn't on mute (I checked by clicking the icon on the desktop toolbar and by going to alsamixer in the terminal)

So I don't know if that information helps anyone guess what could be wrong here.

---

### Post by littletinman on 2008-02-16
I solved the problem on mine. I installed the 64 bit 7.10 and then installed the modules right away. updated, then rebooted and there's those awesome dolbys pumping away. Gotta love it.

---

### Post by rkd on 2008-02-16
The package manager keeps a record of what versions of packages it has installed. When you ask it to show you the version, it looks in its own records and tells you what it finds there. As far as I know, it does not have a way to look at the actual software in the system to determine what version of the software is there.

So when you install something not using the package manager, the version that the package manager tells you is not going to change.  So put that anomaly out of your mind -- it doesn't indicate something is going wrong or that your installation is not working. It might be that your installation isn't working, but looking at the package manager isn't going to tell you yes or no about that.

I think your observation that the mute indicator light is turning red when you boot Ubuntu probably does indicate that there is some software in Ubuntu that is muting your sound. I don't know much about the sound software, so I don't have any suggestions about how to fix it.

One thing I did notice a minute ago when playing around with alsamixer for the first time is that if I make the terminal window bigger, more controls appear than when the terminal window was its normal size. And even the bigger terminal window did not display them all. I had to use the right arrow to move off the end of the screen to get it to bring the hidden controls into view. It might be that the hidden ones are unimportant; I don't know enough to say. But I wanted to point that out in case when you run alsamixer, you might be missing an important control because it is off-screen.

How confident are you that when you tried to install alsa 1.0.15 or 1.0.16 that all the steps were completed without error? I saw in one post you said you don't know the linux commands very well. Could there have been error messages buried among all the stuff the installation puts out that you overlooked?

When you did the ./configure, make, make install steps, were you running them as your regular user or did you activate the root account, switch to root, and run them as root? I ran into problems helping someone else with an install from source, and the problems went away when we did it after logging in as root.

As you've read on those other accounts, people have been able to get the sound working on that computer. We should be able to get it working on yours, too. We just have to figure out what you are doing differently than they did when following the steps given in the instructions.

---

### Post by marie-p on 2008-02-16
ok, I'm trying again to install alsa-driver, alsa-utils and alsa-lib under root. Once again using the ./configure make and make install commands

the driver installed without anything that looked like an error message

then I tried the utils and it told me it couldn't find an updated version of lib
so I installed lib, which seemed to go without problems

now I'm trying to install utils again and it says 'this package requires a curses library'

What's a curse library and where can I find one?

---

### Post by rkd on 2008-02-16
If it is the curses library I'm familiar with, it is a set of software functions that make it easy to write a program produce a user interface on a terminal that is something like the graphical user interfaces we are used to today (though curses and the kind of interface it enables is *much* older). I'll bet the alsamixer program uses the curses library, or something similar to it.

There are a number of variants of curses. I used Synaptic to search for curses and it turned up a lot -- most probably things that require curses. There are some packages there named libcurses and related names, and some named libncurses and related names. Several of them are installed by default, but I guess your package didn't like any of those. Did it give any more hints that would help you tell which of the many curses variants it wants? Is there a file named readme or install or build or something similar that gives some directions about how to go about building the package? It might discuss the particular form of curses it wants in there. If you give me the link to the package you are trying to build when you get that, I'll be happy to look into it if you can't figure it out.

---

### Post by marie-p on 2008-02-16
This is what I found in the install file:

> 
If ./configure command complain that alsa-lib package isn't installed,
please, check if --prefix option is same for alsa-lib and alsa-utils
package. The configure script from alsa-utils package probably cannot find
header file asoundlib.h in $prefix/include/alsa directory (usually in
/usr/include/alsa directory).


and I don't really understand it

---

### Post by rkd on 2008-02-16
The excerpt you posted isn't completely clear to me. I have one guess what it might mean, but if I'm wrong, it could make things more confusing. 

How about telling me the URL(s) where you got the packages?  Then I'll go look at all of the directions and see whether I can figure out for sure what that means.

---

### Post by marie-p on 2008-02-16
> **rkd said:**
> The excerpt you posted isn't completely clear to me. I have one guess what it might mean, but if I'm wrong, it could make things more confusing. 

How about telling me the URL(s) where you got the packages?  Then I'll go look at all of the directions and see whether I can figure out for sure what that means.

I got it from there:
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

---

### Post by rkd on 2008-02-16
The --prefix option is something that is only to be used when you are building for a different operating system.  For example, if you were running kernel 2.6.20 but wanted to build alsa to use on kernel 2.6.15, you would put a copy of kernel 2.6.15 in some out-of-the-way place, perhaps something like /oldkernel, then use the --prefix option on ./configure to point to the place where the kernel is that you want to build for.

Of course, you aren't doing that, so you, correctly, are not using the --prefix option.

What that message really means is that ./configure wasn't able to find some files in the place it was looking for them. The part about --prefix doesn't apply to your situation, so focus on the other part.  It says it probably couldn't find the file asoundlib.h, and that it should be in /usr/lib/alsa.

So go look in /usr/lib and see whether there is a directory named alsa in there. If there is, look in /usr/lib/alsa to see whether there is a file named asoundlib.h in there.

If you can find asoundlib.h, then we need to figure out why ./configure couldn't find it.  If you can't find asoundlib.h, then we need to figure out why building alsa-lib did not put asoundlib.h there.

If asoundlib.h is not there and you can't figure out why quickly, let's do this to try to figure it out: Build alsa-lib, copy all of the output from the terminal window, put it into a text file, and attach that file to a post. (I suggest attach rather than pasting into the post just because I think it probably will be very long.)

If asoundlib.h is there and you can't figure out quickly why the build of alsa-utils can't find it, run the build of alsa-utils, copy all of the output from the terminal window, and either post it here or put it in a text file and attach that file to a post.  Use the attachment approach if the output is too many lines to be reasonable to put in the post.

It probably is a good idea to continue to do the builds as root.

---

### Post by marie-p on 2008-02-16
I couldn't find the alsa folder, but I found the "asoundlib.h" file in the following folder:

/home/marie/alsa-lib-1.0.16/include

a thought occurs... did I download and install all this in the wrong folder?

---

### Post by rkd on 2008-02-16
No, I don't believe you downloaded to the wrong folder.

Generally, you can do the build in any folder you like. The make install part moves the results to the proper standard places.

The location you found looks like the build directory. It should have been copied from there to /usr/lib/alsa. Maybe when you were not using root for the build, it couldn't create the /usr/lib/alsa directory, so it couldn't copy things into it. I'd expect you would have gotten an error message about that, though.

Try finding all the directories and files under /home/marie that have alsa in their names and wipe them out. Download the starting files again and do all the builds fresh while logged in as root. Copy all the output from the builds into text files and save it in case we want to check it later. See how far that gets you.

The reason I suggest deleting everything with alsa in its name is that maybe when redoing the builds as root, there were things left over from earlier builds that made it not do the build completely. The only way to be sure nothing is left over is to do a fresh install of Ubuntu, but I don't want to suggest that you do that again unless we can't think of anything else.

---

### Post by marie-p on 2008-02-16
All I have in the home/marie folder are the compressed files I downloaded and the folders in which they were decompressed. Should there be anything else? 

I tried deleting the folders but it tells me I don't have permission. I know how to log in as root using the su command in terminal, but how do I log in so I can delete these folders?

---

### Post by rkd on 2008-02-16
I didn't know what it might have created, so I wasn't being specific. The files and directories you see are all I would usually expect to see in your home directory when building those three packages. But since the "make install" command didn't put the files in the usual place, I didn't know where else it might have put them.

Once you are logged in as root, you should have permissions to do anything, so to get rid of those directories, get logged in as root, enter```
cd /home/marie
```
and you should be in your regular home directory and can delete the directories with commands something like```
rm -r alsa-driver-1.0.16
rm -r alsa-lib-1.0.16
rm -r alsa-utils-1.0.16
```
Then, still as root, unpack the compressed files again. Then use cd to move into the alsa-driver directory and run the commands to build the driver. Copy the output from the build and put it into a text file that we can look at later, if we need to. Then get into the alsa-lib directory and do its build and save its output, then do the alsa-utils build.

It probably would be a good idea to put the text files holding the build output into your home directory, not within the alsa-driver, alsa-lib, etc. directories. Also, it would be good to use a chmod command to make sure your ordinary login can read them:```
chmod  a+r  build1.txt
chmod  a+r  build2.txt
chmod  a+r  build3.txt
```You don't have to name the files build1.txt, build2.txt. build3.txt -- name them whatever you like. That particular chmod command will ensure that anyone can read the file. 

If you notice any errors that you don't understand, attach the copy of the build output to your post and I'll see whether I can interpret it.

---

### Post by marie-p on 2008-02-16
Ok, I tried again and the result is the same. The driver and lib seem to install properly but the utils says it needs a curses library. 

I saved the text from the terminal but I think I made a mistake with the driver one and only saved the end of it. And the one for lib I had to cut in two to be able to upload it here. 

I have also noticed that the alsamixer still says version 1.0.14

---

### Post by rkd on 2008-02-16
Yes, it appears the driver and lib builds worked okay.

I noticed that in my earlier message I told you to look in the wrong place for asoundlib.h -- it should be in /usr/include/alsa (not /usr/lib/alsa). I apologize for the mixup. The output from the lib build seems to show it putting files in /usr/include/alsa, so I imagine that part worked okay this time.

So the problem now is that it couldn't find a curses library.  Did you try to install one of the curses libraries from the package manager after we discussed it a little while ago? If so, which one did you install? 

After looking through the list again, I think the package named libncursesw5-dev is the right one to use, especially if the package libncursesw5 is already installed on your system, as it is on mine.  If your system does not have libncursesw5 already installed, libncursesw5-dev might not be the correct one for you to use.  Tell me which curses packages are already installed on your system if you are unsure which to install.

To find what was already installed, I used Synaptic, clicked the Search button, put in curses, then looked through the packages listed. Only the ones with the green mark in the box at the left of their line are installed.

alsamixer is built by the utils build, so it hasn't been rebuilt yet. I imagine that is why it still shows the old version. Check again after we get utils to build correctly.

---

### Post by marie-p on 2008-02-16
> **rkd said:**
> Yes, it appears the driver and lib builds worked okay.

I noticed that in my earlier message I told you to look in the wrong place for asoundlib.h -- it should be in /usr/include/alsa (not /usr/lib/alsa). I apologize for the mixup. The output from the lib build seems to show it putting files in /usr/include/alsa, so I imagine that part worked okay this time.

So the problem now is that it couldn't find a curses library.  Did you try to install one of the curses libraries from the package manager after we discussed it a little while ago? If so, which one did you install? 

After looking through the list again, I think the package named libncursesw5-dev is the right one to use, especially if the package libncursesw5 is already installed on your system, as it is on mine.  If your system does not have libncursesw5 already installed, libncursesw5-dev might not be the correct one for you to use.  Tell me which curses packages are already installed on your system if you are unsure which to install.

To find what was already installed, I used Synaptic, clicked the Search button, put in curses, then looked through the packages listed. Only the ones with the green mark in the box at the left of their line are installed.

alsamixer is built by the utils build, so it hasn't been rebuilt yet. I imagine that is why it still shows the old version. Check again after we get utils to build correctly.

i tried with lincurses5-dev and it still didn't work (even after restarting)

right now I have: 
libncurses5
libncursesw5
libncursesw5-dev
ncurses-bases
ncurses-bin

Should I try libncurses5-dev?

---

### Post by rkd on 2008-02-16
If the utils build still is complaining about not having a curses library, then trying with more curses packages might help.

If the utils build is giving a different complaint, then we need to look at the new complaint and figure out what the problem is.

So look at the complaint and make sure it still is complaining about not finding a curses library.

Assuming that the complaint still is about not finding curses: Your post seems a little mixed up about which you tried and which you ask is worth trying (you probably were rushing to get it posted for me to see), but at least this time, that detail probably doesn't matter.  If there is a curses package with -dev at the end of its name that you don't have installed, go ahead and install it and see whether that makes the complaint about curses go away.  I don't know for sure, but I think the various curses packages will not conflict with each other, so I think it is safe to install as many as you like.

---

### Post by marie-p on 2008-02-16
Ok, I installed libncurses5-dev and it did the trick. I was able to install utils without a problem. The alsamixer now shows as version 1.0.16

Bad news is... there's still no sound. ](*,)

I'm not sure what to do now.

---

### Post by rkd on 2008-02-17
Okay, that is progress. If you haven't done this yet, make a note of all the packages you needed to install in order to get the utils build to work, so if you have to reinstall Ubuntu, you will know which packages to install before building alsa again.

I don't know whether it is necessary to restart the computer to make the changes go into effect. I think it might be possible to get the new modules to be activated without restarting, but I don't know what command is necessary to do it, so restarting the computer is sure to put the changes into effect. If you haven't tried that, please do.

If restarting doesn't bring the sound to life, we need to try some more things. I guess you are following the steps recommended in post #8.  Is that correct?  If so, did you go on to make the changes to /etc/modprobe.d/alsa-base and /etc/modules that are described in that post? If you didn't do them, try them. I think you should restart the computer after making those changes. 

If the sound still doesn't work after those changes, before doing the next recommendation (the rm and ln commands), I want to recommend that we first look at the files that are present, save the file that the rm would delete so we can put it back if that change does not fix the problem. So ask me for the details if we need to go on to that step.

If you were following steps of some other recommendation, tell me where to find the recommendation you are following and I'll look at it and suggest what you might do next.

---

### Post by marie-p on 2008-02-17
> **rkd said:**
> Okay, that is progress. If you haven't done this yet, make a note of all the packages you needed to install in order to get the utils build to work, so if you have to reinstall Ubuntu, you will know which packages to install before building alsa again.

I don't know whether it is necessary to restart the computer to make the changes go into effect. I think it might be possible to get the new modules to be activated without restarting, but I don't know what command is necessary to do it, so restarting the computer is sure to put the changes into effect. If you haven't tried that, please do.

If restarting doesn't bring the sound to life, we need to try some more things. I guess you are following the steps recommended in post #8.  Is that correct?  If so, did you go on to make the changes to /etc/modprobe.d/alsa-base and /etc/modules that are described in that post? If you didn't do them, try them. I think you should restart the computer after making those changes. 

If the sound still doesn't work after those changes, before doing the next recommendation (the rm and ln commands), I want to recommend that we first look at the files that are present, save the file that the rm would delete so we can put it back if that change does not fix the problem. So ask me for the details if we need to go on to that step.

If you were following steps of some other recommendation, tell me where to find the recommendation you are following and I'll look at it and suggest what you might do next.

I did the rest of the steps in the instructions. I added the lines to the alsa-base and modules files and restarted.
Still no sound.

I copied the snd-hda-intel,ko file to the document folder and then deleted it through the terminal and typed in the following line. 
I restarted, no sound. 
Then I noticed that the snd-hda-intel.ko file was still in its original folder. :confused: So I did the rm line again and now it's really gone. I restarted the computer again, no sound. 

Is there anything else I can do?

---

### Post by rkd on 2008-02-17
I guess you don't know what an ln command does. lt is a link command. It makes a fake file entry that points to another file. 

Please logon as root and do the ln command again. I'm pretty sure there should be a file entry for snd-hda-intel.ko. Let's put it back so that things are set up as correctly as we can manage.

I think I want to read your system log file, to see whether there are any messages in there that shed light on the problem. 

First, make note of the time, then restart the computer. When it is back up and you are logged in, look at the system log. Maybe the easiest way to look at the system log is to open the file /var/log/syslog in an editor -- whatever editor you like. Go to the end of the file, then page back until you find the messages that note the start of the most recent boot. The timestamps in the log will help you home in on the corresponding area of the syslog quickly. The messages look something like this:```
Feb 13 21:43:31 rkd-desktop syslogd 1.4.1#20ubuntu4: restart.
Feb 13 21:43:31 rkd-desktop kernel: Inspecting /boot/System.map-2.6.20-16-generic
```When you have found the messages from the start of the most recent boot, copy from there to the end of the log and paste into another file, then attach that other file to a post. I'll look at it and see whether it gives me any clues.

---

### Post by marie-p on 2008-02-17
I re-did the ln line and it said "file already exists" or something like that. So I guess that means it worked the first time.

I restarted and copied the system log from the restart, as you suggested. Let me know if you find anything interesting in there. (I had to compress the file to avoid having to cut it in 4-5 pieces, hope that's alright)

(thanks for your patience so far!)

---

### Post by rkd on 2008-02-18
Let's check to see what the current state of those snd-hda-intel.ko entries is. Please enter these commands in a Terminal and post the output:
```
ls -ld  /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
ls -ld /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko 
```

I'm not sure there is anything important revealed in the system log. I'm just a beginner on Linux, so there could be something significant escaping me.

There are a few messages in the system log about recognizing and trying to activate some Bluetooth audio device. There are also some messages about recognizing alsa and oss (Open Sound System, I believe) devices, but I didn't see anything about attempts to activate them.

There are similar messages in the system log on my test system, and my sound worked out-of-the-box -- no fiddling required.  There are lots of differences between my system and yours, but one which might be relevant is that my system contains no Bluetooth features, while yours does.  At least according to HP's manuals, some of the dv2000 models include Bluetooth support.

Are you aware of using any Bluetooth devices with your computer?  In case you don't know Bluetooth, it is a short-range wireless connectivity method.  Bluetooth is not the same as WiFi for wireless network access.  There are wireless keyboards and mice that use Bluetooth for their connection.  I've seen advertisements for wireless cell phone headsets that use Bluetooth for the connection.  I suppose similar headsets are offered for computer audio.  

So are you using anything like that with this computer?  If you are not, it appears that on at least some models of the dv2000, the Bluetooth feature can be disabled in the BIOS.  If you want to try doing that, look on the System Configuration menu in the BIOS.  The HP manual says you get into the BIOS by pushing the F10 key during boot.

My guess is that it is not very likely that this Bluetooth stuff is the cause of your problem, but if your aren't using Bluetooth for anything, and since it seems pretty simple to disable it, I would turn it off to see whether that has any effect.

When looking at the dv2000 manual, I see that there are special keys on the keyboard for turning the sound on and off and controlling its volume.  I don't remember you mentioning whether you tried using those keys to bring the sound to life.  I know that those kind of special keys often aren't supported by Linux, but I think they are on some computers.  So if you haven't tried using those keys to get the sound working, do give it a shot.

I don't understand yet the relationship between alsa and oss (Advanced Linux Sound Architecture and Open Sound System are what the two acronyms stand for, I believe). On my Linux system, under System -> Preferences -> Sound there is a dialog that offers selection among several choices for sound playback in certain contexts and for the default sound mixer.  I have no idea whether adjusting any of those settings could fix your problem.  If you haven't tried fiddling with things there, it is something you could experiment with, but I don't know what to tell you to try.  If you do experiment there, first make note of the settings so you can return them to their current values if you don't have any success with changing them.

I will try to look for other approaches to getting the sound to work, or at least get a clue why it isn't working.  I notice that HP has a number of models with similar names. There is pavilion dv2000, pavilion dv2000t, and pavilion dv2000z, at least. I don't know how they differ, but in case it matters, is your model pavilion dv2000, as you mentioned in your first post, or does it have a letter added to the end?

Did you use the computer at all with Windows?  If so, did the sound work then?

---

### Post by thevjm on 2008-02-18
I'm on a dv6500t and I am having the same issue.

The sound is muted by default.

When I type "alsamixer" in the terminal I get:

function snd_ctl_open failed for default: No such device

I am very new to Linux and don't know what to do.

Any sense of direction is appreciated.

---

### Post by thevjm on 2008-02-18
fixed mine with this:

sudo apt-get install linux-backports-modules

[this](http://aldeby.org/blog/?page_id=87) guide helped me out.

---

### Post by xeth_delta on 2008-02-18
To the OP. If you hve already compiled and successfully installed the drivers, you can try loading the module and reading what the output from dmesg is. It can tell you if there are any errors.
For example, for the snd-hda-intel module:
```
sudo modprobe snd-hda-intel
```
```
dmesg
```
The last lines should refer to the last operations, i.e. loading the drivers.

---

### Post by rkd on 2008-02-18
Be careful with that guide pointed to in post #74.

I imagine most of the advice there is good, and the suggestions about getting the sound to work seem worth trying, but I have to raise a warning about one point.

It recommends using ENVY. I have seen numerous reports that, while ENVY seems to work nicely, it leaves unintentional time bombs in your system that cause problems, sometimes severe problems, when you next upgrade.  The programmer who did ENVY is not malicious; he just did not do things completely correctly, resulting in the package management database on the system getting damaged.

I understand this has been a source of controversy for some time, and I don't mean to inflame it further.  But I do want to point out that there seem to be drawbacks to using ENVY, and encourage you to research it before deciding to use it on your system.

I tried to find a way to contact the owner of that guide, but the comment mechanism on his site is not working, at least at the moment, and I could find no email address or other way to contact him.

---

### Post by marie-p on 2008-02-20
Ok, I haven't been able to work on this for a few days but I'll try again tonight. 

I might just re-install Ubuntu and start from the beginning. And/or I might try this: [http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147) 
I don't know if it's fundamentally different from what I tried before, but I don't have much to loose. I really don't want to have to go back to Windows Vista!

---

### Post by xeth_delta on 2008-02-20
I really think that the first step you should take is to find out what codec is your sound card using.
As I have already mentioned in a previous post, you can look it up from the output of dmesg. 
Try to load the module and then run dmesg. Information about the sound card should be available in the last lines.
With that information, you can look in the alsa source code directory for the file: alsa-kernel/Documentation/ALSA-Configuration.txt, where you will be able to see what configuration parameters you have to give to load the module properly. These parameters are normally placed in /etc/modprobe.d/alsa-base. Before doing anything to that file, please back it up.

---

### Post by marie-p on 2008-02-20
:grin::grin::grin:

I FIXED IT!!!! There's music coming out of my computer speakers!! 

:grin::grin::grin::grin:

I re-installed Ubuntu and tried the other fix I mentioned earlier and there was still nothing. I also read that some people with dual booth have problems with sound when going from Windows to Ubuntu and how they fix that. Now I don't have a dual booth, but since I had Vista on my computer before installing Ubuntu, I gave it a try.

I shut down the computer, unplugged it, removed the battery, put the battery back and turned the computer back on. And that worked!! Weeks of installing and uninstalling tons of stuff, about 8-10 reinstall of Ubuntu... and that's what fixed it. I can't believe it!

Ok, maybe it was that and the fact that I installed a more recent version of alsa first. Either way, I'm happy. That's one problem solved! 

Thanks everyone for your help and patience.

---

### Post by rkd on 2008-02-20
Congratulations!!

I'm sorry it took you so long to find the solution, but I'm glad to see that you kept at it until you won!

I hope any other problems you run into with Ubuntu are much, much easier to solve.

Good luck!

---

### Post by amvella on 2008-02-21
man am happy for you... cos i know it feels when there is no sound.. i mean everything is working fine.. but no sound???? dats not something that we can live with... well congrads...nd yea nice determination.. u didn quit :P most pple would have quit by this time..it took me 3 days 24 hours a day to find a fix for mine.. :P

---

