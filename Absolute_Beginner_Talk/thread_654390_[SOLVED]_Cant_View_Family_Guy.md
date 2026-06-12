---
title: "[SOLVED] Cant View Family Guy"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by joshuanv28 on 2007-12-31
Ok im trying to watch family guy episodes online at [www.familyguyx.net](www.familyguyx.net)  and it wont let me even veiw the picture and the startup or anything?? I have tried to install a number of media players but nothing seems to work. Any HELP???

---

### Post by Perfect Storm on 2007-12-31
Works fine here. You need to install flash to see them.

---

### Post by jualin on 2007-12-31
yeah, works fine for me too. Try installing Flash from synaptic or from Firefox. The whole website is based on flash player, you could try downloading adobe flash player from adobe.com.

---

### Post by RomeReactor on 2007-12-31
Hi. Joshua, try doing this from the terminal:
```
sudo apt-get remove --purge flashplugin-nonfree
```
then:
```
sudo apt-get update
```
and:
```
sudo apt-get install flashplugin-nonfree
```

As far as I know, the flashplugin-nonfree package in the repositories had a bug which has been corrected; if that doesn't correct the problem, download [this package]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466") and double click on it to install it; Flash on Firefox should work then. Thanks go to [daradib]("http://ubuntuforums.org/member.php?u=182332") for [this very useful thread]("http://ubuntuforums.org/showthread.php?t=636397").

---

### Post by joshuanv28 on 2008-01-03
thx it worked great..

---

