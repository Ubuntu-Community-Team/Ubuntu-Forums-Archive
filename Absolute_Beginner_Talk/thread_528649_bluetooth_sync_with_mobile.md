---
title: "bluetooth sync with mobile"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-08-18
I am trying to upload photos from my motorola L6 into Gimp or something similar via bluetooth. With xp it is I simply download the software which came with the dongle and do it, with ubuntu it isn't that easy.
I have added the bluetooth manager which seems to do nothing and have perused the posts which are not very encouraging..Is this possible or will I have to revert back to xp?
I am relatively new and learning as I proceed.
Thanks for any advice.

---

### Post by philinux on 2007-08-18
> **Benbow said:**
> I am trying to upload photos from my motorola L6 into Gimp or something similar via bluetooth. With xp it is I simply download the software which came with the dongle and do it, with ubuntu it isn't that easy.
I have added the bluetooth manager which seems to do nothing and have perused the posts which are not very encouraging..Is this possible or will I have to revert back to xp?
I am relatively new and learning as I proceed.
Thanks for any advice.

My sonyeric K810i works well. Ive got Blue Tooth File Sharing, Bluetooth OBEX and Bluetooth chat from synaptic.

Also if I connect to pc with usb cable then open Gthumb I can browse my phone and its card like a mounted disk! Much quicker too.

---

### Post by Benbow on 2007-08-18
Looks like I am stuck with xp, pity.

---

### Post by Saxenm on 2007-08-18
with xp, i used to use the bluesoleil software for all bluetooth needs, but with ubuntu, i just use the application "Bluetooth File Sharing". My ubuntu box is called "my-laptop", so on my phone, i select all the photos i want to send, and then send via bluetooth. the phone then searches for devices and it finds a bluetooth device called "my-laptop". its very easy man, i believe the package is called "gnome-obex-server" or something like that, so try that out before you decide to switch back to xp.

---

### Post by A$h X on 2007-08-22
Try this:

[http://ubuntuforums.org/showthread.php?t=531753](http://ubuntuforums.org/showthread.php?t=531753)

---

### Post by metapaso on 2007-10-29
I too have an L6, and I managed (finally) to get the phone to send and receive photos in an easy way.  This applies under GNOME, and Ubuntu Feisty 7.04,( not KDE ).

I was not documenting my steps very closely, but the general procedure was:

1.  Open the Synaptic Package manager, (you will have to enter your password) and search for BlueTooth.
2.  Make sure you have the gnome-bluetooth, bluez-utils, bluez-gnome, bluez-pin, libbluetoth, libbtctl, and libgnomebt installed
3.  Restart your system with the bluetooth dongle attached or the built-in bluetooth enabled
4. Run the command 
```
hcitool dev
```
TO make sure that your computer-side bluetooth device is found.  It should appear as 
linux:~$ hcitool dev
Devices:
        hci0    00:10:C6:63:D9:62

5.  In System->Preferences-->BlueTooth Preferences, check to make sure that "Visible and Connectable for other devices" is enabled.  You might want to write down the name of the device as it appears in this window.
6.  On the Motorola L6, go to Main Menu-->Bluetooth Link-->Setup and select Find Me.  You may be prompted to enable bluetooth.  The menu says you will be discoverable for 60 seconds and the bluetooth light will flash.  In my experience, the period of discovery is considerably less than 60 seconds, so you need to have the following step 7 ready
7.  Open a Terminal Window, and type:
```
hcitool scan
```
You should see something similar to the following output:
Scanning ...
        00:1A:1B:E7:3D:1D       Damonmoto

This means that your phone can be seen by the bluetooth subsystem.  If this doesn't work (try it a few times right after pressing Find Me on the Motorola L6 to make sure)...you might have some luck at [http://www.linuxjournal.com/article/9466]("http://www.linuxjournal.com/article/9466")
8.  All that's left is to turn on  Applications-->Accessories-->Bluetooth File Sharing.  You should see a little blue antenna on your top panel.
9.  On your phone, go to Main Menu-->Multimedia-->Pictures.  Choose the picture that you want (or multi-select by marking them with the 0 key), then hit the menu button and choose Copy.  Then choose [Look for Devices].  Your computer should show up and you can choose to copy it there.  The gnome Bluetooth File Sharing will receive the file(s) and put it(them) on your desktop.

Good Luck!
Damon
[http://www.metapaso.com]("http://www.metapaso.com")

---

