---
title: "Repair Install"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-10-06
I am moving my system from an ASUS socket 476 board to a Gigabyte AM2 socket.   The system will boot from the Live CD but not from the installed 7.04 on the existing HDD.

In Windows I would run the CD to perform a repair install which updates the HAL.   I guess there is something similar in Ubuntnu.  Could someone please tell me what is the recommended procedure since I really do not want to have to install and configure again .....

---

### Post by louieb on 2007-10-06
What do you mean by "won't boot" do you mean no gui? or does it stall out somewhere? where? do you get to the GRUB menu?
Will it boot to recovery mode? You might just boot to it and run 
```
dpkg-reconfigure xserver-xorg
```and see if that will fix X.

---

### Post by expatCM on 2007-10-06
what I mean is that the system starts up ...  grub loads and I stop it to add "noapic" at the end of the line to start (which otherwise gives a kernel panic error).   Then restart (press b in grub) and then the system brings up grub and runs through the startup lines.

I can see the line 

Maximum Resident Size: 0KB   Page faults with physical i/o: 0   Fail

and then the system runs through a few more lines and  hangs on the following line

*Running Local Boot Scripts (/etc/rc.local) OK

---

### Post by louieb on 2007-10-06
> **expatCM said:**
> *Running Local Boot Scripts (/etc/rc.local) OK
 
If you press enter at this point you should get the logon prompt or the root shell. Let me know.

---

### Post by expatCM on 2007-10-06
Ok ... you are spot on ...  I am impressed :)

The login prompt is returned.

---

