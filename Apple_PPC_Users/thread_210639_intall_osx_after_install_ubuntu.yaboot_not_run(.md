---
title: "intall osx after install ubuntu.yaboot not run:("
date: 2006-07-07
forum: Apple PPC Users
---

### Post by erez1012 on 2006-07-07
i install ubuntu and after that i install osx
and when i power on the ibook it is go to osx straight  and not through yaboot.

please i dont want to delete anithing
thanks

---

### Post by robino on 2006-07-07
> **erez1012 said:**
> i install ubuntu and after that i install osx and when i power on the ibook it is go to osx straight  and not through yaboot.

please i dont want to delete anithing
thanks

That's because OSX made the partition of OSX the default startup paritition. You can start Ubuntu by holding the ALT key after the Gong, the startup sound after rebooting. 

The system will then search for all start-up partitions, and you can select the Ubuntu partition to start up with.

When in Ubuntu, go to your terminal and type the following code:

```
sudo yabootconfig 
sudo ybin -v
```

And all should be working again after a reboot.

You can also doublecheck the partitions by typing:
```
sudo nano /etc/yaboot.conf
```

However, when you make any changes in yaboot.conf be sure to do:

```
sudo ybin -v
```

You can also read [this HowTo for more information]("https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot"). Please report if it worked.

---

### Post by erez1012 on 2006-07-07
:)) thanks mannn

---

