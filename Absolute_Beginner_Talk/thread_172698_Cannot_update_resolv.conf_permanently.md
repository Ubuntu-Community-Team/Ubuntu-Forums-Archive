---
title: "Cannot update resolv.conf permanently"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by liangtp on 2006-05-09
Hi,
Earlier I couldn't get my internet access because the DNS of my ISP was not set in resolv.conf.

However, after putting in the entry below into resolv.conf
nameserver 202.188.0.133 => it worked.

Funny thing is every now and then the setting will somehow change itself back to the original setting in resolv.conf, below.
nameserver 192.168.1.1 

As a result, I will have the problem of internet access again. How can I make the changes permanent?

Thanks

---

### Post by Azrael on 2006-05-09
The resolv.conf file gets overwritten by your dhcp client program everytime it receives a new lease. I think you can prevent this from happening by telling dhclient not to request any nameservers (or something like that) by editing /etc/dhcp3/dhclient.conf. Check the dhclient man pages for more information.

If you really can't get that to work though, you can of course just add a *post-up cp /etc/resolv.conf.yourcustomversion /etc/resolv.conf* to your /etc/network/interfaces file, ugly as that may be.

---

### Post by liangtp on 2006-05-09
Thanks Azrael, will try it out.

---

### Post by liangtp on 2006-05-21
Hi Azrael,

Below was your reply. However, I do not understand how to do it. Could you please provide me the intricate details on how it's done. Thanks.
 	
The resolv.conf file gets overwritten by your dhcp client program everytime it receives a new lease. I think you can prevent this from happening by telling dhclient not to request any nameservers (or something like that) by editing /etc/dhcp3/dhclient.conf. Check the dhclient man pages for more information.

---

