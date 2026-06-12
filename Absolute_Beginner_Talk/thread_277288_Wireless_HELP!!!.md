---
title: "Wireless HELP!!!"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by mthakur2006 on 2006-10-14
hello,
i have a lenovo 3000 c100 with an intel 2915 abg wireless card. i have 256 mb ram and 1.5ghz cpu. with windows xp, my wireless connection works absolutely fine but when i tried out the ubuntu 6.06 lts live cd, it won't work. It sees my network card and sees the network. I put in the wep code and all the addresses and it said activating interface and then it did nothing. i am using an ad-hoc connection. Please i need help urgently as it is my sole way of connecting to the internet. 
thanks,
mthakur2006

p.s. the system on live cd is also very very agonisingly slow.
can anyone help? i am a complete newbie.

---

### Post by pregoeater on 2006-10-14
the only way i can think of to speed up the live cd would be a faster cd drive


pre

---

### Post by lreyes6 on 2006-10-14
the live cd works based on your RAM... with 256 the system is kind of slow... 

about your wireless card seems like the live cd doesn't have included the  driver for your specific card... i donw know if you can install software on a live cd session but if you can u can install ndiswrapper cant remember the name of the package but you can look for it in the console like this ```
sudo aptitude search ndiswrapper
```and then all you need is the .inf file fron windows xp (ndiswrapper takes the windows driver and make it work on GNU/Linux :D:D )

---

### Post by mthakur2006 on 2006-10-15
Thanks, but the laptop is not connected to the internet, that's why I need the wireless.
Any other suggestions?
thanks for all the help once again,
mthakur2006

---

### Post by mthakur2006 on 2006-10-21
Problem Solved :d

---

