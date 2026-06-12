---
title: "Gimp"
date: 2007-12-15
forum: Art &amp; Design
---

### Post by ThomasWii on 2007-12-15
Hi, i went on to the GIMP website to see if there was a new version, it told me to put in ```
apt-get install gimp
``` but that did not work, so i put in ```
sudo apt-get install gimp
```and it started to download 2.4. when it download i went to Graphics > GIMP Image Editor. clicked on Help > About and it said it was 2.2.13. I restarted my laptop. and it still said 2.2.13.

Please help.

Thanks in advance,

Thomas

---

### Post by smartboyathome on 2007-12-15
What version are you on? 2.4 is only available on Gutsy (and it is the release canadite).

---

### Post by ThomasWii on 2007-12-15
on ubuntu 7.04

---

### Post by smartboyathome on 2007-12-15
> **ThomasWii said:**
> on ubuntu 7.04

You will have to compile 2.4 to get it on Feisty.

---

### Post by ThomasWii on 2007-12-15
how do i do that?

---

### Post by smartboyathome on 2007-12-15
download the tar.gz files, extract them, and then open a terminal in the extracted directory. Type ./compile, and then it will tell you if you have any unmet dependancies (please note, you will have to install the *-dev packages in order for the dependancies to be recognised), and then type make, and then sudo make install.

---

### Post by FuturePilot on 2007-12-15
Check here
[https://help.ubuntu.com/community/GIMP2.4-on-Feisty]("https://help.ubuntu.com/community/GIMP2.4-on-Feisty")
Looks a bit tricky though.

---

### Post by ThomasWii on 2007-12-18
Thanks guy's or girl's. i finely upgraded to 7.10

---

