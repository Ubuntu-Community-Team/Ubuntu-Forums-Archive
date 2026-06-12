---
title: "Another HDA-Audio thread"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Liquidfire- on 2007-12-13
I've read numorous posts and tips, but I get the same problem each time.


First I don't have sound with the old Alsamixer, the update compiles etc.

But when I restart my Ubuntu I doesn't detect any soundcards anymore even when I add.

i'm using alsamixer 1.0.0.0.15 rc3

> 
options snd-hda-intel model=auto

Further information, I can see what soundcard I got using lspci

> 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
**00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)**
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
04:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)


 lsmod | grep snd
 Gives
> 
snd_pcm_oss            43008  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                80644  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35456  0 
snd_seq_midi            9728  0 
snd_rawmidi            26112  1 snd_seq_midi
snd_seq_midi_event      8704  2 snd_seq_oss,snd_seq_midi
snd_seq                54384  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24580  2 snd_pcm,snd_seq
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56708  9 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11272  1 snd_pcm


 cat /proc/asound/cards 
gives

> 
--- no soundcards ---



I've no idea what to do.

So if anyone has any idea, thanks :D


But when i

---

### Post by ^rooker on 2007-12-13
According to this thinkpad wiki:
[http://www.thinkwiki.org/wiki/Intel_82801H_HDA](http://www.thinkwiki.org/wiki/Intel_82801H_HDA)

The alsa driver for this card is called "AD1984" and is available from alsa v1.0.15 and kernel 2.6.23 on.

Which ubuntu version are you running - or: which kernel/alsa version? Are you sure it's 1.0.0.0.15 (because googling that number returns 0 results)?
If your versions are below that it will probably get quite ugly.

---

### Post by stchman on 2007-12-13
> **Liquidfire- said:**
> I've read numorous posts and tips, but I get the same problem each time.


First I don't have sound with the old Alsamixer, the update compiles etc.

But when I restart my Ubuntu I doesn't detect any soundcards anymore even when I add.

i'm using alsamixer 1.0.0.0.15 rc3



Further information, I can see what soundcard I got using lspci



 lsmod | grep snd
 Gives


 cat /proc/asound/cards 
gives




I've no idea what to do.

So if anyone has any idea, thanks :D


But when i

I have a script that will update the ALSA drivers and works with the ICH7 sound cards.  It should work with your card.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

Let me know if it helps.

---

### Post by Liquidfire- on 2007-12-13
> **stchman said:**
> I have a script that will update the ALSA drivers and works with the ICH7 sound cards.  It should work with your card.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

Let me know if it helps.

Still no luck, when I try to open Volume control it just simply states it cannot find any Soundcard
[[IMG]http://img509.imageshack.us/img509/328/screenshotkj3.th.png[/IMG]](http://img509.imageshack.us/my.php?image=screenshotkj3.png)
Makes me a sad little newbie =P:confused:

---

### Post by stchman on 2007-12-13
> **Liquidfire- said:**
> Still no luck, when I try to open Volume control it just simply states it cannot find any Soundcard
[[IMG]http://img509.imageshack.us/img509/328/screenshotkj3.th.png[/IMG]](http://img509.imageshack.us/my.php?image=screenshotkj3.png)
Makes me a sad little newbie =P:confused:

I had this problem a while back when I used to run Edgy.  If I remember right the gnome-volume-manager package was not installed anymore.  An update caused this to happen.  

Check to see if that package is installed.

```
sudo dpkg -l | grep gnome
```

If it is not then install it.

```
sudo apt-get -y install gnome-volume-manager
```

Let me know if this helps.

---

### Post by FuturePilot on 2007-12-13
Try this
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")
Enable the Gutsy Backports and then
```
sudo apt-get install linux-backports-modules-generic
```

---

### Post by Liquidfire- on 2007-12-13
> **stchman said:**
> I had this problem a while back when I used to run Edgy.  If I remember right the gnome-volume-manager package was not installed anymore.  An update caused this to happen.  

Check to see if that package is installed.

```
sudo dpkg -l | grep gnome
```

If it is not then install it.

```
sudo apt-get -y install gnome-volume-manager
```
Nope its running

Let me know if this helps.

> **FuturePilot said:**
> Try this
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")
Enable the Gutsy Backports and then
```
sudo apt-get install linux-backports-modules-generic
```


No succes

---

### Post by Liquidfire- on 2007-12-14
the problem is just that it doesn't see a source to manage(alsa/alsamixer). I need to know how to add a soundcard to the selection scheme, because before I update alsamixer sees the soundcard, but I have no sound. And now it just doesn't see a soundcard at all

---

### Post by Liquidfire- on 2007-12-15
Alright i reinstalled ubuntu 7.10 now it dedects my soundcard, and I can get sound through my headphones, but i'm scared if I will update it i will lose everything again :<

---

