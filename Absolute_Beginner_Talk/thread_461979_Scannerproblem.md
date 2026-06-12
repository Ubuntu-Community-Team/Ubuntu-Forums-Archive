---
title: "Scannerproblem"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Bengt12 on 2007-06-02
Hi
I am new to Ubuntu, and happy with Feisty. But run into a problem when I tried to use my scanner a Agfa Snapscan 1212U. It is detected by Xsane but it give the error message:
Error:
Failed to open device snapscan:libusb:004:002': 
Invalid argument.
This result i got when checked for USB devices 
  Bus=05 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
DT:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:10.4
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=05 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0930 ProdID=6533 Rev= 1.00
S:  Manufacturer=Kingston
S:  Product=DataTraveler 2.0
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=31875us
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=64ms

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.3
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS= 8 #Cfgs=  1
P:  Vendor=06bd ProdID=2061 Rev= 1.00
S:  Manufacturer=AGFA 
S:  Product=SNAPSCAN
C:* #Ifs= 1 Cfg#= 1 Atr=40 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=16ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.2
:

I checked the lists for solutions, but i did not anything that is working for me. So I hope you can help me with this problem
B

---

### Post by Bengt12 on 2007-06-03
Hallo
Anyone out there, with any ideas on how to solve this problem.
B

---

### Post by steefjeqv on 2007-06-04
Hi,

I'm also using the 1212u.

You need to install additional firmware to get the scanner operational.

Just untar the attachement and add it :

/usr/share/sane/snapscan/Snapscan1212U_2.bin

Greetings,
Steven

---

### Post by Bengt12 on 2007-06-07
Thanks for reply.
 will try that
Bengt

---

### Post by steefjeqv on 2007-06-07
Hi,

It should work just fine.
Note : You may have to create the snapscan directory under sane.

Greetings,
Steven

---

### Post by Bengt12 on 2007-06-10
Hi again
I did follow your instructions but I did not get it to work. I still get the same error message.
"failed to open device snapscan:libusb:04:002: invalid argument.
All the best
bengt

---

### Post by steefjeqv on 2007-06-10
Hi Bengt,

This may be a silly suggestion, but I actually had to switch the scanner off and on by using the button next to the green LED.
After doing that Sane recognized the Snapscan.

I forgot to mention one IMPORTANT thing (sorry).
You have to edit line 5 of your /etc/sane.d/snapscan.conf file like follows : see attachement.

This should do the trick.

Greetings,
Steven

---

