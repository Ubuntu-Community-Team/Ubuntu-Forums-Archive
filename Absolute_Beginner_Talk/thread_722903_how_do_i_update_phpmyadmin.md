---
title: "how do i update phpmyadmin?"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by thepiston on 2008-03-12
I used apt-get to install it, but it's 2.10 - isn't that old?  I just did a sudo update and upgrade, btu still 2.10...

---

### Post by scragar on 2008-03-12
> phpMyAdmin 2.11.5 is releasedlatest is 2.11, so it's not too far out of date.

you can just download the latest version and copy your config file over...
[http://www.phpmyadmin.net/home_page/downloads.php](http://www.phpmyadmin.net/home_page/downloads.php)

---

### Post by thepiston on 2008-03-12
yeah, i can do that - but in the future is there a different way to update phpmyadmin, or just use the sudo update/upgrade?

---

### Post by scragar on 2008-03-12
unfortunatly the package manager doesn't always have the latest version of the code available.


[http://packages.ubuntu.com/hardy/phpmyadmin](http://packages.ubuntu.com/hardy/phpmyadmin) <-- the hardy package has the same dependencies but's 2.11.3 so that's very close to the latest version. download link for .deb installer is at the bottom of the page.

---

### Post by Hospadar on 2008-03-13
If you go to System->Administration->Software Sources, and check "proposed updates" and "backports" (backports are packages from hardy that you can install in gutsy) when you update (either when it prompts you, or when you run "sudo apt-get update") you will probably get a ton more upgrades you can install.  If you are looking for newer versions without having to manually pluck them out of the hardy repos, this is a good option to try

---

