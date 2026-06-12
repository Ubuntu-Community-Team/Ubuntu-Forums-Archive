---
title: "Airport firmware?"
date: 2007-04-12
forum: Apple PPC Users
---

### Post by beshroomed_hippie on 2007-04-12
Just a few days ago, I made the switch to linux, using the awesome ubuntu "edgy" distro, but one obstacle remains,

:confused: I've been trying to get my airport wireless to work, and i have everything i need but the firmware. Not knowing of this problem previously, i formatted my mac os , going full on ubuntu. Does anyone know where i  might be able to find this firmware? I've only been able to find updates for firmware on apples site, and they are DMG's so I am not sure if that'd be of any use with linux anyhow. Also, if anyone else has had experience in this realm perhaps they could point me in the direction of the method they used?
 
Am I completely screwed cause i didn't back up that firmware?

---

### Post by berlandb on 2007-04-13
Hi,

the Firmware from the following website works for my Airport Extreme: [http://joona.kuori.org/ubuntu-powerbook/#airportextreme](http://joona.kuori.org/ubuntu-powerbook/#airportextreme)

Good luck.

---

### Post by ExplodingPickle.org on 2007-04-13
DMG's are basically files containing the Mac OS X filesystem (HFS+). To open them on Linux you will need to type this:

$ sudo su root
# mkdir (wherever you want the DMG to be opened)
# mount -t hfs -o loop name/of/dmg.dmg (the folder you just made)

And when your done:

$ sudo umount (the folder you made)
$ sudo rm -r (the folder you made)

---

