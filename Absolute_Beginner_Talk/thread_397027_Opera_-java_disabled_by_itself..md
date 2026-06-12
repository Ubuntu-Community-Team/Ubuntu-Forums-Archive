---
title: "Opera -java disabled by itself."
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by dweller35 on 2007-03-30
Hi,

I'm new to Linux and I have a problem with my Opera.

I have enabled java by selecting Tools > Preferences > Advanced > Content > Enable Java.

Java path > /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/amd64/

Thing is, after I restart my Opera, the 'Enable Java' option will be unchecked. I tried doing the same thing over and over again but still the same thing occured.

I've checked the javapath.txt and it contains the correct path. I've tried to use other path (java 1.5), but it didn't work either.

Am running on AMD64, Ubuntu Edgy.

Any advice?

Thanks.

p.s. I had some difficulties installing Opera before I eventually made it, not sure if that could indirectly cause this kinda problem.

---

### Post by zvacet on 2007-03-30
What kind of difficulties did you have with Opera install.Isn´t it in synaptic?Try to reinstall in synaptic or remove and install again.You shouldn´t have problems because you enebled java by Opera instructions.Maybe reason is that you are using 64version.go to the Java page and see is it any diference between 32 and 64 in installing plugin.

---

### Post by Colonel Kilkenny on 2007-03-30
I'd say that the problem is that your using 32-bit Opera and 64-bit Java.
I'm not using 64-bit Ubuntu myself because my experiences of it weren't that good.
Maybe you could try installing 32-bit version of Java? Although I'm not sure if it's wise.

---

### Post by dweller35 on 2007-03-31
zvacet: Nope it's not in the synaptic. I downloaded the statiq qt package (i386) and install it. The installation went fine, it's just that when I clicked on the Opera launcher, nothing happened. I removed it and re-install, but still the same. It wasn't executable. I was about to give another attempt to install it the other day, but before that I just clicked on the laucher, and miraculously it worked. Opera worked just fine, plugins installation was a breeze. And then this Java problem came up.

zvacet & Colonel Kilkenny: Yea, you guys were right, it is because the 32/64 conflict. I've installed java 32 and changed the java path, and it worked like a charm! Now it doesn't disable by itself anymore. Thanks guys!!!

But there is just one more problem (I hope). I tried to test the java on some pages.. but it's like a blank applet box appeared, and it says "Click to activate and use this control", which I did, but still.. nothing happened. So it's like.. Java is enabled, but it won't execute? Uhmm.

Appreciate any help you could offer.

Thanks again!

---

### Post by zvacet on 2007-03-31
Restart Opera and go to this page
[http://www.opera.com/support/search/view/459/]("http://www.opera.com/support/search/view/459/")

you will see test applets (blue colour)>click on it

---

### Post by dweller35 on 2007-03-31
Nope, just like other pages I've tried - it's like a blank applet loaded. No clock.

---

### Post by dweller35 on 2007-03-31
Owh sorry sorry.. the clock appeared on a new window. Thought it'll load on the same page. I forgot that they have mentioned this on the Opera site before.

Thanks a lot zvacet!

Case close :D

---

