---
title: "problem with ms access"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by raggielyle on 2007-11-23
I need some help please.
1.
 I installed wine and then ms office 2000. All fine except for ms access. Error message that ie 3 or later required. Tried installing ie from disk with wine , installing ie4linux, libmdbodc, libmbtools, mbtools, mbtools-dev, mbtools-gmdb but still no success. Tried using kexi and installed kexi-mdb-plugin but no luck. Kexi just disappears!  Going crazy here as I must have ms access for business purposes. 
2.
Any advice for a beginner whether I should use NetBeans or Eclipse

---

### Post by The Cog on 2007-11-23
You may have to resort to running windows inside vmware or virtualbox. That's what I do for those pesky apps.

---

### Post by markharding557 on 2007-11-23
the cog is absolutley right the only way to run ms office 100% is in a vm 
also are you aware openoffice can do many of the same things

---

### Post by orthodoc on 2008-01-23
The solution is quite simple.

Do the following:
```
sudo aptitude remove kexi-mdb-plugin
```

Then type the following:
```
sudo aptitude install kexi-mdb-driver
```

In case you are using kexi for the first time, then
```
sudo aptitude install kexi kexi-mdb-driver
```

You will be asked for your root password. From then on its very simple to import  the database. Simply clicking on it will bring up the import wizard and you are done. :)

---

### Post by raggielyle on 2008-01-24
thanks for your kind help

---

