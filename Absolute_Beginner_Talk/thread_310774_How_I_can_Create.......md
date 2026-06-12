---
title: "How I can Create......"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by vboyz on 2006-12-01
Dear ubuntu i am a new user of ubuntu for 3 to 4 Days.I dont know how to make a dial-up internet connection in ubuntu .It is very neceessary to me.I am an indian using phone i conncet the internet.....
My internet provider :Sancharnet
Phone No: 172233
Username:vinodn37
password: *******

please help me any one by step by step.Because i am a new user in linux

and also wish to know that can i install both ubuntu an d windows in same system and how

---

### Post by eriefisher on 2006-12-01
What type of modem do you have?

serial?
usb?
winmodem?

---

### Post by deadgobby on 2006-12-01
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by daniminas on 2006-12-01
You can use wvdial:

> sudo wvdialconf

Then edit the file to put the right phone number/user/etc:

> sudo gedit /etc/wvdial.conf
//You will see something like this:
[Dialer Defaults]
Modem = /dev/ttyS2
Baud = 57600
Init = ATZ
Init2 = AT
S11=50
Phone = 555-4242-the-phonenumber
Username = my-user
Password = my-password


And to connect to the internet:

> sudo wvdial

And.. open your web browser and.. that's it..

=)

---

### Post by vboyz on 2006-12-01
Over the CD
frontech internal modem
Model No.: JIL-0313

on the computer
Motorola SM56 speaker phone

---

### Post by Chinkostu on 2006-12-01
use wvdial. it should already have drivers for 56k modems, most internal ones nowadays are the same PCB's and chipsets.

---

### Post by vboyz on 2006-12-02
how i can use > wvdial(from where did i get it)
plase tell in step by step because i am a new user of linux for three days

---

### Post by daniminas on 2006-12-04
If you dont have the wvdial app installed, (console program) do:

> sudo apt-get install wvdial

and then in the console:

> **daniminas said:**
> You can use wvdial:

> sudo wvdialconf

Then edit the file to put the right phone number/user/etc:

> sudo gedit /etc/wvdial.conf
//You will see something like this:
[Dialer Defaults]
Modem = /dev/ttyS2
Baud = 57600
Init = ATZ
Init2 = AT
S11=50
Phone = 555-4242-the-phonenumber
Username = my-user
Password = my-password


And to connect to the internet:

> sudo wvdial

And.. open your web browser and.. that's it..

=)


Good luke!

---

### Post by nixclusive on 2006-12-04
Hello there, do you use an internal modem or an external one?

---

