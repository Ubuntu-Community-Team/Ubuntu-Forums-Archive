---
title: "Photoshop Elements"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Oki on 2007-02-12
So PS CS cant run under Linux, but do you know if PS Elements can? I have tried to google it, but got no answer. 

Thanks

---

### Post by wh0rd on 2007-02-12
Here's a nifty little howto on getting Adobe Photoshop CS2 to work under Wine in Ubuntu:

[http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

I've got Adobe Photoshop 7.0 running with CrossOver Office perfectly (you can try installing it with Wine if you don't want to purchase CrossOver Office). If you really don't need all the features of CS to I'd say go with my method.

---

### Post by Oki on 2007-02-12
I saw that one urlier today. But you see, my father just bought PS Elements 5.0, so I was wondering if it could work under Ubuntu. 

But thanks for your answer:-)

---

### Post by doobit on 2007-02-12
> **Oki said:**
> I saw that one urlier today. But you see, my father just bought PS Elements 5.0, so I was wondering if it could work under Ubuntu. 

But thanks for your answer:-)

I would think it would work the same way under Wine as full Photoshop.

---

### Post by Naegling23 on 2007-02-12
im not big into photo editing, I just play around here and there, while I learn my way around.  My question is why would you want elements?  From what I understand, its a stripped down version of photoshop.  So can you not just use theGIMP for your photo editing?  It runs natively, and its open source.  I find it to be very adequate, but again, im not a professional or anything.

---

### Post by Oki on 2007-02-12
The old discussion isn't it:-) 

While is it true that Elements is a crippled version of PS CS, it has become a very good option for photography. The fact is that most people run PS just because they think its the best, when all tey use are in the Elements version. Besides the better interface then Gimp, it has a powerful engine that lets you do the converting with all its filters in 16bits mode(and yes, that is very important for large prints), it can work with actions, and good for print. This engine works also fast when it comes to RAW files. Gimp cant do none of that(but, I am rely looking forward for the next update!). digikam(and others) are better options for Photo than Gimp under Linux. 

When it comes to Wine it can “only” run PS 7.0. So I guess Elements 5.0 is no go. What I find strange(being a noob to Linux), is that there is a PS Elements version for Mac. I thought Mac was very alike Linux – so why cant they convert that to Linux?

---

### Post by wh0rd on 2007-02-14
Here's another success story: [http://26bits.com/2007/photoshop-cs2-on-linux-ubuntu/](http://26bits.com/2007/photoshop-cs2-on-linux-ubuntu/)
Why don't you give [http://portableapps.com/](http://portableapps.com/) a try then switch it to Linux via Wine?

---

### Post by abh83 on 2007-02-26
> **wh0rd said:**
> Here's a nifty little howto on getting Adobe Photoshop CS2 to work under Wine in Ubuntu:

[http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

I've got Adobe Photoshop 7.0 running with CrossOver Office perfectly (you can try installing it with Wine if you don't want to purchase CrossOver Office). If you really don't need all the features of CS to I'd say go with my method.

okay I'm following the instructions from the link above.

I'v exported HKEY_LOCAL_MACHINE/Software/Adobe/” to “adobe.reg

and pasted the adobe.reg file on my desktop in ubutnu. Now I'm trying to convert it:

> The next step is to copy that file to your Ubuntu box and convert it to the encoding of YOUR system. For example, if your Ubuntu box has as default charset ascii and your Windows box has ucs-2 then “$ recode ucs-2..ascii adobe.reg” would do the trick. After you converted your adobe.reg file, type “$ sudo wine regedit adobe.reg” to import it to wine.

but i keep getting this:

> ~/Desktop$ sudo recode ucs-2..ascii adobe.reg
sudo: recode: command not found

~$ recode ucs-2..ascii adobe.reg
bash: recode: command not found

any idea/solutions?

thx
abh

---

### Post by abh83 on 2007-02-26
help?

---

### Post by abh83 on 2007-03-01
*bump*

---

