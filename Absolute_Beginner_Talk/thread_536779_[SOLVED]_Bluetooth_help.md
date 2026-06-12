---
title: "[SOLVED] Bluetooth help"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by timo_01 on 2007-08-28
the main reason is because of bluetooth.i have tried similar wiki's for ubuntu but i don't seem to get it work though(ubuntu)detects the phone thro bluetooth usb. if anyone found another way,pls post back.
thanks

---

### Post by Dark Star on 2007-08-28
Hmmm strange .. So am planning for dell laptop with ubuntu had to use Xp for bluetooth :| OMG there must some guides lemme search some ;)

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) Hope this helps ..

---

### Post by timo_01 on 2007-08-28
> **Dark Star said:**
> Hmmm strange .. So am planning for dell laptop with ubuntu had to use Xp for bluetooth :| OMG there must some guides lemme search some ;)

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) Hope this helps ..

thanks dark star.
i will try the above link again although i tried it before.

phone specs:Motorola   L6

---

### Post by schorsch on 2007-08-28
Well .... let's start then with plugging in your bluetooth usb dongle and type in terminal:
```
hcitool dev
```
This will show if your dongle is detected and display its MAC adress.
After that turn on bluetooth on your phone and make it visible. Try
```
hcitool scan
```
to search for the phone. Please post the output here.

---

### Post by timo_01 on 2007-08-28
> **schorsch said:**
> Well .... let's start then with plugging in your bluetooth usb dongle and type in terminal:
```
hcitool dev
```
This will show if your dongle is detected and display its MAC adress.
After that turn on bluetooth on your phone and make it visible. Try
```
hcitool scan
```
to search for the phone. Please post the output here.

i will do that direct when i get off from work also with the output.
thanks once again

---

### Post by timo_01 on 2007-09-02
> **schorsch said:**
> Well .... let's start then with plugging in your bluetooth usb dongle and type in terminal:
```
hcitool dev
```
This will show if your dongle is detected and display its MAC adress.
After that turn on bluetooth on your phone and make it visible. Try
```
hcitool scan
```
to search for the phone. Please post the output here.

here s my output
```
pc@pc1:~$ hcitool dev
```
Devices:
        hci0    11:11:11:11:11:11


```
pc@pc1:~$ hcitool scan
```
Scanning ...
        00:9A:DB:12:2A:A0       motorola

what should i do ?

---

### Post by MenZa on 2007-09-02
Try reading the wiki page on BluetoothSetup as linked above, there should be a pretty good guide on how to use bluez to connect to your phone. :)

---

### Post by timo_01 on 2007-09-02
ok.almost there.i tried the wiki as given above,but when i try ```
sudo hidd --connect 00:9A:DB:12:2A:A0
```

i get ```
Can't get device information: Success
```
any suggestions

---

### Post by por100pre1 on 2007-09-02
Read about the [bug in gnome-bluetooth]("https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718") too. I right clicking the file I want to send and select to send it. :)

---

### Post by timo_01 on 2007-09-02
> **por100pre1 said:**
> Read about the [bug in gnome-bluetooth]("https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718") too. I right clicking the file I want to send and select to send it. :)

this really worked.i installed bluetooth file sharing and using the right click method as provided by por.

thanks to all

---

### Post by Perfect Storm on 2007-09-02
Changed title to something more useful and less flamable ;)

---

