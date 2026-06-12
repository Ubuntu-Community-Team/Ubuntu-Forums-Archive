---
title: "issue with some wireless access points"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Zzl1xndd on 2007-03-16
Hey folks. Having a strange issue I have my laptop set up with Wireless and it works at home with a Linksys 54g router, at work with the same router and with the Cities Free wifi network but it will not connect at my friends house. He is using a Siemens 6250 wireless Modem with WEP. I can see the router but it will not connect and Im a little stumped.

also just as a note I use WPA at home and the other 2 networks are open.

---

### Post by oilchangeguy on 2007-03-16
have you entered your friends security code?

---

### Post by mahy on 2007-03-16
try installing wifi-radar, it usually helps

---

### Post by wieman01 on 2007-03-16
And before you enter the WEP key, kill wpa_supplicant from command line:
> sudo killall wpa_supplicant
See if this helps. Also turn off our Firewall if you have configure it (e.g. through Firestarter).

---

### Post by Zzl1xndd on 2007-03-16
thanks for the replies 

Yes I entered the code.

I am using network manager

Thanks ill try that, when I restart will WPA comeback as I will need it for home.

---

### Post by wieman01 on 2007-03-16
> **tweakedenigma said:**
> thanks for the replies 

Yes I entered the code.

I am using network manager

Thanks ill try that, when I restart will WPA comeback as I will need it for home.
When you restart, it will be there again. Promise!

But then... you are using Network Manager? Not sure if this helps then...

---

### Post by Zzl1xndd on 2007-03-16
> **wieman01 said:**
> When you restart, it will be there again. Promise!

But then... you are using Network Manager? Not sure if this helps then...

It might be his Modem/router he has the Siemens speedstream 6250, And I know of one other person with the same laptop as me having the same issue with the same modem only he is using windows.

---

### Post by wieman01 on 2007-03-16
> **tweakedenigma said:**
> It might be his Modem/router he has the Siemens speedstream 6250, And I know of one other person with the same laptop as me having the same issue with the same modem only he is using windows.
Perhaps... But it sounds odd to me though. Routers rely on standard protocols and should create such issues at all. Anyway, perhaps he has got MAC filtering enabled?

Drop us a note if you know what's going on.

---

### Post by Zzl1xndd on 2007-03-16
I'll check it out the next time im over it just seemed odd to me.

---

