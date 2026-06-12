---
title: "Live CD trouble, &amp; Internet connection problems."
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by {A}Poly on 2007-08-23
**read the following, and post below if you can help me out.**

i just got new stuff:

MSI motherboard supports Intel dual core processors, and quad core processors. Supports 45 mn.

Intel dual core e4400 2.0GHz processor

1GB 800MHz DDR2 (1) Kinghston memory

and finally exchanged my 160 IDE hard drive for a 160 sATA 7200RPM hard drive.

I connected all the wires and all the hard ware stuff myself. finished yesterday.

when i put the ubuntu 7.04 live CD in and reboot i select install or whatever. Then it starts and i get this:

"/bin/sh: can't acess tty; job control turned off
initramfs) help"

--------------------------------------------

My second pc which is:

512mb DDR ram
MSI motherboard - supports AMD
AMD athlon 3200+ 2.0GHz with fan
40GB IDE hard drive

I got ubuntu 7.04 on it easy, it's running good.
when i logged on for the first time though. the sound was not detected, and the internet connection was not detected automatically, it should however be automatically detected.

I have my internet connection conected to a D-Link router thingy that connects to both computers. Internet is up 24/7 and should work fine. Before it worked with my other PC that had ubuntu.... but now it doesnt on this PC.


So if anyone could help that would be great. I called my internet provider; "Shaw" which didn't help at all, they said they didn't even support linux. They tried to find a number to contact some ubuntu support but no luck.

anyone if you can help post below!

thanks!

---

### Post by {A}Poly on 2007-08-23
bump...

---

### Post by {A}Poly on 2007-08-23
bump.

---

### Post by nitro_n2o on 2007-08-23
first of all you've got some nice custom parts to assemble a nice pc.. but all the information provided are worthless... a kingston memory is not actually affecting anything.. 
I'd say that your question would've been solved by now if you only asked the Question 
your question should've been something like i can't boot from liveCD i get this error "/bin/sh: can't acess tty; job control turned off
initramfs) help" 
however check this out.. it might solve your problem [http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control](http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control) 

for the internet problem.. these are not enough info.. you haven't configured your network interfaces correctly or maybe some router settings have changed and your router is denying access to your pc.. or maybe the ethernet is not plugged in correctly...etc 
if your first problem is solved... post the output if this command here (to try to know wht's wrong with your internet)
```
ifconfig  eth0
```

---

### Post by {A}Poly on 2007-08-26
> **nitro_n2o said:**
> first of all you've got some nice custom parts to assemble a nice pc.. but all the information provided are worthless... a kingston memory is not actually affecting anything.. 
I'd say that your question would've been solved by now if you only asked the Question 
your question should've been something like i can't boot from liveCD i get this error "/bin/sh: can't acess tty; job control turned off
initramfs) help" 
however check this out.. it might solve your problem [http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control](http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control) 

for the internet problem.. these are not enough info.. you haven't configured your network interfaces correctly or maybe some router settings have changed and your router is denying access to your pc.. or maybe the ethernet is not plugged in correctly...etc 
if your first problem is solved... post the output if this command here (to try to know wht's wrong with your internet)
```
ifconfig  eth0
```

INTERNET PROBLEM = SOLVED

for the other computer : not solved.

the link didn't help i get the same error. I'm taking it down to the place i bought the hard drive.

basically if anyone can help, post here.

again heres the problem more specified:

when i boot the ubuntu 7.04 live CD it does not load i get this error: "/bin/sh:can't access tty:job control turned off"

---

### Post by {A}Poly on 2007-08-26
oh and:

My hard drive is 160GB connected with a SATA cable. It goes from the hard drive to sata1 on my motherboard. the power is connected to the hard drive, and everything should work well. It's all top condition and new. If i can't get help I'm taking it to the computer store where i baught most of the parts, so it'll be there problem :D

---

