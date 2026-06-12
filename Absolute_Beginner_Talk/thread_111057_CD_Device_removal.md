---
title: "CD Device removal"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by seaan on 2006-01-01
Hello,
I installed Breezy on a Dell Latitude C610 and managed to get almost everything working, including my wireless card DLink DWL-G650.

My laptop allows to remove/insert devices (cd drive, floppy drive, battery) from/to the internal bay.
In MS Windows an icon in the tray allows to disable the device before removing it.
How can I safely remove a device in Ubuntu?
I just made a first try removing the CD drive and the system got stuck (had to forcefully switch off the laptop).
Is the same needed when removing USB memory stick?

Thanks in advance.
Sergio

---

### Post by Mustard on 2006-01-01
you would need to unmount them first, which would require you to use the **umount** command if you were to do it via the command line interface.

With regards to the gui method.  In your System>>Administration menu, there is a 'Disks' option, which allows you to mount and unmount devices.  You could use this to unmount the relevant devices.

Alternatively, if the devices are mounted on mount points defined in the /media directory, then they usually appear as icons on the desktop.  By right clicking on these icons, you will be presented with an 'unmount' option or 'eject' in the case of the CD drive.

If you want to learn how to do it via the command line interface you could read the manual in terminal by typeing man umount and man mount which will display manuals for the umount an mount commands respectively.

An example of unmounting a CD is 
```
umount /media/cdrom #this assumes that your CD is mounted on the directory /media/cdrom
```

---

### Post by iand675@gmail.com on 2006-01-01
or you could download a script and put an icon for it on your desktop.

---

### Post by seaan on 2006-01-01
Hi,
unfortunately unmounting is not enough.
I checked that the cdrom was not mounted and removed the device from the laptop to replace it with the second battery.
The system freezed and I had to switch off and reboot.
The log file is showing a long list of:
```
Jan  1 21:23:17 localhost kernel: [4308109.341000] hdc: status error: status=0x00 { }
Jan  1 21:23:17 localhost kernel: [4308109.341000] ide: failed opcode was: unknown
Jan  1 21:23:17 localhost kernel: [4308109.391000] hdc: ATAPI reset complete

```

Any clue?
Thanks

---

### Post by Mustard on 2006-01-01
I'm out of ideas. :)

I tried doing a search for similar problems in the forum, but didn't get any hits.

---

