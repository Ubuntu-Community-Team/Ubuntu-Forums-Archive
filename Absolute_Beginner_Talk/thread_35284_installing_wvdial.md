---
title: "installing wvdial"
date: 2005-05-18
forum: Absolute Beginner Talk
---

### Post by rkenny on 2005-05-18
HI There: I have been using linux for a short time, mandrake10, but have installed ubuntu but when I try to run wvdial, nothing at all happens, I have reinstalled it, but still no joy, what does it take to get it where I can configure my modem, I don't know if my modem has been detected or not, it was with mandrake installed, when I open the run box, its not listed as one of the apps. when I open root terminal and type wvdial it says dialer defaults does not exist in wvdial.conf.  and cannot open /dev/modem: no such file or directory. Help! Thanks Richard

---

### Post by ggozad on 2005-05-19
You have to run wvdialconf. It takes as a parameter the configuration file. So I do
sudo wvdial /etc/wvdial.conf
and this will autodetect your modem if everything is ok.

---

