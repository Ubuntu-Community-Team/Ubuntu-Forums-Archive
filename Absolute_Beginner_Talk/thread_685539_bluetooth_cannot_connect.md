---
title: "bluetooth cannot connect"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by brokenhachi on 2008-02-02
i was able to sync my phone with bluetooth, but when i click browse device and then connect i get this error..


> obex://[00:15:b7:20:14:e1]" is not a valid location. please check the spelling and try again


i have no idea what obex is... help?

---

### Post by PmDematagoda on 2008-02-02
Install the obexftp package using:-
```
sudo apt-get install obexftp
```
and see if that solves your problem.

---

### Post by brokenhachi on 2008-02-02
didnt help...

---

### Post by brokenhachi on 2008-02-02
is there no way to fix this?

---

### Post by Random20230808 on 2008-02-02
Try this :
```
sudo apt-get install gnome-vfs-obexftp
```
It has worked for lots of people.

---

### Post by brokenhachi on 2008-02-02
ok, now it says 

> Couldn't display "obex://[00:15:b7:20:14:e1]" check if the service is available

---

### Post by Random20230808 on 2008-02-02
I have the same problem too.
I' ve read that it is a reported bug.
However for some people it does work.

Try this :```
sudo apt-get install gnome-bluetooth
```
After installation goto Applications->Accessories->Bluetooth  File Sharing.

This application allows you to transfer files between your PC and mobile.
You right-click on the file and you choose Send to...->Send as : Bluetooth...
It does not let you browse your mobile from your PC.

Read more in this webpage : [https://help.ubuntu.com/community/BluetoothSetup?highlight=%28bluetooth%29]("https://help.ubuntu.com/community/BluetoothSetup?highlight=%28bluetooth%29")

---

### Post by brokenhachi on 2008-02-03
well i was able to get that menu, but when i try to send it tells me "unable to connect to device"


maybe because my phone is not on this list i cannot use it?

[http://www.holtmann.org/linux/bluetooth/features.html](http://www.holtmann.org/linux/bluetooth/features.html)

---

### Post by Random20230808 on 2008-02-04
You should first pair your device with your PC.
Make your device and your PC (through the bluetooth icon on the top panel) discoverable.
Search your PC from your mobile and follow instructions.
After you connect the two device, you can send files to each other.

---

### Post by brokenhachi on 2008-02-04
thats what i did and it doesnt work.. it just gives me that error.

---

### Post by Random20230808 on 2008-02-04
Well, try to connect to your PC from your mobile.
Then, when you connect, try to send a file at once.
What do you get?
Do you still get the error message?

---

