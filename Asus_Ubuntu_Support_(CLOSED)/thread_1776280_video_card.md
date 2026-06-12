---
title: "video card"
date: 2011-06-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by calolmos on 2011-06-05
So... i am brand new to linux and not very tech savvy to begin with. i am still learning the very basics of ubuntu. i need someone to hold my hand and tell me how to install a driver for my nvidia EN8600GTS video card. it seems very confusing, i can find linux drivers on the nvidia site. however, i am clueless as to how to install them. i know i need some programs to run some windows stuff but don't know which one or ones to get. If anyone can help, i would be very grateful. 

Thanks

---

### Post by papibe on 2011-06-05
The safest way is to install a tested version provided by Ubuntu. Go to System > Administration > Hardware Drivers.

Check this [tutorial ]("http://www.psychocats.net/ubuntu/nvidia")for more info.

Regards.

---

### Post by calolmos on 2011-06-05
that was so easy, i feel stupid. 

thanks so much for the quick response

---

### Post by papibe on 2011-06-05
> **calolmos said:**
> that was so easy, i feel stupid.

Please don't. Keep asking questions, and enjoying the forums!

Regards.

---

### Post by calolmos on 2011-06-05
hmm... I see that hey have been downloaded but i don't think installed... i get this message in additional drivers "this driver is activated but not currently in use" ?

---

### Post by papibe on 2011-06-05
Could you post the content of this file /etc/X11/xorg.conf ?

---

### Post by calolmos on 2011-06-05
Also, i suppose the pad lock icon over the "additional drivers" has something to do with it. I have administration rights, i think. i can not find a administrator page from system settings,

System > Administration?

---

### Post by calolmos on 2011-06-06
i can not seem to find, or know how to find this file, "/etc/X11/xorg.conf"

sorry,

---

### Post by papibe on 2011-06-06
Open a terminal and run this:
```
$ cat /etc/X11/xorg.conf
```
Regards.

---

### Post by jwcalla on 2011-06-06
After enabling the drivers, did you reboot?  It's one of the unfortunate things that must be done when graphics drivers are installed.

---

### Post by calolmos on 2011-06-07
yes, i did. but now i have a much more serious issue. i did not have a firewall installed, and now ubuntu won't load. don't know for sure if they are related. 
 
when i try to install ubuntu from scratch again, nothing happens

---

