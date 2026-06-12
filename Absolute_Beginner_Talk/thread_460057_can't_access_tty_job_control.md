---
title: "can't access tty job control"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by bilacus on 2007-05-31
I have a brand new mobo asus p5w dh. I have installed edgy 6.1 without problems, last month
I tried to install Feisty, but after few seconds of splash screen it comes out a shell message
can't access tty job control. and there is nothing I can do.

any idea. :KS

---

### Post by AAM on 2007-05-31
press ESC when  GRUB is being accessed (just after BIOS complete), 
[INDENT]press **e **(for edit) 
[/INDENT]and then arrow down to the second line and 
[INDENT]press **e** (for edit). 
[/INDENT]At the end of the line type [INDENT]**irqpoll** 
[/INDENT]then press [INDENT]**<enter>** 
[/INDENT]then 
[INDENT]press **b **(for boot). 
[/INDENT]That may improve your chances. Go away and have coffee and see if it has worked on return. If it does, after install 
[INDENT]type **sudo gedit /boot/grub/menu.lst** 
[/INDENT]and go to the bottom of the file where the load options are displayed and add 
[INDENT]**irqpoll** 
[/INDENT]to the second lines of the two load options for Ubuntu (normal and protected).

I hope this works. 

Might I suggest you also email ASUS and ask them whether this mobo actually supports Linux because you are thinking of purchasing one and will look else where if not. This should get you your information (is it supported?) and send them a message that Linux support is required in 2007 and beyond.

---

### Post by MCSE_Crossover on 2007-06-13
I also had a similar issue and used the IRQPOLL option, but noticed that this seemed to slow down my data transfer speeds significantly for some reason. What I did instead was change the IDE settings within the BIOS from Standard IDE to AHCI and it seemed to work without the IRQPOLL option needing to be specified in the kernel boot parameters. Don't ask me why though...

The only thing is, when having the mobo AHCI, it seemed to take about 30 seconds longer to boot. The error messages had something to do with "ATA2 didn't respond in sufficient time" or something and then it would say "resetting port." After the reset, it seemed to come up just fine and I didn't have the lag during HD to HD data transfers. Pehaps someone can shed some additional light on this. I will try to post error screen shots later.

---

