---
title: "repository vs *.deb and other"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by verby on 2006-10-29
Fist I have to thank you all for help. This is awesome forum.
Some new questions?

1. If you have a choice to install new program as/thorough repository or via downloading deb file, which one is better? (in this case Skype)

2. If I download any program (deb file) do I just double click (like in win) to install it?

3. If I plug a usb device (dig. camera, scanner, printer etc.) does ubuntu recognizes and installs drivers automatically (kind a like win) or do I have to first install drivers and then plug device?

Thanx

---

### Post by TheMono on 2006-10-29
1) Repositories - provide you with automatic updates!
2) Yep.
3) A large amount of things, plug and play - it doesn't even do that annoying windows thing of spending half an hour loading a driver.

---

### Post by 5-HT on 2006-10-29
[quote=verby]
1. If you have a choice to install new program as/thorough repository or via downloading deb file, which one is better? (in this case Skype) [/quote]

It be best to grab stuff from the repos if available.

[quote=verby]
2. If I download any program (deb file) do I just double click (like in win) to install it? [/quote]

Yup. :)

You can always install manually as well:
Code:

```
sudo dpkg -i /path/to/.deb 
```

[quote=verby]
3. If I plug a usb device (dig. camera, scanner, printer etc.) does ubuntu recognizes and installs drivers automatically (kind a like win) or do I have to first install drivers and then plug device? [/quote]
Usually the device will be automatically recognized and the appropriate driver loaded. If not, there's always the chance to install the driver manually.

*EDIT: typing too slow today...

---

