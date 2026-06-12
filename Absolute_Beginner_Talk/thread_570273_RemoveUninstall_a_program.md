---
title: "Remove/Uninstall a program"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2007-10-08
I have downloaded and installed Skype but because i have failed to get any sound i have decided to un-install it. So could someone please tell me how to remove it off my computer. Big Thanks.

---

### Post by jon zendatta on 2007-10-08
in terminal enter:
sudo apt-get remove file:
if that don't work try :
sudo apt-get remove --purge file
:KS

---

### Post by oscarthefish on 2007-10-08
Job done! Cheers Jon

---

### Post by skymera on 2007-10-08
most things are availible using Apt :wink:

sudo apt-get install
sudo apt-get remove
sudo dpkg -i /location/to/file
sudo dpkg -r (package name)

apt-get is easies :wink:

---

### Post by oscarthefish on 2007-10-08
Why thanks Skymera for the info. All help is appreciated.

---

