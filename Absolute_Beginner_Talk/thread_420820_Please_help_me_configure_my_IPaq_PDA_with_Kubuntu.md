---
title: "Please help me configure my IPaq PDA with Kubuntu"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-24
I already have Raki and Kitchensync installed, but I still am unable to sync my Compaq Ipaq with my Kubuntu Feisty Fawn.

I am following [this howto]("http://synce.sourceforge.net/synce/howto.php") and I am already in step 3:" Configuration of the kernel driver". In the section called "Find out USB information about your device", after entering ```
diff /tmp/before /tmp/after
```, the output was

```
46c46
< T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 12 Spd=12  MxCh= 0
---
> T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 13 Spd=12  MxCh= 0
48,49c48,49
< P:  Vendor=045e ProdID=00ce Rev= 0.00
< C:* #Ifs= 1 Cfg#= 1 Atr=40 MxPwr=  2mA
---
> P:  Vendor=049f ProdID=0003 Rev= 0.00
> C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA

```

According to the howto, it should look like this
```
23a24,31
> T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 10 Spd=12  MxCh= 0
> D:  Ver= 1.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS= 8 #Cfgs=  1
> P:  Vendor=049f ProdID=0003 Rev= 0.00
> C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
> I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=ipaq
> E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
> E:  Ad=82(I) Atr=02(Bulk) MxPS=  16 Ivl=0ms
```

Obviously, something is wrong.

What should I do now?

---

### Post by wersdaluv on 2007-04-24
I have just tried synce-serial start. What came out was

```
user@usersmachine:~$ sudo synce-serial-start
Password:

Warning!

synce-serial-start cannot find the dccm process.
Without dccm your PPP connection will soon terminate!


synce-serial-start is now waiting for your device to connect

```

How can I fix this?

---

### Post by wersdaluv on 2007-04-24
*bump*

---

