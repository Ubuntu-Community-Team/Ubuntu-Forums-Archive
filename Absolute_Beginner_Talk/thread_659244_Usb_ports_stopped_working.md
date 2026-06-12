---
title: "Usb ports stopped working"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by siretfel on 2008-01-05
Hi all,

Here's the thing which is quite strange!!

I have 3 usb ports in my notebook

One is the usb mouse
The second is my external HD
The third is not used

I put my system to hibernation and then i boot on to ubuntu 7.10

The external HD usb is working fine. The other two usb ports are not. So the one with the mouse is not working at all. I tried all the combinations...and only the one with the external HD is working. If i put the mouse there it's working.....


What's going on? Can i use a command to force the usb port to work?

Thanks in advance....

---

### Post by blueridgedog on 2008-01-05
With the mouse plugged in, run the command:
```

lsusb
```

And post the results.

---

### Post by siretfel on 2008-01-05
> **blueridgedog said:**
> With the mouse plugged in, run the command:
```

lsusb
```

And post the results.
```

Bus 005 Device 003: ID 04fc:0c15 Sunplus Technology Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000 
``` 

That is the result after restarts. If i go to hibernation again and relogin the row with Microsoft Corp.Wireless Optical Mouse becomes: 0000:0000 like nothing is there!!!!! What is going on?

---

### Post by tgalati4 on 2008-01-05
It looks like your hardware puts the USB circuitry to sleep and then the resume script does not wake it up properly.  It's happened to me with an old Dell Inspiron 7500.  I don't know if there is any fix.  It would help to provide detailed specifications of the machine, including make and model.  Perhaps others have a similar machine that either works or doesn't to confirm your behavior.

---

### Post by siretfel on 2008-01-07
Hi all,

Seems i found a solution which worked this time. I just used this post's information [http://ubuntuforums.org/showthread.php?t=373268&highlight=hibernation&page=3](http://ubuntuforums.org/showthread.php?t=373268&highlight=hibernation&page=3) and seems the solution Gwasanaethau proposes works.

If anyone wanna try and tell me the results let me know. 

I'm using Ubuntu gutsy.

---

