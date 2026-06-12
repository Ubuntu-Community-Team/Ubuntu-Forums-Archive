---
title: "I want to go back to Dapper - A couple questions"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by GotGamble on 2006-11-02
I got a bit ahead of myself and upgraded to Edgy to quickly methinks. Since I am relatively new to *nix , and depend a lot on people who have 'been there, done that' for advice, and quite a few of the installed and working applications I had under Dapper do not work, or do not work properly under Edgy, I think I need to go back to Dapper.

**Questions: **

Is there a 'downgrade' ability to uninstall Edgy? 

Currently I dual boot Xp and Ubuntu, will I have problems with GRUB and the selection for my Xp install if I just wipe the Ubuntu partitions and reinstall on those?

Does the Alternate install CD install the same basic packages by default as the Live CD install, if I choose all the same options during the setup? 

Does the Alternative install CD allow me to auto-partition like the Live CD install? I don't want to have to do the Live CD boot/install/reboot, I would prefer to just do a straight install, but I don't want to risk losing my Xp installation by doing something wrong and mess up my ability to dual-boot by manually editing the partition table during an install.

Any help is appreciated.](*,)

---

### Post by Joe_CoT on 2006-11-02
There's no "downgrade" ability to my knowledge, but you can certainly reinstall dapper.

The alternative install cd and the live cd both install the same packages, assuming you use the default installation type.

To reinstall ubuntu and not lose your windows drive, select manually edit your partitions, select the ubuntu partition, select "yes, format it", and then set that as your root. That will reinstall on that partition, and leave your windows partition untouched (the next screen will list all partitions being formatted and have you confirm, so you can't lose your windows partition by accident). The Grub installation should automatically detect your Windows install and add that to the menu.

---

### Post by GotGamble on 2006-11-02
Cool, thanks a bunch.

---

