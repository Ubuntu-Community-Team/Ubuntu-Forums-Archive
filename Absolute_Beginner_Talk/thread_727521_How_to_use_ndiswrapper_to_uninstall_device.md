---
title: "How to use ndiswrapper to uninstall device?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by caljohnsmith on 2008-03-17
I need to uninstall a wireless card driver that I originally installed with ndiswrapper. If I type "ndiswrapper -l" I get:
mrv8335 : driver installed
        device (11AB:1FAA) present
Note the mrv8335 is referring to my wireless card mrv8335.inf file I originally installed.
Then I type "ndiswrapper -r mrv8335" and it returns:
couldn't delete /etc/ndiswrapper/mrv8335: Inappropriate ioctl for device

So, being a Linux newbie here, what do I do? Thanks for any help!

---

### Post by handydan918 on 2008-03-17
> **caljohnsmith said:**
> I need to uninstall a wireless card driver that I originally installed with ndiswrapper. If I type "ndiswrapper -l" I get:
mrv8335 : driver installed
        device (11AB:1FAA) present
Note the mrv8335 is referring to my wireless card mrv8335.inf file I originally installed.
Then I type "ndiswrapper -r mrv8335" and it returns:
couldn't delete /etc/ndiswrapper/mrv8335: Inappropriate ioctl for device

So, being a Linux newbie here, what do I do? Thanks for any help!

Unless ndiswrapper has changed in the last few months, i believe you want
```
ndiswrapper -e mrv8335
```

If that doesn't work for you, try```
rmmod ndiswrapper
```
first, then do ```
ndiswrapper -e mrv8335
```

---

