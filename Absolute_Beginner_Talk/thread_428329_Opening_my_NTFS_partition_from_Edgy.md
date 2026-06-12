---
title: "Opening my NTFS partition from Edgy"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Diversion on 2007-04-30
When trying to access my NTFS-partitiion from Edgy, I recieve te following message:
" Unable to mount the selected volume"
with the following details:
error: device /dev/hda1 is not removable

error: could not execute pmount

I've had it working out of the box on my previous Edgy installation.
Any suggestions?

thnx in advance,

Colin

---

### Post by Najand on 2007-04-30
try to open a terminal and use the following commands:
```

$ sudo mkdir /media/windows
$ sudo mount -t ntfs /dev/hda1 /media/windows

```
If it works then you need a little more effort to add it to your /etc/fstab
Tell me if it works then I help you to continue.

---

### Post by Diversion on 2007-04-30
I can now open it but now get the following message:

The folders content could not be displayed:
"You do not have the permissions necessary to view the contents of "windows""

I'm of now so won't be able to reply today, but I have the topic notifier on so will be checking in again tomorrow

thnxs in advance

---

