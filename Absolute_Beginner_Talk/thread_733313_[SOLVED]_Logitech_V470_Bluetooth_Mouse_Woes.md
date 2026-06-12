---
title: "[SOLVED] Logitech V470 Bluetooth Mouse Woes"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by orangemoose on 2008-03-23
Bluetooth Mouse Issues

After Gutsy reinstall BT mouse IS working --woo hoo-- But it does not show up in the BT applet and 

hcitool scan times out.

hcitool dev 

Devices:
        hci0    00:1B:FB:58:87:3F

Is that the address of the BT adapter?


grep Bluetooth /var/log/messages

Produces this output.  Does that mean that my BT adapter is recognized and configured?

Mar 23 15:41:10 kernel: [   15.888000] Bluetooth: HCI socket layer initialized
Mar 23 15:41:10 kernel: [   15.960000] Bluetooth: HCI USB driver ver 2.9
Mar 23 15:41:12 kernel: [   20.304000] Bluetooth: L2CAP ver 2.8
Mar 23 15:41:12 kernel: [   20.304000] Bluetooth: L2CAP socket layer initialized
Mar 23 15:41:12 kernel: [   20.464000] Bluetooth: RFCOMM socket layer initialized
Mar 23 15:41:12 kernel: [   20.464000] Bluetooth: RFCOMM TTY layer initialized
Mar 23 15:41:12 kernel: [   20.464000] Bluetooth: RFCOMM ver 1.8
Mar 23 15:58:51 kernel: [   13.556000] Bluetooth: Core ver 2.11
Mar 23 15:58:51 kernel: [   13.556000] Bluetooth: HCI device and connection manager initialized

I tried the Blueman program but it did not produce any different results.

---

### Post by steveneddy on 2008-03-23
Please read [the entire thread.]("http://ubuntuforums.org/showthread.php?t=586105")

---

### Post by orangemoose on 2008-03-24
Reinstall did the trick

---

### Post by steveneddy on 2008-03-25
> **orangemoose said:**
> Reinstall did the trick

Please mark this as solved.

---

