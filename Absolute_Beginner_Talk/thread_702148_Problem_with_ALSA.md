---
title: "Problem with ALSA"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Stunned_flounder on 2008-02-20
I've tried following a lot of the guides and instructions from other threads for configuring sound for Gutsy on my computer, but for some reason, youtube still won't play sound and I get a playback error when I try to make calls in Skype (the test sound button doesn't make any sound).  My media players work, but I assume that somehow flash isn't playing sound, and Skype is just a complete mess.

I also for some reason get the error: ```
alsamixer: function snd_ctl_open failed for default: No such device
```
 when I try to open alsamixer.  I also don't know what it means to run 'make install' as root when installing the alsa driver.

I'm just way too new to this.  Could anybody offer any advice/instructions about this?

My sound card is listed by lspci in terminal is:
```
01:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
```

It doesn't show up as my audio, though.  Do I need to do that?

---

### Post by spiderbatdad on 2008-02-20
This often works:```
asoundconf list
```

Returns a result. ```
asoundconf set-default-card result
```
Reboot.

---

### Post by Stunned_flounder on 2008-02-20
Still no sound on Skype and Youtube.

I've deactivated my motherboard's sound card, but I think the problem lies with not having ALSA fully configured.  For some reason, I can't get alsamixer to open.  When I type 'alsamixer' into the terminal I get this:

```
alsamixer: function snd_ctl_open failed for default: No such device
```

I've seen other people mentioning that error in other threads, but I can't ever find any responses for how to correct this problem.  For some reason, I also get errors trying to get ALSA configured on my computer.

---

### Post by spiderbatdad on 2008-02-20
have you tried installing linux-backports-generic?

are you missing alsa-base?

---

### Post by Stunned_flounder on 2008-02-20
I can't find linux-backports-generic in Synaptic Package Manager, but I do have alsa-base installed.

---

### Post by spiderbatdad on 2008-02-20
sorry linux-backports-modules-generic

---

### Post by spiderbatdad on 2008-02-20
we should have started with```
lspci
```You might want to take a look at this how-to...scroll to the appropriate section for your machine type.[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by Stunned_flounder on 2008-02-20
I've re-installed linux-backports-modules-generic, but still nothing.

lspci brings up

```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:02.0 Communication controller: 3Com Corp, Modem Division USR 56k Internal WinModem
01:03.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (rev 11)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

```

I looked at the guide, but I disabled my onboard sound card and am trying to get all of the sound duties to be carried by my Creative sound card.

---

### Post by Stunned_flounder on 2008-02-21
What's the code I should use to purge ALSA completely and then consequently, the way I should re-download it so that it works?

I know I could hear youtube when I first made the switch over to Gutsy from Windows XP, but didn't get skype yet so didn't know if it would've worked or not.  I'm just lost right now, could anyone offer any advice?

---

### Post by spiderbatdad on 2008-02-21
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

locate the section appropriate to your system.

---

### Post by Stunned_flounder on 2008-02-21
I'm following the instructions at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto), but one thing that confusing me is, they have asterisks in the commands that I need to use, like:

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2
```


What do these asterisks mean?

I also get this sort of interaction with the terminal:

```
john@Sexcopter:/usr/src/alsa$ cp /home/john/Desktop/download /usr/src/alsa
cp: omitting directory `/home/john/Desktop/download'
```

Am I using the wrong syntax?

---

### Post by Stunned_flounder on 2008-02-22
I put my computer together myself, so it's not listed under any of the machines in the list.  I have an Asus motherboard, but it isn't the one listed under asus.  I did, however try to follow the instructions further down in Method H.  This is where I ran into my question about the code.

---

