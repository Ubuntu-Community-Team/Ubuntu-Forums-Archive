---
title: "Gusty won't start unless I press &lt;Ctrl&gt;&lt;Alt&gt;&lt;F2&gt;"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by christina_svats on 2007-11-16
I installed 7.10 using a liveCD on a laptop, that used to be on dual boot (XP+7.04), but now  has Ubuntu alone. After installation (which came with no error messages) I rebooted, but Gutsy wouldn't start.

I get the first screen that says "Starting up..." but then I get a black screen instead of the login screen. If I press <Ctrl><Alt><F2> I get an underscore on my screen and after a while I get "saving VESA state..." and a whole bunch of messages and then, the login screen, and everything works fine,

Does anybody have an idea why this is happening? LiveCD worked great before installation.
It's a pentium IV 3.2 GHz RAM 512MB ATI Radeon 9700

---

### Post by Sturmeh on 2007-11-16
Try a re-install? Maybe something slipped up during install, or some hardware has been added etc.

I don't get this problem, then again I don't have that rig. xD

---

### Post by whazooo on 2007-11-16
might be a grub problem from previous dualboot setup.
check the grub file

---

### Post by trull on 2008-02-06
Hi, 

I have exactly the same problem, have you fixed it, what did you do?

from a cleanly formatted HD i installed XPSP2, then installed 7.10 from a livecd and it doesnt boot (although i havent left it very long) unless i press ctrl-alt-f2, at which point it seems to run though the normal list of things done on boot :s

Any help would be appreciated

Thanks

Trull

---

### Post by divindavid on 2008-02-17
i have the same problem but i am not daul  booting i just have ubuntu i will try what u did

---

### Post by bumanie on 2008-02-17
I think you need to configure your video card. As far as I know vesa is the native ubuntu gpu driver. I don't think  it supports 3d acceleration. You should go to restricted drivers and see if you can install the proprietary driver for your graphics card. Restircted drivers Administration --> Sysytem --> Restricted drivers.

---

### Post by lncoll on 2008-02-17
Hi:
I've  had that problem many times, always with ATI video card, and always solved :)
You must install the fglrx driver via restricted drivers.
This way does not solve the problem every time, if this is your case read the ATI wiki at [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually).
Following this instructions has been the best way for me to solve the problem, and got a fully working vga, compiz etc.
Good look  ;)

---

