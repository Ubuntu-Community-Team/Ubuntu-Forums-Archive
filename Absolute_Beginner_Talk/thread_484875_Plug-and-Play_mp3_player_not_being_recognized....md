---
title: "Plug-and-Play mp3 player not being recognized..."
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-26
I had an XP install with a Gateway dmp-200 mp3 player. I never had to install drivers, and it was a simply drag and drop as a disk drive so I was hoping it would work here.

I am leaving for Costa Rica in about a day, and was really hoping to use this. My other threads have had no luck at all...so please help!

---

### Post by FleetAdmiral74 on 2007-06-26
What the heck...why are my topics being ignored? Is this the wrong forum or something? I swear, you guys have been GREAT answering my other threads, but these ones about my mp3 player have gotten little to no attention...

---

### Post by scxtt on 2007-06-26
plug it in and post the last 20 or so lines of **dmesg** (typed into a terminal window) ...

---

### Post by FleetAdmiral74 on 2007-06-26
```
[11482.748000] usb 2-4: new full speed USB device using ohci_hcd and address 4
[11482.952000] usb 2-4: configuration #1 chosen from 1 choice
[11482.952000] scsi5 : SCSI emulation for USB Mass Storage devices
[11482.952000] usb-storage: device found at 4
[11482.952000] usb-storage: waiting for device to settle before scanning
[11484.344000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[11484.344000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[11487.956000] usb-storage: device scan complete
[11488.140000] usb 2-4: reset full speed USB device using ohci_hcd and address 4
[11532.916000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[11532.916000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[11541.872000] usb 2-4: USB disconnect, address 4
[11545.232000] usb 2-4: new full speed USB device using ohci_hcd and address 5
[11545.436000] usb 2-4: configuration #1 chosen from 1 choice
[11545.440000] scsi6 : SCSI emulation for USB Mass Storage devices
[11545.440000] usb-storage: device found at 5
[11545.440000] usb-storage: waiting for device to settle before scanning
[11550.252000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[11550.252000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[11550.448000] usb-storage: device scan complete
[11550.628000] usb 2-4: reset full speed USB device using ohci_hcd and address 5
ed@database:~$ 

```

omg, thanks for responding!

---

### Post by lamalex on 2007-06-26
i think that player uses mtp to connect. type this in terminal: mtp-detect. you might need to apt-get the mtp libraries.

---

### Post by FleetAdmiral74 on 2007-06-26
:(

```
ed@database:~$ mtp-detect
No MTP devices.
No devices.

```

---

### Post by scxtt on 2007-06-26
hmm can't really tell what device address it's been assigned, what does **ls -l /dev | grep sd** show (when the player is plugged in)?

and the output of **sudo fdisk -l**

i'm hoping you can just mount it ...

---

### Post by FleetAdmiral74 on 2007-06-26
```
ed@database:~$ ls -l /dev | grep sd
crw-rw-rw- 1 root tty       2,  61 2007-06-26 00:26 ptysd
crw-rw-rw- 1 root tty       3,  61 2007-06-26 00:26 ttysd
ed@database:~$ 

```

I am hoping I can just mount it too!!! :)

edit: seems to be same when it is unplugged, but the player gets power and the usb port is good.

---

### Post by skymera on 2007-06-26
mine dosent mount eiother.
its an internal battery mp3.
im gonna follow this laters when my problem is sorted :)

sory for being off topic.

---

### Post by scxtt on 2007-06-26
hmm, that's not good ... i don't see any sd* devices listed ...

you would have something like:
```
:> ls -l /dev | grep sd
brw-rw---- 1 root  disk    8,   0 Jun 25 20:46 sda
brw-rw---- 1 root  disk    8,   1 Jun 25 20:46 sda1
brw-rw---- 1 root  disk    8,   2 Jun 25 20:46 sda2
brw-rw---- 1 root  disk    8,   3 Jun 25 20:46 sda3
brw-rw---- 1 root  disk    8,  16 Jun 25 20:46 sdb
brw-rw---- 1 root  disk    8,  17 Jun 25 20:46 sdb1
```
those are my 2 hard drives - when i plug in my mp3 player it shows up as sdc ...

---

### Post by FleetAdmiral74 on 2007-06-26
Well I plugged in my jumpdrive (which works fine), did the command and got 

```
ed@database:~$ ls -l /dev | grep sd
crw-rw-rw- 1 root tty       2,  61 2007-06-26 00:26 ptysd
brw-rw---- 1 root plugdev   8,   0 2007-06-26 11:24 sda
brw-rw---- 1 root plugdev   8,   1 2007-06-26 11:24 sda1
crw-rw-rw- 1 root tty       3,  61 2007-06-26 00:26 ttysd
ed@database:~$ 

```

It shows two sda things, could one of them be the mp3 player? or are both the drive...

I am not sure if this helps at all, its all I could think of.

---

### Post by lamalex on 2007-06-26
they are both the drive, sda is the whole drive sda1 is the partition volume.

---

### Post by FleetAdmiral74 on 2007-06-26
grr, that is not what I wanted to hear! :x

---

### Post by FleetAdmiral74 on 2007-06-26
Don't quit on me now people!

---

### Post by scxtt on 2007-06-26
when it's plugged in, what's the output of: **/usr/bin/lsusb**

---

### Post by FleetAdmiral74 on 2007-06-26
```
ed@database:~$ /usr/bin/lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 03f0:8604 Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0f19:0103 Oracom Co., Ltd 
Bus 001 Device 005: ID 045e:009f Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
ed@database:~$ 

```

HP is the printer, thats about all I recognize. The other usb item I have plugged in is my mouse. And the player, of course.

---

### Post by scxtt on 2007-06-26
i'm almost starting to think it's not gonna work ... you'd need a block device in /dev to be able to mount it, but it's not showing up when you plug in the device ... last idea i have is to plug it in, then reboot when it's plugged in and see if the device is created when the system is up ... i've not had a problem like this, so i've not troubleshooted it before ...

---

### Post by biggaloot on 2007-06-29
Having the same problem, as well as the problem of being a noob. The oracom is the mp3 player.

Hope this helps. I still can't figure out how to mount it with the info i have.

---

