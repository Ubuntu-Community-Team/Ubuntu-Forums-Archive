---
title: "Backup Video Settings to CD. File Recommendations Please?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by RhubarbnCustard on 2007-07-19
Hi - I've been trying out 7.04 (Feisty Dawn?) for a few days and now I want to purge Windows from my machine and go with a clean Ubuntu install. I had a few problems getting the screen resolution I was used to (Voodoo3, IBM G54 Mon., on a hybrid IBM 300PL (I 'found' it!)), but managed to get it working ok through reading other peoples posts and just shutting my eyes and trying things.

Now I'm wondering if I can just backup xconf.org to a cd and then plop it back in /etc/x11/ after the reinstall and hey-presto I don't have to fiddle anymore? It's not that simple, is it? I've been using *cough*windows for 20 years and nothing like this has ever been simple ;-)

Also, does anyone recommend a 'best' way to prepare/make use of dual drives (I should put the swap on a separate drive to the master, right?) Is that simple enough to do using the Ubuntu install utility? I'm going to dban both disks first.

Lastly - thanks - I actually feel I'm joining a community that isn't just about cash!!!!!! I could kiss you all.

---

### Post by tgm4883 on 2007-07-19
> **RhubarbnCustard said:**
> Hi - I've been trying out 7.04 (Feisty Dawn?) for a few days and now I want to purge Windows from my machine and go with a clean Ubuntu install. I had a few problems getting the screen resolution I was used to (Voodoo3, IBM G54 Mon., on a hybrid IBM 300PL (I 'found' it!)), but managed to get it working ok through reading other peoples posts and just shutting my eyes and trying things.

Now I'm wondering if I can just backup xconf.org to a cd and then plop it back in /etc/x11/ after the reinstall and hey-presto I don't have to fiddle anymore? It's not that simple, is it? I've been using *cough*windows for 20 years and nothing like this has ever been simple ;-)

Also, does anyone recommend a 'best' way to prepare/make use of dual drives (I should put the swap on a separate drive to the master, right?) Is that simple enough to do using the Ubuntu install utility? I'm going to dban both disks first.

Lastly - thanks - I actually feel I'm joining a community that isn't just about cash!!!!!! I could kiss you all.

Well you will probably have to install your graphics card drivers and the file is /etc/X11/xorg.conf

If you want to keep all your other settings, most are in your home directory in hidden folders.

And a common way to partition is to have your /home be a separate partition.  That way through upgrades and reinstalls (and distro changes should that occur)  Your files and settings will remain.

---

### Post by RhubarbnCustard on 2007-07-19
Thanks tgm4883

---

