---
title: "edit text file from command prompt"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Foudre on 2007-02-27
After changing my fstab to add a drive, for some stupid reason that killed my xserver, and now i can't get it working again, even dpkg-reconfigure xserver-xorg won't restore it, how do i edit a text file from the command prompt so i can restore the fstab, cause i get a system beep when it says loading file systems and then after the phase of loading stuff it goes to comman prompt login after i log in it flashes the image of kubuntu and freezes, i can still hit ctrl+alt+f1 to do stuff, so, why the hell did that kill my xserver or what ever its doing?

---

### Post by ieee488 on 2007-02-27
*vi* editor is what I use.

---

### Post by highneko on 2007-02-27
Nano's good too maybe better. n_n

---

### Post by mikewhatever on 2007-02-27
sudo nano /FullPathtoFile

you may want to back up the files you edit first, for example,

cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

It might be a good idea to always do it prior to editing.

---

### Post by actuary286 on 2007-02-27
vi is a very powerful editor, but can be difficult to use and is probably overkill for editing your fstab. I use nano and can recommend it very highly. To edit a file in nano you type:

```
nano *filename*
```

To edit your fstab you will need root privileges, so type:

```
sudo nano /etc/fstab
```

In nano all the common commands are listed at the bottom of the screen. The meta key (^) is usually the CTRL key, so saving a file is CTRL-O and exiting nano is CTRL-X.

Hope this helps.

---

