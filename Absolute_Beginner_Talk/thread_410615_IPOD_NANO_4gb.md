---
title: "IPOD NANO 4gb"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by joshb86 on 2007-04-15
Hi. I have a friend who i recently converted to ubuntu and so far they love it. Only problem i have ran into is getting his daughters ipod nano to work with ubuntu. If you are viewing "computer" and looking at the attached drives.... you can plug in the ipod and for a split second "Apple Ipod" will pop up in the drive list. But then it's gone and gtkpod nor banshee can see it. 



 I have done everything i can find on these forums to get it working and still fail. I do know that on the ipod settings menu it shows the format as "windows". I'm guessing it could possibly be ntfs. Would that be part of the problem?


 Any help is greatly appreciated.



Thanks!

---

### Post by lamalex on 2007-04-15
have you tried amarok? make sure libgpod is installed too. Amarok has worked with every ipod i've ever plugged in without any configuration.

---

### Post by cwmaxson on 2007-04-16
Sounds strange, maybe try Songbird, it's still quite alpha, but it works great with my ipod.  It's the itunes alternative written in xul like firefox and thunderbird.

---

### Post by joshb86 on 2007-04-16
Actually those are ideas im going to try. Havent tried amarok yet.... only gtkpod. I'll try both of your suggestions and let you know the update. Thanks guys!!

---

### Post by aysiu on 2007-04-16
This may be worth looking at, too:
[http://en.wikipedia.org/wiki/Comparison_of_ipod_managers#Linux](http://en.wikipedia.org/wiki/Comparison_of_ipod_managers#Linux)

---

### Post by joshb86 on 2007-04-16
Ahh.....amarok is clearly the winner... should have thought about trying it to start with. Thanks

---

### Post by frogotronic on 2007-04-24
> **cwmaxson said:**
> Sounds strange, maybe try Songbird, it's still quite alpha, but it works great with my ipod.  It's the itunes alternative written in xul like firefox and thunderbird.

Can Songbird transfer files to an iPOD?

If so, do I need any dependencies...

- CH

---

### Post by bytejunkie on 2007-04-28
I've got the same sort of problem. Thing is, the Ipod refuses to mount, so no matter which manager i choose to use, I'm not going to be able to connect to the device.

anyone know how to force feisty to pick up a 1st gen Ipod nano?

Matt

---

### Post by frogotronic on 2007-04-29
> **bytejunkie said:**
> I've got the same sort of problem. Thing is, the Ipod refuses to mount, so no matter which manager i choose to use, I'm not going to be able to connect to the device.

anyone know how to force feisty to pick up a 1st gen Ipod nano?

Matt

do you have 

```
sudo apt-get install ipod libgpod1 libgpod-common libipod-cil libipoddevice0 libipodui-cil 
```


installed?

---

