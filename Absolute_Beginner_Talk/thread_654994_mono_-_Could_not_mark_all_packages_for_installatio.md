---
title: "mono - Could not mark all packages for installation or upgrade"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-12-31
Trying to reinstall Mono -- the .NET runtime.

I get this error:

Could not mark all packages for installation or upgrade.

The following packages have unresolvable dependencies.
Make sure that all required repositories are added and enabled in the preferences.

mono:
  Depends:  mono-common but it is not going to be installed
  Depends:  mono-jit but it is not going to be installed


How do I get Mono reinstalled????

Thanks

Carl

---

### Post by taurus on 2007-12-31
Which release are you running and can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by BhRaviKiran on 2008-01-14
Hi Team,
                   From wher did u get the mono-packages for Ubuntu. I'm in search of mono 1.2.2.1 on Ubuntu 7.10. Plz redirect me where i can find mon 1.2.2.1 or higher for Ubuntu 7.10.

Thanks in advance.
Regards,
Ravi.

---

