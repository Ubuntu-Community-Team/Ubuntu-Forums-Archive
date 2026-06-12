---
title: "[SOLVED] can't access ktorrent"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by axamax on 2007-11-17
I click the icon on the launchbar and usually an icon appears in the "system tray"?? However the separator at the end of the system tray moves over to make space for another icon , but it doesn't appear!!

Any Ideas?
I've tried reinstalling and rebooting the pc.

---

### Post by daimaru on 2007-11-17
run ktorrent from console and check the output errors

---

### Post by axamax on 2007-11-17
How do I do that? 
Terminal
sudo run ktorrent?

---

### Post by ajgreeny on 2007-11-17
Accessories > Terminal, and just type **ktorrent**

---

### Post by axamax on 2007-11-17
The icon has now appeared in the system tray and ktorrent opens.

The result of terminal was:
ubuntu@ubuntu-desktop:~$ ktorrent
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Qt: Warning: QObject::disconnect: Unexpected null parameter
Qt: Warning: QObject::disconnect: Unexpected null parameter
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Launched ok, pid = 6493


Let me know if you spot a problem please

---

### Post by davidc502 on 2007-11-17
Did you install ktorrent from the Add/Remove Applications?

Also, what type of hardware do you have?

Thanks,

David

---

### Post by axamax on 2007-11-17
Installed from synaptic.
Hardware Dell dimension2300 1.8ghz celeron 1GB RAM 

I've been having problems since upgrade to gutsy with the screen freezing. I don't know if this might be Ktorrent, but it's always on since the upgrade.

---

### Post by davidc502 on 2007-11-17
This probably won't work worth 2cents, but I just compiled the latest version of Ktorrent 2.2.3-1.

You are welcome to try this[ version]("http://davidc502.home.comcast.net/packages/ktorrent_2.2.3-1_i386.deb") to see if it works any better.

I compiled my own because I was having problems with version 2.2.1.

This is just a shot in the dark, and probably won't work. This really sounds like your upgrade has issues, but I thought I'd offer.

If it doesn't work, go back to the Add/Remove and remove the package. Then go to the directory the .deb was downloaded to and remove it as well.

---

### Post by axamax on 2007-11-17
Thanks I'm trying it now. I'll let you know how it goes
When I was doing the Gutsy upgrade my internet crashed so I don't know if any files were damaged. I'd have expected Synaptic to show them as broken packages though.
I keep losing my windows share and the screen freezing have been the main problems to date. I end up having to pull the plug out of the back of the computer and restart it.

Thanks again.

---

### Post by davidc502 on 2007-11-17
I think there might be a "repair" option. Try booting to Ubuntu CD, and see if there is indeed a repair option. I remember Suse linux does, but not sure about Ubuntu.

Or you can try this.... From a terminal try

$sudo apt-get install -f

This command line option may fix broken packages, if any.

---

### Post by axamax on 2007-11-17
Worth a try. I should know if the freeze problem is solved by the morning as well. I've got two more computers waiting to cross over to ubuntu, but I need to know it's going to work reliably first. I'd no problems with Feisty.

---

### Post by axamax on 2007-11-18
PC and ktorrent have been running through the night without freezing. 9 hours so far. The new version of ktorrent seems to have been the answer. I'll have a look at a repair option on my cd later. I'll monitor this for a day or two before closing it.

Thanks everyone for your help.

---

### Post by davidc502 on 2007-11-18
Great! Enjoy that new build! The old version Ubuntu has available for download seems problematic!  Well lets hope this new package doesn't crash! Good luck!

David

---

### Post by axamax on 2007-11-19
No probs for last couple of days Thanks everyone

---

