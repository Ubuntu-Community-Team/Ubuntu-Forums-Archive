---
title: "Upgrade from Breezy to Edgy"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Drew555 on 2007-03-08
I'm running Breezy Badger and want to upgrade to Edgy.

I've been told I can do this without using a CD.

Can I?

And how?

Step by step would be nice.. n00bish behaviour alert...

---

### Post by Del Boy on 2007-03-08
You need to upgrade to Dapper first.

```
sudo aptitude update 
sudo aptitude dist-upgrade
```

Edit: You need to update your sources.list first. Change every occurrence of breezy to dapper.

```
sudo gedit /etc/apt/sources.list
```

---

### Post by taurus on 2007-03-08
I don't think it will work if you go from Breezy directly to Edgy.  You first need to upgrade from Breezy to Dapper and then from Dapper to Edgy.  

To upgrade from Breezy to Dapper, you need to edit /etc/apt/sources.list and replace all the word **breezy **in there with **dapper**.  

```
gksudo gedit /etc/apt/sources.list
```
Save it and run

```
sudo aptitude update
sudo aptitude dist-upgrade
```
Then reboot to make sure your system is still working.  Then, if you want to go from Dapper to Edgy, you need to follow this guide.

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by Malac on 2007-03-08
> **Drew555 said:**
> I'm running Breezy Badger and want to upgrade to Edgy.

I've been told I can do this without using a CD.

Can I?

And how?

Step by step would be nice.. n00bish behaviour alert...
I think the command is ```
gksu "update-manager -c -d"
```
Not sure whether this is still relevant but there was a bug.
[https://launchpad.net/ubuntu/+source/update-manager/+bug/78673](https://launchpad.net/ubuntu/+source/update-manager/+bug/78673) 
The fix is easy you just need to create folder .gnupg in your home folder.

---

### Post by Drew555 on 2007-03-08
Just done the upgrade, about to reboot to see what happens.....

If you never hear from me again, send help.....

---

### Post by Drew555 on 2007-03-08
All sorted.

Thanks a million guys!

---

