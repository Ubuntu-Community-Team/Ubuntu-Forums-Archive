---
title: "Amarok won't retain collection"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by VortexSpin on 2008-01-14
I have a pretty big music collection, so it's stored on an NTFS external hard drive.  I go to Tools -> Configure Amarok, click the collection tab, find my external hard drive in the media folder of root, and select it.  Then I click the Rescan Collection button, and it adds all my music.  Problem is that when I exit Amarok and go back in, it's all gone and my hard drive is no longer selected to be monitored.  What gives?  I don't want to rebuild my collection every time I use Amarok.

---

### Post by dgray_from_dc on 2008-01-14
I've had similar problems.  I think it has something to do with the fact that it's an external drive.  Copy some of your music locally add it to your collection, and test to see whether or not you encounter the same problem.  Please post your results if you decide to do it.  I'd be interested in knowing as I'm currently rebuilding my whole home network and can't test it myself.

---

### Post by wlesguillier on 2008-01-14
I'm having the same problem. I'm under kubuntu 7.10 and I'm having a lot of trouble with my usb hard drive since I upgraded from 7.04.

A few problems I'm having now and didn't have before:
[LIST]
[*]The HD doesn't appear on the desktop at startup, I need to browse it in Konkeror first only then it appears on the desktop and in other applications (including amarok).
[*]The pc is really slow when using the HD especially while and after doing things like building amarok's collection.
[*]amarok's collection disappears everytime I restart the computer...
[*]amarok hangs if dealing with too many files while building collection
[/LIST]

Any solution appreciated.

---

### Post by thelatinist on 2008-01-14
When your external HD is mounted, is it always at the same mountpoint?  Have you tried temporarily setting a local folder for your collection and seeing if that setting is carried across amarok sessions?     Have you tried just rescanning your collection?

---

### Post by wlesguillier on 2008-01-14
Some mp3 I have on my local hard drive are well detected by amarok and present over different sessions, those on the HD are not.

With 7.04 I never tweaked any mount configuration, it just worked. The HD is always plugged on my laptop and was considered as a removable media (automatically mounted?) in /media/<mount-name>. In 7.10 if I mouse over the HD icon the type given is "Unmounted removable medium".

The mount-name is always the same. 7.10 also mounts the HD in /media/<mount-name>, Amarok and Picasa for example use this path to designate the HD but I saw that Dolphin uses sdb1 instead of the mount-name. I never saw sdb1 in 7.04, would there be a name conflict with this?

Is it a good thing to mount the drive with fstab or should it work without it?

---

### Post by thelatinist on 2008-01-14
I wonder if Amarok is not preserving this setting because it is a removable device.  If this external HD is always plugged in, it might be a good idea to mount it using fstab.

1) Use the following command to create a mount point for this drive (change *mountpoint* to a name that is not already in use and will be easy to recognize and remember):

```
sudo mkdir /media/*mountpoint*
```

2) Use the following command to back a back up of your fstab file in case something goes wrong:

```
sudo cp /etc/fstab /etc/fstab.bak
```

3) Use the following command to open fstab for editing:

```
sudo gedit /etc/fstab
```

Add one of the following line (depending on filesystem type) to your fstab to cause it to automatically mount (replace *sda#* with the name of the device you wish to mount and *mountpoint* with the mountpoint you created in step 1):

**For ext3:**
```

/dev/*sda#* /media/*mountpoint* ext3 defaults,errors=remount-ro 0 1
```

**For NTFS:**
```
/dev/*sda#* /media/*mountpoint* ntfs-3g defaults,nls=utf8,umask222 0 0
```

**For Fat32 or Fat16:**
```
/dev/*sda#* /media/*mountpoint* vfat user,utf8,fmask=0111,dmask=0000 0 0
```

**For reiserfs:**
```
/dev/*sda#* /media/*mountpoint* reiserfs nodev,nosuid 0 0
```

---

### Post by wlesguillier on 2008-01-14
Thanks for your answer, that's really cool to have such a support.

Before going into the fstab stuff I looked into the settings to see if something was wrong and found a quick solution: in System Settings -> Advanced -> Disk & Filesystems I edited my HD properties and checked "Enabled at startup". It seemed to have made the trick.

Now the drive is mounted automatically at startup, as it was before in 7.04, amarok is started after that and therefore detects the drive and loads the collection properly.

As for me the problem is solved.

---

