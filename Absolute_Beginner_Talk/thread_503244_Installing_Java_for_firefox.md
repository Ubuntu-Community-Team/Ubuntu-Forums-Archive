---
title: "Installing Java for firefox"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Mekanto on 2007-07-17
I tryed the Synaptic package manager and it did have some java on, which i have already installed. Although i need a different java download.

I have it on my desktop and it will not show in the Synaptic package manager or the add/remove applications. How do i install this. Firefox said I had to do a manual installation.

Please help?:confused:

---

### Post by Majorix on 2007-07-17
Do you have the java plugin installed? It should be called sun-java6-plugin or something similar.

Search Synaptic with the keyword "sun java" and you will see it for sure.

---

### Post by Mekanto on 2007-07-17
Well it looks like that worked thanks. My mistake was i was searching for just "java" but when i tryed "sun java" it came up. Thanks alot Majorix.

---

### Post by RavanH on 2007-07-17
> **Majorix said:**
> Do you have the java plugin installed? It should be called sun-java6-plugin or something similar.

Search Synaptic with the keyword "sun java" and you will see it for sure.

Very strange... I'm having the same issue but cannot find this sun-java6-plugin (or java5-plugin) in synaptic :(

I'm running Feisty AMD64 but with Firefox 32bit and want to install java5 32bit because java6 doesn't seem to be working very well. I've found and installed the packages:
- ia32-sun-java5-bin "Sun Java(TM) Runtime Environment (JRE) 5.0 (32-bit)"
- sun-java5-jre "Sun Java(TM) Runtime Environment (JRE) 5.0 (architecture independent files)"

Why would the plugin package not be in the repositories? Because of the 64bit Feisty? And if so, what to do next?

--ravan

---

### Post by vnrat on 2007-07-17
so am i, my company use Java Apllication, but Firefox doesn't work, after that I use Konqueror, Konqueror is working good, don't know why !??

---

### Post by maduranga on 2007-07-18
maybe Automatix will be a good answer for this problem. I'm using Automatix to install Java and I don't have experience any problem with it

---

### Post by testube_babies on 2007-07-18
> **maduranga said:**
> maybe Automatix will be a good answer for this problem. I'm using Automatix to install Java and I don't have experience any problem with it

Automatix is almost always a bad idea; Ubuntu Guide will allow you to install all of the most popular software packages the proper way.  [http://ubuntuguide.org](http://ubuntuguide.org)

"Automatix2 is a proprietary script that tries to install some software, and often fails and breaks systems. The Ubuntu community doesn't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to install a fresh copy of Ubuntu."

> **RavanH said:**
> Very strange... I'm having the same issue but cannot find this sun-java6-plugin (or java5-plugin) in synaptic...Why would the plugin package not be in the repositories? Because of the 64bit Feisty? And if so, what to do next?

Java isn't supported in 64bit.  Here's a how-to:
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

---

