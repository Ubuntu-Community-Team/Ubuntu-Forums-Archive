---
title: "MP3 Player, Flash Disk read/write issue"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-02-07
Cheers,

I just bought myself a 1GB mp3 Player.  At first I can place mp3 files in it, and I can even have amarok transfer files from my playlist into my mp3 player.

Now after doing some file transfers for a few hours all of a sudden I noticed that I can no longer add/delete files or folders to my mp3 player.  I have the same problem with one of my USB Flash Drive, I can't seem to add/delete files/folders to it as well.  But when I tried it with my WindowsXP machine at work, I can read/write to it.

Any ideas on how to solve this?

tia
Randy.

---

### Post by ^rooker on 2007-02-07
Please be more precise about what you mean by "can no longer add/delete files or folders to my mp3 player"?

Are they not showing up when you drop them there, or are they simply "gone" after you unplug the device again? 
(if latter is the case, you might have forgotten to unmount it properly - Try "Eject" in the right-click menu of the mp3-player-usb-item on your desktop)

---

### Post by delphiguy on 2007-02-07
Before I can Drag/Drop files to and from the mp3 player, and then all of a sudden I can no longer do that.

If I try to copy from konqueror I get this error :
Could not write to /media/usbdisk/queens.mp3

And I get the same thing in Terminal.

I also am having the same problem with my USB Flash Disk, and no it is not write protected but some how Kubuntu wont give write access to those devices.

I am using Kubuntu 6.10.

---

### Post by delphiguy on 2007-02-07
dont know if this will help but my mtab looks like this.

/dev/sdc /media/usbdisk vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

---

### Post by ^rooker on 2007-02-07
a few things come to my mind:

1) might sound stupid, but maybe the stick's full?
What is "df -h" saying?

2) what model is that mp3-player? (manufacturer, model-type)
I've seen strange things with USB sticks/MP3 players trying to do some "security stuff" designed for windows-only.

3) any info in "/var/log/messages" or in "dmesg" output?

---

### Post by delphiguy on 2007-02-07
Ok for the USB flash disk df -h says that it still has 228MB left
and for the mp3-player it says 792MB left.

So definitely theyre not full.  The thing is that when I tried to USB Flash disk at
my WindowsXP machine at the office it works.  I dont yet if the same is true for the mp3-player, as I dont have access to a WindowsXP machine at this moment.

The USB Flash disk's brand is TwinMOS 512MB, I dont know about the mp3-player but its a clone of iPodMini.  And when I do lsusb I get this.
Bus 003 Device 034: ID 08ec:0845 M-Systems Flash Disk Pioneers
Bus 003 Device 033: ID 10d6:1101 Actions Semiconductor Co., Ltd
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 09da:001a A4 Tech Co., Ltd Wireless Mouse & RXM-15 Receiver
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by delphiguy on 2007-02-07
I have tried to mount it as Root by doing
sudo mount -t vfat /dev/sdc /media/usbdisk and still no luck.

---

### Post by delphiguy on 2007-02-07
Ok I think I fixed this issue for me at least.
What i did is format both devices using gparted and it seems to be working fine now... 
Why the problem came up the first place is still a mystery to me.

---

