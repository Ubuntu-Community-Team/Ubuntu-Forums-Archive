---
title: "[SOLVED] New to Ubuntu 7.10 Issues"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by orangemoose on 2008-03-22
Issue 1

I have searched, read and attempted to get a Logitech Bluetooth mouse working, but it is still no go.

1. Edited etc/default/bluetooth and set 

BLUETOOTH_ENABLED=1

HIDD_ENABLED=1
HIDD_OPTIONS="--master --server"


2.  WIth mouse light blinking I run hcitool scan and hidd --search.  Both return no information.

3. I right click on bluetooth icon and browse device and no devices appear.

Any suggestions on where to look for more documentation would be greatly appreciated.

Issue 2

Touch pad is really flaky.  Can't grab windows and move them.  Double tapping is must be done very hard.  Adjusted setting under System->Preferences->mouse and still not working well.  

Issue 3

At boot up screen shows Failed to Allocate [.... something message.  Should I be concerened or just ignore the message?

Thank you if you can help.

---

### Post by jan quark on 2008-03-22
have you tried this guide:
[LIST]
[*][https://help.ubuntu.com/community/BluetoothMouse?highlight=%28bluetooth%29](https://help.ubuntu.com/community/BluetoothMouse?highlight=%28bluetooth%29)
[/LIST]

---

### Post by orangemoose on 2008-03-22
Yes, I tried this.  However, no devices show up in the list.

This mouse is functional in Vista so at least I know it works.

---

### Post by orangemoose on 2008-03-23
Ok, reinstall solved touchpad issues.

---

