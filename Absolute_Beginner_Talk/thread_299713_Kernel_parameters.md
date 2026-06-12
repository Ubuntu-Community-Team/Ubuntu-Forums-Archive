---
title: "Kernel parameters"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Robert.Zapata on 2006-11-14
Hello Team and pardon my ignorance......:( 


How do you configure the Kernel parameters...???

I'm trying to install the madwifi driver for my Atheros card and following the instructions at:

[http://madwifi.org/wiki/UserDocs/KernelConfig](http://madwifi.org/wiki/UserDocs/KernelConfig)

> 
Kernel 2.6.x: ¶

    * General setup &#8594; Configure standard kernel features (for small systems) &#8594; Sysctl support: enabled
    * Loadable module support &#8594; Module versioning support: disabled
    * Device Drivers &#8594; Network device support &#8594; Wireless LAN (non-hamradio) &#8594; Wireless LAN drivers (non-hamradio) & Wireless Extensions: enabled
    * Cryptographic options &#8594; Cryptographic API: enabled
    * Cryptographic options &#8594; Cryptographic API &#8594; HMAC support: enabled
    * Cryptographic options &#8594; Cryptographic API &#8594; AES cipher algorithm: enabled (optional, needed for WPA/WPA2 with CCMP) 


I know that the parameters go in the file /etc/sysctl.conf

but how do you input the commands mentioned in the link...??

Thank you very much.

---

### Post by Blutack on 2006-11-14
From the looks of this is a list of stuff that should be compiled into the kernel when it is built.  If you have not compiled your own kernel (you would know if you had) then I'm fairly sure they will all have been compiled in when the Ubuntu team built the edgy kernel.  So you don't need to do anything!

---

### Post by Robert.Zapata on 2006-11-14
Blutack:

I'm still using 6.06LTS. Do not want to upgrade yet. So far I have 6.06 installed in another Notebook (Toshiba Satellite P35) and an Intel Desktop and everything works fine.

My problem is with this new Thinkpad R60e and the Wireless card (Atheros AR5212)

Thanks. ;)

---

