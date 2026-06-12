---
title: "Cruzer Mini(s)"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Greg Mueller on 2008-04-05
I have several Cruzer Mini USB memory sticks I transport stuff around on. Some of them are recognized by Ubuntu and some are not.

What's the difference that makes some recognized?

---

### Post by m60dude5 on 2008-04-05
Honestly, I don't know. I have two or three and one works, the other doesn't. I think older ones might work because the drivers would be recognized better than ones that just came out with brand new drivers. But that's my best guess.

---

### Post by sayakb on 2008-04-05
I have 2 Sony memory sticks for my Cybershot. None of them work on my box. :(

---

### Post by Jerry N on 2008-04-05
My Sandisk Cruzers came with the U3 software thing and I couldn't get Ubuntu (or LinuxMint) to acknowledge them without removing the U3 junk.  The on-board software contains a U3 remover but it only works on a Windows machine.  After getting rid of U3, they worked fine.

Jerry

---

### Post by bapoumba on 2008-04-05
> **Jerry N said:**
> My Sandisk Cruzers came with the U3 software thing and I couldn't get Ubuntu (or LinuxMint) to acknowledge them without removing the U3 junk.  The on-board software contains a U3 remover but it only works on a Windows machine.  After getting rid of U3, they worked fine.

Jerry
I know it is quite useless to post a "works for me". I got a 1Go sandisk cruser with the U3 stuff in it and it works so well that I bought a 4Go this morning. Working fine too. I just left the U3 part alone. Running gutsy on two laptops, one with usb2 and one with usb1 ports. Quite strange.

Did you have any error message?

---

### Post by ghost_ryder35 on 2008-04-05
Have you guys tried to manually mount them?  This may make them work.

---

### Post by stephanvaningen on 2008-04-05
You maybe can do this. Warning with this: result will be:
[list]
[*]lYou maybe loose U3
[*]The data on it now will not be available, first backup on another box
[/list]
Start fdisk -l to see which is the device name for your USB:
 ```
sudo fdisk -l
```
If you are not sure: first remove the USB, do this fdisk, then insert the USB and after some seconds re-issue the fdisk command: the /dev/sdx appearing is your USB stick's device ID in Ubuntu: take note of this device id (x)

Then, unmount this via a command:
 ```
sudo umount /dev/sd[color=red]x[/color]1
```
where [color=red]x[/color] is the ID you took note of earlier.
Now format the USB:
 ```
sudo mkfs.vfat -F 16 -n usb-label /dev/sd[color=red]x[/color]1
```
Where usb-label is a label-name which you can choose yourself

Remove and re-insert the usb stick...

Did this help?

*(source: info partially from [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/))*

---

### Post by Greg Mueller on 2008-04-05
Not for me

---

