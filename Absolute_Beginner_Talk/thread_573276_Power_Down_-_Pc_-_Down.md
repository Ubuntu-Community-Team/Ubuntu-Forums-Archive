---
title: "Power Down - Pc - Down"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by klgsx on 2007-10-11
UBUNTU, Kerner 2.6.20-16-generic
UBUNTU, Kerner 2.6.20-16-generic(recovery mode)
UBUNTU  Kerner 2.6.20-15 generic
UBUNTU, Kerner 2.6.20-15-generic(recovery mode)
UBUNTU MEMTEST86+

I selected the second choise... a bunch of stuff hapen on my pc... files are listed and It looks like it been check... OK

I get a message saying "settiing up console, fonts and keymap... OK

then I get a prompt msg

root\DataCenter>

what can I do to get my desktop back?   I typed  "exit"  and i get a series a lines saying "loading".... gray screen.

Any suggestions?

---

### Post by skymera on 2007-10-11
try

sudo /etc/init.d/gdm start

---

### Post by overdrank on 2007-10-11
> **klgsx said:**
> UBUNTU, Kerner 2.6.20-16-generic
UBUNTU, Kerner 2.6.20-16-generic(recovery mode)
UBUNTU  Kerner 2.6.20-15 generic
UBUNTU, Kerner 2.6.20-15-generic(recovery mode)
UBUNTU MEMTEST86+

I selected the second choise... a bunch of stuff hapen on my pc... files are listed and It looks like it been check... OK

I get a message saying "settiing up console, fonts and keymap... OK

then I get a prompt msg

root\DataCenter>

what can I do to get my desktop back?   I typed  "exit"  and i get a series a lines saying "loading".... gray screen.

Any suggestions?

HI if you are in recovery mode you will have to reboot
```
reboot
```
Is the command

---

### Post by rahimveron on 2007-10-11
Choose the 1st option UBUNTU, Kerner 2.6.20-16-generic or 3rd option, depending whck kernel you want to use,and you will be booted to your Desktop.

---

