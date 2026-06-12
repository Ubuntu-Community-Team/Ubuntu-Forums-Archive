---
title: "sharing the printer"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by manishraichur on 2006-11-15
Hi guys
How do i share the printer which is connected to my desktop?
I have Ubuntu installed on my laptop and i have a wireless network.

P.S Thanks to this wonderful forum i was finally able to connect to the internet and i am loving Ubuntu !!!!

Thanks
manish

---

### Post by ]Nbx*cmD[ on 2006-12-10
Hi,

First of all 

```
 sudo apt-get install samba 
```

Samba is the window$-protocol networking software you use in unix based systems.

Usually it will detect your printers during installation and configure them to be used in the network, otherwise configuring it is rather easy, just edit /etc/samba/smb.conf and follow the instructions. :)

Don't forget to check samba's manpages!

```

 man samba 
 man smb.conf

```

---

