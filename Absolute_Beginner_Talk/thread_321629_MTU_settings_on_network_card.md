---
title: "MTU settings on network card?"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by mattgaunt on 2006-12-19
Hey every1

I have a sweex broadband router, but i am with virgin.net broadband, and in windows i had to use a program called "Dr. TCP" and chang an MTU setting on the wireless network.

Now by doing this i could look at hotmail.com and other things whereas before changing the setting i couldn't do certain things using the internet and certain things i couldnt do

So the big question is, if i can change it in windows, can  i change it in good old ubuntu????

Thanks for any help or ideas

Matt

---

### Post by zgornel on 2006-12-19
Yes. Try: ```
sudo ifconfig eth0 mtu XXXX
``` and to make it permanent, edit /etc/network/interfaces and put **mtu XXXX** in the eth0 entry.

---

### Post by eXisor on 2006-12-19
zgornel's suggestion will not work if you get an IP from the router's DHCP server. 

Instead, edit /etc/network/interfaces and change the 'iface eth0 inet dhcp' section as below:

```

iface eth0 inet dhcp
	pre-up /sbin/ifconfig $IFACE mtu 1352
```

In the code instance I set the mtu to 1352

---

