---
title: "no composite extension available"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Pap3rbag on 2008-01-23
i have a ati 1650 and when i got to enable desktop affects i get this message

---

### Post by Hospadar on 2008-01-23
you need to install the restricted drivers, although ati can be finikey, so you may have to do more, but for starters

System->Administration->Restricted Drivers Manager and enable the restricted driver

---

### Post by wormser on 2008-01-23
ATI cards require an extra program called XGL in order to be able to run Compiz.

```
sudo apt-get install xserver-xgl
```

You have to reboot for this to take effect!

---

### Post by gvartser on 2008-01-23
Check this post, maby this could help you out.

[http://ubuntuforums.org/showthread.php?t=291464](http://ubuntuforums.org/showthread.php?t=291464)

/G

---

### Post by Pap3rbag on 2008-01-23
> **wormser said:**
> ATI cards require an extra program called XGL in order to be able to run Compiz.

```
sudo apt-get install xserver-xgl
```

You have to reboot for this to take effect! thats all i have to do? dont want to screw anything up finally got my drivers working :)

---

### Post by rhc on 2008-01-23
If anything messes you can delete that > xserver-XGL from Synaptic anytime you want.
But nothing bad will happen,don't afraid : )

---

