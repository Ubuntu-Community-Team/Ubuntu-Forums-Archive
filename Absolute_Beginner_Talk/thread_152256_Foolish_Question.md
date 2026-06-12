---
title: "Foolish Question"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by kwjaxon on 2006-03-29
I have been reading, googleing, and trying to get a new Ubuntu online for about 10 days.  The questions I have are: 1.  When you can't logon how do you use all the help you obtain when they all seem to be run from Ubuntu operating online?  2. How do you install the items needed when you do not get them from source.  What I guess I am saying is how do you dload or install files from CD or from floppy, and from flash drive to Ubuntu.  Have about given up.  May not know enough to run Ubuntu.  TIA

---

### Post by aysiu on 2006-03-29
[QUOTE=kwjaxon]I have been reading, googleing, and trying to get a new Ubuntu online for about 10 days.  The questions I have are: 1.  When you can't logon how do you use all the help you obtain when they all seem to be run from Ubuntu operating online?[/quote] First of all, when you can't log in, something's seriously wrong. That's not normal. But if you have to type in commands to get things working again, boot into recovery mode (it's usually the second option in the boot menu, right above "memtest"). This will put you to a console operating as root.  > 2. How do you install the items needed when you do not get them from source.  What I guess I am saying is how do you dload or install files from CD or from floppy, and from flash drive to Ubuntu.  Have about given up.  May not know enough to run Ubuntu.  TIA This is what sucks about Ubuntu right now. There's a project to get [an Add-On CD](http://www.ubuntuforums.org/showthread.php?t=136955) and a few of us have made a few hodgepodge ones you're welcome to download, but other distros generally have official add-on CDs (Debian has something like 7 or 14) where you can get more software.

Ubuntu without internet isn't worth it, in my opinion.

---

### Post by trent dillman on 2006-03-29
Visit packages.ubuntu.com and download what you want to install, then use dpkg to install them.

It can be done. It's just a bit of a pain, especially when you hit dependency issues and have to download more stuff.

---

### Post by pbaehr on 2006-03-29
I'm more concerned about why you can't log in. Does your computer make it through the boot process? Do you ever reach a login prompt? That's definitely the first problem that needs tackling. Can you give more details?

---

### Post by trent dillman on 2006-03-29
I thought he meant he couldn't log on to ubuntu forums, not the system.

---

### Post by kwjaxon on 2006-03-29
Hey Guys, or Girls, sorry to be unclear.  I have the OS installed and running.  Camera, scanner, printer and just about everythink I have tried.  Even purchased a new hardware modem.  I thnik I have read enough to do most of what I am interested in, if I could just get online.  Neither my old winmodem or my new hardware even though has file for linux on CD.  I guess I need a more simple procedure for putting in the linux file off the CD.  Hope this helps some.

---

### Post by catlett on 2006-03-29
Sorry to bother you but could you satisfy my curiousity? Do you mean you can't access the internet? That your computer has Ubuntu installed, you can get into the OS and do offline stuff but you can't access the internet? That your modem isn't working? And you are looking for a driver or program that will allow you to access the internet , but you can't get anything else on your system besides what came on the install disc because your not connecting with the internet? The thread has just piqued my curiousity.

---

### Post by kwjaxon on 2006-03-29
As they say from where I come from, you hit the nail on the head.  Seem to be able to do everything that I have tried except get online.  Even with the hardware Linux approved modem.  Have all the files and necessary software supposedly to make it work, but unable to put it into Ubuntu.  Could you help?

---

### Post by jamesr on 2006-03-29
Are we talking about a dialup modem? or broadband?
Internal / external ?

---

### Post by kwjaxon on 2006-03-29
Dialup hardware modem Intel 536ep.  Have drivers for Linux.

---

### Post by kwjaxon on 2006-03-29
Sorry, internal.  In my research, most seems to think hardware modem or serial external modem would work.  Thanks.

---

### Post by catlett on 2006-03-30
I am not very fluent in Ubuntu but I wanted to reply so your post would get back on the front page of the forum. That way your more likely to get someone really capable to view your post. The only thing that pops into my head is,  did you try the Live CD? Does it work with that? Or what about booting from another distros Live CD and see if you can access the internet. That way if you can get on, you can download what you need. Like I said I don't know much. Hopefully someone Intelligent will now see your post and save the day . Regards, Catlett

---

### Post by jamesr on 2006-03-30
There is a large section on the wiki [https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")about installing modems and it seems to contain a significant section on 536ep. 
There seem to be several stages,
1) install sources
2) compile sources
3) put module in the correct location
4) get system to recognise module
5) modprobe module to activate
and so on

---

### Post by erniewinner on 2006-03-30
](*,)  you don't get problems like this with ethernet...

---

### Post by ferebee on 2006-03-30
[QUOTE=erniewinner]](*,)  you don't get problems like this with ethernet...[/QUOTE]

No offence, erniewinner, but ethernet just isn't an option for everybody.
Sometimes you're stuck with dial up and that's that.

kwjaxon, If you don't want to try the procedure that jamesr linked to, 
you might try to get your hands on an external serial modem.
These rarely need drivers, and are compatible with most
linux distros.  I have a US Robotics Courier modem and every
distro I've tried has recognised it. 

An external moden can be hard to find and can be pricey new,
but I got mine second hand for under $30 Cdn. 

Just an option to consider.

---

### Post by erniewinner on 2006-03-31
:mrgreen:  i know but looking at the page of text i was a little perturbed! i don't think too many newbies want to do all that if they can't get it to work as an end result! and the price of broadband is surely at the same price of dialup now? when i was on windows i decided i couldn't afford not to switch to broadband because of the problems with dialer software... anyway if he gets no joy ethernet is as plug and play as you can get. and most pc's and laptops have them already built in? i gotta say i was supprised ubuntu had drivers that worked for my ethernet to usb adaptor of the bat!!! :D

---

### Post by ferebee on 2006-03-31
[QUOTE=erniewinner]:mrgreen:  i know but looking at the page of text i was a little perturbed! i don't think too many newbies want to do all that if they can't get it to work as an end result! and the price of broadband is surely at the same price of dialup now? when i was on windows i decided i couldn't afford not to switch to broadband because of the problems with dialer software... anyway if he gets no joy ethernet is as plug and play as you can get. and most pc's and laptops have them already built in? i gotta say i was supprised ubuntu had drivers that worked for my ethernet to usb adaptor of the bat!!! :D[/QUOTE]
I know looking at that kind of serious stuff to get my modem online as a newbie put me off using Linux for a while, but I still really wanted to try, so I got an easier modem! :)

 I don't know about where kwjaxon lives but where I am, out in
a rural area broadband is just starting to become available at almost twice the price we are paying for dial up. A lot of rural areas won't get access to broadband for some time yet. 

I would looove to switch, but I just can't afford that much extra on the monthly bills, plus the cost of new hardware for our computers. :(

---

### Post by kwjaxon on 2006-04-01
Thanks for all the help and concern.  As previously stated, dialup modem is my only choice.  From a financial view that is.  Am 76 yrs old and have more time than money.  Again thanks for the help, am now looking for external serial modem.  Long live Linux.

---

