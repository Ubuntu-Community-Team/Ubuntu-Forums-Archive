---
title: "Gutsy and ethernet"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Roaster on 2007-09-24
Hello all, I running the latest Gutsy, all updates, everything seems to be great but I have to manually choose the ethernet port, because Gutsy chooses the one I do not use(it's a pci router). I guess the best way to resolve this is to remove the pci card, but maybe some one out there can tell me how to just disable it so that Gutsy does not 'see' it. Hope so, and thanks. Best to all,

---

### Post by djchandler on 2007-09-24
> **Roaster said:**
> Hello all, I running the latest Gutsy, all updates, everything seems to be great but I have to manually choose the ethernet port, because Gutsy chooses the one I do not use(it's a pci router). I guess the best way to resolve this is to remove the pci card, but maybe some one out there can tell me how to just disable it so that Gutsy does not 'see' it. Hope so, and thanks. Best to all,

In Feisty, all you would need to do is place a minus sign in front of the interface you don't want in Network Settings. Just leave the check in front of the hardware you wish to use. This should be saved with your user settings, I would think. If this got changed in gutsy, you may need to post this in the Development (Gutsy Gibbon) forum under Other Community Discussions instead of Beginners.

DJ

---

### Post by Roaster on 2007-09-24
> **djchandler said:**
> In Feisty, all you would need to do is place a minus sign in front of the interface you don't want in Network Settings. Just leave the check in front of the hardware you wish to use. This should be saved with your user settings, I would think. If this got changed in gutsy, you may need to post this in the Development (Gutsy Gibbon) forum under Other Community Discussions instead of Beginners.

DJ

Thanks, yeah it works fine with Feisty but on Gutsy each time I boot it selects the pci card(Realtec router card). I'll go there and see what I find, Regards

---

### Post by Roaster on 2007-09-24
Can't post there so I'll live with it maybe fixed in final release.

---

### Post by Kilz on 2007-09-24
> **Roaster said:**
> Can't post there so I'll live with it maybe fixed in final release.

Every member of this forum can post in the development section. If you choose to install a development version you should as a good member of this community report all bugs. Not just in the forums [but on launchpad.]("https://bugs.launchpad.net/"). Waiting for others to do it results in bugs not fixed and lowers the quality of the software you and everyone else uses.

---

