---
title: "how to uninstall an application completely"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by kamumosp on 2007-12-25
Hi all,
How to uninstall an application completely (including settings) under ubuntu.
I tried sudo apt-get remove and sudo aptitude remove.

Thanks
kam

---

### Post by r4ik on 2007-12-25
Try,

apt-get remove --purge

---

### Post by overdrank on 2007-12-25
> **kamumosp said:**
> Hi all,
How to uninstall an application completely (including settings) under ubuntu.
I tried sudo apt-get remove and sudo aptitude remove.

Thanks
kam

Hi and you can try
```
sudo apt-get remove "package name"  --purge
```

Edit to late

---

### Post by kamumosp on 2007-12-25
Hi Thanks for your reply...
Let me be more specific about my problem.
I installed VLC Media Player and downloaded few skins for it. Later I changed few settings related to skins. 
How it opens VLC is that, it opens a skin and also normal vlc default media player with no options enabled. I can not open an existing video file using skin interface.
I tried un-installing vlc media player using apt-get and aptitude with --purge option. also i removed saved debian packages for vlc player in /var/cache/apt/archives directory.
but when i reinstall vlc media player, all the previous settings are preserved.
Can somebody please help me how to remove all the previous settings.

Thanks & Regards
Kam

---

### Post by zvacet on 2007-12-25
In nautilus>home dorectory>view<show hodden files>.vlc .Delete that folder and reinstall VLC

---

### Post by kamumosp on 2007-12-25
Thanks a lot zvacet.... it worked...

kam

---

### Post by vishzilla on 2007-12-25
> **kamumosp said:**
> Thanks a lot zvacet.... it worked...

kam

you can also try
```
sudo apt-get autoremove 'packagename'
```

---

