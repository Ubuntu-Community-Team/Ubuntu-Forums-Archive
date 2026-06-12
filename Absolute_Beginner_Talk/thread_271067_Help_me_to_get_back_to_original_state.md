---
title: "Help me to get back to original state"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by i-m-p on 2006-10-04
I followed this wiki page and I didn't like the result. I would like to get my system back 
 to the state before I tried this method.

[https://help.ubuntu.com/community/Fixing_Japanese_Fonts_in_Dapper](https://help.ubuntu.com/community/Fixing_Japanese_Fonts_in_Dapper)
The page says.

> * This method will make your Japanese fonts look ridiculously good, but it will also change your default sans, serif, etc. system fonts' settings. In the end, it was worth it for me.

I don't like this settings.

I've removed ipfont and ipamonafont already. I think probably I have to modify /etc/fonts/local.conf file to original state. But /etc/fonts/local.conf.backup is blank.

Any Ideas?

---

### Post by tdrusk on 2006-10-04
since you did that, try rebooting?

---

### Post by Stone123 on 2006-10-04
Just a wild guess , did you try:

sudo apt-get update
sudo apt-get remove ipafont ipamonafont
sudo mv /etc/fonts/local.conf.backup /etc/fonts/local.conf 
sudo reboot
sudo dpkg-reconfigure fontconfig

---

### Post by i-m-p on 2006-10-04
These are what I have in /etc/fonts/
conf.d  fonts.conf  fonts.dtd  language-selector.conf  local.conf

Or is this only a matter of changing the font prefernce by system/preferences/font ?

Should I delete some files?

---

