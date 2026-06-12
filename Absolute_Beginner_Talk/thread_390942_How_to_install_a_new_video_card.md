---
title: "How to install a new video card"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-22
Hey! I just bough a GeFORCE fx 5200 and I was just wondering how to install it... after I put it in my computer, is ubuntu going to see it? Do I have to use the cd that comes with it to install the drivers? Do I need to do commands in Terminal?

---

### Post by digitzero on 2007-03-22
Hey your card should be automatically detected by Ubuntu when you boot up into it.

However, if you want to use the card for any fun stuff you'll want to install the Nvidia drivers.  Check out [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) for more info on the drivers.

---

### Post by taurus on 2007-03-22
Before you shut it down to put in your new graphic card, modify your /etc/X11/xorg.conf from a terminal

```
gksudo gedit /etc/X11/xorg.conf
```
and replace whatever the current driver with vesa.

```
Driver     "vesa"
```
Then, shut down the computer and insert the new nVidia graphic card.  Boot the machine and X should come up except the refresh is kind of slow which is expected since you are using vesa driver.  Now, install nVidia driver for your graphic card with this.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by julie_lebou on 2007-03-22
But the drivers I need are not all on the cd? Do I use the cd at all?

---

### Post by taurus on 2007-03-22
Don't worry about the CD that comes with your card.  It's for Windows.  Use the link from my previous post to download envy.  Then, use envy to install nVidia driver for your new graphic card.

---

### Post by julie_lebou on 2007-03-22
Thanks you! Makes sence!

---

