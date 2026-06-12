---
title: "[SOLVED] Many questions, little time"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Bob_12 on 2007-09-01
So I installed Kubuntu 7.04 on my friends Dell Inspiron 1000 and things went decently smoothly up until now. Whenever I try to update, or use Adept, or Ad or Remove programs it tells me that the package manager is already in use by another program. There is no other program running that I know of using the package manager. How can I fix this? 

 Next, she has an ntfs external USB hard drive and how can we make it read and write to the hard drive? All her important files are on it and she needs them transferred to her laptop.

 Lastly, we need DVD and mp3 support on the laptop for KUbuntu. What program should she get and how can we get that extra support?

 Thanks so much in advance.

---

### Post by wormser on 2007-09-01
I would reboot to make sure that there is not another package manager open.

Install ntfs-3g and ntfs-config.  Then configure it under Applications> System Tools> NTFS Configuration Tool.

---

### Post by GuitarRocker2562 on 2007-09-01
and for you last question, in ubuntu clicking on your unplayable media files automatically list the programs need to play them and gives you the option of installing them, i think this may be done in Kubuntu too.

---

### Post by sumguy231 on 2007-09-01
For the mp3 and dvd support, install the ubuntu-restricted-extra package. Make sure you have the 'multiverse' repository enabled in Synaptic. Then follow the instructions here:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#head-e3dafb305e64ec576176ee706e287bb4d839cb12](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#head-e3dafb305e64ec576176ee706e287bb4d839cb12)

Edit: To address the above, you should be prompted to install the needed codecs when you try to play an mp3, but I don't think that works with DVDs.

---

### Post by Bob_12 on 2007-09-02
Thanks for the help so far. I've rebooted many times and it always says that I have another package manager open. Its really confusing me.

---

### Post by SOULRiDER on 2007-09-02
Type:
```
 sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a
``` in a console.

---

