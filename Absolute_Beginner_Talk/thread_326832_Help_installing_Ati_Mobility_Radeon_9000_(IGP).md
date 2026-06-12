---
title: "Help installing Ati Mobility Radeon 9000 (IGP)"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by manutdfan2850 on 2006-12-28
Hi, 

I am new to linux and i am running Ubuntu Edgy. 

I want to install the ATI drivers for my Laptop's Mobility Radeon 9000 (IGP). I tried following some guides using the terminal but when that didn't work I found that I could easily do it using ATI's driver package. 

I went to: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html), selected Linux x86, then selected Integrated/Motherboard, then  Radeon 9000 IGP and downloaded the full driver package which is 22.5 mb. 

Ok. Next I right clicked on the file, and went to Properties, and made it executable. 

Next I double clicked it and selected Run in Terminal. It automatically did some stuff in the terminal but then terminated without installing anything. I was able to catch a screenshot of what it said before closing itself. 


[[IMG]http://img82.imageshack.us/img82/7692/screenshotxy7.th.png[/IMG]](http://img82.imageshack.us/my.php?image=screenshotxy7.png)


It says that I have 7.1.1 version of X.org and that only 7.0.x is supported by the driver. 

I can't get an updated version of the ATI drivers because they don't support my card. 

So how can i downgrade my X.org version? I know that 7.1 is for Edgy (which I have). Does this mean I have to downgrade to Draper to install my ati drivers or can i do it on edgy?? please help.  

Thanks

---

### Post by manutdfan2850 on 2006-12-28
anyone?? plz and thanks in advance

---

### Post by Kubunteando on 2006-12-28
Have a look at this post:

[http://www.ubuntuforums.org/showthread.php?t=325212](http://www.ubuntuforums.org/showthread.php?t=325212)

I have a Dell Latitude D600 with an ATI Mobility Radeon 9000 with edgy.
The newest ATI proprietary drivers you can get are the 8.28.8 (those can be downloaded from ATI and installed in edgy), but ATI will not support it further. Those have some nasty bugs (that I have suffered). I can recommend the same to you and use the MESA DRI drivers. Have a look at the post above, and read the links.I can tell you that some compilation is required, but the result worths the time you will spend. Plus you will learn during the process.

---

### Post by believe it or not on 2008-06-27
ok i need a lot of help. i have a dell latitude d600 laptop. i need a better driver. what do i do. im very new to linux. ive had it on my laptop for 2 days now. so your gonna have to spoon feed every thing to me. thanks alot.

---

