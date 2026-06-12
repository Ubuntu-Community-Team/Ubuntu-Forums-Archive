---
title: "new question about ATI driver for Gutsy Gibbon"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by moose4204l on 2007-12-10
ok so, I have read the forums and tried everything. Initially, i had a blank screen on logon but after endless trials and errors of following mine and other peoples forums, I got it to work through. I did method 1 on the 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
page. Then I did the 

sudo dpkg-reconfigure xserver-xorg and picked Vesa from the list and just hit enter/ok through the rest. I now have a GUI! 

my question is now, how do I update the ATI driver and configure it so I can have running and operating the original way I had it?

I need a dumb down version because I am still a noob with linux/ubuntu

thanks

---

### Post by Vadi on 2007-12-10
I applaud your persistence... here, try this?

[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#)

---

### Post by moose4204l on 2007-12-12
nope, that didnt work , plus a lot of people said that it doesnt work for them on the feedback section. any other ideas? im tired of this vesa crap giving me lines some times.

---

### Post by prasadz8 on 2007-12-25
**i have the same problem**, after doing this:*sudo dpkg-reconfigure xserver-xorg* everything was on form. BUT! I still have the problem of my logon screen going "blank". Nevertheless, the logon console is still there, but my monitor does not show it. :confused: Resolution problem perhaps?

Anyway, I log on [blindly] and ubuntu runs with compiz just [SUPERBLY] fine.
Eventually, I set it to log on automatically, bypassing the blank nuisance.

**my Q**: can i see my logon screen again, please? It feels like having an awesome ride without a sound system in it! Just incomplete.

**my efforts**: tried most of it, didn't work out for me too. Any dead-end solutions to this?

Praz runs on: ATI Radeon x550 **+** AMD Sempron **+** 15" 4:3 SyncMaster 510N monitor.

---

### Post by Vadi on 2007-12-25
So just the login window screen doesn't appear properly?

---

### Post by prasadz8 on 2008-01-12
oh yeah, i got it fixed by messing around with the Login Window tool under administrations. A lil tweak here and there did the job. As I expected, it was the resolution.

---

