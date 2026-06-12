---
title: "Unmount CDRom"
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by Stag on 2005-07-22
Hi All,

Linux newbie here. SIlly question but it is very frustrating! How do I unmount a CD so I can take it out the machine and insert another. At the moment the only way I can get this right is to restart the machine each time!

I have tried right clicking on the desptop icon and selecting eject but it comes back with the message that it is busy and cannot unmount. Yet I have closed all applications that had access to the CDRom.

Help a newbie please.

Stag ??:

---

### Post by jasmuz on 2005-07-22
sudo umount -l /dev/hdxX (x's mean that you must know where your cdrom is located at.)
and after, just type eject

if it dosent work just do a sudo eject (it will take it out no matter what)

---

### Post by poofyhairguy on 2005-07-22
[QUOTE=Stag]
I have tried right clicking on the desptop icon and selecting eject but it comes back with the message that it is busy and cannot unmount. Yet I have closed all applications that had access to the CDRom.
[/QUOTE]

Hmmm....can you tell if the CD rom is still spinning?

---

### Post by [pl]ice on 2005-07-23
hey, got the same problem :) no ideas at the moment,
 probably umount /cdrom -l will say umounted but it won't eject the cdrom ??
i tried various things still no use. have you tried to upgrating the ubuntu???(patches...) ?
the only way i can take my cdrom out, i by rebooting it :(

---

### Post by poofyhairguy on 2005-07-23
Here is what I do:

Install K3B. Start a new audio cd. Put like one thing in.

Then K3B will eject the drive when it starts to burn. Then exist K3B before it burns the CD.

---

