---
title: "unable to connect bluetooth devices"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by ubunt22rock on 2008-02-10
guys i just installed wammu for my SE w850. i cant connect it thro bluetooth. i noticed i cant send or receive files through bletooth either. please help. i think i have installed bluez.

---

### Post by linuxwizard on 2008-02-10
Look over this
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by ubunt22rock on 2008-02-12
thanks for the reply. but, the documentation helps only feisty users but i'm a gutsy user

---

### Post by ubunt22rock on 2008-02-12
i tried the commands on the page anyway. 
the command:
hcitool dev
returns nothing.
my laptop has integrated bluetooth.how do i make use of it?

---

### Post by linuxwizard on 2008-02-12
That link will work for all versions. Is your device supported ? Here is a list you can go through. If your device has an HCI version listed, it should work under Linux.

[http://www.holtmann.org/linux/bluetooth/features.html](http://www.holtmann.org/linux/bluetooth/features.html)

---

### Post by piju on 2008-02-12
restart ur bluetooth, type sudo /etc/init.d/bluetooth restart

then on bluetooth on ur devices

using hcitool, scan ur devices, type sudo hcitool scan

is ur device scanable ?

---

### Post by ubunt22rock on 2008-02-12
hcitool scan returns
Device is not available: No such device

i dont think my device is detected

---

