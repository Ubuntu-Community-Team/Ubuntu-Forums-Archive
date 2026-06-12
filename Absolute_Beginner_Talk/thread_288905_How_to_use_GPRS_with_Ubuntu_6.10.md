---
title: "How to use GPRS with Ubuntu 6.10"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by crucifier on 2006-10-30
Dear Sir,

Sorry for my English skill,

I need to start using linux with Ubuntu 6.10 but I dont know to to connect to the Internet with my Motorola c380 via GPRS modem.

It is very important for me. If I can not access to the Internet, I can not start working with linux!!!

How should I do.

Best Regards,
Nat VT

---

### Post by mips on 2006-10-30
Do a search in the networking forum for keywords like GPRS etc.

---

### Post by Uncle Che on 2006-10-30
If you are using the usb cable, you have two choices, search the forum or go to this site:

[http://www.ax697.org/452332/motorola-gprs-on-ubuntu/](http://www.ax697.org/452332/motorola-gprs-on-ubuntu/)

Follow the step by step directions and you are in business. It works like a charm and have used three different motorola phones on 5 different ubuntu installs using these directions.

---

### Post by crucifier on 2006-10-30
Thank you very much, Uncle Che.

Now I can access to the Internet via GPRS!
However, Why do I need to open the terminal and cant clos it while I access to the Internet? Have you got any other solution?

Sorry for my English skill.

Thank you so much.
Nat

---

### Post by Uncle Che on 2006-10-30
Glad you got it working!

I tried to find a way to get gprs internet to work doing a lot of different ways over the course of about a year since I use gprs exclusively at home. I finally got the idea to do this from several different sources and played around until it worked. I haven't tried to get it working any other way because first, this works and I am lazy and secondly my knowledge of Linux is limited, maybe someone with more in-depth experience could let us know how to run it in the background.

---

### Post by mips on 2006-10-31
> **crucifier said:**
> 
However, Why do I need to open the terminal and cant clos it while I access to the Internet? Have you got any other solution?


Try:
```
sudo wvdial &
```

Why not just create a nice panel/desktop icon you can click on instead of typing this every time.

---

### Post by crucifier on 2006-10-31
Thank you everyone. I don't worry anything after I can connect to the Internet becauase I can work and can search a solution if I have a problem. I will try to learn Linux more.

Sorry for my English skill.

Thanks again.
Nat, new linux user ^^

---

### Post by adewale on 2006-11-17
i had previously edited the wvdial.conf file but when i give the command in terminal the gprs logo comes on for only a second and it gives exit code=10 as error message. am in Africa does my location have anything to do with that? and on windows i use moto phone tools to connect to the web easily i also tried bluetooth but stil the same problem the logo comes up for a second

---

