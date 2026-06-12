---
title: "Converting RPM to a DEB file"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by jazzybob on 2007-08-29
I have a printer driver that is only available in a RPM  - my simple mind knows DEBs can be installed, so how can I convert a RedHat Package, RPM for use on my UBUNTU box?

Thank you.

Jazzy

---

### Post by Dr Small on 2007-08-29
```
sudo apt-get install alien
sudo alien nameoffile.rpm
```

---

### Post by ThrobbingBrain66 on 2007-08-29
```
sudo apt-get install alien
```

Then I think the command is as simple as 'alien package_name', but don't quote me on that.

---

### Post by jazzybob on 2007-08-30
Thanks - here's a real beginner problem:  Got alien

The file is on the desktop

How do I change directories to properly have alien covert the package?

See below:

root@lecom-laptop:/home/jazzybob# sudo alien Xerox-Phaser-6180-1.0-1.noarch.rpm
File "Xerox-Phaser-6180-1.0-1.noarch.rpm" not found.

---

### Post by Outrunner on 2007-08-30
```
cd Desktop
```

And just a question, why are you running as root?

---

### Post by sdim on 2007-08-30
If it is on your desktop, write: _cd Desktop_,and the Desktop directory will be activated.

---

### Post by maxamillion on 2007-08-30
> **sdim said:**
> If it is on your desktop, write: _cd Desktop_,and the Desktop directory will be activated.

Activated? .... there is no activation, you simply **c**hange **d**irectory.

---

### Post by jazzybob on 2007-08-31
Thank you - each and every one.  This is a great resource.  And populated by great users with great advice.

---

