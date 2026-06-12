---
title: "Need help with Stratitec IC56A modem and Ubuntu 5.10"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Crow550 on 2006-07-14
The modem is asuppose to work with linux. But dahhhhh? What drivers do I use? I'm new to Ubuntu and linux in general.

[http://customer.stratitec.com/product_info.php?products_id=830](http://customer.stratitec.com/product_info.php?products_id=830) info on the modem

Thanks,

Crow550

---

### Post by az on 2006-07-14
An ISA hardware modem should not require drivers.  It should just be a serial device (/dev/ttyS0, /dev/ttyS1 /dev/ttyS2 or /dev/ttyS3)

---

### Post by Crow550 on 2006-07-14
It's pci and Ubuntu sees the modem when I look in devices.

---

### Post by Crow550 on 2006-07-14
bump...

---

### Post by Crow550 on 2006-07-14
Help? Anyone?

---

### Post by az on 2006-07-14
So what exactly happens when you try to configure your connection?

---

### Post by Crow550 on 2006-07-14
I goto network setup and click on the modem and click auto detect the modem and it doesn't find it. I try dev/ttyS0, /dev/ttyS1 /dev/ttyS2 and /dev/ttyS3 and none of em work.

---

### Post by az on 2006-07-14
Okay, it's not a hardware modem.

See here for drivers.

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

DSP is probably a Lucent modem, but I am not sure.

---

### Post by Crow550 on 2006-07-14
It is I believe. I think that's what Ubuntu says.

---

### Post by Crow550 on 2006-07-16
Confused about terminal commands. [https://help.ubuntu.com/community/DialupModemHowto#head-cc17ea0ff3df391406e74527f1aed569be04709f](https://help.ubuntu.com/community/DialupModemHowto#head-cc17ea0ff3df391406e74527f1aed569be04709f)

So I type in $ sudo sh -c "echo ltserial >> /etc/modules"
  $ sudo sh -c "echo ltmodem >> /etc/modules" 
Doesn't work with the $ sign and without it, it says /ect/modules does not exist. I will try doing a clean install of Ubuntu.

hmmm....

---

### Post by az on 2006-07-16
> **Crow550 said:**
> Confused about terminal commands. [https://help.ubuntu.com/community/DialupModemHowto#head-cc17ea0ff3df391406e74527f1aed569be04709f](https://help.ubuntu.com/community/DialupModemHowto#head-cc17ea0ff3df391406e74527f1aed569be04709f)

So I type in $ sudo sh -c "echo ltserial >> /etc/modules"
  $ sudo sh -c "echo ltmodem >> /etc/modules" 
Doesn't work with the $ sign and without it, it says /ect/modules does not exist. I will try doing a clean install of Ubuntu.

hmmm....

You can just open that file with any editor using sudo and add the word ltmodem to the end of the file on a line by itself.

sudo gedit /etc/modules

---

### Post by Crow550 on 2006-07-16
Well I found out the optical drive is either dirty or going bad. So I think the installation was corrupt so ill pop in a different optical drive and install it and enter the commands and see if it gives me the "/ect/modules does not exist"

---

