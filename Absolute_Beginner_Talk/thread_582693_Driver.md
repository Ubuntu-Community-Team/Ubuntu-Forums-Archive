---
title: "Driver"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Otrebor6 on 2007-10-20
Hi, im new to Linux, I have the ubuntu distro installed, it works fine apart from I cant seem to connect to the internet. I have googled the internet and found some confusing stuff i am a noob running INPROCOMM IPN2220 Wireless LAN Card on a Acer laptop. :(

---

### Post by Espreon on 2007-10-20
Kay,

Look for the driver (its usually in an .exe file) on your manu's (or on Acer's) site, download it, extract it in Winblow$, 

The important files are a .inf and a .sys file

then enter this stuff in the terminal:

```

sudo apt-get install ndiswrapper ndisgtk ndiswrapper-utils-1.9

```

Then goto: System>Administration>Windows Wireless Drivers

and drag and drop the .inf file on the empty space.

Then enter this in the terminal:

```

sudo modprobe ndiswrapper

```

Good luck.

---

### Post by Otrebor6 on 2007-10-20
I have found the site [http://support.acer-euro.com/faqs/faqsearch.html](http://support.acer-euro.com/faqs/faqsearch.html) . What's the file that I must download?

---

