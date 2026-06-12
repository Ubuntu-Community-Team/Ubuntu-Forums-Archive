---
title: "USB Stick Help"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by Otto-C on 2006-07-28
I insert my USB Stick and it shows up on desktop menu. 
But, when I click it, shows nothing as to content. Does 
give an error message something about 'pmount'. Do not 
understand what needs to be done. Some help please.
tia
Otto-C

---

### Post by beniwtv on 2006-07-28
It would be helpful if we knew the exact message from pmount.

Try also this in the terminal:

```
sudo mount -t vfat /dev/sda1 /media/floppy
```

Maybe it shows up. If not, give the output too.

Good luck

---

### Post by Otto-C on 2006-07-28
From Desktop shows:
Corsair Flash Voyager
Dbl-click on it
Shows:
Unable to mount the selected volume
> Show more details
Error: Could not execute pmount
From sudo mount -t vfat /dev/sda1 /media/floppy
Shows:
mount: mount point /media/floppy does not exist

tia
Otto-C

---

### Post by beniwtv on 2006-07-29
ok, the dir /media/floppy doesn't exists, create it:

```
sudo mkdir /media/floppy
...
sudo chmod 777 /media/floppy

```

Then:

```
mount -t vfat /dev/sda1 /media/floppy
```

Hint: This is only to see if it works. Later we won't mount it in /media/floppy.

Try and give feedback.

---

### Post by Otto-C on 2006-07-30
Worked Great


ok, the dir /media/floppy doesn't exists, create it:


Code:
sudo mkdir /media/floppy
...
sudo chmod 777 /media/floppy
Then:


Code:
mount -t vfat /dev/sda1 /media/floppy
Hint: This is only to see if it works. Later we won't mount it in /media/floppy.
...
 
Did change your:
mount -t vfat /dev/sda1 /media/floppy
To
sudo mount -t vfat /dev/sda1 /media/floppy

Displayed the stick directory
Did a
sudo unmount /media/floppy

Whats next.
Otto-C

---

### Post by beniwtv on 2006-07-30
Ok, now that we know it works, you could add a static mount point for your device:

```
sudo mkdir /media/usbdevice
sudo chmod 777 /media/usbdevice
```

You can replace "usbdevice" with anything you like.

Then edit fstab:

```
sudo gedit /etc/fstab
```

And add the line:

```
/dev/sda1     /media/usbdevice    vfat   rw,user,noauto,utf8    0     0
```

This should do the trick. Let me know.
A good thing is also to add the gnome disk mounter to your panel if you haven't already.

---

### Post by Otto-C on 2006-07-31
Did the above. Tried to save the item but it gave error:
Could not save the file /home/otto/etc/fstab
Unexpected error. File not found.
When I exit at prompt otto@forensics it shows:
** (gedit:7229): Warning **: Hit unhandled case 1 (File not
found) in gedit_unrecoverable_saving_error_message_area_new

Otto-C

---

### Post by infoseeker on 2006-07-31
The fstab file is under 

/etc

and not under /home...........

Under Ubuntu do ------> gksu gedit /etc/fstab

Under Kubuntu do -------> kdesu kate /etc/fstab

---

### Post by Otto-C on 2006-08-01
Did the above. Also removed floppy from /media.
Seems to be working like I would expect.
Thanks the guys who helped.
Otto-C

---

