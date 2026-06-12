---
title: "Asus K53Br Support?"
date: 2012-08-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dgaa1991 on 2012-08-14
hi i am mabey gonna buy the Asus k53br amd. laptop
but how is working with ubuntu 12.04 LTS?

AMD Dual-Core Processor E450 (1,65GHz)
AMD Radeon&#8482; HD 7470 1GB DDRIII VRAM Grapichcard. (15,6 " / 1366 x 768)
4GB DDR3 1333MHz

will i be able to watch HD videos ?
and how will the overall Performace be ?

---

### Post by johnathansmith on 2012-08-14
So far looks like nobody tested this notebook with linux. If you are planning buying new notebook look [HERE]("http://www.ubuntu.com/certification/desktop/") first. Specially if you are serious about using ubuntu, you should choose well at the beginning. This saves a lot of troubles in the future.

---

### Post by dgaa1991 on 2012-08-14
yearh the problem is just that i ordered it yesterday and i am mabey gonna return it again :S

but what do u guys think ? will it work or it is a no go?

---

### Post by johnathansmith on 2012-08-14
Fastest way is use live usb stick or live cd and try it. In your place I would returned notebook and choose on from the list that I posted before. You will avoid a lot of problems with network/graphic/sound cards etc.

---

### Post by venky96 on 2012-08-15
As far as I know, almost all ASUS laptops have their Webcams mounted upside down. I have used 5 different ASUS laptops and each of them had this same problem. As the webcam is mounted upside down,You'll have some problem with Skype and aMsn. But with a few command line tricks you can fix it.

---

### Post by azurehoney on 2012-08-19
> **dgaa1991 said:**
> hi i am mabey gonna buy the Asus k53br amd. laptop
but how is working with ubuntu 12.04 LTS?

AMD Dual-Core Processor E450 (1,65GHz)
AMD Radeon™ HD 7470 1GB DDRIII VRAM Grapichcard. (15,6 " / 1366 x 768)
4GB DDR3 1333MHz

will i be able to watch HD videos ?
and how will the overall Performace be ?


I have it

- forget 720p @ 60fps with proprietary and open source drivers
- 720p @ 30 fps is not smooth either with proprietary drivers
- major issue with open source radeon drivers is temperature. At idle it's constantly around 70C. Compare this to 49C in Windows!
- with proprietary drivers temperature is much lower, for example with Chrome browser open and video playing in youtube I get:


```
amdconfig --adapter=all --odgc --odgt

Adapter 0 - AMD Radeon HD 6320 Graphics
                            Core (MHz)    Memory (MHz)
           Current Clocks :    275           667
             Current Peak :    507           667
  Configurable Peak Range : [275-507]     [667-667]
                 GPU load :    0%

Adapter 1 - AMD Radeon HD 7400M Series
                            Core (MHz)    Memory (MHz)
           Current Clocks :    100           150
             Current Peak :    800           800
  Configurable Peak Range : [400-800]     [800-800]
                 GPU load :    14%

Adapter 0 - AMD Radeon HD 6320 Graphics
            Sensor 0: Temperature - 58.00 C

Adapter 1 - AMD Radeon HD 7400M Series
            Sensor 0: Temperature - 52.50 C
```

- [I can't install newer drivers]("http://ubuntuforums.org/showthread.php?t=2041251")

- overall experience is pretty sluggish -- both in Windows and Ubuntu

---

