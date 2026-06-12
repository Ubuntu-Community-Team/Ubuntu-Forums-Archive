---
title: "Installation Problem on HP Pavilion XE793"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by dotjosh77 on 2008-03-23
I am new to Linux and I am trying to install Ubuntu 7.10 on my (older) HP Pavilion XE793 desktop.  It has Windows ME and an Intel(r)  Celeron(tm) processor, 63.0 MB RAM, Intel(r) 82810 Graphics Controller.

I can boot from the CD and get to the Install options. After clicking "Start or Install Ubuntu" I get an Ubuntu loading screen and then after a couple of minutes the screen goes black and nothing happens. I have left it on for several hours and still nothing. Any help would be greatly appreciated.

---

### Post by waspbr on 2008-03-23
with 64 mb of ram , well, I think xubuntu would be your best bet. Also try running the live CD in safe graphics mode, see if that solves the problem

---

### Post by overdrank on 2008-03-23
> **dotjosh77 said:**
> I am new to Linux and I am trying to install Ubuntu 7.10 on my (older) HP Pavilion XE793 desktop.  It has Windows ME and an Intel(r)  Celeron(tm) processor, 63.0 MB RAM, Intel(r) 82810 Graphics Controller.

I can boot from the CD and get to the Install options. After clicking "Start or Install Ubuntu" I get an Ubuntu loading screen and then after a couple of minutes the screen goes black and nothing happens. I have left it on for several hours and still nothing. Any help would be greatly appreciated.

Hi and with the low memory I would recommend the alternate cd as a text based installer
[http://us.releases.ubuntu.com/7.10/](http://us.releases.ubuntu.com/7.10/)
It will more than likely run slowly on the low memory also

---

### Post by dotjosh77 on 2008-03-23
Thanks I am trying to run in safe graphics mode now. I may need to install more memory. Also when i press CTRL+ALT+F1   I get a message that says    ACPI: no BIOS year, acpi=force is required to enable ACPI

---

### Post by dotjosh77 on 2008-03-23
low graphics mode is alsonot working....i need a newer machine lol

---

### Post by waspbr on 2008-03-23
at the livecd menu, where you choose start in safe graphics mode, press f6, this should show you the command line, then type  
```
noapic
```

see if that works, still think you should try xubuntu instead of ubuntu

---

### Post by dotjosh77 on 2008-03-23
yes i think i will try xubuntu .....thanks for all your help

---

### Post by waspbr on 2008-03-23
don't mention it don't hesitate to post if u need help

---

### Post by dotjosh77 on 2008-03-23
i tried to install in text mode and it worked , but it is confusing

---

### Post by overdrank on 2008-03-23
> **dotjosh77 said:**
> i tried to install in text mode and it worked , but it is confusing

Hi and it is installed? and what is confusing?

---

### Post by dotjosh77 on 2008-03-24
it was confusing because it asked me some questions that i did not understand

---

### Post by dotjosh77 on 2008-03-24
yes the questions aked during installation were a bit confusing for me

---

### Post by xeth_delta on 2008-03-24
Still, if you have the chance to install more memory, do it. It is always a good way to gain performance on a computer, and besides, 63MB of RAM is not very much.

---

### Post by dotjosh77 on 2008-03-24
yes i am going to install more memory soon...the computer was an old one that my mom had in her office and i decided to make a linux project out of it......thanks for the suggestion

---

### Post by hackenslay on 2008-04-28
I am having the same problem with the same model, HP Pavilion XE793, the acpi=force message, which i typed in the command prompt. This enabled a quicker shutdown, but did not enable power management. I have to manually turn the power off with the power button, and then it only acts as a reset button. I have to hold the button in for 4 seconds before it actually shuts off. Do you have a solution? My wife uses the PC for email only, booting into a windows partition for any offline work.

---

