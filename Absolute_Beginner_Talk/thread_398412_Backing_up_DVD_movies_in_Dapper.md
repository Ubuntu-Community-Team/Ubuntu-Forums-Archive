---
title: "Backing up DVD movies in Dapper"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Gyrotwister on 2007-04-01
I've been runnung Dapper since its release but this is the first time I've tried to backup a DVD movie.  

DVDFab Decrypter seems to have run ok under WINE.  I know where the resulting files are.  

Which application should I use to burn to a blank DVD?

---

### Post by wargames on 2007-04-01
Open a terminal window and type:

growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video *name of directory containing your ripped dvd files*/

so if you ripped your dvd using DVDFab Decrypter to a directory called DVDBackup then type:

growisofs -speed 1 -dvd-comat -Z /dev/dvdrw -dvd-video DVDBackup/FullDisc/****/

**** is the dvd disc name that shows under the DVD Desktop icon when you insert a DVD disc. If I remember correctly DVDFab creates a subdirectory called FullDisc or something then creates your DVD disc name as a subdirectory then this DVD disc name directory contains the actual DVD files for burning.

Ex.
If your backing up Stargate dvd and the dvd disc name is Stargate, then DVDFab will create in your DVDBackup directory this:
DVDBackup/FullDisc/Stargate/

So type:
growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video DVDBackup/FullDisc/Stargate/

Make sure you know whether you're burning a single layer or dual layer DVD and have your blank in the drive before your type the above command. Sit back and wait for it to finish burning.

Hope this helps. :)

---

### Post by Marsolin on 2007-04-01
[K3b]("http://linuxappfinder.com/package/k3b") is a good DVD burner.

If you are interested in a native Linux app for backing up a DVD there are some good options. [K9Copy]("http://linuxappfinder.com/package/k9copy"), [Thoggen]("http://linuxappfinder.com/package/thoggen"), [XDVDShrink]("http://linuxappfinder.com/package/xdvdshrink"), and K3b by itself are all useful programs.

---

### Post by Gyrotwister on 2007-04-06
Sorry about the delay, I've had a busy week.  

Thanks wargames, that  worked once I managed to type the path correctly.  

growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video /home/username/DVDFab/FullDisc/*****/

Thankyou Marsolin,  I've installed Thoggen and am checking it out at the moment.

---

