---
title: "Dapper disaray"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by nnjond on 2007-03-04
i have a duel boot. My data is on an aux disc, ((hdb5), which i can acces in Windows), but the permisions tabs on these directories are all greyed out so i can't write to them and i am informed;

"You are not the owner, so you can't change these permisions"

How can i change these permisions ?

---

### Post by SunnyRabbiera on 2007-03-04
huh, are you trying to edit the permissions from windows?

---

### Post by mrmonday on 2007-03-04
I am not sure if this will let dapper access them... But under windows (I am presuming your on XP) if you boot in safe mode and log on as 'Administrator' You should be able to change permissions from there.

---

### Post by mrmonday on 2007-03-04
By the way to boot in safe mode hit F8 once you have selected windows (possibly whilst - I have not used safe mode since I installed Ubuntu)

---

### Post by kinematic on 2007-03-04
```
sudo chown nnjond:nnjond /mountpoint-of-hdb5
```
chown stands for change owner and nnjond:nnjond makes it a part of the nnjond group and sets user nnjond as owner.
you could also make it a part of group root and set nnjond as owner by doing
```
sudo chown root:nnjond /mountpoint-of-hdb5
```
to get read/write and if you want execute permissions do
```
sudo chmod -R 774 /mountpoint-of-hdb5
```
chmod stands for change mode and this changes permissions recursively and lets root(or whatever group you made it a part of)and nnjond read/write/execute and others can only read.

---

### Post by nnjond on 2007-03-04
Thank for your help.

chmod: cannot access `/mountpoint-of-hdb5': No such file or directory
nnjond@nnjond-desktop:~$


How do i find out the mount point of hdb5

---

### Post by kinematic on 2007-03-04
i assumed it is an ext3 partition :lolflag: 
what kind of file sytem is on hdb5?
it's probably mounted under the /media directory since that's the ubuntu default so just look there.

---

