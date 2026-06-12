---
title: "Can't install modem driver"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Dev2 on 2006-08-28
I have SuSE 10.1 but I hope any Linux distro questions are acceptable it didn't say against it in the rules. Anyway I have a Netopia Cayman 3341 modem for my broadband(USB and Ethernet). On my Ubuntu machine luckily I just plugged it in and it worked. Unfortuantely for SuSE 10.1 it doesn't work. I was pointed to a driver thats still in development but that should work.

This is the said driver [http://sourceforge.net/projects/cayman3341/](http://sourceforge.net/projects/cayman3341/)
 
Unfortunately I have bumped into a hurdle with installing the extracted driver. Here are the installation readme instructions.

[i]"Go to directory src. Type:
    make
    sudo cp cayman3341.ko /lib/modules/`uname -r`/kernel/drivers/usb/net/
    sudo depmod"[/i]

I'm almost 100% sure I followed them to the letter but I get an error saying that there is no directory 'kernel/drivers/usb/net/'

Could somebody help me with this. Thanks 
-Dev

---

