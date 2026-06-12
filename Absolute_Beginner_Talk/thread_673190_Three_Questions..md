---
title: "Three Questions."
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Ludford on 2008-01-20
I've recently installed Ubuntu with wubi and I have 3 questions...

1) aMsn and gaim don't make any sounds when I have XMMS playing music... can Ubuntu only play one sound at a time or something?

2) my Usb stick seems to be doubling up. I have an icon on my desktop for it regaurdless of weather it is in or not. it can't be deleted or unmounted. And when I DO plug it in I get another Icon for USB

3. My friend just tried installing and it's saying it can't find menu.lst when he first booted into it.

---

### Post by LaRoza on 2008-01-20
> **Ludford said:**
> I've recently installed Ubuntu with wubi and I have 3 questions...

1) aMsn and gaim don't make any sounds when I have XMMS playing music... can Ubuntu only play one sound at a time or something?

2) my Usb stick seems to be doubling up. I have an icon on my desktop for it regaurdless of weather it is in or not. it can't be deleted or unmounted. And when I DO plug it in I get another Icon for USB

3. My friend just tried installing and it's saying it can't find menu.lst when he first booted into it.

1. I think so. What are you using for sound? (Headphones/USB device/speakers/etc)

2. If you can delete the icon if it is not a real device. Did you have this plugged in when you installed?

3. ```

gksudo gedit /boot/grub/menu.lst

```

---

### Post by Ludford on 2008-01-20
> **LaRoza said:**
> 1. I think so. What are you using for sound? (Headphones/USB device/speakers/etc)

2. If you can delete the icon if it is not a real device. Did you have this plugged in when you installed?

3. ```

gksudo gedit /boot/grub/menu.lst

```

1. I'm using some large 70watt speakers plugged into the green audio plug in the back of my pc. Seriously? can it not play more than one sound? I am suprised it's not all over the internet thats a major bug.

2. Yes I had it plugged in during installation

3. Should he be in a command line? And he just puts that in and it boots?

---

### Post by forestpixie on 2008-01-20
you should be able to use more than one sound source at the same time - I can, although I've no idea if aMSN or Gaim work with xmms, nor whether they'd work as such in Wubi - because I don't use any of them :)

as far as your friend's problem goes - it sounds to me that grub didn't install properly

---

### Post by Ludford on 2008-01-20
> **forestpixie said:**
> you should be able to use more than one sound source at the same time - I can, although I've no idea if aMSN or Gaim work with xmms, nor whether they'd work as such in Wubi - because I don't use any of them :)

as far as your friend's problem goes - it sounds to me that grub didn't install properly

It dosn't matter I'm just a noob. I solved the sound problem by switching to ALSA and the USB problem by rebooting with the stick not in.

> **forestpixie said:**
> 
as far as your friend's problem goes - it sounds to me that grub didn't install properly

I didn't think Wubi installed Grub. since on mine it just modified the windows MBR and added Ubuntu to it.

---

### Post by forestpixie on 2008-01-20
if I'd known the friend used Wubi I wouldn't have answered - as I've no idea about it at all :)

---

### Post by Ludford on 2008-01-20
> **forestpixie said:**
> if I'd known the friend used Wubi I wouldn't have answered - as I've no idea about it at all :)

I don't know much about how it functions either :). From what I understand it saves the OS to a part of your HD without the need to partition it. It then modifies windows's boot.ini to give the option of using the HD space as a bootable partition or something.

EDIT: aMSN is still not making sound with music.... although now  can have a movie play sound and play music at the same time.

EDIT2: Infact now the volume control won't work at all and I can only control volume through the speaker controls.

---

### Post by alzie on 2008-01-20
WUBI should have installed GRUB.  

Its should have an uninstall in the Windows Programs area.  He should be able to just uninstall and reinstall and it hopefully will correct the problem.

When I used it I gave it a separate partition on the hard drive.  I'm not sure if this would make a difference but I was planning on using that partition for Ubuntu If I was happy with Ubuntu.

Good Luck

---

