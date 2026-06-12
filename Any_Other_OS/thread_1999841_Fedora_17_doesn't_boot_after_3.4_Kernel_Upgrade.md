---
title: "Fedora 17 doesn't boot after 3.4 Kernel Upgrade"
date: 2012-06-08
forum: Any Other OS
---

### Post by Dlambert on 2012-06-08
I installed fedora today to experience GNOME shell again, and now after updating it wont boot. When I select Fedora 3.4XXXX from Grub it starts to load then the screen flashes (nouveu starting i think) and then my monitor says "no signal". I was updating the kernel before installing the Nvidia drivers. GTX 560 TI. Any help?

---

### Post by dverbeek84 on 2012-06-08
i've got the accept same problem, if also got a GTX 560 ti. i am trying allday to get it fixed, but no sollution yet

---

### Post by Dlambert on 2012-06-08
Im trying: [http://www.if-not-true-then-false.com/2012/fedora-17-nvidia-guide/](http://www.if-not-true-then-false.com/2012/fedora-17-nvidia-guide/)

Then trying to boot using nouveau.noaccel=1  and trying runlevel 3 as well. Wish me luck!

---

### Post by Dlambert on 2012-06-08
Just rebooted and it's working! Just follow the steps from that URL on an older kernel then reboot using the latest!

---

### Post by Dlambert on 2012-06-08
> [dlambert@dlambert-pc ~]$ uname -a 
Linux dlambert-pc 3.4.0-1.fc17.x86_64 #1 SMP Sun Jun 3 06:35:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
[dlambert@dlambert-pc ~]$ 


Success

---

### Post by dverbeek84 on 2012-06-08
Nice! Thank you! i'am going to try it now.

---

### Post by Dlambert on 2012-06-08
> **dverbeek84 said:**
> Nice! Thank you! i'am going to try it now.

No Problem!

---

### Post by dverbeek84 on 2012-06-08
it works :D

---

### Post by Dlambert on 2012-06-08
> **dverbeek84 said:**
> it works :D

Glad it worked for you too! Woo! I'm so happy. :lolflag:

---

