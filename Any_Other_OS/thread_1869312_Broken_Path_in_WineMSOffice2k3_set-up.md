---
title: "Broken Path in Wine/MSOffice2k3 set-up"
date: 2011-10-25
forum: Any Other OS
---

### Post by Smithie on 2011-10-25
Hey folks:

Although I do most work in OO, I need to occasionally verify that the .doc formatting I'm sending to others does not have any formatting errors, and I use MSOffice2k3 for this.  I'm running Mint 11, and recently the Office component in wine has completely failed (although it worked briefly a while back).  I've tried uninstalling and re-installing wine 1.2 and 1.3, and deleting and re-installing Office 2k3 as best I could, but I can't ever seem to delete all the Office software before I try a new install, even after deleting the hidden .wine file as root.

The message I get after re-installing MSOffice is:

office2003pro install completed, but installed file /home/superdoof/.local/share/wineprefixes/office2003pro/dosdevices/c:/Program Files/Microsoft Office/Office11/WINWORD.EXE not found

After this, I receive an "There is no Windows program configured to open this type of file" error message when I try to open a document in office.  In addition, if I go to the "open with another application" tab, I find 7 different listings for "a wine application" and multiple versions of MS Excel (16), Outlook (9), Powerpoint (7) and Word (6), but none of them seem to work.

Thanks for the help!!

---

### Post by oldtimer7777 on 2011-10-25
I think you will have better results if you install it with PlayOnLinux. It is about half the way down this list:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

PlayOnLinux will work on Mint, as long as it isn't pure debian. Otherwise you will need to refer to the PlayOnLinux web site for the proper command line installation instructions. 

Also you can run Office in Window Virtualbox 4.1 where this problem won' t happen. I do it that way instead.

> **Smithie said:**
> Hey folks:

Although I do most work in OO, I need to occasionally verify that the .doc formatting I'm sending to others does not have any formatting errors, and I use MSOffice2k3 for this.  I'm running Mint 11, and recently the Office component in wine has completely failed (although it worked briefly a while back).  I've tried uninstalling and re-installing wine 1.2 and 1.3, and deleting and re-installing Office 2k3 as best I could, but I can't ever seem to delete all the Office software before I try a new install, even after deleting the hidden .wine file as root.

The message I get after re-installing MSOffice is:

office2003pro install completed, but installed file /home/superdoof/.local/share/wineprefixes/office2003pro/dosdevices/c:/Program Files/Microsoft Office/Office11/WINWORD.EXE not found

After this, I receive an "There is no Windows program configured to open this type of file" error message when I try to open a document in office.  In addition, if I go to the "open with another application" tab, I find 7 different listings for "a wine application" and multiple versions of MS Excel (16), Outlook (9), Powerpoint (7) and Word (6), but none of them seem to work.

Thanks for the help!!

---

### Post by Perfect Storm on 2011-10-26
Moved to Other OS/Distro Talk.

---

