---
title: "Is this a normal shutdown for Ubuntu Feisty Fawn?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Relztrah on 2007-05-09
System>Quit>Shut Down does not turn my machine off. The Ubuntu logo appears on the screen. The on/off button on my computer does *not* power down the unit. (In fact it doesn't do anything.) There is no power switch next to the power supply like on some computers. So I am forced to pull the plug. Is this normal?

I am willing to attempt any fix but I am an absolut novice with Linux so before you suggest any GRUB commands or such, please give simple step-by-step instructions on how to open an edit screen, save, close, etc. and where to go from there.

Thanks, 
Relztrah

---

### Post by mejy on 2007-05-09
It sounds like an ACPI problem, which means you're best bet's either waiting for an update, filing a bug on launchpad.net or trying another distro.  I'm assuming this is a fairly modern computer?  ACPI is the standard used for power control in computers, and MS essentially crippled it with a bunch of proprietry add ons and the like.

You could also try runnning 'sudo halt' in the terminal, in case it's a bug at a higher level.

---

### Post by edgecoug71 on 2007-05-09
It doesn't sound like a normal shutdown....I do the same as you and mine turns off..may there is an update that will help, but you can turn off your machine in the CLI as root, but I don't know how to do it for Ubuntu yet, only Fedora Core 6....sorry, hope everything works out for you......you may want to run a search for your issue and see what comes up if you haven't already....The way I do it in Fedora if you want to try is....

1. open terminal
2. login as superuser
3. type shutdown -h now (to reboot it is -r)
4. the computer will start its shut down procedures

Here is a brief tutorial i found on the internet....may work, may not but good luck :) 


To shut down the system at a certain time, you normally give that time as an argument; use the special `now' argument to begin the shutdown process immediately. 

To immediately shut down and halt the system, type: 
# shutdown -h now [RET]

To immediately shutdown the system, and then reboot, type: 
# shutdown -r now [RET]

You can follow the `now' argument with a quoted message that will be displayed on all terminals of all users currently logged in. 

To immediately shut down and halt the system, and send a warning message to all users, type: 
# shutdown -h now "The system is being shut down now!" [RET]

---

### Post by mjwhitfield on 2007-05-09
have you tried holding down the power button on the front for 10-20 seconds, that'll turn your machine off, rather than yanking the power out.

---

### Post by Delkster on 2007-05-09
> **mjwhitfield said:**
> have you tried holding down the power button on the front for 10-20 seconds, that'll turn your machine off, rather than yanking the power out.

It should do that in even less, around four seconds.

By the way, I've seen similar problems with some older Ubuntu releases. Never got around to troubleshooting them (yet), but if I happen to do that in the near future, I'll post here.

---

