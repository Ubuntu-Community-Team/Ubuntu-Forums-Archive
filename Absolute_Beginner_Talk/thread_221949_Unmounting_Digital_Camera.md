---
title: "Unmounting Digital Camera"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Quicky on 2006-07-24
Or should that be dismounting?

Anyway, I have a Canon Ixus 500 digital camera which is detected perfectly well by Dapper and lets me transfer my pictures across no problem. However I have noticed in various places on the forums that it’s good practice to unmount drives after use. unfortunately no icon appears on the desktop when my camera is plugged in (as it does when my mobile phone is plugged in, or CD is in the drive), so I am unable to right-click on it and choose ‘unmount’. How can I therefore unmount the camera? Does it actually make any difference if I just turn it off or unplug it?

Thanks

---

### Post by Lord Illidan on 2006-07-24
How do you transfer images then? By using DigiKam?

If you know the location of the camera, like /dev/sda1, or whatever, just ```
sudo umount /dev/sda1
``` in a terminal.

If you don't know the location, enter ```
dmesg
``` in a terminal after you plug in the camera, and examine the last few lines of code for the location, which should be similar to /dev/sda followed by a number.

---

### Post by Quicky on 2006-07-24
Cheers, I’ll give that a go when I get home.

With regards to transferring pictures, when I plug the camera in, a message box pops up saying ‘A camera has been detected. Would you like to transfer images?’ or something similar, then I click OK and a screen appears showing thumbnails of everything on the camera, I can choose a location to download to, and it begins the transfer. Sorry, can’t remember what the name of the program is – the whole process is essentially automatic. I can tell you that it knows what camera I have – ‘Canon Ixus 500’ appears on the transfer screen.

Incidentally, should I have an icon on the desktop? It has never appeared, I’m just wondering if there’s an option I need to check somewhere to activate this?

---

### Post by Lord Illidan on 2006-07-24
The icon might not be an actual camera icon. WIth my camera, a Nikon Coolpix 7900, I get an image of a USB drive (1 gig) on the KDE desktop..
> **Quicky said:**
> Cheers, I’ll give that a go when I get home.

With regards to transferring pictures, when I plug the camera in, a message box pops up saying ‘A camera has been detected. Would you like to transfer images?’ or something similar, then I click OK and a screen appears showing thumbnails of everything on the camera, I can choose a location to download to, and it begins the transfer. Sorry, can’t remember what the name of the program is – the whole process is essentially automatic. I can tell you that it knows what camera I have – ‘Canon Ixus 500’ appears on the transfer screen.

Incidentally, should I have an icon on the desktop? It has never appeared, I’m just wondering if there’s an option I need to check somewhere to activate this?

---

### Post by Quicky on 2006-07-24
Yeah - I get icons for other hardware I plug in via USB (like my phone which has an SD card in it), but no icon appears on my desktop when the camera is plugged in. It’d be obvious if it did appear since I don’t have anything else on my desktop normally. It’s weird because the camera is obviously detected, and works fine, there’s just no icon, so I can’t unmount.

---

### Post by MrHorus on 2006-07-24
> **Lord Illidan said:**
> 
If you don't know the location, enter ```
dmesg
``` in a terminal after you plug in the camera, and examine the last few lines of code for the location, which should be similar to /dev/sda followed by a number.

Yes but if the unit has been plugged in for some time then there might be a lot of kernel messages, especially if you have some problem like dodgey ACPI support like I do.

The best way do find where it is mounted is by typing "mount" as this will show both the block device in the /dev dir AND the mount point and once you know the /dev block device, you can then unmount it.

---

### Post by Lord Illidan on 2006-07-24
> **MrHorus said:**
> Yes but if the unit has been plugged in for some time then there might be a lot of kernel messages, especially if you have some problem like dodgey ACPI support like I do.

The best way do find where it is mounted is by typing "mount" as this will show both the block device in the /dev dir AND the mount point and once you know the /dev block device, you can then unmount it.

Ah yes.. But if you type dmesg **immediately **after you plugin the camera, then it should be plainsailing. Typing mount itself is a good idea, didn't know about it, but it lists a lot of locations which can be confusing.

---

### Post by Quicky on 2006-07-24
Thanks for the advice guys, but I'm still struggling. I've just given the 'mount' command a go to see what happened. As far as I can tell, the output is identical in both instances.

By the way, the program that gets activated when the camera is plugged in seems to be called 'Import Photos' (at least that's what appears in the title bar). Also, I tried entering 'dmesg' but it produced a huge amount of output in the terminal, and I got scared and ran away.

'mount' before camera plugged in:

```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
```


'mount' after camera plugged in and switched on (Import Photos program activated):
```

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
```

If I understand 'mount' correctly (and please correct me if I'm wrong), this lists the mounted filesystems, so I can't understand why it would produce the same output in both instances. If Ubuntu imports the images without a problem, why doesn't the output from 'mount' change? And would this explain the fact that no icon appears on the desktop?

---

### Post by moma on 2006-07-24
Right-mouse clik on the panel and select "+Add to panel" from the menu.
Drag & drop "Disk Mounter" gadget onto the panel.

[o--> A picture... ]("http://home.online.no/~osmoma//tmp/disk-mounter.png")
It will help you to mount and unmount devices (disk-drives, USB-cameras etc)

// moma
   [http://www.futuredesktop.net/ubuntu6.06.html]("http://www.futuredesktop.net/ubuntu6.06.html")

---

### Post by Quicky on 2006-07-24
Cheers for that. I added the disk mounter gadget to the panel, plugged in the camera, turned it on and the gadget did nothing. I put in a CD and the gadget displayed a CD icon. Does this mean therefore, that the camera is not actually being mounted?

---

