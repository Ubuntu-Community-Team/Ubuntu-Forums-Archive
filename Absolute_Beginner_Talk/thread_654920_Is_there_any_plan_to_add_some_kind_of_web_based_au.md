---
title: "Is there any plan to add some kind of web based auto-upgradeable feature in Ubuntu?"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-12-31
Thank you for reading my post.
I was thinking that whether Ubuntu has an upgrade mechanism? 
Something that can upgrade Ubunut 7.4 to 7.10 automatically using web based repositories?

Using this way, people can upgrade their Ubuntu without need to get and put a DVD into the drive.
I think it will be very easy to use and very efficient.
Because we usually keep our applications up to date and for example when 7.10 came out, we may need to update an small set of packages.
but without the upgrade feature I must get the DVD and install the system from DVD.

Please pardon me if this feature is present, I could not find it.

thanks

---

### Post by Paqman on 2007-12-31
You can do an in-place upgrade through the normal update manager. You'll get a button asking if you want to upgrade when the new version is available.

People tend to be divided about whether to upgrade or do a reinstall when new version are released. Personally, I say try the upgrade, and if it breaks something, do the reinstall.

---

### Post by oldos2er on 2007-12-31
It's Update Manager. When there's a dist-upgrade available, it will inform you.

---

### Post by Sef on 2007-12-31
> It's Update Manager.

System > Administration > Update Manager

---

### Post by Majorix on 2007-12-31
You can also run it to check for testing releases like this:
```
gksudo update-manager -d
```

---

