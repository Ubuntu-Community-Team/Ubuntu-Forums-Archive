---
title: "Installing Ubuntu on existing windows partition?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by l0k1_ on 2007-01-19
I am currently running windows xp professional but am planning on installing ubuntu alongside it. I have one hard drive but it is currently separated into two different drives (C: and D:). One partition has all my programs (C:) , the other is just music files, movies, documents etc (D:). Could I just install Ubuntu on one of the existing windows partitions, that doesn't have the windows installation on it (D:)? Will the installer allow me to do this? Right now I have no free unpartitioned space to install Ubuntu on and I don't want to uninstall windows just to install ubuntu.

---

### Post by sankarj12 on 2007-01-19
Yes, that is possible.  When installing Ubuntu, on step 5, choose to install on HDB (that's Drive D)  Be aware that you're wiping out everything on Drive D, so backup your music,movies, etc. before doing this.  I'm glad you're making the switch to Linux!:)

---

### Post by oilchangeguy on 2007-01-19
sorry i don't have the total answer for you. but you can do this, if you have the live cd go ahead and load it. once at the desktop select the icon to install. no changes to your setup will be made uless the install is allowed to finish. follow the prompts until you get to the part about how you want to set up ubuntu, and your present partitions should be shown. if you choose to let ubuntu resize your d: partition and leave c: alone.

---

### Post by l0k1_ on 2007-01-19
Wow thanks for the answers. I'll need to keep windows awhile while I migrate completly over but linux sounds awesome. I was wondering, I was testing the LiveCD this morning and for some reason I got this CPU error message after a reboot saying that my computer was in safe mode ... any experience with this. It asked me to go into the BIOS/setup/CMOS to do something ...

---

### Post by igknighted on 2007-01-19
> **sankarj12 said:**
> Yes, that is possible.  When installing Ubuntu, on step 5, choose to install on HDB (that's Drive D)  Be aware that you're wiping out everything on Drive D, so backup your music,movies, etc. before doing this.  I'm glad you're making the switch to Linux!:)

This is not entirely true^^^.  Linux needs its own partition (and you do have two partitions so I'm going to assume you understand the concept).  It also needs a swap partition (think windows pagefiles, but it has its own little partition to avoid the mess pagefiles cause).  You have two options, either you can move the data from your second partition (the movies and such) or you can resize on of the partitions to free up space.  Either way you will need to split one of them to make the swap partition.  Ubuntu can resize and set up your partition scheme automatically if you want as well.  The naming of the partitions as far as Ubuntu is concerned will either be hda# (where # is some number, probably 1-4, with hda1 being windows) if you have an IDE drive (big flat ribbon cable) or sda# if you have a serial ATA drive.  The reason I said not entirely true above is because hdb would be a physically separate disc, while different numbers refer to different partitions on the same disc.  If you are curious, hda refers to the master drive on the primary IDE channel.  hdb would be the slave on the primary channel.  hdc and hdd are likely your CD drives, and are the master/slave on the secondary IDE channel.  Be careful and review the partitions carefully before committing them to disc, because if there is one spot where you are most at risk of losing data this is it.

Good luck, it really isn't as intimidating as I just made it seem, go slow and make sure you know what you are doing at each step and you will be fine!

---

### Post by oilchangeguy on 2007-01-19
not sure about the error message. anyway can you post the complete message? also before you make the conversion, run the live cd to make sure all you your hardware performs as it should, if not search the forum for answers.

---

### Post by l0k1_ on 2007-01-19
Problem is I havn't gotten to try installing Ubuntu and the error message hasn't come up. I think what I'll do right now is delete the D partition completely and split that space into the swap and linux partitions. yes?

---

