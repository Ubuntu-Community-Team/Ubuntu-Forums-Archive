---
title: "Services, processes and memoryusage"
date: 2005-07-18
forum: Absolute Beginner Talk
---

### Post by Nasso on 2005-07-18
Howdy :)

Is there any way to control what processes and services are started when ubuntu is loaded? I was looking through my processes and i found stuff like cups there. I only got 256mb memory in my laptop and i really need to get the memoryusage down. anyone got any hints?

---

### Post by amohanty on 2005-07-18
use bum (BootUp Manager) kind of like RH serviceconf.
[http://ubuntuforums.org/showthread.php?t=42129](http://ubuntuforums.org/showthread.php?t=42129)

---

### Post by DJ_Max on 2005-07-18
Whats your usual memory percentage?

---

### Post by poofyhairguy on 2005-07-18
[QUOTE=Nasso]Howdy :)

Is there any way to control what processes and services are started when ubuntu is loaded? I was looking through my processes and i found stuff like cups there. I only got 256mb memory in my laptop and i really need to get the memoryusage down. anyone got any hints?[/QUOTE]

Gnome is whats eating your memory. Its hard to make Gnome not want a lot of ram. The best solution is to install XFCE. It can be made to work like Gnome.

---

### Post by Nasso on 2005-07-19
[QUOTE=poofyhairguy]Gnome is whats eating your memory. Its hard to make Gnome not want a lot of ram. The best solution is to install XFCE. It can be made to work like Gnome.[/QUOTE]

it wasnt as horrible as i thought :)
Im using the systemmonitor applet. it said 
Memory:
94% in use of which
21% is chache

and that was just after i started the computer and fired up firefox. when i click on the applet and the system monitor started i could read on the resources tab that i used 55% memory and no swap. does anyone know why? :P

---

### Post by DJ_Max on 2005-07-19
I would only worry if I'm using a lot of my swap. And if you have  all your swap used, it's usually a memeory leak with an application. What app is using the most resources?

---

### Post by Nasso on 2005-07-19
[QUOTE=DJ_Max]I would only worry if I'm using a lot of my swap. And if you have  all your swap used, it's usually a memeory leak with an application. What app is using the most resources?[/QUOTE]
 its not really a problem anymore. i was only using 50% :) it was the applet that was showing me the wrong numbers :)

---

### Post by doclivingston on 2005-07-20
Determining how much memory is "in use" is always fairly tricky on Linux. The basic answer is to look at how much swap memory is in use - if none is, or only a small amount) then everything is fine. If a moderate amount in use, then it's okay but it will work a lot better with some programs killed. If you have a large amount in use (and are almost out) then you need to kill things, or get more ram.

Linux aggressively uses ram as cache, much more so than Windows, so if it looks like it's all ine use, but no swap memory is being uses, then don't worry.

---

