---
title: "Life after ATI fix"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by kcmoblueeyes on 2007-06-04
I did the ATI fix posted by Mike.  Now I get the following error message: "Failed to start the X server" The log file really doesn't show anything.  If I say no to see error message, I get the message that the x server is disabled and to restart GBM when it is configured correctly.

How to I restart X server?

Thanks
Randy

---

### Post by Bluecircle on 2007-06-04
Try:

```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

```

When reconfiguring X, select the correct driver. You may need to use apt to download the correct video driver

```

sudo apt-get install xserver-xorg-video-[correct driver]

```

Edit: the standard ati driver is ati, so do

```

sudo apt-get install xserver-xorg-video-ati
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

```

---

### Post by Crafty Kisses on 2007-06-04
I don't know if you backed up your Xorg.conf file. If you don't know how to backup the Xorg.conf file. Open up terminal and type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
```
After you have done that, you can recover your Xorg.conf file by going in the terminal and typing:
```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```
Hope this helps. :p Any other questions please post back.

---

### Post by Bluecircle on 2007-06-04
> **Codename said:**
> I don't know if you backed up your Xorg.conf file. If you don't know how to backup the Xorg.conf file. Open up terminal and type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
```
After you have done that, you can recover your Xorg.conf file by going in the terminal and typing:
```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```
Hope this helps. :p Any other questions please post back.

When reconfiguring x, it automatically makes a backup copy when changes are made.

---

