---
title: "Accesing protected files"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-01-23
So, i need to modify some a file in etc/udev/ in order to access usb devices with virtualbox. Now  i thought i would have the full administrative rights on this computer as I put the whole system up, but i am not able to modify those files. If i look under user & groups there are two users, me(andreas) and root. Do i have to change some settings in the user & groups window in order to modify those files?

Thanks
Andreas

---

### Post by bodhi.zazen on 2008-01-23
naw, Ubuntu uses sudo and gksu

So you can :

```
gksu gedit /etc/udev/<file>
```

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

