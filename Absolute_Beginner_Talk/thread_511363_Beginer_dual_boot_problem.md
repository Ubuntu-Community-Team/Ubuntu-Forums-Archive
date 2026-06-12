---
title: "Beginer dual boot problem"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by The7Saint7 on 2007-07-27
Hello

First of all let me make sure you know that i  am an absolute beginer, i know nothing of linux and all its crasy comands, but i am willing to learn.

Now for my problem
I have Windows XP installed on my first SATA HD.
Then i went and installed ubuntu from a live CD on an other IDE harddrive.

When i boot my machine, XP starts wihtout a dual boot menu i was expecting
When i use the boot menu option of the BIOS, i choose the HD where i installed ubuntu. i do get a boot menu to select ubuntu or windows. Except the ubuntu choise gives me "Uanble to mount partion" error. But the "Windows XP" menu work just fine.

Please help! I dont mind re-installing Ubuntu, but i absolutly cant touch my Window instalation
Ho and in case this is somehow relevent, i installed Ubuntu on a Second Master IDE drive.

Thanks :)

---

### Post by FleetAdmiral74 on 2007-07-27
Using a LiveCD, the output of

```
sudo sfdisk -l
```

might be helpful

---

### Post by kyphi on 2007-07-27
First of all: Welcome to Linux and welcome to Ubuntu.

The problem you are experiencing is not Linux related but rather applies to computers in general.  SATA drives work via a controller on your motherboard and IDE drives work via a different controller on your motherboard.

Master and slave settings do not apply to SATA connected drives, only to IDE drives.

It is OK to have two optical drives running via IDE and configured to master and slave.

Your option is to either have 2 SATA HDs or 2 IDE HDs.  You could also fit an IDE to SATA adapter to your IDE drive.  You can get the adapter from your computer shop.

---

### Post by The7Saint7 on 2007-09-17
Ok so here is how i ended up doing it. 

I removed all my hard drives but left the SATA plugged in, installed Ubuntu on it.

then i removed the SATA drive and put back my IDE drive, installed windows.

Now i use the boot option when the computer starts if i wanna switch back to windows (wich is only for gaming, so not so often)

Leaving both or more HD in the computer during the installation seemed to mess things up a bit, a friend of mine said it had something to do with the MBR and i know nothing about that. But this way i finally got it to work so im happy :KS

---

