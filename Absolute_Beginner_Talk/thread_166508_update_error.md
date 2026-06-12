---
title: "update error"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by rameez on 2006-04-26
I am getting this error everytime I open software update or synaptic
```
W: Couldn't stat source package list http://koti.mbnet.fi breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
```
Can anyone please tell me how to get rid of it.

Thanks.

---

### Post by testube_babies on 2006-04-26
If this always happens, then you should probably just comment out that line in your sources list.
```
sudo gedit /etc/apt/sources.list
```

Find "deb [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy" and possibly "deb-src [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy" and add a '#' character before each of them (ie #deb [http://...../](http://...../) breezy).  Save, close the window, and try an update to see if it works.

---

### Post by rameez on 2006-04-26
thanks

---

