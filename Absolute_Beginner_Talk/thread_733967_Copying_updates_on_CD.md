---
title: "Copying updates on CD"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by nandan on 2008-03-24
Hi
I am thinking of dumping my current computer (it has worked well for more than 5 years, bless it!) and go in for a newer one. I will certainly install Ubuntu on the new computer. However, it is very expensive to download all the updates again. Is it possible to save the current updates on my system and load them on to the new computer via CD/ other removable media? If yes, how does one do it?
Downloading 60-80 MBs of updates is not very feasible for me and I would like to avoid the ISP (Internet Service Provider) bills if I can.
Thanks a lot!

---

### Post by LowSky on 2008-03-24
you pay per Megabite? Are you on Dialup? Who's your ISP?

also a new version of Ubuntu comes out next month (4-24-08) what are you going to do then?

---

### Post by nandan on 2008-03-24
Thanks for the reply...
Well, I am on broadband (or what ISPs here in India like us to believe is broadband). I get speeds of around 25-30 kbps and I pay by time. 
The question about the new version is valid, and I am sort of hoping that I would be able to upgrade from the CD directly (not just a clean install, but an upgrade). If that doesn't work out, I will have to wait for the new CD and then have another partition and all that. (Highly avoidable).

Would appreciate your answer to my question...

Thanks!

---

### Post by nandan on 2008-03-25
Anybody home?? :)

---

### Post by plucky on 2008-03-25
@nandan,

> Is it possible to save the current updates on my system and load them on to the new computer via CD/ other removable media?


Have a read about [AptonCd](http://aptoncd.sourceforge.net/index.html) which is in the repositories.

Also all your downloaded **.deb** files are stored in ```
/var/cache/apt/archives
``` so all you need to do is copy them to a CD or USB Pendrive and reinstall.

The commands to reinstall are ```
cd /var/cache/apt/archives
sudo dpkg -i *.deb
```

I have not tried this so I don't know if it will work,but the APTonCD method does work.


Good Luck

---

### Post by nandan on 2008-03-26
Thanks! This should help...

Cheers
Nandan

> **plucky said:**
> @nandan,




Have a read about [AptonCd](http://aptoncd.sourceforge.net/index.html) which is in the repositories.

Also all your downloaded **.deb** files are stored in ```
/var/cache/apt/archives
``` so all you need to do is copy them to a CD or USB Pendrive and reinstall.

The commands to reinstall are ```
cd /var/cache/apt/archives
sudo dpkg -i *.deb
```

I have not tried this so I don't know if it will work,but the APTonCD method does work.


Good Luck

---

