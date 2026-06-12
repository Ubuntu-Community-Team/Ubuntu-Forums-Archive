---
title: "Digital Camera connects but ..."
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Samurai Penguin on 2008-03-22
the digital camera is recognized and shows in Device Manager after running the following:

tail -f /var/log/messages

then I connect the USB cable to the camera and the camera beeps twice
and  Terminal shows all this:

tomana@HAL:~$ tail -f /var/log/messages
Mar 22 21:53:48 HAL kernel: [  991.124000] usb 1-7: USB disconnect, address 4
Mar 22 21:53:48 HAL kernel: [  991.124000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/media/video/zr364xx.c: Zoran 364xx webcam unplugged
Mar 22 21:54:00 HAL kernel: [ 1003.556000] usb 1-7: new full speed USB device using ohci_hcd and address 5
Mar 22 21:54:00 HAL kernel: [ 1003.768000] usb 1-7: configuration #1 chosen from 1 choice
Mar 22 21:54:00 HAL kernel: [ 1003.768000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/media/video/zr364xx.c: Zoran 364xx compatible webcam plugged
Mar 22 21:54:00 HAL kernel: [ 1003.768000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/media/video/zr364xx.c: model 0d64:3108 detected
Mar 22 21:54:00 HAL kernel: [ 1003.768000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/media/video/zr364xx.c: 320x240 mode selected
Mar 22 21:54:00 HAL kernel: [ 1003.768000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/media/video/zr364xx.c: Zoran 364xx controlling video device 0
Mar 22 21:57:41 HAL kernel: [ 1224.388000] usb 1-7: USB disconnect, address 5
Mar 22 21:57:41 HAL kernel: [ 1224.388000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/media/video/zr364xx.c: Zoran 364xx webcam unplugged
Mar 22 21:57:55 HAL kernel: [ 1238.256000] usb 1-7: new full speed USB device using ohci_hcd and address 6
Mar 22 21:57:55 HAL kernel: [ 1238.468000] usb 1-7: configuration #1 chosen from 1 choice
Mar 22 21:57:55 HAL kernel: [ 1238.468000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/media/video/zr364xx.c: Zoran 364xx compatible webcam plugged
Mar 22 21:57:55 HAL kernel: [ 1238.468000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/media/video/zr364xx.c: model 0d64:3108 detected
Mar 22 21:57:55 HAL kernel: [ 1238.468000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/media/video/zr364xx.c: 320x240 mode selected
Mar 22 21:57:55 HAL kernel: [ 1238.468000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/media/video/zr364xx.c: Zoran 364xx controlling video device 0

Terminal will not accept any more code lines so I close Terminal and re-open it and run this code:

sudo mkdir /media/camera

and then

sudo mount /dev/sda1 /media/camera

then I go to Places > Home Folder > File System > Media > Camera

and instead of showing me the photos I see File System again and I click on Camera
and that folder is empty

not sure why it shows all the folders in File System twice ???


I opened Device Manager and the camera shows in the list of devices but where are the pictures from the camera put when the camera connects ?

---

### Post by Taino on 2008-03-23
> **Samurai Penguin said:**
> where are the pictures from the camera put when the camera connects ?

I have a Kodak camera, when i plug the camera in
XSane pops up a small window prompting to export
the photos, i save them to /home then view and
move them somewhere else.

maybe yours are in /home ? if not then /home/photos ? or /tmp ? worth a look. :)

---

### Post by Samurai Penguin on 2008-03-23
Hey, that's great that yours works, sure is nice when it just flows
on through and works. I tried gtKam but my Vivicam 3330 is not
in the supported list so I used the above code. I need to find out how to
retrieve the pictures from the camera. Thanks for your reply.

---

### Post by Taino on 2008-03-23
> **Samurai Penguin said:**
> I need to find out how to
retrieve the pictures from the camera.

Plug in your camera, then making sure its on,
go to a terminal window and put in this command.

```
lsusb
```

post back the output of that here.


:popcorn:

---

### Post by Samurai Penguin on 2008-03-23
ok, I can plug in the camera now without using terminal and it beeps twice and then
shows in Device Manager. Then I ran the code you gave me ...

tomana@HAL:~$ lsusb
Bus 002 Device 003: ID 0d64:3108 DXG Technology Corp. 
Bus 002 Device 002: ID 047d:1022 Kensington 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
tomana@HAL:~$

 the camera shows as DXG Technology Corp

---

### Post by Taino on 2008-03-23
Okays this is all experimental here :) so in the end it may or may not work, it just so happens you have a -Vivitar- Vivicam 3330 and thats a camera thats seems to have limited support (so far) in linux.

Camera's are either seen as (camera's or mass storage devices) one or the other.

The Vivicam 3330 model is seen as a (mass storage device) based on its internal chip.

Try and and mount it this way...

```

sudo mount -t vfat /dev/sda1 /mnt/camera

```

instead of this way

```

sudo mount /dev/sda1 /media/camera

```

Then if you have gthumb installed, launch gthumb and in its menu, goto file --> import photos. (it would put them in /home/<YourUsername> but thats if it mounts. :) no guarantee's!

There is some driver support for Vivitar's in gphoto & gphoto2, you said you tried gtKam look into gphoto as well.

[gphoto's site]("http://gphoto.org/")

Key thing is to mount the camera since this model's chip is seen as a storage device, if that can be done then there are a few different ways to pull the photo's out, it can even be done with a script. :)

But if it cant be mounted nothing can be done :( if it was recently purchased you could return it for a more linux friendly Vivitar model or other brand/model.

:popcorn:

---

### Post by Samurai Penguin on 2008-03-23
here's the result of running that command line:

tomana@HAL:~$ sudo mount -t vfat /dev/sda1 /mnt/camera
[sudo] password for tomana:
mount: mount point /mnt/camera does not exist
tomana@HAL:~$ sudo mount -t vfat /dev/sda1 /mnt/camera
mount: mount point /mnt/camera does not exist

gthumb didn't see the camera

Downloaded gphoto2 and it will not finish configuring without an error
being generated. Firt, it asked for a file so I used synaptic. Now it gives
this error:


checking popt.h usability... no
checking popt.h presence... no
checking for popt.h... no
configure: error:
* Cannot autodetect popt.h
*
* Set POPT_CFLAGS and POPT_LIBS correctly

---

