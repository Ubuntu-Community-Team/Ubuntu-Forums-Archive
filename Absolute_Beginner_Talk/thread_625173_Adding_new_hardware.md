---
title: "Adding new hardware"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by prob69 on 2007-11-27
I have just purchased a new pci raid ide controller mainly for Windows but wondered how you install this to work with ubunto. Cant seem to find add new hardware option like windows.

---

### Post by Grey Box on 2007-11-27
There are three possiblities:

1. It is already detected and the driver was loaded when you rebooted. This is usually the case. Unlike in Windows, Linux has hardware support for countless devices out of the box. Go to System -> Preferences -> Hardware Information and see what it says about your system.

2. There are no drivers in the Linux kernel that you are using, but there may be support for the hardware from the vendor. Search google or altavista or equivalent for your device's model number, plus something like 'ubuntu' or 'linux'. 

3. There is neither 1 or 2 and you are out of luck. If you have bought something that's totally novel and (as is sometimes the case) is 'designed for Windows' or something like that, then you will probably have to wait a while before it gets supported in Linux. That could be anything from a couple of months to years, depending on how bizarre your hardware is.

I hope that helps.

---

