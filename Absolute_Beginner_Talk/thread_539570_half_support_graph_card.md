---
title: "half support graph card"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-08-31
I have bought a new pc with powercolor 2600xt DDR4.
Without the restricted driver if I change the resolution, the screen just **** up like a multi-color rainbow.
With restricted driver I can't even boot into gui version of ubuntu.
I got this error.
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Image009.jpg[/IMG]

---

### Post by marx2k on 2007-08-31
Who makesthet video card?

Please post /etc/X11/xorg.conf
Please post /var/log/Xorg.0.log

Also, if you could, post the output of 'lspci | grep VGA'

---

### Post by zerobinary on 2007-08-31
k i will try.

---

### Post by zerobinary on 2007-09-01
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9588
In order to get it work i have to reinstall linux.
I reinstall two times already but still face the same issue, and restricted driver only make it worst.

---

### Post by splintercellguy on 2007-09-01
Strange the unknown device, have you tried Envy?

---

### Post by zerobinary on 2007-09-01
envy, what is that.

---

### Post by zerobinary on 2007-09-01
Envy is not working.
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-16.png[/IMG]

---

### Post by zerobinary on 2007-09-02
any support

---

### Post by zerobinary on 2007-09-02
Need some help plz.

---

### Post by overdrank on 2007-09-02
> **zerobinary said:**
> Need some help plz.

Hi if you will use the command in the terminal 
```
sudo update-pciids
```
This will update the ids and hopefully with the lspci command you can tell us which video card you have.

---

### Post by zerobinary on 2007-09-03
```

zerobinary@zerobinary-desktop:~$ 
zerobinary@zerobinary-desktop:~$ sudo update-pciids
Password:
--11:40:45--  http://pciids.sourceforge.net/v2.2/pci.ids.bz2
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 126,631 (124K) [text/plain]

100%[====================================>] 126,631      212.57K/s             

11:40:46 (212.16 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [126631/126631]

Done.

```
I am using powercolor 2600xt ddr4

---

### Post by zerobinary on 2007-09-03
when i change the resolution it still screw up.
And i can't take a screen shot for it, the image just turn back to normal when I restart the pc.

---

### Post by zerobinary on 2007-09-03
how the screen look
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Image007-2.jpg[/IMG]

---

### Post by marx2k on 2007-09-04
Well, how's it look to you? :) The colors seem a little off to me.

---

### Post by zerobinary on 2007-09-05
LOL, yeah that's what happen when i try to change the resolution too.
And try installing restricted driver is even worst.

---

### Post by zerobinary on 2007-09-05
When will dirvers for ati 2600xt ddr4 come out

---

