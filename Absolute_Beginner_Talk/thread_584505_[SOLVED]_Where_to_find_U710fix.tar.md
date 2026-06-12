---
title: "[SOLVED] Where to find U710fix.tar?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Cet on 2007-10-21
I wanted to create a install/live/persistent usb-stick following this manual: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
but cannot find the mentioned U710fix.tar. 
Anyone knows where to find? 
And did anyone tried this persistent usb-stick? Last time I tried it with 6.10 and 7.04 I had to give up, it was quite frustrating as it did not worked because it locked up my notebook.
But I will try it again and again with every new Ubuntu release because the hope dies at last! ;-)

---

### Post by mikeyphi on 2007-10-21
Sure you followed the guide?
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I downloaded the U710fix.zip OK (Perhaps the original .tar is now packaged as .zip)?

---

### Post by Cet on 2007-10-21
> **mikeyphi said:**
> Sure you followed the guide?
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I downloaded the U710fix.zip OK (Perhaps the original .tar is now packaged as .zip)?

I  cannot find the download link for U710fix in your link. Can you please give me the download link for U710fix? TIA, Cet

---

### Post by bodhi.zazen on 2007-10-21
The command is malformed, it should read :

```
wget http://pendrivelinux.com/downloads/U710fix.zip
```

workd fine : > bodhi@VirtualUbuntu:~$ wget [http://pendrivelinux.com/downloads/U710fix.zip](http://pendrivelinux.com/downloads/U710fix.zip)
--13:32:04--  [http://pendrivelinux.com/downloads/U710fix.zip](http://pendrivelinux.com/downloads/U710fix.zip)
           => `U710fix.zip'
Resolving pendrivelinux.com... 69.89.27.206
Connecting to pendrivelinux.com|69.89.27.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 939 [application/zip]

100%[====================================>] 939           --.--K/s

13:32:05 (32.05 MB/s) - `U710fix.zip' saved [939/939]

---

### Post by Cet on 2007-10-21
> **bodhi.zazen said:**
> The command is malformed, it should read :

```
wget http://pendrivelinux.com/downloads/U710fix.zip
```

workd fine :

Thank you! Download worked fine at me, too! :popcorn:

---

### Post by staticvoid on 2007-11-16
Yay! Me too! Mark this thread as [SOLVED]  :)

---

### Post by champsampson on 2007-12-03
Don't forget to re-connect to the internet while running off live CD. 

That was my problem. :)

---

### Post by MDuffy on 2007-12-18
For those of you who may still be struggling with getting the U710fix fle, try this URL: [http://www.progdan.no-ip.org:25000/fileadmin/downloads/U710fix.zip](http://www.progdan.no-ip.org:25000/fileadmin/downloads/U710fix.zip)

---

