---
title: "[SOLVED] Loss of all sound when upgrading to Ubuntu Studio"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by NAbreu on 2008-02-22
Hello.  I am new to Linux and Ubuntu, looking to use the audio synthesis programs in Ubuntu Studio.  I have a Dell M1330.   I was able to load Ubuntu 7.10 just fine and had audio.  When I upgraded to Ubuntu Studio 7.10 though, I lost all audio.  I do not have anything muted and I believe that Ubuntu has detected my sound card (see below). 

Help please!


lshw -C multimedia

WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel



I don't know if this will be helpful, but I'm including this as well:

lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by lespaul_rentals on 2008-02-22
Try running this:

```
sudo usermod -a -G audio <yourusername>
```

---

### Post by NAbreu on 2008-02-22
I was prompted to enter my password, but then nothing was displayed in the terminal after that and I still do not have audio.  Any other suggestions?

---

### Post by kpkeerthi on 2008-02-22
> **lespaul_rentals said:**
> Try running this:

```
sudo usermod -a -G audio <yourusername>
```
You need to logout and and log back in after running that command.
If you continue to hear NO sound, type **alsamixer** in a terminal and see if the channel volumes are OK and not muted (MM indicates muted, OO indicates unmuted. Use 'm' key to toggle mute/unmute)

---

### Post by kpkeerthi on 2008-02-22
More troubleshooting tips here...
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by NAbreu on 2008-02-22
Unfortunately I am still not hearing a peep.

After logging back in, I received this error message 

There was an error starting the GNOME Setting Daemon.  The last error message was:   Failed to connect to socket /tmp/dbus-KLUjXAui34: Connection refused 

and the desktop display was different.  Though, after I logged out and back in again the error message disappeared and the displayed returned to the regular Ubuntu Studio.


There was no problem with the ALSA mixer.

When I took a look at the ALSA driver list, INTEL HDA (ICH8 Family) was not listed.  Does this mean I don't have the right driver?  But when I look at Volume Control > File > Change Device, HDA Intel is listed as the Alsa mixer.

I am still quite confused.  Thank you for bearing with me.

---

### Post by kpkeerthi on 2008-02-22
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)
[http://ubuntuforums.org/showthread.php?t=588285](http://ubuntuforums.org/showthread.php?t=588285)

---

### Post by lespaul_rentals on 2008-02-22
> **NAbreu said:**
> I was prompted to enter my password, but then nothing was displayed in the terminal after that and I still do not have audio.  Any other suggestions?

When using **sudo** you will not see a password echoed in any way, shape or form as you type it.  Not even asterisks.  Just type it right as you know it and press Enter when done.  It will either carry on or say you entered it incorrectly.

---

### Post by NAbreu on 2008-02-22
Thank you very much for your help.  I just followed the instructions in the below thread, making sure to specify the module for the rt kernel (for Ubuntu Studio), and Voila!  beautiful beautiful sound.

[http://ubuntuforums.org/showthread.php?t=588285]("http://ubuntuforums.org/showthread.php?t=588285")

---

