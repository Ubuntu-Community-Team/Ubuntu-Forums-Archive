---
title: "How can I exclude updating certain programs"
date: 2014-12-08
forum: Apple Hardware Users
---

### Post by jacatone on 2014-12-08
The only thing that'll install on my old Powerbook G4 is Lubuntu 12.04. Installing updates does improve performance but it always installs Firefox 34.00 which doesn't work well at all. Is there a Linux command I could use to prevent my original version of FF to remain untouched yet update everything else? Going through the Update Manager and trying to uncheck items is a pain.

---

### Post by tgalati4 on 2014-12-08
Try "[pinning]("https://help.ubuntu.com/community/PinningHowto")" the *firefox* package.  What specific problems are you having with firefox 34?

---

### Post by Dennis N on 2014-12-09
> Is there a Linux command I could use to prevent my original version of FF to remain untouched yet update everything else?
Instead of a command, you can use Synaptic Package Manager to do this. In Synaptic, it is called "Lock Version". Start Synaptic, highlight the package(s) in the right pane, then in the menu, use **Package > Lock Version**.

With this method, Update Manager will then not list that package for upgrading, but if you subsequently use apt-get update, I have noticed a package may still be shown for upgrade, even though locked through Synaptic. So you should not use apt-get for updates.

---

### Post by mörgæs on 2014-12-09
Uppdates are done for a reason, first of all to fix security bugs. Running an old browser sounds scary. 

Let's check the hardware and see if we can find something better than Lubuntu 12.04, which in itself is a security breach. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

