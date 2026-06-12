---
title: "Canon Pixma MP460 - How to install ?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Xanatosplus on 2007-04-01
Hi, 

when i add a New Printer (Canon Pixma MP460, connected via USB #1) Ubuntu 6.10 recognize it.
The printer itsel if working fine, all the hardware is set as the manual say.

The driver suggested by Ubuntu (during the automated procedure) are the MultiPASS C2500, but the printer don't work after the installation, and the printing process alt itself on stanby, no matter what i do.

The official Canon printer page show driver only for Windows and Mac, no Linux driver are listed.

Anyone can tell me were i can find these driver ?
Or maybe if the driver is already set in Ubuntu, what is it ?

---

### Post by mikeyphi on 2007-04-01
Sorry to say that it looks as though Canon do not have a Linux driver for your printer yet. I'm in the same boat with my MP150.
I've got 2 options at present - use a paid-for solution from [http://www.turboprint.info/](http://www.turboprint.info/)
or dual boot back into XP to print.

---

### Post by Xanatosplus on 2007-04-01
I hope the new relase of Ubuntu will have these drivers... :(

The pay solution is not the reason i've switched Windows Xp for Ubuntu, and i don't understand why such an important driver is still missing.
Canon is, after all, a good diffused printer.

---

### Post by puredoxyk on 2007-04-06
Ouch!  I just bought one of these.  I haven't used Windows at home for years and have no intention of going back ... what a nasty situation.  I know Canon probably has no intention of making a driver, so hopefully some lovely Ubuntu coder does.

---

### Post by dudds on 2007-04-06
Same here. Does anyone know of other drivers that may work with this printer?

---

### Post by dudds on 2007-04-07
Guys just came across the following link at Canon Europe web site:

[http://www.canon-europe.com/Support/Software/Linux/registration.asp](http://www.canon-europe.com/Support/Software/Linux/registration.asp)

If you click on the other printer users link you can register your interest in a Linux printer driver for a particular printer.

---

### Post by Repent on 2007-04-07
I have a canon i960 and the only way I could get it to run was to use TurboPrint.

---

### Post by ramjet_1953 on 2007-04-07
> **Xanatosplus said:**
> I hope the new relase of Ubuntu will have these drivers... :(

The pay solution is not the reason i've switched Windows Xp for Ubuntu, and i don't understand why such an important driver is still missing.
Canon is, after all, a good diffused printer.

What a lot of people don't understand, is that companies like Canon and especially Lexmark do not support any other OS than Windows. 

In fact, it sometimes seems that they go out of their way to lock their printers into Windows and nothing else.

I am amazed that we have programmers working for free in the Linux community with such expertise that they are able to reverse-engineer the driver for a printer, needed to work in Linux.

Of course, this takes much time to do and fairly new printers may not yet have a driver available.

The fault lies with the printer manufacturers, not Linux. 

If you feel so stongly about a Linux driver not being available for your printer, I suggest you complain to Canon, where the fault lies.

Regards,
Roger 8)

---

### Post by johncro13 on 2007-04-14
I have one of these, too.  Great printer, but totally useless in 'nix so far.  You can use the Turboprint option and download the trial, then set the print quality to 300dpi, if I remember from a google link correctly.  
Honestly, I wouldn't mind paying good programmers, hackers and crackers for the fine work they've done.  I remember a time when I thought Linux was more about self-education and a can-do attitude than about waiting around for somebody else to do something for you for free as an MS monopoly alternative.

But just like groupies aren't all musicians, and art critics aren't all artists, Linux users can't all be code monkeys.  It looks like we're just going to have to wait a while.  

[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by dantae@sk on 2007-06-10
Hello all,

I have Canon Pixma MP460 and was trying to make it run under Gentoo linux for few days.
And I was successfull :p

I will post you the details and hopefully you will find way how to install it under Ubuntu.

I was doing according to page [http://gentoo-wiki.com/Canon_Pixma_Series](http://gentoo-wiki.com/Canon_Pixma_Series).
I have used the package cnijfilter-2.70.
And then in CUPS configuration, I was trying all the drivers. All of them were comunicating with my printer, some of them make the printer print only empty paper, some of them printed, but the colors were not in sync. Finally I tried the driver mp160 and the output was good.

I have also tried the drivers from turboprint which are not free (or free for personal use, but on some printers there is turboprint logo on each printed page). There was driver for my MP460, so I tried it and it was working fine, but there is that turboprint logo on each page.

And a compare from using cnijfilter package, mp160 driver and that one from turboprint: on that few pages wich I printed, the outputs are very similar. Actually the colors when using cnijfilter are looking a bit better.

I had problems printing from postscript, so I have look on that, but currently I do not need it.

---

### Post by rob.webinator@gmail.com on 2007-06-10
It is the manufacturers choice to support or not support an operating system; it is part of their business model.  It's too late for those who have already made their purchases, but for those who haven't, it is strongly recommended to check a hardware compatibility list (HCL) like the following before your purchase:
[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)

I for one, after purchasing many peripherals w/out consulting an HCL have become extremely frustrated as many of you are now and now I go out of my way not to support companies that do not support linux.

Best of luck!

---

### Post by Sohum on 2007-06-25
I think I got it working! See instructions at [http://ubuntuforums.org/showthread.php?t=484436](http://ubuntuforums.org/showthread.php?t=484436)

---

