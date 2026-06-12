---
title: "Upgrading to Feisty from live CD"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by CalvinChile on 2007-04-19
Hi,

Is it possible to upgrade Edgy to Feisty, using the Live CD but without having to install from scratch? The idea is to not loose the data and partions + applications.

Thanks
Calvin

---

### Post by aysiu on 2007-04-19
No.

You need the Alternate CD.

---

### Post by CalvinChile on 2007-04-19
Thanks.

Where I can get get more information on how to use the Alternate CD?

---

### Post by aysiu on 2007-04-19
> **CalvinChile said:**
> Thanks.

Where I can get get more information on how to use the Alternate CD?
I'm sure's a GUI way to do it, but here's how you'd do it from the terminal: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo apt-cdrom add
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by nhandler on 2007-04-19
Also, you could just update from edgy to feisty using the internet repositories instead of the cd. Just modify your sources.list file and replace every edgy with feisty.
```
sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y dist-upgrade
```

---

### Post by CalvinChile on 2007-04-19
Yeah, but I read that there is too much trafic now.... so that's why I prefer to download an ISO image through torrent and then use the Alternate CD as proposed.

---

### Post by kittyhawk63 on 2007-04-19
It is Thursday, 4:25pm on the west coast. I'm right now downloading the alternate install CD of Feisty somewhere between 280 and 350KB/s. That ain't bad. It will be downloaded in 38 minutes. I am using broadband on charter.com. Anyone else want to go this route, you may want to give it a try.
[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)
kh

---

