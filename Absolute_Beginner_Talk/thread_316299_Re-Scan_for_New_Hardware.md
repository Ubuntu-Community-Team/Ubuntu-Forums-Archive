---
title: "Re-Scan for New Hardware?"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by unquenchablefire on 2006-12-10
I installed xUbuntu on my ancient eMachine 333id. It runs pretty well, considering how old the machine is. I installed new hardware after i installed Linux however, and i would like to know how to scan for new hardware. I installed a DVD drive and a Wireless networking card.

---

### Post by grumpymole on 2006-12-10
I believe that hardware should be automatically detected.  Depending on the type, you may need to do some extra configuration to get it working.  There are a couple of options to see if it has been detected:

1.  In a command window, type *dmesg* and see if you can see any messages relating to the specific hardware.
2.  Alternatively and also in a command window, type *tail -f /var/log/syslog*.  Then, insert the hardware, like the wireless card and see what messages come up.  This should give you an indication of whether the hardware is being detected or not.

There is some good information [here]("https://help.ubuntu.com/community/WifiDocs") for installing wireless networking cards.

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

