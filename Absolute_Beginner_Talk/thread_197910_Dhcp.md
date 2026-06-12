---
title: "Dhcp"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by czambran on 2006-06-16
How can I force my card to try to renew/get an ip?

On windows I do it with: ipconfig /renew

I am looking for how to do the same on linux.


Thanks All

---

### Post by kb3hkg on 2006-06-16
you can do it through the GUI Network Manager, or by command line using ifconfig down <interface> and ifconfig up <interface>

---

### Post by 5-HT on 2006-06-16
[quote=kb3hkg]you can do it through the GUI Network Manager, or by command line using ifconfig down <interface> and ifconfig up <interface>[/quote]

With DHCP, after entering the commands listed by kb3hkg, you may also need to enter ```
 sudo dhclient <interface> 
``` 

To find your interface (usually 'eth0' for the primary NIC), just entering 'ifconfig' (~ equivalent to ipconfig -all in windows) will let you know.

There will be no need to enter the dhclient command if you're releasing/renewing from the GUI utility.

HTH

---

