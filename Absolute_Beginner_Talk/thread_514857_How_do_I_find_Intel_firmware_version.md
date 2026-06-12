---
title: "How do I find Intel firmware version?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-08-01
Hey folks. I'm installing new firmware for my Intel 2200BG card, but I'm not sure which version I have or need. How would I find this out? (It's not on the little sticker) Thanks.

---

### Post by bswilson on 2007-08-01
Have you tried looking at your network card in the Ubuntu Device Manager?  Click on **System,** then **Preferences,** then **Hardware Information**.  I've attached a screen shot that shows this applet on my system.  There are tons of details on your hardware there.

---

### Post by into_311 on 2007-08-01
To find out what model of wireless card you have installed you can do.
```

lspci

```

There is a sourceforge project out for the drivers of the ipw wireless cards (intel pro wireless). With Ubuntu Fiesty (v7.04) - they added a new feature where you can easily install the wireless card driver you need for your intel card by using the restricted driver manager. That is just a point and click away. I would highly recommend doing it this way.

Go to: 

System>Administration>Restricted Drivers Manger

Then put a check box in the intel wirless card there. It may prompt you to reboot, and wallah! It's installed.

if that doesn't work, post the ouput of 

```

lspci

```

and 

```

lsmod

```

and we should be able to help you from there.

---

### Post by walkerk on 2007-08-01
> **CheshireMac said:**
> Hey folks. I'm installing new firmware for my Intel 2200BG card, but I'm not sure which version I have or need. How would I find this out? (It's not on the little sticker) Thanks.

```
lspci | grep ipw
```

that should do the trick.

---

