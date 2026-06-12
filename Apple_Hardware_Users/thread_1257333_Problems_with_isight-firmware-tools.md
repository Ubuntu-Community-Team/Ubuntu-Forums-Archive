---
title: "Problems with isight-firmware-tools"
date: 2009-09-03
forum: Apple Hardware Users
---

### Post by robin.nightingale on 2009-09-03
Hello i just installed Ubuntu 04.9 64bit on my Macbook 3.
I tried to get the isight runnig with the following howto:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight]("https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight")
But it wont work i just get the following error:

```
Apple driver file not found                                             
The file you specified does not exist. The firmware extraction has been   aborted.   

```

I also copied the File "AppleUSBVideoSupport" to the Desktop and tried to extract it from there but i get the same error.


Could somebody help me ?

Thanks

---

### Post by gotenks05 on 2009-09-04
> **robin.nightingale said:**
> Hello i just installed Ubuntu 04.9 64bit on my Macbook 3.
I tried to get the isight runnig with the following howto:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight]("https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight")
But it wont work i just get the following error:

```
Apple driver file not found                                             
The file you specified does not exist. The firmware extraction has been   aborted.   

```

I also copied the File "AppleUSBVideoSupport" to the Desktop and tried to extract it from there but i get the same error.


Could somebody help me ?

Thanks

it needs to go in "/lib/firmware/"

then type:

```
sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport
```

does that change anything?

---

