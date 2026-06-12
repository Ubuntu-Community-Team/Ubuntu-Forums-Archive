---
title: "CD/DVD drive won't stop or eject after failed burn attempt"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by dhughes on 2007-03-12
I was trying to burn an .iso using GNOMEBaker but it failed, now the CD is spinning away even after I closed the Baker app. It won't stop and it won't eject.

 Of course I tried pushing the eject button
 I tried right clicking the DVD/CD-ROM drive icon 
 umount /dev/hdc doens't work
 umount /media/cdrom0 doesn't work either

 I tried to find what process it is but I can't, I thought could kill it in Terminal but I can't let it keep spinning I can't wait I guess I will have to log out or reboot I don't want to damage my DVD drive.

**edit:** I had to reboot, logging out didn't stop it. Even when the system was going down the drive was still spinning away I thought it may stop when everything was being shutdown getting ready for the reboot. Only when the power was interrupted during the reboot is when it stopped.

---

### Post by jdfreshwater on 2007-03-13
I believe you can always try

*sudo eject /dev/hdc*

Only root can eject a disc.  This should work when it will not eject.

---

### Post by dhughes on 2007-03-23
No that doesn't work, I even tried the command umount for /dev/hdc and also umount for /media/cdrom0 but I get a message that says the drive is not even mounted.

 This is my #1 problem with Ubuntu, I can't seem to get this solved and it seems to be common but there isn't any solution.

 I had to physically unplug my cd-rom drive, I have the case open most of the time since   I am always doing something in it.

 The application I was using was Brasero and not GnomeBaker, I was trying to make a bootable disk on a CD but the Cd was rejected as being bad, which it wasn't. That's when it wouldn't eject it.

---

### Post by kostkon on 2007-03-23
It's strange but also it happened to me once when I had a bad burn (99% are successful burns, I have a good ASUS cd-rw).  Anyway, when it happened I also had to reboot.

In general, the worst that I get from the cd-rw is the *device is busy* message when i try to eject a CD. Loging out and login back in, it solves the problem and I can eject the CD.

---

### Post by FaceLeg on 2007-04-24
I am installing Half Life 2 with Wine, when it requests CD2, I find I am unable to eject the CD in order to swap them... Restarting allows me to, but this is no help as I have to start the installation all over again...

I have tried this in a console also:

```
sudo eject
```

Which gets this:

```
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
eject: unmount of `/media/cdrom0' failed
```

Other variants I have tried are: 

```
sudo eject /media/cdrom0
sudo umount /dev/cdrom
```

Which all get similar output.

---

### Post by FaceLeg on 2007-04-24
Found the answer:

```
sudo umount /media/cdrom0 -l
```

Then:

```
sudo eject
```

I was missing the -l ... though what it stands for I have no idea...

Of course, to get the next CD recognised:

```
sudo mount /dev/cdrom /media/cdrom0
```

In case you were wondering, I got this from this thread:

[http://ubuntuforums.org/showthread.php?p=2484355](http://ubuntuforums.org/showthread.php?p=2484355)

---

