---
title: "bluetooth?"
date: 2006-09-11
forum: Apple PPC Users
---

### Post by davidmaxwaterman on 2006-09-11
Hi,

I'm trying to get bluetooth working on my TiBook running latest Ubuntu.

I followed a how-to, but got stuf on :

$ hcitool scan
Device is not available: No such device

strace seems to suggest it's not trying to access any /dev/ files. The only noticable thing I see is the creation of a 'PF_BLUETOOTH' socket, which it quickly closes.

I've tried a couple of USB bluetooth dongles.

Any ideas?

Max.

---

### Post by spinz8 on 2006-09-23
Hi,
Try to install the frontend's GUI BT utility "gnome bluetooth". It's in the repos.
It works for me. Recognised most BT phones and even BT mouse. I can transfer/receive files from BT phones.
Haven't configured my BT  mouse though.
Regards.

---

### Post by davidmaxwaterman on 2006-09-23
I already have that installed.

Can you tell me what h/w you're running on? Is it also ppc? What bluetooth h/w?

Perhaps I am just not configuring/running it correctly. Could you give me a step-by-step?

Thanks!

Max.

---

### Post by spinz8 on 2006-09-23
Hello Max,
My hardware is iBook G4-1.33mhz (BT 2.0 + EDR). 
On Synaptic Package Manager, search for "bluetooth" and " OBEX". I have the following Libraries installed:
libbtctl2
libopenobex 1.0.0
apart from lib associated with gnome-bluetooth.
Tested on N9500, SE K610 (i think),N6680 and Apple BT mouse.
To send file:
1. Preferences> Bluetooth File Manager
2. Devices>scan (ensure your phone is in discoverable mode).It will take about 30-45 sec to recognise BT device-a lot faster if you  use terminal's hcitool scan command. A generic phone icon with profile name should appear.
NB there isn't any pairing available.
3 Click on any file (text,image, video etc)
4. Right click (mouse) or menu> Edit> sendwindow dialog comes up and choose "OBEX". default is Evolution, and send file.
To receive file
1. Accessories> Bluetooth File sharing
2. A window dialog will come up asking  you if you want to accept inoming file transfer. The default file saved location is your Home folder.Please note that Bluetooth Sharing applet will appear also on the top right panel.
Trust this helps.

---

