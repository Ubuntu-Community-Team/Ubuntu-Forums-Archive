---
title: "Networking doesnot work after hibernate"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by vijayanand_sodadasi on 2007-03-19
Hi,

Networking doesn't seem to work after hibernating.  I had to reboot the system to get the internet working.  I am connected to ADSL modem via USB port.    So I am not sure if its USB related or networking related. 

I searched the forums and found that many had similar problems with hibernate option.  But none of those threads have a solution.  

I am using Edgy.  (It was actually Dapper and then I upgraded from the notification icon.  So I believe its Edgy now, however I am not sure and I don't know how to check which version of ubuntu I am using:???:).  

So does any body know how to fix this hibernate thing.

Thanks,
Vijay

---

### Post by zvacet on 2007-03-21
Probably you didn´t set your net configuration properly.That is the reason why you have to reboot.If something is wrong with USB you will not be able to connect. Try set your connection like this
> After you are done with your modem>properties>select type of connection>close
you need to go to DNS and there is one address which isn´t your(I belive it is default)so delete it and put your nameservers>close

```
pppoeconf
```

for version chek
```
uname -a
```

---

### Post by vijayanand_sodadasi on 2007-03-23
Thanks zvacet, I will check this.  Probably my USB networking will work without changing any of the settings next time I do a hibernate. :)

---

