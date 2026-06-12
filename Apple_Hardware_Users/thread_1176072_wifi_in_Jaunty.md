---
title: "wifi in Jaunty"
date: 2009-06-01
forum: Apple Hardware Users
---

### Post by m.musashi on 2009-06-01
After trying an upgrade from intrepid to jaunty I decided to do a clean install. I have an iMac 5,1 and the Broadcom STA wireless driver says it's active but not currently in use. Not sure what that means but I certainly don't have wifi. The little network icon does not give the option to enable wifi either so I'm assuming something isn't properly "turned on". I've search this forum and google and can't find any info on how to get this to work. Everything I find says it's working for whomever. I was under the impression that the included proprietary driver was working. Did I miss something?

Thanks.

---

### Post by Clement_User on 2009-06-01
This works for me. Try disabling the Broadcom driver, rebooting, re-enabling, then reboot again. Does that help?

---

### Post by m.musashi on 2009-06-02
Yeah, I actually gave that a try and it worked. Not sure why it doesn't work out of the box but now it's working fine.

Thanks.

---

### Post by cyberdork33 on 2009-06-02
> **m.musashi said:**
> Yeah, I actually gave that a try and it worked. Not sure why it doesn't work out of the box but now it's working fine.

Thanks.
yep, same for me on my iMac5,1

---

### Post by m.musashi on 2009-06-03
Well that was short lived. Now it's not working again. It sees the networks and tries to connect but fails. It always comes back asking me for the wpa password (which it knew before). If I put the password in again it still fails and asks for the password again. It's not the wrong password. What's wierd is that when it asks again for the password there is already one there. If I click the box to show password it's a different one. If I delete that one and put the right one in again it does the same thing - fails to connect and asks for the password and the one in password box is the same wrong one from before.

I think it's an issue with wpa as it will connect to an open network just fine. EDIT: sorry, that's not true now. Seems it won't even connect to an open network.

---

### Post by cyberdork33 on 2009-06-04
make sure that the b43 module is not loading... it would conflict.

---

### Post by dman777 on 2009-06-05
I think the problem is in your kernel with something being enabled when it shouldn't. In my kernel I have wifi support(The parent directory in the kernel) disabled all together and I use the closed source Broadcom driver. It works beautifully. Remember, anything in your kernel will take procedence over any external driver.

I am not familiar with Ubuntu, but if there are any modules that would interfere with it it should only be ndiswrapper. I would unstinall any broadcom driver from ndisrwapper. And if you only use ndiswrapper for just that I would uninstall ndiswrapper also. 

Aslo, I don't think you need it. In fact, 90% sure you don't. But as a last resort I would install the firmware cutter for the broadcom card. But only do this as a last result. If it's already installed and has been installed all this time, try takeing it out then.

---

### Post by cyberdork33 on 2009-06-05
> **dman777 said:**
>  Aslo, I don't think you need it. In fact, 90% sure you don't. But as a last resort I would install the firmware cutter for the broadcom card. But only do this as a last result. If it's already installed and has been installed all this time, try takeing it out then.
this is the b43 driver I was referring to. Even without the firmware available, it can load and take control of your hardware. It is best to block it if you are going to use the wl driver from broadcom (b43 doesn't work with most of these mac broadcom cards anyway).

---

### Post by m.musashi on 2009-06-05
> **cyberdork33 said:**
> make sure that the b43 module is not loading... it would conflict.

Thanks for the tip but I don't think that's it.
```
jim@mac-desktop:~$ rmmod b43
ERROR: Module b43 does not exist in /proc/modules
```

Unless I'm going about it wrong. However, it seems to be loaded.

So others aren't having this issue? There is nothing special about my setup and it's a clean install. Should work like others with an iMac 5,1.

---

### Post by cyberdork33 on 2009-06-05
can you post lsmod?

---

### Post by m.musashi on 2009-06-06
Thanks for the help but I seem to have stumbled upon a solution. Not sure why it mattered but I switched my router from being set on a single channel to "auto" mode and suddenly I was able to connect just fine. Since the wireless nic seemed to be working fine as it could see and try to connect to networks I started to wonder if something was goofy on the router. My other computers didn't have any issue, but I thought maybe the problem was external to the OS. Still, it didn't have this issue when running Intrepid so something seems to have become more sensitive.

Although this should have had nothing to do with not connecting to an open network as the one I was trying was a neighbor's so my router settings would be irrelevant. Weird. Things don't quite add up on this and that bugs me but it's working so oh well.

In any case, if others have a similar problem (wifi works but won't connect) maybe it's router related.

---

### Post by prasanth.ooty on 2009-06-06
> **dman777 said:**
> I think the problem is in your kernel with something being enabled when it shouldn't. In my kernel I have wifi support(The parent directory in the kernel) disabled all together and I use the closed source Broadcom driver. It works beautifully. Remember, anything in your kernel will take procedence over any external driver.

I am not familiar with Ubuntu, but if there are any modules that would interfere with it it should only be ndiswrapper. I would unstinall any broadcom driver from ndisrwapper. And if you only use ndiswrapper for just that I would uninstall ndiswrapper also. 

Aslo, I don't think you need it. In fact, 90% sure you don't. But as a last resort I would install the firmware cutter for the broadcom card. But only do this as a last result. If it's already installed and has been installed all this time, try takeing it out then.



you can use wicd by sudo apt-get install wicd

---

