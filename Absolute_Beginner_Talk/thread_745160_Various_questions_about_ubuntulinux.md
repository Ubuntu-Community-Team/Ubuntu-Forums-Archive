---
title: "Various questions about ubuntu/linux"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Vorteilspreis on 2008-04-04
Is there any way I can unmount any drive that is mounted on the deskptop? (whenever I try to unmount a drive I get a message saying "you are not privileged to unmount this volume" and under details it says "only root can unmount"
Can I hide my "recent documents" under "places"?
What is the best torrent client for linux?

---

### Post by Slushdoot on 2008-04-04
Right click it, select Unmount volume

rTorrent is the best client IMO.  It is, however, a CLI program.  Transmission is pretty good as a GUI client.  Many people also run uTorrent in WINE.

EDIT: Re recent documents
From the Ubuntu Desktop Guide:
To hide Recent Documents from the Places menu, open a terminal and run the command:

Code:

chmod 000 ~/.recently-used

To enable it again, run the command:

Code:

chmod 600 ~/.recently-used

---

### Post by roaldz on 2008-04-04
I dont know about hiding your recent p*rn eehw, documents, but deluge, ktorrent, azureus and transmission are pretty good!

---

### Post by bovus on 2008-04-04
> **pat666rick said:**
> 
"only root can unmount"


in linux, certain operations can only be executed by the administrator or root.  To run commands that require you to be root, put sudo before the command and then you will be prompted for root's password.

so it would be like:

```

$ sudo unmount sda1

```
sda1 being replaced by any drive/partition you are trying to unmount

---

### Post by bumanie on 2008-04-04
I run deluge for bittorrents.
To unmount a drive either right click and choose unmount device or open terminal and use the sudo followed by the device name (eg /media/sda1, or whatever your device is designated as). Don't know your second question.

---

### Post by Vorteilspreis on 2008-04-04
Before I seemed to be able to unmount my drives with no problem by right clicking them in the desktop, why is this not working anymore?

---

### Post by Slushdoot on 2008-04-04
What does it do?  Does it give any error messages?

---

### Post by aeiah on 2008-04-04
to remove your recently opened documents from the list use the menu to go to places>recently viewed documets> and at the bottom there should be a button to clear the documents.

---

### Post by Miko_UK on 2008-04-04
What is the best torrent client for linux?
I've tried azureus and Ktorrent and find Ktorrent far better, but azureus has more users so some one must like it.

---

### Post by mtbeedee on 2008-04-04
What kind of drive are you trying to umount?  Check the fstab (/etc/fstab) and see if "user" is listed as one of the options for that device.  It's been a while but I think that is how you tell the OS to allow the user to do things like mount and unmount that device.

---

### Post by mikewhatever on 2008-04-04
Are partitions really mounted on the desktop? That's possible, but very uncommon. Most probably those are just icons on the desktop and the real mount points are in /media or /mount. Post the output of <cat /etc/fstab> to verify that.

---

