---
title: "ATI Restricted Driver Help"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by ElseIf on 2008-01-14
So, I decided to download new restricted drivers from the ATI website. (I already had the default ones installed) Yeah... bad idea. They're far worse than the old ones, and I can't figure out how to get rid of them and install the old ones again. (I've tried reinstall them and everything, but it keeps using the ones I got from the ATI website instead of the original ones)
If at all possible, I'd like to keep from reformatting, since I am doing my school on this computer.
I'm using an ATI X1600 PRO if that helps at all. 
Any help would be greatly appreciated!

EDIT: Heck yes!! I figured out the problem, thanks to your comment. On the ATI website, under the installation intructions it also gave me the command to uninstall them:

1. Launch the Terminal Application/Window and navigate to the /usr/share/ati folder.
2. Type in: "sudo sh ./fglrx-uninstall.sh" 

I then restarted, went to Menu > System > Administration > Restricted Drivers and reinstalled them from there. 

NOTE: It may help to open up Synaptic, go to Settings > Preferences > Files, and clear your cache there before you reinstall the restricted drivers. Only do that if you need to though.

Thanks a ton for your help man!

---

### Post by overdrank on 2008-01-14
> **ElseIf said:**
> So, I decided to download new restricted drivers from the ATI website. (I already had the default ones installed) Yeah... bad idea. They're far worse than the old ones, and I can't figure out how to get rid of them and install the old ones again. (I've tried reinstall them and everything, but it keeps using the ones I got from the ATI website instead of the original ones)
If at all possible, I'd like to keep from reformatting, since I am doing my school on this computer.
I'm using an ATI X1600 PRO if that helps at all. 
Any help would be greatly appreciated!

HI and how did you install the ati drivers? in the read me file there should be instruction on uninstall.

---

### Post by ElseIf on 2008-01-14
It was a .run file that installed it, and it did not include a readme file. 

Thanks for the reply!

---

