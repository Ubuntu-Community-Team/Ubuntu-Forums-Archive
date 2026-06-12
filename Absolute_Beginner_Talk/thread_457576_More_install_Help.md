---
title: "More install Help"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Wilzer on 2007-05-28
K...so ive sucessfully made an install of ubuntu on my laptop. I think im having some problems in the video  card department so I booted into safe mode Im getting a prompt "root@ubuntu :# " with a flashing cursor ....what do I do?

---

### Post by nickburns on 2007-05-28
What problems are you having with the video card?  What hardware do you have?  can you post your /etc/X11xorg.conf file?

---

### Post by taurus on 2007-05-28
Reconfigure it with

```
dpkg-reconfigure xserver-xorg
```
Then, reboot and see if X is running again.

```
shutdown -r now
```

---

### Post by Wilzer on 2007-05-28
If you dont mind, Id like to start from the beginning....I installed Ububtu on an old HP 5445 Laptop... the install is successful but when I boot up, after the boot screen and install bar I get a black screen...its a black screen that is lit if that makes sense....I really need to know where to go from here. I do hear a short ubuntu drum roll as it changes from boot screen to black.

---

### Post by taurus on 2007-05-28
Okay, after you hear the sound, press <Ctrl><Alt>F2 to get to a console.  Log in with your login name and password.  Then at the prompt, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```
If you are not sure about a question, just use the default and use **vesa** driver for your graphic card for now until you get X up and running again.  Then, you can install a driver for it.

When done, press <Alt>F7 to get back to GUI login screen and press <Ctrl><Alt>Backspace to restart X.  Otherwise, reboot if you wish.

What is the graphic card on your laptop anyway?

```
lspci
```

---

### Post by Wilzer on 2007-05-28
k so after the drums I hit ctrl,alt f2 and the screen fades into something but it looks like greyish black venetian blinds. no console ...any Idea how to get the console? Im looking for vid card info atm

---

### Post by taurus on 2007-05-28
How about <Alt>F3, <Alt>F4, or even <Alt>F5?

Otherwise, boot into recovery mode from GRUB menu and reconfigure X again with

```
dpkg-reconfigure xserver-xorg
shutdown -r now
```

---

### Post by Wilzer on 2007-06-02
K ive still had no luck ...my video card seems to be an Intel Corp 82830 CGC...Im still having trouble getting this working even with the vesa driver...If im doing this all right

---

### Post by taurus on 2007-06-02
Can you boot your machine with the LiveCD at all?  If you can, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Wilzer on 2007-06-02
the result of this is....

Disk /dev/sda: 20.0 GB 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot                  Start           End             Blocks             Id          System
/dev/sda1   *                     1           2342          18812083+      83         Linux
/dev/sda2                    2343           2432             722925           5         Extended
/dev/sda5                    2343           2432             722893+       82        Linux swap / Solaris


hope this helps

I did this from Safe Mode

---

### Post by taurus on 2007-06-02
Are you able to boot your machine with the LiveCD?  I am thinking about copying /etc/X11/xorg.conf from the LiveCD over to your harddrive and see if you can run X again with the version from the LiveCD.

---

### Post by Wilzer on 2007-06-02
Ill try... I think I have a Ubuntu Live CD but it may be the version right before fiesty fawn...is that ok?

---

### Post by Wilzer on 2007-06-02
I get an error message  There was and error starting GNOME Settings Daemon and this thing is ssssllllllooooowwww ...I think im on the edge or slightly below the ram limits

---

### Post by Wilzer on 2007-06-02
It appears I can boot from live CD and get the gui...can you walk me through what you want me to copy and how please

---

### Post by taurus on 2007-06-02
Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
sudo cp /etc/X11/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf
sudo umount /dev/sda1
```
Reboot (and remove the LiveCD) and see if X is coming up fine this time.

---

