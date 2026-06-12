---
title: "I'm having some trouble getting my wireless card to work"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2005-12-26
...getting it to work in moniter mode that is. I have a Lucent wavelan silver card which is supported fine by breezy in normal mode. I can connect to my AP and the internet just fine, but I can't put the card in moniter mode or scan mode, and I need moniter mode to run kismet. After some searching I came up with this: [http://ubuntuforums.org/showthread.php?t=79160](http://ubuntuforums.org/showthread.php?t=79160)

Everything in the guide works fine until I try to make the drivers. Upon doing so, I am greeted with several compiler warnings, but I ignore these because they arn't important. At the end though...
```

/usr/src/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_suspend':
/usr/src/orinoco-0.15rc2/orinoco_pci.c:330: error: too many arguments to function `pci_save_state'
/usr/src/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_resume':
/usr/src/orinoco-0.15rc2/orinoco_pci.c:347: error: too many arguments to function `pci_restore_state'
make[2]: *** [/usr/src/orinoco-0.15rc2/orinoco_pci.o] Error 1
make[1]: *** [_module_/usr/src/orinoco-0.15rc2] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.12.4'
make: *** [modules] Error 2

```
The directory paths are different because I copied it off a website, but the errors themselves are identical. If it helps, I'm running the 2.6.12-9-386 kernel that comes default with breezy.

---

### Post by wr0x2 on 2005-12-26
OK, I got the driver working by modifying the source and kismet works now! dmesg tells me that my card enters promiscous mode, and iwpriv lists a different set of private loctls for eth0, but moniter isn't listed. Also, iwlist scan doesn't work. Here's the output when I try to run it:

```

$ iwlist scan

eth0 Failed to read scan data : No data available

```
and then with sudo...
```

$sudo iwlist scan

eth0 Interface doesn't support scanning : Network is down

```

WTF is going on here? dmesg says that my card enters prom. mode, wouldn't that be the same thing as moniter mode?

---

