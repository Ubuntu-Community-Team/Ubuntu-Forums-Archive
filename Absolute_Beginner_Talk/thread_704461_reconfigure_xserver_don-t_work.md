---
title: "reconfigure xserver don-t work"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by petegreenhorn on 2008-02-22
Help i ve been trying for the last 3 days to get my machine to boot into gui with no sucsess
after reading , and following various instructions to very similar problems to my own i-m still no closer to solving the problem .the message i get after grub is The gdm is disabled . so i ran ( sudo dpkg-reconfigure xserver-xorg ) from both the live cd and the tty thing after the above message . no sucsess can anyone help or do i need to back up my home and reinstall

---

### Post by bodhi.zazen on 2008-02-22
What video card do you have ?

---

### Post by petegreenhorn on 2008-02-22
Hi it's onboard sis i think
i'm new at this so you'll have to bear with me please
if it helps i tried to load the hard drive onto my new case without sucsess and when i put it back in this one presto here i am

---

### Post by petegreenhorn on 2008-02-22
BTW i followed some instructions you gave to someone else yesterday , he was in the same (more or less ) situation but no go for me

---

### Post by bodhi.zazen on 2008-02-22
Well, I am sorry you are having problems. If that command did not work it may take some effort, ie installing the ATI or Nvidia (or other) driver.

You can try these commands to see if you can identify your hardware :


```
lspci
```

```
sudo lshw
```

```
cat /etc/X11/xorg.conf
```

in xorg.conf you are looking for something like this :

> Section "Device"

    Identifier  "6600gt_twinview"
   ** Driver      "nvidia"**
    BusID       "PCI:01:00:0"

<clip>

You can also try to reconfigure X and use the vesa driver,

```
sudo dpkg --reconfigure xserver-xorg
```

Select the defaults for everything but your video driver. For that, select vesa.

---

### Post by petegreenhorn on 2008-02-22
sorry for late reply , here's what the sectio " device read 

Section "Device"
        Identifier      "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
        Driver          "sis"
        BusID           "PCI:1:0:0"
it dosn't help me much and i ran the code you suggested ot reconfigure three times with the same result
but thanks for your help all the same

---

### Post by bodhi.zazen on 2008-02-22
Not sure about your card, try the vesa drive, it usually works.

---

