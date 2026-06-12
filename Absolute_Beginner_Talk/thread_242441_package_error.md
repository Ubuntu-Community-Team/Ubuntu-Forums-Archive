---
title: "package error"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Tucatts on 2006-08-23
Ok, I have been trying to install a printer with little success and now I seem to have a package error that is hurting my system. I get the following whenever I access the terminal. "unknown error- exceptions.system error(E: the package fax4100lpr needs to be reinstalled but I can't find an archive for it. When I go to update I get the same error plus I get E; Internal error opening cache(1).
How do I delete the package fax4100lpr so it is no longer causing a problem. I have tried to reinstall to no avail so deleting it is my guess now.
Thanks,
Tucatts

---

### Post by ciscosurfer on 2006-08-23
Try 'updatedb'....wait....then 'locate fax4100lpr'```
sudo updatedb
locate fax4100lpr
```

---

### Post by nixclusive on 2006-08-23
> **Tucatts said:**
> Ok, I have been trying to install a printer with little success and now I seem to have a package error that is hurting my system. I get the following whenever I access the terminal. "unknown error- exceptions.system error(E: the package fax4100lpr needs to be reinstalled but I can't find an archive for it. When I go to update I get the same error plus I get E; Internal error opening cache(1).
How do I delete the package fax4100lpr so it is no longer causing a problem. I have tried to reinstall to no avail so deleting it is my guess now.
Thanks,
Tucatts

This command purges a package from the entire system (including config):
```
sudo dpkg -P <package-name>
```

This might not help your problem..but it sure will remove all traces of fax4100lpr from your system:
```
sudo dpkg -P fax4100lpr
```

---

