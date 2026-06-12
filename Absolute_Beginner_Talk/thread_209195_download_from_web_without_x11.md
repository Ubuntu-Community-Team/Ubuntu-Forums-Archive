---
title: "download from web without x11?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by mycoplasma on 2006-07-04
i just installed breezy badger (i burnt the cd before Dapper Drake came out and never got around to installing it until now), and x cant activate the GUI.  After looking through the log info, ive determined that the drivers installed probably aren't up to date enough to handle my geforce 7600GT, so i need to download new ones.  Can anyone please tell me how to browse the web from the command line so i can get the driver?

---

### Post by yabbadabbadont on 2006-07-04
I don't know if they are included on the install cd you have, but lynx, links, and w3m are all text mode web browsers.

---

### Post by 23meg on 2006-07-04
links2 will help you; make sure you've enabled the Universe repository and type ```
sudo apt-get install links2
```to install.

---

### Post by it.henrik on 2006-07-04
If you know the URL you can get the file with wget.

wget [http://my.example.org/examplefile.bin](http://my.example.org/examplefile.bin)

---

### Post by ardchoille on 2006-07-21
> **23meg said:**
> links2 will help you; make sure you've enabled the Universe repository and type ```
sudo apt-get install links2
```to install.

I installed links2 and it won't run as normal user in tty1. I can run it as normal user in gnome-terminal, but it will only run as root in tty1. What's up?

---

### Post by aysiu on 2006-07-21
Try *lynx*.

---

### Post by wildseven on 2006-07-21
try
```
 wget http://www.example.com/example.bin
```

---

