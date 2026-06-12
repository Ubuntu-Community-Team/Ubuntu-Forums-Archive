---
title: "GPRS Mobile connections"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by dodgy_devil on 2007-02-16
I am trying to connect to the internet from my Sony Ericsson W800i using a data cable. I was able to connect through wvdial using the following wvdial config file
/**
[Dialer Defaults] 
Phone = *99***1# 
#Phone = *99# 
Username = anything 
Password = anything 
Stupid Mode = 1 
Dial Command = ATDT 

[Dialer pin] 
Init1 = AT+CPIN=1234 

[Dialer gprs] Modem = /dev/ttyACM0 
Baud = 115200 
Init2 = ATZ 
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2 
ISDN = 0 
Modem 
Type = Analog Modem
*/

then, connect with


"sudo wvdial gprs"

I can see on the phones display that it connects as well as in the terminal but when i browse the internet i get no response. Is there any way i can see what is my connection status or it might even be that the OS are still using my ethernet connection settings althought it is plugged. OS = Ubuntu edgy

Hope someone can helphttp://ubuntuforums.org/images/icons/icon13.gif
Thumbs down

---

