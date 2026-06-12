---
title: "Wireless Troubles in Mint 8 on Macbooks"
date: 2010-03-22
forum: Apple Hardware Users
---

### Post by amuench on 2010-03-22
Hey, I just helped two kids in my dorm dual boot Linux Mint 8 on their Macbooks.  I followed the procedures listed here : [https://help.ubuntu.com/community/MacBook4-1/Karmic#Wireless](https://help.ubuntu.com/community/MacBook4-1/Karmic#Wireless) (AirPort) to set up their internet, which involved installing the broadcom driver.  The wireless worked and successfully connected to the internet right after they were installed.  Then I put them back onto an ethernet connection so that I could download updates and some programs and whatnot for them.  Now, neither of them can connect to wireless networks.  They are able to detect them, but the wireless icon just keeps sitting there with only one green light on.  Upon reinstalling after this point, the same problem persisted.  I have no problems with any internet networks on my Linux Mint boot on my non-mac laptop.  I feel like it's a driver issue...anyone know how to remedy this?

---

### Post by linuxopjemac on 2010-03-22
so the wireless is a problem...did you try wicd ?

```
sudo apt-get install wicd
```

---

