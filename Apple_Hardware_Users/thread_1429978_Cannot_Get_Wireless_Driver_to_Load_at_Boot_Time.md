---
title: "Cannot Get Wireless Driver to Load at Boot Time"
date: 2010-03-14
forum: Apple Hardware Users
---

### Post by mikeyrogers on 2010-03-14
I followed the instructions that came with the 802 .11 Linux STA driver and was able to initialize my card and connect to a protected network!  The instructions also tell me how to load the drivers at boot time, but I get an error when I try to run

```
# sh: for i in `find /lib /var -name wl\.ko`; do mv $i ${i}.orig; done
```The message returned is

```
bash: syntax error near unexpected token `do'
```Upon restarting, my wireless is no longer active.  My card is

Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

Thanks for your help!

---

### Post by mikeyrogers on 2010-03-16
Just curious if anyone has an answer for me.

Probably should add that I tried using the built-in driver installer, but am given an error, which is why I am trying to manually install the driver.

Thanks again.

---

### Post by linuxopjemac on 2010-03-16
what happens if you do:
```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by alexmurray on 2010-03-16
I agree, instead of trying to install the drivers manually, you should really try using the prepacked Ubuntu provided version of the driver which as @linuxopjemac said above you can easily install by installing the [bcmwl-kernel-source]("apt://bcmwl-kernel-source") package - this should be all which is needed rather than fussing about trying to install the driver manually.

---

### Post by linuxopjemac on 2010-03-16
Maybe he did not yet update his repository. Make sure you are connected to a wired internet connection. Then update your repository:

```
sudo apt-get update
```

Then you install the bcmwl-kernel-source

---

### Post by mikeyrogers on 2010-03-17
> **linuxopjemac said:**
> Maybe he did not yet update his repository. Make sure you are connected to a wired internet connection. Then update your repository:

```
sudo apt-get update
```Then you install the bcmwl-kernel-source

Sorry.  That didn't work.  It spits out:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
The following packages were automatically installed and are no longer required:
  python-urwid
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by linuxopjemac on 2010-03-17
So your broadcom driver was already installed. I would try to purge and reinstall:

```
sudo apt-get remove --purge bcmwl-kernel-source
```

then reinstall that package:

```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by mikeyrogers on 2010-03-18
> **linuxopjemac said:**
> So your broadcom driver was already installed. I would try to purge and reinstall:

```
sudo apt-get remove --purge bcmwl-kernel-source
```then reinstall that package:

```
sudo apt-get install bcmwl-kernel-source
```

Perfect, that did it!  Much appreciated!

---

