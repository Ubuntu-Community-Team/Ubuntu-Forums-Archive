---
title: "KDE and Gnome?"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by zyx on 2007-03-13
hi,

I use adept to remove some programs, now I lose kde and gnome, only Xfce left! I use adept to set kde and gnome again, however, they do not come back! Does some one help me to help me? and tell what do I need for kde and gnome?
Thanks!

---

### Post by Kateikyoushi on 2007-03-13
Did you install the full ubuntu-desktop and kubuntu-desktop ?
If so copy these to terminal to reinstall them.

```
sudo aptitude install ubuntu-desktop
sudo aptitude install kubuntu-desktop
```

If you used a slimmer kde then

```
sudo aptitude install kde-core
```

---

### Post by zyx on 2007-03-13
Thanks for your reply!
however, I run the command you give me, I got the error as follows:
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How do I fix these? Thanks!

---

### Post by mozkaynak on 2007-03-13
This message is telling you that there is a lock file preventing your package manager from getting exclusive access.  Package managers create these lock files when they starts and if they crash, you reboot, your power goes out, etc, before they are completed, the lock file remains and the next manager believes another manager is already running.Use the following to delete the lock files, but make sure another copy of a package manager isn't running first.sudo rm /var/lib/dpkg/lock sudo rm /var/cache/apt/archives/lockGood luck!

---

### Post by zyx on 2007-03-13
Thank you very much for your reply!
I set the kde and gnome, however, my login environment do not have choice to choose kde or gnome! login environment is only Debian Gnu/Linux, when I login it is Xfce environment! What do I miss to set up? Does anyone give me some clue? Thanks!

---

