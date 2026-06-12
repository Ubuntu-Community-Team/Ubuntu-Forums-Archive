---
title: "How can I get Ubuntu to remember DNS?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by WhiteSphinx on 2007-03-08
I got the internet to work by deleting the two DNS addresses that Ubuntu had in the network settings and replacing them with one that I knew was good.  Is there any way I can get Ubuntu to remember this address.  I have to put it in again every time I boot up or switch user.

---

### Post by dotman on 2007-03-08
The DNS entries are saved in /etc/resolv.conf but your network manager utility should be updating that file for you. If you search the forums you will find a few posts about that specific problem because while editing the resolv.conf file will help you in the short term, you may need it to dynamically change in the future.

Just out of curiosity, what is your setup like? Is your computer getting bad dns addresses from your router or are you directly connected to the modem?

---

### Post by yabbadabbadont on 2007-03-08
Modify /etc/dhcp3/dhclient.conf and add a line like this:
```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```
Change the IP addresses to the proper values for your setup.  (Mine refer to opendns.com by the way)

---

### Post by WhiteSphinx on 2007-03-08
I've tried all these solutions but the system always reverts back to the same bad addresses after reboot.  I have four computers (three of them are Windows computers and one is Ubuntu) hooked up to a Netgear eight port hub which in turn is hooked up to an Actiontec DSL Modem.  The Windows machines have no trouble at all connecting to the internet.

I have changed the /etc/resolv.conf file but the system changes it back after reboot.
I have changed the /etc/dhcp3/dhclient.conf file and even though it does not reset after reboot like the /etc/resolv.conf file does, it still has no effect.

---

### Post by keyo on 2007-03-09
I am having exactly the same problem, my router keeps updating my dns. Nothing has worked in etc/dhcp3 or etc/resolv.conf. It is incredibly anoying having to change the dns ips every 15mins just to having working internet.

---

### Post by craigdele on 2007-03-09
Try locking the DNS addresses. Edit etc/resolv.conf with the correct addresses then lock this file with the command:

sudo chattr +i  /etc/resolv.conf

To unlock:

sudo chattr -i  /etc/resolv.conf


Dele

---

### Post by dotman on 2007-03-09
I guess another question is why the router has the wrong dns adresses in the first place. If it is automatically getting from the ISP then maybe the ISP is having problems. Maybe see if your router will let you have manual DNS entries while using DHCP. Though, it may just change them back when your lease renews.

---

