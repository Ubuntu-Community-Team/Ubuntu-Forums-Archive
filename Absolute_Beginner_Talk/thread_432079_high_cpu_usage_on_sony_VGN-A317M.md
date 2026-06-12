---
title: "high cpu usage on sony VGN-A317M"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by stijngysemans on 2007-05-03
I just installed Ubuntu on a friends laptop, this particular Sony model. 
In windows he has a high cpu usage.
This also happens to be the case in ubuntu. The computer does crash (you can't do anything anymore) both in Windows and Ubuntu, probably caused by heat problems?

What can I do?

---

### Post by jfinkels on 2007-05-06
> **stijngysemans said:**
> I just installed Ubuntu on a friends laptop, this particular Sony model. 
In windows he has a high cpu usage.
This also happens to be the case in ubuntu. The computer does crash (you can't do anything anymore) both in Windows and Ubuntu, probably caused by heat problems?

What can I do?

To view processes and their CPU usage, go to the terminal and type:
```
top
```
Press 'q' to quit. 

To kill a process that is eating up your CPU, type the following:
```
killall *programname*
```

Perhaps you could tell us what process it is that is using the CPU? What does the 'top' program  show you?

---

### Post by stijngysemans on 2007-05-07
Ok thanks for your information.
So the following strange things appear to happen:
• "system monitor" takes already up to 32% cpu usages.
• when launching firefox, firefox takes up 40%
• when changing a webpage, cpu usage rises till 100%, as long as the new page is loading!

---

### Post by hessiess on 2007-05-07
use a air compressor to blow out all of the coolers. or if you dont have one you will haft to dismantle it to cleen them. dust builds up verry quicly destroying efective cooling.

---

### Post by www.rzr.online.fr on 2007-10-09
**This post could be related to an Ubuntu bug filed at**: [http://rzr.online.fr/q/viao](http://rzr.online.fr/q/viao) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				About  sony VGN-A317M, I have an offtopic question :

I have a friend w/ a similar laptop, he screwed his powersupply and thought about useing the battery plug to power it.

But can help him, and tell me the voltage on a charged battery on each pin ?

Regards 

--
[http://rzr.online.fr/q/viao](http://rzr.online.fr/q/viao)

---

