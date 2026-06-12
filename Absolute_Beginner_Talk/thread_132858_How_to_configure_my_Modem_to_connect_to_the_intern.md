---
title: "How to configure my Modem to connect to the internet?"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by agarwaldvk on 2006-02-19
Hi Everybody

Can someone assist me in configuring my modem (Supervoice HSF modem) so that I can connect to the internet?

In the least, pointers to the right web page where I can find the relevatn information is all I am looking for.


Best regards


Deepak Agarwal

---

### Post by kvorion on 2006-02-19
What kind of internet connection are you using? Does the operating system recognize your modem?

---

### Post by agarwaldvk on 2006-02-19
Hi KVorion

Sorry, mate!

I am using dial up - no broadband yet, Can't afford it yet!

I don't know what you mean by 'If the OS recognize it'?. My Windows 2000 does. Are you talking about Ubuntu Hoary OS? If yes, how do I check if it is or it is not?

Admittedly, I am an ABSOLUTE novice when it comes to Linux and it variants but I want to get in and abandon Windows for GOOD!!!!!!!

So please continue to bear with me! I will eventually get there!


Best regards


Deepak Agarwal

---

### Post by OBnascar on 2006-02-19
[QUOTE=agarwaldvk]I am using dial up [/QUOTE]

Lets start out asking you if your dial-up modem is a internal or external. If it is a external I should be able to help you. If you have an internal modem, you will most likely not have much luck to get that connected in Linux. You would be better off purchasing a external from the get-go, less headaches and they do work. You can get one on Ebay for around $20.

---

### Post by agarwaldvk on 2006-02-20
Guys

It appears that I cannot connect to the internet because I have an internal modem. That's ok, not really but well if that's what reality is all about so be it.

However, would I have the same problem with broadband?


Best regards


Deepak Agarwal

---

### Post by manicka on 2006-02-20
[QUOTE=agarwaldvk]
However, would I have the same problem with broadband?
[/QUOTE]

The short answer is 'no' as you wouldn't be using a winmodem to connect. Depending on what type of winmodem it is, you still may be able to use it. This link may help

[https://wiki.ubuntu.com/DialupModemHowto#head-cc17ea0ff3df391406e74527f1aed569be04709f](https://wiki.ubuntu.com/DialupModemHowto#head-cc17ea0ff3df391406e74527f1aed569be04709f)

---

### Post by agarwaldvk on 2006-02-20
Manicka

Thanks for your response.

I shall try and see if I can this going using the link that you have shown.


Best regards


Deepak Agarwal

---

### Post by Preksus on 2006-02-20
I have been here with my modem.  Basically there are two types of modem, software modems and hardware modems.  Software modems rely on software in windows for them to work.  Hardware modems dont use the software in windows, so working independently from an operating system.  You need either an internal hardware modem or a preffered external modem which will be detected by and Linux flavour operating system.

John Knowles

---

### Post by curley_sue on 2006-03-01
in general u can follow:
[http://easylinux.info/wiki/Ubuntu#How_to_identify_Modem_chipset](http://easylinux.info/wiki/Ubuntu#How_to_identify_Modem_chipset)

easiest way to install HSF modem driver on BREEZY:
[http://www.linuxant.com/drivers/hsf/downloads-installer.php](http://www.linuxant.com/drivers/hsf/downloads-installer.php)
download the installer (there's a link on the page under "How to install the driver using the installer"): [http://www.linuxant.com/drivers/hsf/full/archive/cnxtinstall.run](http://www.linuxant.com/drivers/hsf/full/archive/cnxtinstall.run)

and follow the instructions...

it worked on my laptop (HP Pavilion ze2070ea) which has:
Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M)
AC'97 Modem Controller,

pls note:
The  SubSystem 103c:3080  Hewlett-Packard Company has a Conexant chip.

There channels:
----active COMM services are ------------
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:77:32:73
          inet6 addr: fe80::2c0:9fff:fe77:3273/64 Scope:Link
eth1      Link encap:Ethernet  HWaddr 00:0E:35:E3:4D:C8
          inet6 addr: fe80::20e:35ff:fee3:4dc8/64 Scope:Link

must be shut down before modem usage or browser naviagation will fail.
 Do so with
$ sudo ifdown eth0
$ sudo ifdown eth1
Verify they are not seen in output of
$ ifconfig


two problems:
1. unless u get the lisence (for which u have to pay 20$ at the time of writing)
u will have limited connectivity (14k I think) and no fax...
2. suspend to RAM stopped working on my laptop after the installation. fuctionality was retrieved after i removed the installation of the HSFmodem using Synaptic. (I can't really tell how and why, newbie after all...)

Hope that helps...

---

