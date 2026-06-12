---
title: "DHCP IP Address Renewal"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-03-30
is there an Ubuntu command for ipconfig?  I plugged my Ubuntu desktop into my network and it isn't grabbing an IP.  I tried thru the Network Config, but it isn't grabbing it.  Suggestions?

---

### Post by kc5hwb on 2007-03-30
anyone?

---

### Post by sinean on 2007-03-30
There is ifconfig 
just "man ifconfig"  to show usage.

---

### Post by kc5hwb on 2007-03-30
Thanks, I think that is what I was thinking of.  Its just been too long since I used Linux....sadly.

---

### Post by kc5hwb on 2007-03-30
Well, I tried ifconfig and all it does it give me the adapter info.  How can I tell it to grab an IP?  Shouldn't it do this automatically anyway?

---

### Post by cowlip on 2007-03-30
ifdown eth0
ifup eth0

---

### Post by sinean on 2007-03-30
Well I'm on my solaris box at work but try ipconfig hme0 <--what ever it is call for network adaptor then type auto-dhcp.

ipconfig hme0 auto-dhcp

I myself use the gnome-network-manager, you could install via apt-get but after install make sure the previous network manager has all network devices unchecked.

I could give you more detail but not at home atm.

---

### Post by sinean on 2007-03-31
I meant to say ifconfig not ipconfig
gah!!!!

---

### Post by kc5hwb on 2007-03-31
I tried the gnome-network-manager...it listed the device, but I couldn't figure out how to renew the ip from there.

I'm gonna go try this and I will post again with the results.

---

### Post by zigx on 2007-04-02
> **cowlip said:**
> ifdown eth0
ifup eth0

this works! 

thank you

---

