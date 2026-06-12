---
title: "Help needed - Powerbook G4 - Feisty - Wireless + Codec + Touch Pad"
date: 2007-04-21
forum: Apple PPC Users
---

### Post by hevo on 2007-04-21
Hello Everyone,

I am relatively new to Ubuntu.

Installed Feisty on a 12 inch PowerBook G4

I want to know or have any link that can help me to:

1 - How to setup the wireless card + network connection
X-  How to add codecs to play avi, ogg, etc  -- Done
3 - How to configure the touch pad to add 2 fingers click, custom work, etc
4 - Video card drivers so the we can use video enhancements  

Thanks a lot for any help or link.

H

I update this thread with any link or solution that i find.

---

### Post by hevo on 2007-04-21
**Codec Installation**

Just run the video or music you want to play.
The add/remove application will start and install the needed codecs.

---

### Post by stmiller on 2007-04-21
sudo apt-get install bcm43xx-fwcutter

---

### Post by hevo on 2007-04-22
For wireless ---

[http://joona.kuori.org/ubuntu-powerbook/](http://joona.kuori.org/ubuntu-powerbook/)

Airport Extreme

Install the bcm43xx-fwcutter:
apt-get install bcm43xx-fwcutter

Download Airport Extreme firmware here: wl_apsta.o

Extract the firmware:
sudo bcm43xx-fwcutter -w /lib/firmware /path/to/wl_apsta.o

Reload the module.
sudo modprobe -r bcm43xx
sudo modprobe bcm43xx

---

