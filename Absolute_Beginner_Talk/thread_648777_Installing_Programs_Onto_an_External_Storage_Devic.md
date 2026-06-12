---
title: "Installing Programs Onto an External Storage Device"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Mike_H on 2007-12-24
Here's the situation. I have an Asus EeePc with 4GB of flash storage. I also have a 2GB flash drive that I use for music. I would like to install some things like Open Arena, or Frets on Fire, but space on the main 4GB SSD is at a premium, and games like that would be too tight of a fit. Is there a way for me to install a game like Open Arena onto the flash drive, WITHOUT moving all of /usr/bin onto the flash drive, because I would like to remove it and plug it in only when it is necessary.

Thanks.

---

### Post by daengbo on 2007-12-24
You can 
a) mount the flash drive as /opt, then compile these programs with  --prefix=/opt 
b) mount the flash drive to your ~/bin and install to there

---

