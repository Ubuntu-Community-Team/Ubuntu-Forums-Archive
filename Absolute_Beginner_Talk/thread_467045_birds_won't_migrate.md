---
title: "birds won't migrate"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by flavio newbie on 2007-06-07
I have the hd partition icon of windows on my ubuntu desktop, i can open it, read file and copy them, but not save on it... how can I do it?? Absolute beginner....
Thanks in advance

---

### Post by Outrunner on 2007-06-07
If your Windows partition is NTFS then you'll need ntfs-3g(search for it in synaptic)

---

### Post by taurus on 2007-06-07
What filesystem is your Windows partition?  If it's ntfs, then you need to install ntfs-3g driver first before you can write to it.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install ntfs-3g ntfs-config
gksudo ntfs-config
```

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by flavio newbie on 2007-06-07
Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 I get this error.... :(

---

### Post by taurus on 2007-06-07
Do you have synaptic open and try to run "sudo aptitude update" at the same time?  You need to either use synaptic only or close down synaptic and install it from a terminal.  Can't run those at the same time.

---

### Post by Outrunner on 2007-06-07
Is synaptic or Add/Remove... open? Or another APT based process running? You need to close them.

EDIT: Hmm, I need to exercise faster typing :(

---

### Post by flavio newbie on 2007-06-07
yes, im downloading vlc media player.... you guys know it all.... thanks a lot btw

---

