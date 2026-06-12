---
title: "Install Specific Version on Software"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by flycast on 2006-08-13
I have used Synaptic to install packages. I want to match a specific web serving environment ie. a certain version of Mysql and PHP. If I use Synaptic or apt-get then it gets the latest version. How do I install a specific version of a certain software package rather than the latest?

Thanks,
Eric

---

### Post by Ziox on 2006-08-13
> **flycast said:**
> I have used Synaptic to install packages. I want to match a specific web serving environment ie. a certain version of Mysql and PHP. If I use Synaptic or apt-get then it gets the latest version. How do I install a specific version of a certain software package rather than the latest?

Thanks,
Eric

Select the package you want to install, Go to the menus bar at the top of synaptic, and i think the middle option (I'm running Window$ right now, so I can't recall the specific name. Just check all the options) One of the options there should say "Force Version" or something similar.  There you should be able to choose the different versions for that particular app.  (Once I get back on my Ubuntu Computer, I'll edit this to be more specific).

---

### Post by flycast on 2006-08-13
I checked and found that while it list on other version (5.0.21-Obuntu6.06(dapper-security)) I need to install version  	3.23.58. Is there a way to force more alternate versions to show up or do I need to download and "make"?

---

### Post by Ziox on 2006-08-13
> **flycast said:**
> I checked and found that while it list on other version (5.0.21-Obuntu6.06(dapper-security)) I need to install version  	3.23.58. Is there a way to force more alternate versions to show up or do I need to download and "make"?

Well, that's a big downgrade, uhhh...either do "make" or you can add either breezy/warty/hoary repository, there must've been a version in one of them.

However, I highly suggest not messing with the repository, since it is likely that you'll encounter dependency problems.  Ultimately resulting in an unstable system.

---

