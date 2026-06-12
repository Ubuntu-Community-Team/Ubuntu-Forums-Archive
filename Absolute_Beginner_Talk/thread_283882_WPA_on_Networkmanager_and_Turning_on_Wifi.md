---
title: "WPA on Networkmanager and Turning on Wifi"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-24
1) How do I add WPA support on networkmanager? I really like the program, but if it supported WPA so I can connect to my friend's network, it would be great. Thanks!

2) I finally figured out how to turn off the wifi card on my Dell Inspiron E1405 laptop. Hold the Fn key and press 2/@. However. If I turn it off and restart the computer. The wifi card remains off. This is expected behaviour. However, when I turn it on when Ubuntu booted with it being off, networkmanager does not recognize the wifi card. I have to restart again to use it. How do I fix this issue? Thanks!

---

### Post by amitroy5 on 2006-10-25
bump

---

### Post by amitroy5 on 2006-10-25
bump

---

### Post by TheMono on 2006-10-25
As far as the first question is concerned, it should work by default? 

If you left click on Network Manager and click 'connect to other wireless network', under the options for encryption do you have WPA in there?

As far as the second is concerned, I'm unsure sorry.

---

### Post by amitroy5 on 2006-10-25
Thanks for your help. I restarted and mysteriously, my wifi card has wifi support. So, #1 is solved. I still need help on #2 though. Thanks!

---

### Post by studentism on 2006-10-25
For #2: After turning it back on (hardware), do you get any valid extensions from iwconfig?

---

### Post by amitroy5 on 2006-10-25
I am not sure what you mean.

> **studentism said:**
> For #2: After turning it back on (hardware), do you get any valid extensions from iwconfig?

---

### Post by studentism on 2006-10-26
> **amitroy5 said:**
> I am not sure what you mean.

Type ```
iwconfig
``` at a terminal and see which one gives about 8 lines of output (the first of which should contain "ESSID: foo" or so (foo part is variable).  Write down the name of the connection.  (This should be done on a boot where you had it enabled/working.)

Then, when you get the chance, reboot the machine with the hardware switch off.  "iwconfig" at a terminal should show nothing with a wireless extension.  Next, hardware switch on, and then "iwconfig".  See if there is a difference after that switch.

There are a few ways to proceed after that based on the results.

---

