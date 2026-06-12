---
title: "Quicksilver G4: No Network"
date: 2005-05-18
forum: Apple PPC Users
---

### Post by ipixel on 2005-05-18
Just finished installing Kubuntu on a second HD - system: PowerMac G4 'Quicksilver' (dual processor 1.25Ghz, 1Gb RAM, Kubuntu HD = 160Gb). 

I have no network connection - even though installation went fine, and the installer seemed to find all the update servers, and download all the software it needed... I have a DHCP server, and it seems that it retrieved the original information from the server, but somewhere along the line, the config file must have become corrupt. The Network control panel says that the Default Gateway is "1.0.168.192" - which seems to be back-to-front. When I try to enter 'Administrator Mode', the system accepts my password, and then promptly shows me the generic "Internet Configuration" page (?). If I go back to "Network", I have to enter 'Administrator Mode' again...and again...and again... No way to get out of the loop.

Please, help! I'm a newbie, and am totally lost!

---

### Post by ipixel on 2005-05-18
UPDATE:

Starting from the Kubuntu Live CD, the network works without a problem.

After (re)installing Kubuntu (using the installation CD), the network drops...

---

### Post by Len on 2005-05-20
According to your processor speed you probably have a Mirrored Drive Doors powermac instead of a Quicksilver ([http://www.info.apple.com/support/applespec.html)](http://www.info.apple.com/support/applespec.html)). I have almost the same machine (single 1.25 GHz) but no network problems. Open a terminal and post the output of 'ifconfig' and 'lsmod' here.

You could try to enter 'sudo modprobe sungem', my powermac uses the sungem driver for the ethernet card.

---

### Post by ipixel on 2005-05-21
Len, thanks for the reply! - yes, you are right, it *is* a Mirrored Drive Doors model. 

I re-installed Kubuntu from scratch, and the second time around, the network worked. Something must have become corrupted during the first installation! - strange...

---

### Post by Len on 2005-05-21
Seems that the autoprobe for hardware doesn't work perfectly then... I'm glad it worked out!

Remember: your G4 uses the 'sungem' driver for network, always handy when you encounter this problem and/or want to compile your own kernel ;-). Took me hours to find this out by accident in the past, I'm no linux expert either :P.

---

