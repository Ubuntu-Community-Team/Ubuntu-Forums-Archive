---
title: "Please Help with SATA drive problem"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by fillyfloater on 2007-05-13
I'm new to ubuntu, played with Mandrake years ago. Just had to redo my computer, new MB, CPu etc so I figured Id scrap Windows and try Linux. I have an ASUS M2V MB with 1gb Corsair pc800 ram, nvidia pcie card (cheap), amd 64x2 3800+ and I bought a seagate 320gb sata hdd. Which is my problem, I can't get Ubuntu to recognize the drive to install onto it.  For Windows XP I had to create a floppy and do the F6 during install, does Ubuntu have something similar to that? Please help, i'm sick of shelling out $100s to Bill Gates every few years for new OSs.:confused:

---

### Post by taurus on 2007-05-13
Are you able to boot your machine with the LiveCD?  And if you do, open a terminal, Applications -> Accessories -> Terminal, and post the output of this command here.

```
sudo fdisk -l
```

---

### Post by overdrank on 2007-05-13
> **fillyfloater said:**
> I'm new to ubuntu, played with Mandrake years ago. Just had to redo my computer, new MB, CPu etc so I figured Id scrap Windows and try Linux. I have an ASUS M2V MB with 1gb Corsair pc800 ram, nvidia pcie card (cheap), amd 64x2 3800+ and I bought a seagate 320gb sata hdd. Which is my problem, I can't get Ubuntu to recognize the drive to install onto it.  For Windows XP I had to create a floppy and do the F6 during install, does Ubuntu have something similar to that? Please help, i'm sick of shelling out $100s to Bill Gates every few years for new OSs.:confused:

Hi a quick search of the forums for your mb suggest the alternate cd.
[http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/)
find the alternate cd and try that download and make sure to follow the how to on the burn
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Good luck !:)

---

