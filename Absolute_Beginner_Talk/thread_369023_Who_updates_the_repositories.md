---
title: "Who updates the repositories?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Talon2 on 2007-02-24
A new version of BOINC was released recently but the repositories still contain the old v5.4.  This new version contains some new features I really need in order to go full speed again.

As I'm still learning the os my attempt to download and install the released version (non-deb) has been unsuccessful.  Maybe someday I can help with this os but while I'm coming up to speed I need help.  How is the best way to handle this issue?

Thanks.

---

### Post by yabbadabbadont on 2007-02-24
Read through the information available here: [http://www.ubuntuforums.org/forumdisplay.php?f=47](http://www.ubuntuforums.org/forumdisplay.php?f=47)

If the new version meets the requirements listed there, then you can put in a request for it there too.  :)

---

### Post by Talon2 on 2007-02-24
> **yabbadabbadont said:**
> Read through the information available here: [http://www.ubuntuforums.org/forumdisplay.php?f=47](http://www.ubuntuforums.org/forumdisplay.php?f=47)

If the new version meets the requirements listed there, then you can put in a request for it there too.  :)

Thanks for the info but that was confusing.  I followed the link to find a msg that says to use Launchpad.  I followed that link... things didn't get better.

While I only have a few months experience learning Ubuntu I have over 30 years of experience using and programming computers.  I can only image how frustrating it can be for your average windows user.  It appears to me that what we have here is a widely used application where a badly needed update has been released but end users are being held hostage until "someone" gets around to packaging it.  

I've actually seen folks on here question users who vent about how difficult it can be to install software.  To these people who question how difficult it is, I say wakeup.  I don't call this freedom and it certainly isn't easy; it is more like being held hostage.

If I was to the point that I could package and test this release I would.  Hopefully I will be someday but this is not the long term solution to the lack of a common standard that is easy for developers and users to follow.  It should not matter who releases a new app, any user should be able to install it immediately on any version of Linux.  United we stand, divided we fall.

Here is the link to the new version of BOINC:

[http://boinc.berkeley.edu/download.php](http://boinc.berkeley.edu/download.php)

Thanks for allowing me to vent.

---

### Post by PriceChild on 2007-02-24
Ubuntu uses a freezed release system.

Once each 6 month development cycle is over, the distribution is frozen forever. The only exclusions that are made are critical bug fixes and security patches.

This allows us to keep a release rock solid. If you want then you can always install the application reasonably easily yourself, or enable the backports repository which contains updates of a small number of packages.

See [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) for how to install anything.

---

### Post by nhandler on 2007-02-24
If the file your are trying to install is a .rpm file, use alien to convert it to .deb. Alien is in the ubuntu repositories. If the file is in a .tar.gz file, right click it, and extract it. Then, open up the folder, and view the readme for info on how to install it. Most likely, it involves:
cd ~/Desktop/FOLDERNAME
./configure
make
sudo make install

---

### Post by PriceChild on 2007-02-24
> **Cheater said:**
> If the file your are trying to install is a .rpm file, use alien to convert it to .deb. Alien is in the ubuntu repositories. If the file is in a .tar.gz file, right click it, and extract it. Then, open up the folder, and view the readme for info on how to install it. Most likely, it involves:
cd ~/Desktop/FOLDERNAME
./configure
make
sudo make installalien can make bad things happen... IMO compiling from source is always preferable, where debs beat them all.

---

