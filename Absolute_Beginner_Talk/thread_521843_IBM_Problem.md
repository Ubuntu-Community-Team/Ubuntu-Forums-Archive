---
title: "IBM Problem"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by bob along on 2007-08-09
Both Ubuntu and Xubuntu won't install to the hard drive an IBM 831921U. They get to the time zone selection screen and then won't move forward from there. I double click on New York but it will not accept the selection and continue..

---

### Post by p_quarles on 2007-08-09
While I seriously doubt this has anything to do with the time zone you want to select, you *could* try selecting a different city in the same time zone -- Cleveland or something.

That said, I imagine this is a problem with what comes next, which I believe is partitioning (correct me if I'm wrong, anyone). The best advice I can give you is to try to install using the "alternate" disk, which is a text-mode installer. It solves a lot of problems that people encounter while using the live disk.

You'll have to download again to get it, unfortunately. When you're selecting the version to download, make sure you check the "alternate" checkbox.

---

### Post by bob along on 2007-08-09
Thanks, I will try the alternative disk. I think I found one problem. When I am running the live disk the screen size looks fine but once the installation starts it looks like the image is too big for the screen and I lose the bottom couple of inches that has the forward and back buttons on. I managed to get past this screen but got stuck again at the partition screen.

---

### Post by p_quarles on 2007-08-09
> **bob along said:**
> Thanks, I will try the alternative disk. I think I found one problem. When I am running the live disk the screen size looks fine but once the installation starts it looks like the image is too big for the screen and I lose the bottom couple of inches that has the forward and back buttons on. I managed to get past this screen but got stuck again at the partition screen.
Uh-huh. The alternate cd will definitely help then. The resolution problem is likely due to the fact that the live CD is using the wrong driver for your video card. 

After installing, too, you may find that you will need to manually configure the video card. If the card is an Intel, it'll be a snap to fix. If it's nVidia, it will require getting the Linux driver from them. If it's ATI, it could be more of a pain, but it's doable.

---

