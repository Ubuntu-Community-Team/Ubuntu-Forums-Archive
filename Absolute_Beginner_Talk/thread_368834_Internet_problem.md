---
title: "Internet problem"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by bluezapper on 2007-02-23
Hi,

I managed to connect to Internet using NetGear Usb wireless Lan adapter successfully and it was working perfectly fine as connection speed was perfect .

I am using Dapper Drake. Then it started installing updates. I installed all of them(around 113). When I rebooted the system the Network connection shows its connected as before but Firefox does not load any pages.

It tries and tries and finally says "server not found". I set ipv6 to true but still it does not work.

Please help me:( ,

thanks

bluezapper.

---

### Post by taurus on 2007-02-23
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ping -c 3 www.google.com
```

---

### Post by bluezapper on 2007-02-23
Hi Taurus,

Thanks for the reply. I finally made it work.\\:D/ 

I changed the setting from DHCP to static IP adress and filled in the details and Bingo firefox started and everything is fine. Infact Iam sending this reply from the Ubuntu internet connection.

But I would like to know if I will face this problem when I reboot again and above all why did this happen after updating as before I was connecting with DHCP.

thanks for the replies,

bluezapper

---

### Post by taurus on 2007-02-23
To learn whether your changed would work or not, you just have to reboot.  [-o<

---

### Post by bluezapper on 2007-02-23
I rebooted and you know what. It does not connect again. I changed the settings to DHCP and it works now.

Is there some Magic going on here :?

---

