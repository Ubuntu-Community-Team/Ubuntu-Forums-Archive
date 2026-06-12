---
title: "Uninstall Deepin / Install Ubuntu"
date: 2017-07-07
forum: Apple Hardware Users
---

### Post by geogrammer on 2017-07-07
Hello Everyone!

Last night i installed Deepin on MacOS El-capitan, prior to this i had rEFInd installed to manage booting MacOS and Ubuntu(On an external HD).  I created a separate partition on the Mac HD and installed Deepin there via live cd. 

Now it all worked fine but on reboot the Deepin grub menu shows only deepin, no option to go to Mac OS. Today I tried installing Ubuntu but the live cd won't work. I get the same error "failure reading from sector 0x0 from cd0". I've try 2 different live cds, remade the live cd with rufus, unetbootin etc all to no avail.

IS there anyway of reinstalling the grub to show the Mac OS or uninstallin Deepin or installing Ubuntu from Deepin. Also would Deepin dissapear if i delete/format the partition on which it is installed.

Any other advice/assistance is highly appreciated

This is my first time here so i dont really know the posting rule, i'd be happy to spply further info on this issue if required

Thank you.

---

### Post by yancek on 2017-07-07
Have you tried running sudo update-grub from Deepin?

If this is a Mac, you are using EFI, correct?  Are you booting with rEFind or Grub?  I've never used a Mac so I'm not familiar with that software.
If you can boot Deepin, you can probably boot the Ubuntu iso from Grub if you have it available on the drive.

> Also would Deepin dissapear if i delete/format the partition on which it is installed.


Yes.

If you still can boot Deepin, do that and from a terminal run this command and post the output:  sudo efibootmgr

---

### Post by slickymaster on 2017-07-07
*Thread moved to **Apple Hardware Users**.*

---

### Post by geogrammer on 2017-07-07
Thank you for your help, i managed to install reFInd on Deepin and now i gave the whole options available on reboot - MacOS, Deepin, Ubuntu and recovery. Now i'll retry the live cd and see if i can get it to install

---

