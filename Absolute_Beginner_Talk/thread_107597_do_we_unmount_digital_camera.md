---
title: "do we unmount digital camera?"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2005-12-23
The camera is seen perfectly by gtkam and everything is fine.

I usually try to unmount the camera with sudo umount -a bc. I couldn't figure out where it is mounted. It usually unmounts some weird looking folder / device (tmp-something, always changes)...

Do we unmount the digital camera just like any other filesystem, or do we just unplug it after we are done?????? :confused:

[edit]
result: it seems you need to power off the camera first, than unplug it... see post #7. This is for cameras *not* recognized as storage devices. If yours is recognized as a storage device, you need to unmount it (not sure if power off = unmount in this context)
[/edit]

---

### Post by 5-HT on 2005-12-23
I don't have a digital camera myself, so someone else with direct experience may provide a much better suggestion...
(the following comes from my searching of how to deal with USB flash drives so YMWMLV)

Is is plugged in via USB?

If so, while it shouldn't be absolutely necessary * per se * to unmount it, I always prefer to err on the side of caution and unmount any removable media prior to unplugging.

The vital thing is to make sure you wait until there is no reading/writing occurring before unplugging (which if not done could potentially corrupt the file system and/or media).

If it's mounting in a weird location, would you mind posting the output of "mount" with the camera plugged in to try and track down exactly where it's being mounted?

As an alternative, I belive you could set up an entry for the camera (if it's recognized as a mass storage device...sorry not too familiar with digi cams) in /etc/fstab to then mount/umount.

HTH

---

### Post by bscbrit on 2005-12-23
When I connect my camera it creates its own icon on the desktop.  To umount it, I simply right click on the icon and select Unmount.  Check your desktop next time you attach your camera.

---

### Post by towsonu2003 on 2005-12-23
Camera is a Canon Powershot G6

[quote=bscbrit]
When I connect my camera it creates its own icon on the desktop. To umount it, I simply right click on the icon and select Unmount. Check your desktop next time you attach your camera.[/quote]no camera icon in desktop... 

o poop... so I have a small problem here I guess :)

Let me give some info on this and hope someone will help a little :)
After camera is plugged,
dmesg:```
[4295227.959000] usb 4-1: new full speed USB device using ohci_hcd and address 2
```
/var/log/messages (nothing in there)
fstab: no reference to camera's filesystem whatsoever
lsusb: ```
Bus 004 Device 002: ID 04a9:30b3 Canon, Inc. 
```

---I also discovered that if I do sudo umount -a && sudo mount -a, I will not be able to 'autoplug' the camera again unless I reboot... -----

[QUOTE=5-HT]
Is is plugged in via USB?[/quote]yes
[QUOTE=5-HT]
If it's mounting in a weird location, would you mind posting the output of "mount" with the camera plugged in to try and track down exactly where it's being mounted?[/quote]here it is (deleted stuff that I know what they are):
```

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-686/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
```
[QUOTE=5-HT]
As an alternative, I belive you could set up an entry for the camera (if it's recognized as a mass storage device...sorry not too familiar with digi cams) in /etc/fstab to then mount/umount.
[/QUOTE]I am not sure how that would interact with gtkam... I need to do research I guess (again, as usual :( ) 

In the meantime, any input is very welcome :)

---

### Post by bscbrit on 2005-12-23
this might help

[http://www.tldp.org/HOWTO/USB-Digital-Camera-HOWTO/index.html](http://www.tldp.org/HOWTO/USB-Digital-Camera-HOWTO/index.html)

---

### Post by towsonu2003 on 2005-12-23
[QUOTE=bscbrit]this might help

[http://www.tldp.org/HOWTO/USB-Digital-Camera-HOWTO/index.html](http://www.tldp.org/HOWTO/USB-Digital-Camera-HOWTO/index.html)[/QUOTE]
nope... fdisk shows no partitions to mount. I think ubuntu mounts it as usbfs (???) but have no idea what's going on here yet. Also, after opening up gtkam and closing, I think camera stays mounted although I read at other posts that it is supposed to be unmounted automatically when u're done with pictures?

I think camera isn't seen as a usb storage device.

Also, the camera turns itself off after a while and I unplug it, but mount output stays the same (so, it was not mounted at al??? or what?? very confused). lsusb shows the camera isn't there any more.

Edit: It seems that cameras that are not recognized as storage devices are recognized with gphoto2 (not installed here???) and gtkam (installed). How do we unmount gtkam stuff?

---

### Post by towsonu2003 on 2005-12-23
oh finally I found something! here: [http://www.linuxworld.com.au/index.php/id;298681864;fp;2;fpid;37](http://www.linuxworld.com.au/index.php/id;298681864;fp;2;fpid;37)

it says: > Downloading images from your camera

There are two ways to access and download images from a digital camera under Linux. Determining which method is best for your camera will depend on the model of camera that you have. Some cameras work with the first method, others with the second. The best way to work out which method suits your hardware is simply to indulge in a little trial and error. They're both free, after all.

gPhoto

gPhoto >[http://www.gphoto.org/](http://www.gphoto.org/) is a "one size fits all" solution to accessing photos stored on your digital camera, and includes native driver support for hundreds of cameras. A complete list is available at [http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php), and you'll find a copy of gPhoto on this month's cover disc. If your camera isn't listed in gPhoto, the chances are that it can be accessed using the USB Mass Storage method covered in the next section.

gPhoto includes a simple GUI interface, named gtkam. To access your camera, connect your digital camera to the USB port on your computer and switch the camera on. Once the camera is on, start gtkam by typing at a prompt:

$ gtkam

If supported, the camera will be auto-detected by gtkam and thumbnails of the images stored on it will be displayed. You can now copy these images to your computer. ** * _When you're done using gPhoto, remember to turn your camera off before disconnecting it from your computer ** * _. 

I'll contact the authors for documentation... -> [http://sourceforge.net/tracker/index.php?func=detail&aid=1389150&group_id=8874&atid=108874](http://sourceforge.net/tracker/index.php?func=detail&aid=1389150&group_id=8874&atid=108874)

---

### Post by nitricacid on 2005-12-23
If Linux is like mac (and it basicly is) then you need to Unmount everything.
You can pull it out without unmounting first but it might cause problems later on.

---

