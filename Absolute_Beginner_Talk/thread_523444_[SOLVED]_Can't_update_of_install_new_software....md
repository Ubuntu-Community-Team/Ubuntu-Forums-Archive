---
title: "[SOLVED] Can't update of install new software...?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-11
hi,

i can't update or install new software, firefox is working...any ideas?

thanks

---

### Post by overdrank on 2007-08-11
> **Hopeless said:**
> hi,

i can't update or install new software, firefox is working...any ideas?

thanks

Hi could you give a little more detail of what you are trying to install?

---

### Post by Hopeless on 2007-08-11
i went to install amule and got nothing... so i went to update manager and it said i got 13 files but get error or Hit on each one it says..

he repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://kr.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://kr.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)
[http://kr.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2](http://kr.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2)
[http://kr.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2](http://kr.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2)
[http://kr.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2](http://kr.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2)
[http://kr.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2](http://kr.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2)
[http://kr.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://kr.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)
[http://kr.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2](http://kr.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2)
[http://kr.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2](http://kr.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2)

is the Ubuntu network working?

Ahhh... looks like the server might be down in Korea... [http://kr.archive.ubuntu.com/](http://kr.archive.ubuntu.com/) gets nothing...should i wait or can i change servers?

---

### Post by Paul133 on 2007-08-11
I assume you mean you're trying ```
 sudo aptitude update
``` or sudo apt-get install [program] Are you sure the program is in the repositories you have enabled?

---

### Post by aysiu on 2007-08-11
To install *new* software, use Synaptic Package Manager. This link will help orient you to that:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

Security *updates* will arrive periodically (the update notifier will prompt you from the notification area/system tray).

Otherwise, each release of Ubuntu is frozen version-wise. Ubuntu 6.06 will never get Firefox 2.0. Ubuntu 7.04 will never get Firefox 3.0. If you want updated versions of the software, wait six months until the next Ubuntu release.

---

### Post by Hopeless on 2007-08-11
the server is down in Korea...went to System >> Admin >> Software Sources and changed to US...trying now...

---

### Post by Hopeless on 2007-08-11
Working now !!!

thanks guys..!!

Can someone tell the guys over in Korea that the Korean Ubuntu server is down????

---

