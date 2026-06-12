---
title: "mount/unmount USB flash drive"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Elsa on 2007-12-06
Hello, I know there have been many threads about this issue. I tried some of the suggestions last night and sometime I could mount but after I dismounted and mounted the drive again, I received a "Cannot unmount volume" error message. I'll post the exact messages when I get back to this forum tomorrow/if somebody asks, but this is what I did:

I installed Xubuntu 7.10 about four weeks ago.

I mounted a 512 MB PNY Attache flash drive (USB 2.0) to my USB 1.1 port. (During installation I used that port for a mouse, but now I attached the mouse to the PS/2 port.)

Some of the suggestions I saw in the threads were to look up where my USB drive was attached after I mounted it, using
```
dmesg |tail
``` 
I found among the lines this line: sd : sda1, so I assume that the drive was at sda1. Then I wrote
```
sudo mount /dev/sda1 /media/usbstick 
```

I think I received several errors, which I didn't understand (I am a newbie and no computer programming experience at all .... I just want to use my USB flash drive). One of them said something about a dead device (I am assuming that's my flash drive), and another said about an I/O error.

But then I looked in the media folder and the USB drive's actual name actually showed up (UDISK), along with usbstick, but when I tried to open, it disappeared.

I might have done something wrong along the way. I'd appreciate any help/pointer to the right direction.

---

### Post by lespaul_rentals on 2007-12-06
Try running this:

```
sudo apt-get install gnome-volume-manager
```

Then:

```
gnome-volume-manager
```

This will install gnome-volume-manager, which is not included when you install a "variation" of Ubuntu, such as Xubuntu.  Sometimes this will fix the problem.  After you install it, plug your flash drive back in.

---

### Post by philinux on 2007-12-06
You could try installing usbmount or pmount from synaptic.

---

### Post by Elsa on 2007-12-07
Hi, thank you for the suggestions. I did try both of your suggestions. I wrote down what I did but I didn't bring the notes today. I managed to mount and unmount one USB flash drive (PNY Attache 1GB) but not the other one (PNY Attache 512 MB but it shows that it has 967 MB capacity). I am still confused why it seems there's a selectivity in mounting devices. With the first one I did see a line /dev/sda1 when I typed sudo fdisk -l but not with the other one.

Now the flash drive appeared on the desktop. When I tried to mount it, I still got "Unable to mount volume" message, but then the file manager appeared and I was able to use the drive as usual (copying, pasting, etc.) Unmounting was not a problem either. It seems though that I had to actually take the drive out after unmounting so the next time I tried to mount the drive I would not have a problem. 

Also I noticed that now I have usb directory and usb0 to, I think, usb8 in /media. Is this because I installed usbmount? Thank you.

---

