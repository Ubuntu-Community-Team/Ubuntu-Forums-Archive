---
title: "Please help this newbie!"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by sjlandau on 2007-04-10
I recently installed the newest version of ubuntu and things were working fine.  Tonight, I downloaded the available updates and now I can no longer access my network.  I was able to set up my wireless card and connect before tonight's updates were installed.  I am very new to this and I need someone to walk me through.  I get a message that no network devices found.  Again, this was working perfectly before tonight's update.  Please help.

---

### Post by mi_were on 2007-04-10
> **sjlandau said:**
> I recently installed the newest version of ubuntu and things were working fine.  Tonight, I downloaded the available updates and now I can no longer access my network.  I was able to set up my wireless card and connect before tonight's updates were installed.  I am very new to this and I need someone to walk me through.  I get a message that no network devices found.  Again, this was working perfectly before tonight's update.  Please help.

Of the top of my head I would suggest reinstalling the wireless drivers. I am assuming you had to use ndiswrapper to install your driver. If this is not successfully please post the model of wireless card you are using and the version of Ubuntu you are running. Don't forget to quote the error you get.

---

### Post by sjlandau on 2007-04-10
Thanks for your help.  I am using a Netgear WG511T.  I don't think I used ndiswrapper.  I just installed from the live CD, set up my wireless network, and everything worked fine.  Could you please tell me how to reinstall the driver?  I am using the ubuntu 7.04.

---

### Post by sjlandau on 2007-04-11
bump...

I am hoping some of the experts can get me up and running again.  I am unable to do anything network related at this point.  This is very frustrating because it was working before I installed the recommended updates.  If someone could please tell me how to install the driver for a Netgear WG511T wireless card or how to completely re-install ubuntu to the same partitions, I would be very thankful.

---

### Post by Bachstelze on 2007-04-11
I guess it was an update of the kernel that broke your wireless. Normally, the old kernel should still be there for you to boot into.

---

### Post by rjfioravanti on 2007-04-11
This guy seems to be having the same problem

[http://ubuntuforums.org/showthread.php?t=403895&highlight=Netgear+WG511T](http://ubuntuforums.org/showthread.php?t=403895&highlight=Netgear+WG511T)

---

### Post by sjlandau on 2007-04-11
This was not a kernel update.  But, I did try booting into an earlier kernel but it still would give the message that no network devices found.  I received no errors on the update.

---

### Post by rjfioravanti on 2007-04-11
This guys fixed the problem by upgrading to feisty

[http://ubuntuforums.org/showthread.php?t=390422&highlight=Netgear+WG511T](http://ubuntuforums.org/showthread.php?t=390422&highlight=Netgear+WG511T)

---

### Post by sjlandau on 2007-04-11
I am using fiesty.  This was just a non-kernel update that I performed.  I had no problems with fiesty before this and had no problems with my wireless card before this.  My wireless card still works in windows.

---

### Post by Paul41 on 2007-04-11
> This guys fixed the problem by upgrading to feisty

sjlandau is using the ubuntu 7.04 so he/she is already using feisty.

---

### Post by rjfioravanti on 2007-04-11
try

sudo apt-get dist-upgrade

---

### Post by Paul41 on 2007-04-11
If dist-upgrade doesn't work try:

```
apt-get -f install
```

---

