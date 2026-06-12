---
title: "ATI 3D on Sony Vaio VGN-S360"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by sorty on 2007-03-10
I'm running Ubuntu 6.10 Edgy on a Sony Vaio Laptop VGN-S360 with ATI MOBILITY RADEON 9700.

Have been trying to get 3D acceleration working, followed the instructions in Help to install appropriate drivers, but after configuration and restart when I check for 3D acceleration I get the following message.

ss@ss-laptop:~$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No

So it seems 3D is not working, what am I missing?

Would appreciate any help.

Thanks all.

---

### Post by overdrank on 2007-03-10
> **sorty said:**
> I'm running Ubuntu 6.10 Edgy on a Sony Vaio Laptop VGN-S360 with ATI MOBILITY RADEON 9700.

Have been trying to get 3D acceleration working, followed the instructions in Help to install appropriate drivers, but after configuration and restart when I check for 3D acceleration I get the following message.

ss@ss-laptop:~$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No

So it seems 3D is not working, what am I missing?

Would appreciate any help.

Thanks all.

Hi you may have to use the fglrx drivers check out this link
[http://doc.gwos.org/index.php/ATI_AMD_fglrx_Edgy](http://doc.gwos.org/index.php/ATI_AMD_fglrx_Edgy)
I had a good time to get my ati card going and I am running bery also.
Good luck hope this helps!:)

---

