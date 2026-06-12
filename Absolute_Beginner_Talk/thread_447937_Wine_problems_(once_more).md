---
title: "Wine problems (once more)"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-05-18
I cannot use wine...

When I put a virtual desktop and I close winecfg and reopen it, the desktop appears, but when I re open it the destkop disappears.

It doesn't recognise the devices, I give autodetect adn they show up, but when I try to install something even in the same window (or reopening it, it doesn't makes difference) wine again does not recognise the devices.... any solution you can give to me?

---

### Post by Hobo Joe on 2007-05-18
I'm having trouble understanding your question...
Are you saying that your virtual desktop closes when you try to open it?

If that's that case, WINE's virtual desktop auto-closes when there is nothing running in it.

---

### Post by Jorge32 on 2007-05-18
no, it does not appears the next time of configuring it, and even like that I cannot install nothing because wine does not recognises my partitions, it does not recognise even the one where Ubuntu is located.

---

### Post by zvacet on 2007-05-18
You can install in several ways.
1.Put exe in any folder and right click on it and you will see option **open with**.
2.put exe in .wine folder (hidden folder in your home directory) >C>program files After that go to the programs>accessories>wine file With wine file go to the C>program files>your exe and double click on it
3.Put exe in any folder(for example let say folder name is programs)  type in terminal

```
wine /home/your_username/programs/your_exe
```

---

