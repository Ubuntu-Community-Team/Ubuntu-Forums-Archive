---
title: "Wrong wireless card recognized"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Eberulf on 2007-11-03
My girlfriend built a desktop computer in a class and loaded Ubuntu.  We attempted to add an Airlink AWLH4130 wireless PC card later, and it will not work.  The system appears to think it is a Atheros card, but it is not.  I loaded NDISWrapper and it shows the netwl4130 driver as loaded, but hardware not present.

I have tried physically removing and replacing the card, but it still thinks it is an Atheros card.  It attempts to use the Atherors Hardware Access Layer proprietary driver, but that does not enable the card, from what I can tell.  There is no wireless option to configure under Networks.  The power light on the card does blink green, so I believe it is connected correctly. 

I ran lspci, and it gave me the following data about the wireless card (abbreviated output):

-----------------
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
-------------------

I ran iwconfig and it came back as nothing enabled.

--------------------------
jane@jane-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
---------------------------

Any suggestions, besides swearing profusely, which I have also tried?

---

### Post by snkiz on 2007-11-03
I feel your pain and while I'm no expert form what know about linux this sort of thing is handled by the kernel I would try another distro and see what happens. or maybe a a bios issue? thats my thought. are you sure swearing had no effect?

---

### Post by Eberulf on 2007-11-04
I am not sure what you mean by another distro.  Can you be more specific?

---

### Post by argie on 2007-11-04
It is detected correctly. That card has an Atheros chipset.
[http://www.airlink101.com/products/awlh4130.html](http://www.airlink101.com/products/awlh4130.html)

If you installed it using ndiswrapper, what happens when you run the following in the terminal?
```
sudo ndiswrapper -l
```
That's a lower case L.

---

### Post by Eberulf on 2007-11-04
I get the following:

jane@jane-desktop:~$ sudo ndiswrapper -l
[sudo] password for jane:
netwl4130 : driver installed
jane@jane-desktop:~$

---

### Post by argie on 2007-11-07
> **Eberulf said:**
> I get the following:

jane@jane-desktop:~$ sudo ndiswrapper -l
[sudo] password for jane:
netwl4130 : driver installed
jane@jane-desktop:~$

I'm sorry, I was away for a few days. Can you try the following?
```
sudo depmod -a
```
and then
```
sudo modprobe ndiswrapper
```

Now if you try the following what do you get?
```
sudo ndiswrapper -l
```
Same command as before, that's a lower case L.

---

### Post by kvonb on 2007-11-07
-

---

### Post by Eberulf on 2007-11-07
OK, I get the following.  I am not familiar with depmod or modprobe, but it didn't seem like they did much.

--------------------------------------------
jane@jane-desktop:~$ sudo depmod -a
[sudo] password for jane:
jane@jane-desktop:~$ sudo modprobe ndiswrapper
jane@jane-desktop:~$ sudo ndiswrapper -l
netwl4130 : driver installed
jane@jane-desktop:~$ 
---------------------------------------------

---

