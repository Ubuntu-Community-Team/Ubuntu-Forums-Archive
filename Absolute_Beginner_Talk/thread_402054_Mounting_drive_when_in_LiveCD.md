---
title: "Mounting drive when in LiveCD"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Makaze on 2007-04-05
I'm looking for some help. I am unable to boot into my Ubuntu do to me making a silly change to my xorg.conf . I was informed if I booted into the LiveCD and mounted my drive and restored a backup I should be ok. Unfortunately I don't know how to do this. 

Any help would be greatly appreciated.

---

### Post by taurus on 2007-04-05
Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 **/dev/hda1** /mnt/ubuntu
sudo cp /mnt/ubuntu/etc/X11/xorg.conf.backup /mnt/ubuntu/etc/X11/xorg.conf
```
1.  Assuming your / partition is /dev/hda1.
2.  Assuming your backup copy is called xorg.conf.backup.

---

### Post by xopher on 2007-04-05
If the only thing you've done is altered the xorg.conf, you don't need the LiveCD to fix it. If you remember what you changed of course..

When you get the X-server error, just press CTRL+ALT+F1, login, and run:
```
sudo nano -W /etc/X11/xorg.conf
```

There you can undo any changes you've made, and fix your X so it starts again.

When you've saved and quit nano, just do a:

```
sudo invoke-rc.d gdm restart
``` to restart X and be able to login graphically.

---

### Post by Makaze on 2007-04-05
ok well crud. I was successful in getting the xorg.conf fixed, but not I still cannot boot into ubuntu. All I originally did was make a change to the xorg.conf trying to fix a mouse setting. After that it would not boot into normal or recovery mode. 

Since the restore of xorg.conf I still cannot load ubuntu, but I can now get into recovery mode

any suggestions?

---

### Post by Makaze on 2007-04-06
I can get to the ubuntu loading screen (the one before the standard splash you see prior to logging in) and it gets anywhere from 4 bars to half way done and then I get a weird blue/green line across the center of the screen and it just locks up. I'm not sure what could be causing this since I've fixed the xorg.conf.

---

