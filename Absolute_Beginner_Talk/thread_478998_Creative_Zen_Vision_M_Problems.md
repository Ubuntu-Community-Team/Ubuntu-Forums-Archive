---
title: "Creative Zen Vision M Problems"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by kevCast on 2007-06-19
I was wondering, how do I get my Creative Zen Vision M 60GB player to be recognized in Feisty? I've tried Gnomad 2, but it froze my player, yet was still recognized. Then I upgraded the firmware on it, now it's not recognized at all in Gnomad, but still freezes. Is there anyway to get this thing to work?

---

### Post by schwascore on 2007-06-20
1 - install Amarok from the repositories
2 - plug in your Zen (**not** in USB mode)
3 - Open Amarok
4 - Settings --> Configure Amarok
5 - On the Media Devices tab, click on "Add Device"
6 - Select "MTP Device" from the pull-down menu
7 - Enter a name for your mp3 player
8 - Click "Ok", "Ok"
9 - Click on the "Devices" tab on the left-hand side of Amarok.
10 - At the top left, click on Connect.

That should do it!  Make sure you still have Gnomad2 installed or at least libmtp5 because Amarok's MTP support depends on it.

---

### Post by drivel on 2007-06-20
> **schwascore said:**
> 1 - install Amarok from the repositories
2 - plug in your Zen (**not** in USB mode)
3 - Open Amarok
4 - Settings --> Configure Amarok
5 - On the Media Devices tab, click on "Add Device"
6 - Select "MTP Device" from the pull-down menu
7 - Enter a name for your mp3 player
8 - Click "Ok", "Ok"
9 - Click on the "Devices" tab on the left-hand side of Amarok.
10 - At the top left, click on Connect.

That should do it!  Make sure you still have Gnomad2 installed or at least libmtp5 because Amarok's MTP support depends on it.

Amarok is for KDE,how about Gnome users?

---

### Post by schwascore on 2007-06-20
Amarok works in Gnome with no problems.  Enjoy!

---

### Post by drivel on 2007-06-20
> **schwascore said:**
> Amarok works in Gnome with no problems.  Enjoy!

But Qt soft is unstable in Gnome~

---

### Post by schwascore on 2007-06-20
I have never had problems with Amarok in Gnome.  All I can tell you is that from my own experience, Amarok is the best / only media player that fully supports the Zen Visions (with the exception of video / photo transfer).

Anyways, what's the harm in trying? you can always apt-get remove....

---

### Post by Sushubh on 2007-06-20
right i use amarok in gnome all the time...

doesn't zen connects to the linux comp as a USB powered hard drive?

---

### Post by schwascore on 2007-06-20
Zen Visions can show up as both, but only files on the MTP partition are available to be played.  But yes, you are correct, the Vision *can* show up as a USB hard drive, but only if you tell it to. In that mode it's  just a hard drive, not a music player.

---

### Post by Sushubh on 2007-06-20
umm. from what i remember. i have connected the vision media player as a USB disk. copied media files to it and they played fine on disconnecting from the computer!

---

### Post by blkno1 on 2007-06-30
> **Sushubh said:**
> umm. from what i remember. i have connected the vision media player as a USB disk. copied media files to it and they played fine on disconnecting from the computer!


Can you confirm this?.  And if so how?

---

### Post by toasterofirony on 2007-06-30
I use Amarok in gnome and it works fine for the most part, though if I try and upload several thousand songs (something I do from time to time) I develop a huge memory leak in amarok that eats everything in its path. I get it too if I try and run remuco to control Amarok with my 'phone over a BT connection, so I'm guessing something isn't sitting right with Amarok/ Qt in gnome.

---

### Post by schwascore on 2007-06-30
> **blkno1 said:**
> Can you confirm this?.  And if so how?

I can confirm that the Zen Vision:M *does NOT* play music transfered to its USB Disk partition.  It only plays music on its MTP partition, which you need extra software like Gnomad2 or Amarok to access.

Perhaps earlier versions of the Vision, which I am unfamiliar with, were just USB devices, but that is no longer the case with current versions.

---

### Post by Abaddon on 2007-07-03
Along a similar vein, I'm using Kubuntu Feisty (just recently jumped over from Gnome), and can get Amarok to recognise my player, but I'm unable to copy files over to it.

Info:
Kubuntu Feisty, Kernel 2.6.20.16
KDE 3.5.6
Amarok 1.4.6

mtp-detect works and gives the following:
```
Attempting to connect device(s)
PTP: Opening session
Detect: Successfully connected 1 devices
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 041e
   idProduct: 413e
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Device flags: 0x00000000
Device info:
   Manufacturer: Creative Technology Ltd
   Model: Creative Zen Vision:M
   Device version: 1.62.02_0.00.23
   Serial number: 00023C02C2A0B57B58DC75CE540213D9
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0;microsoft.com/WMPPD: 10.0;mi
crosoft.com/WMDRMPD: 10.1;audible.com: 1.0;
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1007: Get object handles
   100c: Send object info
   100d: Send object
   100f: Format storage
   1014: Get device property description
   1015: Get device property value
   1006: Get number of objects
   1008: Get object info
   1009: Get object
   100b: Delete object
   1010: Reset device
   1016: Set device property value
   1017: Reset device property value
   101b: Get partial object
   9801: Get object properties supported
   9802: Get object property description
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   9808: Send object property list
   9807: Get interdependent property description
   9810: Get object references
   9811: Set object references
   9201: Report Added/Deleted Items
   9101: Get secure time challenge
   9102: Get secure time response
   9103: Set license response
   9104: Get sync list
   9105: Send meter challenge query
   9106: Get meter challenge
   9107: Get meter response
   9108: Clean data store
   9109: Get license state
Events supported:
   None.
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Device Friendly Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd201: Unknown property

```

The amarok error is:

Error:
Failed to copy track to media device:  <local filename>

There isn't any more extra information to get from running amarokapp in the console.

This isn't a deal breaker for me - I can still boot into windows and copy my files over that way, but I use Ubuntu all the time now except for when I'm playing games, and I've just got my MP3s all re-tagged in Amarok, so it would be really nice to be able to do one-stop-for-all.

Any suggestions appreciated.

---

### Post by fictivetoast on 2007-07-08
The newest Rhythmbox within the repositories includes a functional MTP plugin that allows transfering songs ; for playlists or other files though, Gnomad2 is still the best bet.

---

### Post by Amablue on 2007-07-08
What about Video? Is there any relatively easy way to get videos to the ZVM?

---

### Post by redsparrow123 on 2007-07-27
What do you mean by "not in usb mode"?   Sorry, I'm new to this.

Also there's no "mtp" in the drop down list for me.  I tried using "creative nomad" but it did the same thing as before when i tried plugging my player in (froze the player, didn't read it at all).

---

### Post by schwascore on 2007-08-01
USB mode is when the Removable Disk feature on the Zen Vision:M is activated.  This makes the player function as a "normal" USB drive (ex. thumb drive).  When this mode is not activated, it can only be connected to via the MTP protocol.

Which version of Ubuntu are you using?

Also, make sure that you have the libmtp5 package installed as well as the amarok package installed from the standard repositories.  If you compiled / installed either on you own, it might not work with my instructions.

---

### Post by kou on 2007-08-01
hi
I have the same Zen Vision M.
Take a look a this tutorial .... after this steps Zen works "genial"

[http://mmejiav.wordpress.com/2007/06/13/compilacion-de-gnomad2-para-creative-zen-visionm-de-30-gb/](http://mmejiav.wordpress.com/2007/06/13/compilacion-de-gnomad2-para-creative-zen-visionm-de-30-gb/)

---

### Post by schwascore on 2007-08-02
That is a great tutorial as long as you are satisfied with the features (and limits) of Gnomad2.

Gnomad2 is still the best way to transfer videos and photos onto your device, however the software has limitations.  For example, it can be very difficult to sync music between the Zen Vision:M and your computer.  Also, making a playlist is not that easy.

I still suggest a combination of Amarok and Gnomad2.  Amarok for syncing music and creating playlists while using Gnomad2 to transfer videos and photos.

Besides, when you use Amarok to transfer music, it automatically transfers the album art too (assuming you have downloaded it through the album cover feature in Amarok).

then again, you could always just use all of the mtp- commands from the terminal, but that's quite an adventure!

just my two cents...

---

### Post by wantime on 2007-08-12
I have followed the instructions - made sure that the Creative VisionM has USB mode disabled, the libmtp5 file is installed as are Amarok and Gnomad2.  Still my VisionM crashes and is not recognised??   I am running a fresh install of Feisty Ubuntu with KDE desktop.  Can anyone think of anything else that might be wrong?

Here is some output from dmesg
...
[  864.924000] usb 4-3: new high speed USB device using ehci_hcd and address 4
[  865.056000] usb 4-3: configuration #1 chosen from 1 choice
[  870.056000] usb 4-3: can't set config #1, error -110
[ 1433.092000] usb 4-3: USB disconnect, address 4
[ 1437.724000] usb 4-3: new high speed USB device using ehci_hcd and address 5
[ 1440.836000] usb 4-3: device descriptor read/64, error -110
[ 1456.052000] usb 4-3: device descriptor read/64, error -110
[ 1456.268000] usb 4-3: new high speed USB device using ehci_hcd and address 6

The results of mtp-detect are:

$ mtp-detect
Found non-autodetected device "Creative Zen Vision:M (DVP-HD0004)" on US
usb_claim_interface(): No such file or directory
Connection error.

---

### Post by ConsumingFire783 on 2008-04-03
Hey, here's what I did to get my Zen Vision:M working.

Go to the terminal
type "lsusb" with the player in a usb port, and it should be listed as a creative product.
then type "mtp-detect"
if that doesn't work, if an error message comes up, or nothing happens...
type "sudo apt-get install mtp-tools"  

After this, I went back into Gnomad2, and it worked perfectly.

---

