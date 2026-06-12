---
title: "[SOLVED] Open Office problem"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by cartisdm on 2008-03-11
My Open Office recently started acting all screwy for no reason.  When I try scroll down it goes spastic and if I try to close it it doesn't want to close all the way.  I figured I'd simply just reinstall it but I wasn't so lucky when trying to do that within Add/Remove programs.  How can I accomplish this?

---

### Post by spiderbatdad on 2008-03-11
You could mark openoffice-common and openoffice-core for reinstallation in synaptic package manager and see if it helps. I really don't know it's a complex suite of programs. I would venture a guess the problem is more likely in one of the engines that drives open office.

---

### Post by TeaSwigger on 2008-03-11
You could also try deleting your user profile files. In Nautilus, in your home folder, select "show hidden files" and you should find one named .openoffice.org2. Remove that and see if it's still misbehaving the same.

---

### Post by Hagar Delest on 2008-03-13
If renaming your OOo user profile doesn't fix it, you can try to install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by cartisdm on 2008-03-21
> **TeaSwigger said:**
> You could also try deleting your user profile files. In Nautilus, in your home folder, select "show hidden files" and you should find one named .openoffice.org2. Remove that and see if it's still misbehaving the same.

So I have no idea what that did but it worked.  What does that file do and how does deleting it fix whatever my problem was?

---

### Post by Hagar Delest on 2008-03-25
That folder contains all the configuration files related to the user logged in. Sometimes some of them get corrupted, who knows why? Renaming the profile makes OOo to create a completely new one with brand new configuration files.

If you've customized your OOo installation, you can replace new folders by old ones, the trick is to avoid the one with the damaged files.

---

### Post by JoseReyes on 2008-03-25
> **spiderbatdad said:**
> You could mark openoffice-common and openoffice-core for reinstallation in synaptic package manager and see if it helps. I really don't know it's a complex suite of programs. I would venture a guess the problem is more likely in one of the engines that drives open office.

Thank you for your suggestions. This really worked for me. It saved me from having to re-install ubuntu... :)

---

