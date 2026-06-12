---
title: "Installed a new Ati card and broke X"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by breander on 2007-09-02
I upgraded my graphics card from an ati radeon 9800 to a ati x1650 and now I cannot get the gui to load in ubuntu 7.04. I have tried getting new drivers to install by using

sudo apt-get install xorg-driver-fglrx

But all i get is an security error with the server it is trying to download it from.

Any help would be appreciated.

---

### Post by taurus on 2007-09-02
Boot into recovery mode from GRUB menu and try to reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
shutdown -r now
```

---

### Post by breander on 2007-09-02
Doesn't seem to work it still does not want to recognize my graphics card.

---

### Post by taurus on 2007-09-02
When you go through the options with that command, pick **vesa** driver for now and once you get X back, then install the latest driver for your graphic card.  

What is the exact error message when you reboot your machine while X is trying to start up?

---

### Post by breander on 2007-09-02
Ok I did like you said and I still dont have x back.

my error message is

VESA: No matching Device section for instance (BusID PCI:1:0:0) found

No devises detected

No screens found

---

### Post by taurus on 2007-09-02
How many graphic cards do you currently have on your machine anyway?  Any chance you also have an onboard graphic controller?  What's the output of this command from a terminal?

```
lspci | grep VGA
```

---

### Post by breander on 2007-09-02
Only have one a AGP ATI X1650. I'm pretty sure I have no built in video card.

The output is

01:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600]

---

### Post by taurus on 2007-09-02
Can you post the whole /etc/X11/xorg.conf?

---

### Post by breander on 2007-09-02
Im not sure how i can do that since im reading everything from a command line. I'm using a buddies computer next to it to reply and post in these forums.

---

### Post by breander on 2007-09-02
Ok I was able to get x back. I was finally able to install the new ati drivers and that got me my gui back. But now I think I configured my mouse wrong when i Was configuring my xserver. I have a usb mouse what option am I supposed to pick to configure that correctly. Theres nothing labled usb mouse.

---

