---
title: "not using full power of CPU on laptop"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by snoopgst on 2005-06-27
kubuntu is only recognizing 550mhz of my cpu.  I have an amd 1500+ which is around 1.3  any ideas on how to fix this? thanks.

I am running kubuntu on a compaq presario 905US laptop.

---

### Post by dialate on 2005-06-27
Actually, this is a good thing. If your processor was running full bore all the time, it would stay hot and the noisy processor fan would have to run all the time. It would drain the battery too. It's called "throttling", and Windows does this too, even though you can't see it.

When you do something that requires a lot of processing power, it will automatially turn the speed up for you. Try starting OpenOffice, or compile something, and look at the speed again. It will go up to whatever your max is usually, and then whenever the processor usage drops back down, it goes throttles the processor back down.

And, for something better than Windows does, you can use performance profiles. You could select "powersave" which means your processor will only run at the lowest speed no matter what, to extend the life of your battery. You could select "performance", which runs the processor at full speed no matter what. Or, use the standard "ondemand", which is what I described in the previous paragraph. There's "userspace"...I'm not exactly sure what it does, but it seems to behave like "ondemand".

To enable performance profiles, right click the KLaptop icon (the one that displayes your battery charge and whether you are plugged in , or not), and go to Configure KLaptop. Go to the last tab, click enable helper application. Once thats done, check "Enable Performance Profiles". There are some other options there, but use them at your own risk, becuase they are experimental, and buggy. On my Presario 2195 laptop, returning from suspend or hibernations results in hard freezes.

---

