---
title: "connect my nokia n series to gprs with data cable"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by tony2 on 2007-10-09
how to connect to internet using nokia n series phone. i am able to connect to gprs internet in windows. i want to connect to the gprs internet using ubuntu. 

kindly guide me as to how to connect to the net using nokia n series mobile and through gprs. please kindly note i don't use bluetooth. i use a data cable to connect my nokia phone with my computer.

---

### Post by mmarshall on 2007-10-11
Using the phone with USB should be about the same as with bluetooth... you just skip the bluetooth part :)  For me the phone will show up as /dev/ttyACM0.

Here is a guide using kppp that should work:
[http://www.integrasoftware.it/index.php?option=com_content&task=view&id=84&Itemid=28](http://www.integrasoftware.it/index.php?option=com_content&task=view&id=84&Itemid=28)

Just skip ahead to the "Connection setup" part :)

MWM

---

### Post by MrKlean on 2007-10-11
I use wvdial for my N75 and it works great ; )

---

### Post by tony2 on 2007-10-13
ok i will try to explain as far as i can so that someone could help.

in my xubuntu 7.04 wvdial package is installed but the graphical user interface of the dialer is not installed. so i don't see any dialup icons. 

i tried to download from synaptic but since i currently dont have any other connection and the only internet connection i use is not working yet i couldn't download the wvdial gui interface. 

anyhelp to connect me to the net would be of immense help to me as well as to many others. thankz.

Update: the package that is not installed is gnome-ppp. can i download it directly from the net in windows?

---

### Post by tony2 on 2007-10-18
i installed gnome-ppp now. but my nokia phone (via usb cable) is not detected now. how to make xubuntu detect my nokia phone.

---

### Post by mmarshall on 2007-11-04
Try typing the command "dmesg" after plugging in your phone.  See if there is anything new printed at the end.

I get this:
[118843.309000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[118843.521000] usb 2-2: configuration #1 chosen from 1 choice
[118843.523000] cdc_acm 2-2:1.0: ttyACM0: USB ACM device

You see the "ttyACM0" part?  That means my modem is at /dev/ttyACM0

I hope that helps.

MWM

---

### Post by tony2 on 2007-11-12
yes i see "ttyACM0" part. But i am not able to get connected to internet.

an operating system without an internet connection is useless nowadays. 

that is my current situation now :(

---

