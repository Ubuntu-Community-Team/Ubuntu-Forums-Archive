---
title: "Problem with LAN internet."
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Nuthael on 2008-03-09
Hi, I recently installed Ubuntu, and I am having a problem.

I plugged in my ethernet ASDL modem into my computer, and it registered a connection, but does not let me use that connection at all. All that I have been able to do is download the list of applications available for download, but when i go to download one of them, it says the list is unavailable and i need to refresh, which I do and then it does the same thing again.

Someone please help me, I'll supply you with any information you ask...

---

### Post by halitech on 2008-03-09
does your ISP use PPPoE or a straight connection? what does 
```
ifconfig
```
show for your ip address?

---

### Post by Nuthael on 2008-03-09
i didnt know and so i ran the PPPoE installation thingy and it couldnt find anything, so I assumed it was a direct connection. My IP address is apparently, according to ifconfig, 

169.254.6.107

---

### Post by halitech on 2008-03-09
that is why you can't connect, 169.254 addresses normally indicate your computer didn't connect to your router/modem. have you checked the cable connections?

---

### Post by Nuthael on 2008-03-09
yep, everything is connected properly. Any other idea of what it could be?

---

### Post by halitech on 2008-03-09
go back into the terminal and do 
```
 ifconfig up
```

post back any errors (if you get any) and we'll go from there

---

### Post by handydan918 on 2008-03-09
> **halitech said:**
> go back into the terminal and do 
```
 ifconfig up
```

post back any errors (if you get any) and we'll go from there
Did you mean ```
sudo ifup eth0
```

Might also try ```
sudo dhclient
```

---

### Post by halitech on 2008-03-09
ummmm yeah, sorry time change and my brain is still asleep over here:oops: guess that would give him errors if he does my command

---

### Post by Nuthael on 2008-03-10
sudo ifup eth0 said that the interface was already configured.

sudo dhclient said a bunch of things, DCHPREQUEST on 255.255.255.255 and then DCHPACK 10.1.1.1 SIOCDDHP (I think...) no such process
bound to: 220.238.68.58

---

### Post by handydan918 on 2008-03-10
Are you connecting to a modem or a router/gateway? Is it set up to do dhcp? Can you ping the device?
try posting the output of ```
ifconfig
```and ```
dhclient
```

---

### Post by Dr Small on 2008-03-10
Have you tried to configure your connection from System > Administration > Network?

---

### Post by Nuthael on 2008-03-10
yes, I switched it to DCHP, and added my nameserver. Didn't know what else to do. Still doesnt work

---

