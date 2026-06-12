---
title: "How to connect and transfer data from mobile phone SE k700i"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by duvkata on 2007-03-02
I don`t know how to connect my mobile phone to the computer.I am using ubuntu 6.10 and my phone is Sony Ericsson K700i.I have a bluetooth device connected to the usb.It`s called Bluesoleil if that matters : [http://www.bluesoleil.com/products/index.asp?topic=main_bluesoleil]("http://www.bluesoleil.com/products/index.asp?topic=main_bluesoleil")
if someone can help me i`ll be very happy.thanks in advance

---

### Post by Goodson1974 on 2007-03-02
Hi

I've been able to transfer stuff to and from my SE K700i using the USB connection cable and a program called Wammu.

I've not tried anything with bluetooth yet.

If you've got the UBS cable i'd suggest trying that first :)

---

### Post by kronepils on 2007-03-07
I have used a k700i over bluetooth (it's broken now, so i can only help you from memory)

The first question, do your bt dongle work out of the box?

You should install all bluetooth stuff. bluez is the library, gnome-bluetooth is also important. I don't know which is default or if there is more you need.

There are several gnome applications that can send/receive files.
From nautilus, you should be able to send files to any bluetooth unit. You have to start a small app to receive files. It's in programs->accesories (is it called that? Mine is in Danish...) and called something like "Bluetooth file sharing" (again, in Danish here).


Try to run "hcitool scan" from a terminal. It should scan for all bt devices, and list your phone (if it's enabled)

Edit /dev/bluetooth/rfcomm.conf, using the example, but change the device to the hardware adress of your phone (from hcitool scan output)

Next, you have to edit /etc/default/bluetooth to enable bluetooth a startup.

After a reboot, or a /etc/init.d/bluetooth restart, you should have a device called /dev/rfcomm0 that you "talk" to.

You can use wammu, but I can't remember the settings. The device is /dev/rfcomm0 and I think you should use btobex (or something like that)


Good luck!! You'll need it! (Just kidding :))

---

### Post by negativex on 2007-05-04
maybe this will help
[http://stefans.datenbruch.de/k750i/#interfacing](http://stefans.datenbruch.de/k750i/#interfacing)

---

