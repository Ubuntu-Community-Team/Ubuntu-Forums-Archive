---
title: "Mp3 Player"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by majestix06 on 2006-07-08
Hello,

i have a problem with my mp3 Player on Ubuntu 6.
My Mp3 Player is a Medion Mobile Jukebox MD 96300.
The Player has 20 GB and it is connected with USB.
But if i connect to my PC and change into USB Mode, the Computer doesnt discern the Player. 
Here is a part of a Logfile:

Jul 8 12:01:08 localhost kernel: [17179839.232000] Vendor: MTC Model: MUSIC Jukebox Rev:
Jul 8 12:01:08 localhost kernel: [17179839.232000] Type: Direct-Access ANSI SCSI revision: 00
Jul 8 12:01:08 localhost kernel: [17179839.236000] SCSI device sda: 39063025 512-byte hdwr sectors (20000 MB)
Jul 8 12:01:08 localhost kernel: [17179839.240000] sda: Write Protect is off
Jul 8 12:01:08 localhost kernel: [17179839.240000] SCSI device sda: 39063025 512-byte hdwr sectors (20000 MB)
Jul 8 12:01:08 localhost kernel: [17179839.244000] sda: Write Protect is off
Jul 8 12:01:08 localhost kernel: [17179839.244000] sda: unknown partition table
Jul 8 12:01:08 localhost kernel: [17179839.256000] sd 28:0:0:0: Attached scsi removable disk sda
Jul 8 12:01:08 localhost kernel: [17179839.256000] sd 28:0:0:0: Attached scsi generic sg0 type 0
Jul 8 12:01:08 localhost kernel: [17179839.500000] usb 4-1: reset high speed USB device using ehci_hcd and address 92
Jul 8 12:01:09 localhost kernel: [17179840.004000] usb 4-1: reset high speed USB device using ehci_hcd and address 92 

Sincerely

---

### Post by majestix06 on 2006-07-08
Must i adjust something? If yes, wat?

---

### Post by JoshHendo on 2006-07-08
```

Jul 8 12:01:08 localhost kernel: [17179839.244000] sda: unknown partition table

```

I had this problem once, and I ended up having to format the player.

- Josh

---

### Post by majestix06 on 2006-07-08
With format u mean delete all datas?
And that isnt pointless?
Cause i have got a lot of datas on that.

Sicerely

---

### Post by majestix06 on 2006-07-08
so, wat shall i do now?

---

### Post by majestix06 on 2006-07-08
What is with my problem?
Why does nobody help me?

Sincerely

---

### Post by zih3r on 2006-07-08
Wich file format you use on your player?

---

### Post by raptros-v76 on 2006-07-08
did you look through synaptic for drivers? that may help.

---

### Post by ifokkema on 2006-07-08
Hi,

This message:
> **majestix06 said:**
> Jul 8 12:01:08 localhost kernel: [17179839.244000] sda: unknown partition table
Indicates the system does not recognize how the data is organized on the disk. What does this output:
```
sudo fdisk -l /dev/sda
```
when you have the player connected? This should show the partition table, but, in your situation, might give an error message.

As suggested, reformatting (and/or partitioning) may fix this issue, but will erase all data on your player. If you have a Windows installation running nearby that does recognize your player properly, you can put your data on that for backup, reformat (and/or repartition) the drive under Linux, then put your stuff back from Windows.

---

### Post by majestix06 on 2006-07-08
Fat32 is the format.


If i tipp that:sudo fdisk -l /dev/sda in the terminal, i am asked to give password and then nothing happens

---

### Post by majestix06 on 2006-07-08
Synaptic drivers

whats the name of them?

---

### Post by annda on 2006-07-08
looks like your player is set to act as a windows media device. can you change its settings? to usb drive? at least that's what it's called on my player (archos gmini).

otherwise it tries to communicate using the windows media protocol and does not report as a standard media storage device. see the player's settings and maybe check the manual.

does that help?

---

### Post by majestix06 on 2006-07-08
I dont know how to change the settings.

Sincerely

---

### Post by annda on 2006-07-08
read the manual. i looked at [www.medion.de](www.medion.de) (in german) and they have one online. it says there that in the main manu you can set your player to some sort of data manager mode. try if it works only for external devices (digital cameras and so on), or maybe it will turn your player into a regular external usb drive - this is what you need.

hope it works.

---

