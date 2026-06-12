---
title: "Apple bluetooth keyboard support with ubuntu-mate"
date: 2017-01-09
forum: Apple Hardware Users
---

### Post by ubuntini2 on 2017-01-09
Am much closer following this 'recipe' (3rd answer) and also cross referencing Arch wiki

[http://askubuntu.com/questions/73031...nnect-in-15-10]("http://askubuntu.com/questions/730316/apple-wireless-keyboard-wont-connect-in-15-10")

Only change so far is had to  use
     
     ```
sudo apt-get install bluez:i386 
```
to get bluetoothctl

ok so works initially BUT
after reboot NO bluetooth icon in my Panel and bluetooth not working

Also if I try and duplicate the install I get


     > [bluetooth]# scan on
Failed to start discovery: org.bluez.Error.NotReady
 

result of [bluetooth]# show

     > Controller 5C:F3:70:7D:3D:BC
    Name: Art3mis
    Alias: Art3mis
    Class: 0x000000
    Powered: no
    Discoverable: no
    Pairable: yes
    UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
    UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
    UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
    Modalias: usb:v1D6Bp0246d0525
    Discovering: no 
result of systemctl status bluetooth:

     > bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: active (running) since Tue 2017-01-10 09:52:19 EST; 10min ago
     Docs: man:bluetoothd(8)
 Main PID: 9221 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;9221 /usr/lib/bluetooth/bluetoothd

Jan 10 09:52:19 Art3mis bluetoothd[9221]: Not enough free handles to register se
Jan 10 09:52:19 Art3mis bluetoothd[9221]: Not enough free handles to register se
Jan 10 09:52:19 Art3mis bluetoothd[9221]: Not enough free handles to register se
Jan 10 09:52:19 Art3mis bluetoothd[9221]: Current Time Service could not be regi
Jan 10 09:52:19 Art3mis bluetoothd[9221]: gatt-time-server: Input/output error (
Jan 10 09:52:19 Art3mis bluetoothd[9221]: Not enough free handles to register se
Jan 10 09:52:19 Art3mis bluetoothd[9221]: Not enough free handles to register se
Jan 10 09:52:19 Art3mis bluetoothd[9221]: Sap driver initialization failed.
Jan 10 09:52:19 Art3mis bluetoothd[9221]: sap-server: Operation not permitted (1
Jan 10 09:52:19 Art3mis systemd[1]: Started Bluetooth service. 

hcitool scan

     > Device is not available: No such device 
Any bluetooth experts reading this that can help? Am using an Asus BT400 Bluetooth dongle.

---

### Post by howefield on 2017-01-10
Thread moved to the "*Apple Hardware Users*" forum.

---

