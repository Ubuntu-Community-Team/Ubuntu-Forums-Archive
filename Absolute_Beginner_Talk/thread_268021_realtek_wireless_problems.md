---
title: "realtek wireless problems"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by plounted on 2006-09-29
i have an hp2315us laptop with a realtek wireless card. 
i ahve tried a lot of crpa to get it to work. ive installed ndis wrapper.
is there anyone who knows how to get ubuntu to recognize my wireless card and then pick up my signal?
im using a netgear router. 

sorry about my noobishness. 
ive been using linux for two days now.

---

### Post by Metacarpal on 2006-09-29
Hello, and welcome to Ubuntu!

Sorry to hear you're having wireless trouble...

What model card do you have?  Different models are detected differently.  For example, my card with the RTL8185L chipset works fine...  Tell us what you have, and we'll tell you how to get it working!

---

### Post by theknave on 2006-09-29
I had nothing but trouble getting my wireless up and running.

Have you got the ndiswrapper graphical interface installed? That made my life a whole lot easier.

---

### Post by plounted on 2006-09-30
i have ndis wrapper installed, but i dont know how to access it 
or anything about the graphical interface. 
how do i detect my card or find out what car id have?

---

### Post by blx_286 on 2006-09-30
> **plounted said:**
> i have ndis wrapper installed, but i dont know how to access it 
or anything about the graphical interface. 
how do i detect my card or find out what car id have?

Maybe this will help with finding your card [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

On the GUI, I believe it's called ndiswrapper-utils and I think you can install it with the Synaptic Package Manager. Once it's installed, you will find it at >System >Adminsitration >Windows Wireless Drivers

---

### Post by plounted on 2006-10-01
i have now installed the ndis wrpper utils and i do not get an icon that says wireless drivers. 
what have i done wrong?

---

### Post by blx_286 on 2006-10-01
> **plounted said:**
> i have now installed the ndis wrpper utils and i do not get an icon that says wireless drivers. 
what have i done wrong?

Sorry dude I told you wrong, install ndisgtk_0.6-0ubuntu1_all.deb to get the GUI. You should be able to install that with the Synaptic Package Manager, or in Terminal I think with 

```
sudo apt-get install ndisgtk_0.6-0ubuntu1_all.deb
```

I have a different card, but have you tried searching the forum for RealTek?

---

### Post by Metacarpal on 2006-10-01
> **plounted said:**
> i have ndis wrapper installed, but i dont know how to access it 
or anything about the graphical interface. 
how do i detect my card or find out what car id have?

Is there a model number physically printed on your card?

---

