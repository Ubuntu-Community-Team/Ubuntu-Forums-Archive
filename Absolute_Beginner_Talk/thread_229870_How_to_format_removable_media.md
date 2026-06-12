---
title: "How to format removable media?"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-08-05
I have an M-Audio microtrack and I need to format the compact flash card. In Wondows it's easy, you just Right-click "Removable Disk" and select "Format..."  But I cannot figure out how to do it with Ubuntu. There is an icon "usbdisk" on the desktop, but still I can't fit how to do it. Also, actually the compact flash card which is in it is fine, and that mentioned icon appears. But actually the card I want to format is another one. If I turn of my microtrack, swap cards and turn it back on, the icon doesn't appear at all! I find that strange. But anyway, I can't figure out how to format either cards anyway.
Thank you!
Justin

---

### Post by Jagot on 2006-08-05
You need GParted:

```
sudo aptitude update
sudo aptitude install gparted
```

You'll be able to format with that program.

---

### Post by woodlandjustin on 2006-08-05
Thanks. SO I just followed your instructions. But I am used to Windows. When I install a program, I get an icon on the desktop and on the applcations list. But I see no such thing now saying gparted. Where is it? How do I find where it is, so I can start it?
Thanks
Justin

---

### Post by Jagot on 2006-08-05
Go to System, Administration, then you should see in that menu gnome partition editor - thats what you want.

---

### Post by woodlandjustin on 2006-08-05
Okay, GParted is up and running. But although there is an icon for usbdisk on my desktop, there is nothing except the hard disk displayed by GParted. What do I do?
Thanks
Justin

---

### Post by Jagot on 2006-08-05
Up in the top right hand corner of the window there should be an icon for your hard disk label.  Click that whilst your compact flash card is in there and it should be on that menu - select it.

---

### Post by woodlandjustin on 2006-08-07
> **Jagot said:**
> Up in the top right hand corner of the window there should be an icon for your hard disk label.  Click that whilst your compact flash card is in there and it should be on that menu - select it.

There is an icon like you say, but there is no sign of my removable media. None at all. And clicking on that hard drive icon does nothing at all.l

Must I really install windows just to format this media?? Linux seems to be more and more laborious.
Justin

---

### Post by mcduck on 2006-08-07
> **woodlandjustin said:**
> There is an icon like you say, but there is no sign of my removable media. None at all. And clicking on that hard drive icon does nothing at all.l

Must I really install windows just to format this media?? Linux seems to be more and more laborious.
JustinEject the USB disk first. You can't edit filesystems on mounted devices :)

---

### Post by woodlandjustin on 2006-08-07
> **mcduck said:**
> Eject the USB disk first. You can't edit filesystems on mounted devices :)

I fail to see the logic in that. If gparted cannot see my compact flash card when it IS connected, how will it see it if it is ejected?? Anyway I tried all the same. But, that icon up there still only displays the HD.

Shouldn't it be rather simple how to reformat this card? 

Justin

---

### Post by woodlandjustin on 2006-08-08
Is anyone still out there? I would genuinely like to reformat this card. I can find no way to do it! Now even I did the automatix thing and that somehow gave me another tool too. It appears on the system menu simply as "disks". But it can't see it either. Actually, now the behavious of gparted is different. When I have the microtrack plugged in and on, then I start up gparted, it just waits and waits with that orange bar going back and forth at the bottom, saying "scanning all devices", and never stops! (unless I unplug the microtrack.)
Can anyone advise me?
Thank you
Justin

---

### Post by orb9220 on 2006-08-08
if the device shows up on the desktop it means it is mounted. Gpart cannot format a device if it is mounted. right click the icon on the desktop and select unmount then run gparted.

---

### Post by Kaidelong on 2006-08-08
Open a terminal window. Plug in your device.

dmesg | tail

you should see something there about the kernel finding your device and assigning it a device name (probably "/dev/sdx", where x is some letter.)

umount /dev/sdx

then, you can use the fdisk utility to edit the partition table, and one of the mkfs utilities to format a partition on it ("ls /sbin | grep mkfs" should show you your options.)

I don't know if this is discoverable enough, but as far as I can tell something like this should work? You will also be able to use gparted after the "umount" step.

---

### Post by wpshooter on 2006-08-08
Do you have all of the updates for Ubuntu downloaded and installed ?

---

### Post by woodlandjustin on 2006-08-08
> **Kaidelong said:**
> Open a terminal window. Plug in your device.

dmesg | tail

you should see something there about the kernel finding your device and assigning it a device name (probably "/dev/sdx", where x is some letter.)

umount /dev/sdx

then, you can use the fdisk utility to edit the partition table, and one of the mkfs utilities to format a partition on it ("ls /sbin | grep mkfs" should show you your options.)

I don't know if this is discoverable enough, but as far as I can tell something like this should work? You will also be able to use gparted after the "umount" step.


Okay, I had to reinstall because I wanted to dual boot with windows. Since then I did the automatix thing too. Anyway, now, no icon ever appears for "removable media" on my desktop. As if there is no recognitoin if my devise at all (except I know it must see something, as it has the ability to make gparted not work). 

Anyway I tried to follow you instruction. If I got you right I was meant to enter dmesg | tail into the terminal? This was the result:

justin-laptop:~$ dmesg | tail
[17190918.732000] end_request: I/O error, dev sda, sector 7
[17190918.732000]  unable to read partition table
[17190918.736000] sd 3:0:0:0: Attached scsi removable disk sda
[17190918.736000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[17190918.756000] usb-storage: device scan complete
[17190923.804000] usb 1-2: new full speed USB device using uhci_hcd and address 8
[17190926.916000] usb 1-2: device descriptor read/64, error -110
[17190942.132000] usb 1-2: device descriptor read/64, error -110
[17190942.348000] usb 1-2: new full speed USB device using uhci_hcd and address 9
[17190945.460000] usb 1-2: device descriptor read/64, error -110

---

### Post by woodlandjustin on 2006-08-08
> **wpshooter said:**
> Do you have all of the updates for Ubuntu downloaded and installed ?

Yes. Installed and restarted.

---

### Post by snaga on 2006-08-08
> **woodlandjustin said:**
> I fail to see the logic in that. If gparted cannot see my compact flash card when it IS connected, how will it see it if it is ejected?? Anyway I tried all the same. But, that icon up there still only displays the HD.
Justin

When it was suggested that you eject, that didn't mean to physically remove it. It meant to unmount the device. It is still attached to the system, but is not associated with a filesystem. Requiring that a device be unmounted during a format guards against any other users on the system trying to access the device at the wrong time.

---

### Post by Qrk on 2006-08-08
You can also use the command line. fdisk is a fairly easy tool to use. Just run

```
fdisk /dev/sda
```

Press "m" and you'll see a list of letters. Press "p" to find out what paritions you have, "d" to delete one and "n" to make a new one. "l" will show you what kind of partitions you can create.
 
make sure that it is /dev/sda first

You may want to continue trying to use gparted, but I also had trouble with it when I wanted to format an SD card.

---

### Post by woodlandjustin on 2006-08-08
Okay I did it again and it went differently. I think the first time (just now) the microtrack had gone into a different mode. Anyway, it went like this, and then you will see my attempts at following your instructions:

justin@justin-laptop:~$ dmesg | tail
[17191498.840000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17191498.844000] SCSI device sda: 4030465 512-byte hdwr sectors (2064 MB)
[17191498.848000] sda: Write Protect is off
[17191498.848000] sda: Mode Sense: 45 00 00 00
[17191498.848000] sda: assuming drive cache: write through
[17191498.856000] SCSI device sda: 4030465 512-byte hdwr sectors (2064 MB)
[17191498.860000] sda: Write Protect is off
[17191498.860000] sda: Mode Sense: 45 00 00 00
[17191498.860000] sda: assuming drive cache: write through
[17191498.860000]  sda:
justin@justin-laptop:~$
justin@justin-laptop:~$ unmount sda
bash: unmount: command not found
justin@justin-laptop:~$ unmount /dev/sda
bash: unmount: command not found
justin@justin-laptop:~$ unmount device sda
bash: unmount: command not found
justin@justin-laptop:~$

---

### Post by snaga on 2006-08-08
use umount, not unmount

---

### Post by Qrk on 2006-08-08
The command to unmount something is "umount" not "unmount"

```
umount /dev/sda
```

---

### Post by woodlandjustin on 2006-08-08
Okay, I tried that. It says:

justin@justin-laptop:~$ umount /dev/sda
umount: /dev/sda is not mounted (according to mtab)
justin@justin-laptop:~$

Now what?

---

### Post by wpshooter on 2006-08-08
Have you tried just right clicking on the icon when it is on the desktop and then unmounting the device and then attempting to format the media ?

It seems to me that I have followed this very same procedure on one of my USB keys, but I am at work right now (no Ubuntu here) and so I can not test it to make sure.  

If you haven't resolved, I will check back when I get home.  About 5 hours from now.

---

### Post by woodlandjustin on 2006-08-08
> **Qrk said:**
> You can also use the command line. fdisk is a fairly easy tool to use. Just run

```
fdisk /dev/sda
```

Press "m" and you'll see a list of letters. Press "p" to find out what paritions you have, "d" to delete one and "n" to make a new one. "l" will show you what kind of partitions you can create.
 
make sure that it is /dev/sda first

You may want to continue trying to use gparted, but I also had trouble with it when I wanted to format an SD card.


Okay so Itried that too. Here is the result:

justin@justin-laptop:~$ fdisk /dev/sda
m
p


The command line apparently did nothing. Anyway I went along and tried m and p like you said but nithing happened there either.

---

