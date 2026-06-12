---
title: "bluetooth keyboard help..."
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-08-25
i have a stowaway bluetooth keyboard by Think Outside.

the probelm is it cant maintain its connection...can anyone help?


i can get it to connect like this:
sudo hidd --search 
and then really really fast typing in 4 numbers before i get the output: Connecting to device 00:16:38:EC:27:0D

for some reason this procedure can only be done once per boot...
if i go out of range or lose my connection hidd --search wont detect the keyboard again unless i reboot.

I tried sudo gedit /etc/bluetooth/hcid.conf 

and adding:

device 00:16:38:EC:27:0D {
     name "Think Outside Keyboard";
     auth enable;
     encrypt enable;
 }



and i also tried 
sudo gedit /etc/default/bluez-utils

and adding:
 HIDD_ENABLED=1
 HIDD_OPTIONS="--master --connect 00:16:38:EC:27:0D  --server" 

can anyone help me, this is really frustrating....
thanks

---

