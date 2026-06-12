---
title: "g4 powerbook white screen on restart"
date: 2009-07-22
forum: Apple Hardware Users
---

### Post by mbaucco on 2009-07-22
I have just installed Ubuntu 9.04 on a 867mhz g4 powerbook and I am getting a white screen when I try to restart. It used to do that on start up too, but I found a fix on the forums (adding video=ofonly to /etc/yaboot.conf iirc).

The problem is that the computer the screen goes white when I try to restart and I have to manually power down. If I choose shutdown, the screen goes white but the laptop does power off eventually. Is there a way to fix this?

Thanks,
Matt

---

### Post by roym4 on 2009-07-28
When I've installed 9.04 on G4 powerbooks/ibooks, I've had to type: 
Linux nosplash vga=1 at the second boot prompt when doing the initial reboot. This seems to fix the hanging with a blank screen problem permanently.

---

### Post by thomas.rs on 2009-07-31
where on the second reboot do you type this?

---

