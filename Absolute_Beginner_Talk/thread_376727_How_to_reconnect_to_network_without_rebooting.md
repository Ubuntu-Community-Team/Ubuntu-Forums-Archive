---
title: "How to reconnect to network without rebooting?"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-03-05
For some reason, if I boot into ubuntu without my ethernet cable plugged in it won't connect to the network even when I plug in the cable.  I need to reboot with the cable plugged in to get it to connect.  Is there a way to reconnect to a network without rebooting?

---

### Post by xyz on 2007-03-05
Only speaking for myself but it works here:
- I go to the Network Connection (top panel), click on it and Deactivate it > OK
- I unplug the modem and wait 30 seconds or so.

- replug the modem and wait for about 30 seconds.
- I (re)go to the Network Connection (top panel), click on it and Acttivate it > OK

See if it works for you and let us know.

---

### Post by maniacmusician on 2007-03-05
> **Matt1632 said:**
> For some reason, if I boot into ubuntu without my ethernet cable plugged in it won't connect to the network even when I plug in the cable.  I need to reboot with the cable plugged in to get it to connect.  Is there a way to reconnect to a network without rebooting?
yup, simple command

> sudo /etc/init.d/networking restart

---

### Post by Matt1632 on 2007-03-05
Thanks, that's what I was looking for.

---

### Post by anaconda on 2007-03-05
thanks "maniacmusician" .. good to know.

and "Matt1632".. are you sure it wont connect? with my laptop it takes about 60s before it connects, but I dont need to do anything.. just wait.

---

