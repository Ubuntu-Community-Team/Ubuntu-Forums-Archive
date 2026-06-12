---
title: "MacBook Wireless Help"
date: 2008-09-01
forum: Apple Hardware Users
---

### Post by Noob1234 on 2008-09-01
Well I still have not been able to figure out the whole wireless issues with my macbook.  I have a core2duo.  I looked at the wiki and still have no success, somebody please guide me in the right direction.  Very simple instructions would be extremely appreciated.  Let me know if you need any additional information regarding my macbook.


core2duo purchased in the summer of 07.

---

### Post by cyberdork33 on 2008-09-01
It would be helpful if you found the exact version of your macbook (see the "before you post" link in my signature)

Also, when referring to a how-to or some other direction it is most helpful to link to it so that we all know what you have tried (there is more than one macbook wiki page).

---

### Post by Noob1234 on 2008-09-01
> **cyberdork33 said:**
> It would be helpful if you found the exact version of your macbook (see the "before you post" link in my signature)

Also, when referring to a how-to or some other direction it is most helpful to link to it so that we all know what you have tried (there is more than one macbook wiki page).

Alright I will do the best that I can.



  Model Name:	MacBook
  Model Identifier:	MacBook2,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2.16 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache:	4 MB
  Memory:	1 GB
  Bus Speed:	667 MHz
  Boot ROM Version:	MB21.00A5.B07
  SMC Version:	1.17f0


If you need anything more please let me know.  Also I went to the link stickied at the top of this page and clicked the macbook wiki with basic setup instructions.  As for what I have tried, I tried what it says to do for core2duo machines though I have probably done them wrong.  I hope that you can give very specific instructions as to what to do step by step.

Thanks

---

### Post by cyberdork33 on 2008-09-01
that driver is still rather experiemental. Uninstall the ath9k driver, try using madwifi. You can try this:
```
sudo apt-get install build-essential subversion automake autoconf
svn co http://svn.madwifi.org/madwifi/trunk madwifi
cd madwifi
make
sudo make install
```

---

### Post by Noob1234 on 2008-09-01
> **cyberdork33 said:**
> that driver is still rather experiemental. Uninstall the ath9k driver, try using madwifi. You can try this:
```
sudo apt-get install build-essential subversion automake autoconf
svn co http://svn.madwifi.org/madwifi/trunk madwifi
cd madwifi
make
sudo make install
```

So just type in that code step by step into terminal?

---

### Post by cyberdork33 on 2008-09-01
> **Noob1234 said:**
> So just type in that code step by step into terminal?
yes. Note that it came from here:
[https://help.ubuntu.com/community/MacBookPro#Wireless](https://help.ubuntu.com/community/MacBookPro#Wireless)

It should be close enough.

You should uninstall the previous driver first to avoid any conflict.
```
sudo apt-get remove compat-wireless-ath9k-generic
```

---

### Post by Noob1234 on 2008-09-01
> **cyberdork33 said:**
> yes. Note that it came from here:
[https://help.ubuntu.com/community/MacBookPro#Wireless](https://help.ubuntu.com/community/MacBookPro#Wireless)

It should be close enough.

You should uninstall the previous driver first to avoid any conflict.
```
sudo apt-get remove compat-wireless-ath9k-generic
```

Ok I will give it a wirl and report back, thanks for your help.

---

### Post by Noob1234 on 2008-09-01
Alright I just did that, seemed to work.  Is there anything that I am supposed to do after that?

---

### Post by cyberdork33 on 2008-09-01
> **Noob1234 said:**
> Alright I just did that, seemed to work.  Is there anything that I am supposed to do after that?
reboot and your wireless interface should be available in network manager.

---

