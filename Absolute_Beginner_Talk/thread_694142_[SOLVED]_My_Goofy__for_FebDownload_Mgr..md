---
title: "[SOLVED] My Goofy ? for Feb/Download Mgr."
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2008-02-11
Every time I boot/reboot Abdominal Primate the DL Mgr. insists that I install 15 megs of KDE files. I don't, and never will use Kubuntu, therfore I have absolutely no use for said files. So, the question is; How do I tell this thing to go away and leave me alone?

Many thanks,

Jon

---

### Post by taurus on 2008-02-11
You don't have to install Kubuntu to have KDE on your machine.  Did you install any KDE app at all?

---

### Post by Romin-1 on 2008-02-11
I got the Gutsy CD in the mail and made a clean install on a standalone Linux PC. I believe the entire KDE/Kubuntu package came with it as there is a load of stuff in add/remove.

 As I don't use any 'K' progs I can see no reason to keep downloading updates to a system I don't need. Just chewing up disc space.

Jon

---

### Post by PeterJS on 2008-02-11
Install the updates you want then with update manager, this should leave only the offending packages as upgradeable. Open synaptic up, in the filters you can use Status > Upgradeable and that will list all the packages that have upgrades available (ie the kde packages you don't want), and then mark them all for uninstallation. I'd bet that it'll pop up wanting to uninstall additional packages you do use that you didn't know were based on KDE.

---

### Post by Romin-1 on 2008-02-11
Thanks for all your replies guys.

Guess what I'm really looking for is a way to stop it from automatically looking for upgrades. Just look when I tell it to.

Have a happy,

Jon

---

### Post by PeterJS on 2008-02-11
You can disable automatic updates under System > Administration > Software Sources > Updates.

---

### Post by nikoPSK on 2008-02-11
> **PeterJS said:**
> You can disable automatic updates under System > Administration > Software Sources > Updates.

but not recommended.

---

### Post by lswest on 2008-02-12
in the synaptics package manager you can choose "lock to current version" on the packages, so they stop being updated, but this isn't recommened, because eventually they'll need to be updated.

highlight the packages and go to package-->lock version

---

