---
title: "Open Office Uninstall Help"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by willbur on 2007-01-20
Hi all

I'd like to completely remove Open Office from my Edgy installation. Using the standard applications - add/remove dialog warns me that other things depend on OOo and that I should use Synaptic Package Manager. Can anyone pls give me a list of packages to remove using Synaptic? Is the removal order important?

Many thanks :D

---

### Post by Ecthelion on 2007-01-20
Ehh...
I'm not sure you want to remove openoffice...

As far as I know it is a dependencie for Ubuntu-desktop, so uninstalling it would nearly uninstall your whole system...

Or can someone correct me ?

Why would you want to uninstall it anyway?

---

### Post by willbur on 2007-01-20
Hi Ecthelion

Thanks for the reply. I'd like to uninstall OOo as it's UI fonts are almost unreadable on my IBM think pad with ATI card, and GNUmeric and Abiword work perfectly for me. OOo Ui fonts seem to be a problem for only a small number of users judging from the OOo forums, so I don't imagine a fix is imminent ;) 

Other threads talk about happily removing a package called ubuntu-desktop when removing OOo as it's a 'metapackage'. If anyone has removed OOo from an Edgy installation, I'd be very grateful for any information...

Many thanks

---

### Post by melancholeric on 2007-01-20
> **Ecthelion said:**
> Ehh...
As far as I know it is a dependencie for Ubuntu-desktop, so uninstalling it would nearly uninstall your whole system...

Or can someone correct me ?

As far as I know ubuntu-desktop is just a metapackage and removing it with apt-get or synaptic won't actually remove anything else. Been there, done that.

If you use aptitude,  on the other hand, I think it will actually remove the whole desktop. If I'm not mistaken.

---

### Post by Ecthelion on 2007-01-20
> Other threads talk about happily removing a package called ubuntu-desktop when removing OOo as it's a 'metapackage'. If anyone has removed OOo from an Edgy installation, I'd be very grateful for any information...

Yes that is also possible.
Well then you'll have to wait for someone to confirm.
I think you are right but wouldn't swear on it.

---

### Post by konst88 on 2007-01-20
It is safe to remove open-office both with apt-get and with aptitude.
Aptitude automatically removes only what he automatically installs, and open office was built in.
Ubuntu desktop is just a virtual package. It contains nothing.
I think the easiest way to remove it is to remove the core package, and then most of the other OO packages will be removed because of dependencies.
After this you may search synaptic for the remains.

---

### Post by willbur on 2007-01-20
OK, I'll use Synaptic to uninstall OOo core, and then use it a second time to clean up anything that's left.

Could I please thank everyone for their help and advice with this newbie question? Its all very much appreciated....

---

### Post by jolly7777 on 2007-06-19
To remove the OOo you can:
apt-get remove --purge openoffice*

This will remove anything regarding OO and the magic ubuntu-desktop which is a meta, and not do anything important untill some point later when you may be prompted to install it/update it.

---

