---
title: "HP Mini 210 netbook  wifi issues... again"
date: 2012-01-30
forum: Any Other OS
---

### Post by theHands on 2012-01-30
Hi,
My Hp Mini 210 netbook was running windows 7, but got a real bad virus.
 
So I installed xp on it for now at least.
 
I'm also trying out linux mint inside xp on it, to see how it goes.
(I hope someone here knows just a little about how mint works?)
 
But i cant get the wifi to work.
I was hopeing linux had addressed this issue by now?
 
I'm also not at all clued up on having to type 'linux language' to add programme, drivers, etc.
It maybe easy when you know how, but then so is other computer language.
I dont know how, and dont really want to know to be honest.
 
Isn't there an easy way to find a working driver, and just use the mouse to run and install it like on other OS's?
that would be usefull , thanks
 
 
otherwise i guess i'll be uninstalling linux for a 4th time lol.
 
lets hope its atcually usable by now

---

### Post by ahallubuntu on 2012-01-30
> **theHands said:**
> Isn't there an easy way to find a working driver, and just use the mouse to run and install it like on other OS's?

Linux itself is no worse than the other OSes in this regard.  It has a lot of drivers built in but not always.

Windows and Mac also both lack drivers for lots of new hardware.  When you buy a new piece of hardware like a printer, plug it in, and Windows can't find the driver, what do you do?

A: Insert the CD that came with the printer, or download the driver from the printer manufacturer's website.  Right? It's often not just "use the mouse and install."

So why can't you sometimes do this with Linux?  Because the HARDWARE MANUFACTURER CHOSE NOT TO SUPPORT ITS PRODUCT IN LINUX.  This isn't Linux's fault.  Blame the manufacturer of the hardware who chose to include a CD that works with Windows and Mac but not Linux.

> **theHands said:**
> otherwise i guess i'll be uninstalling linux for a 4th time lol.
 
lets hope its atcually usable by now

Linux is very usable if you understand it's the hardware manufacturers, not the operating system, that determine whether hardware works.  Blame HP, not Linux.

People here WILL help you get your wireless card to work in Linux, if you have the right attitude, if you understand that to make up for lousy manufacturer support for some hardware, volunteers have spent hours creating solutions to make it work, even the solution isn't always simple.

If not, go back to Windows, and enjoy the viruses!

---

### Post by Bucky Ball on 2012-01-30
There's every possibility your card is supported in Linux. This next solution is really not tricky. Open a terminal and type:

```
sudo lspci
```Post the result back here and that will let us know what wireless card you are using and we can go from there. Have you plugged in an ethernet cable and gotten online that way? If not, do it, get updates. This may fix things 'automagically'. For legal reasons not all drivers can be included in Linux, they must be installed manually so you can agree to manufacturers terms during the install.

Do you have 'Additional Drivers' in Linux Mint? If so, after the update, check in there to see if it has found something and it is disabled. If so, enable. 

This may be a lot simpler than you imagine and you may be assuming things about an OS that you admit yourself you know little about. ;)

---

### Post by Perfect Storm on 2012-01-30
Moved to Other OS/Distro Talk.

---

### Post by theHands on 2012-01-30
''Blame the manufacturer of the hardware who chose to include a CD that works with Windows and Mac but not Linux''
 
I blame both
I cant expect every software to bend for linux, when linux is so very unpopular compared to windows or mac.
linux does love to give the impression that its plain sailing tho...
I keep falling for it...
and keep finding out its not.
 
however, i dont want to be accused of 'flaming'
you are free to say 'go back to windows and enjoy your viruses'
but if i comment on linix, im likely to be warned about it lol..
this is common...
nevermind.
 
thanks for the help and tips..
 
And im very pleased to say that  linix mint Did find a driver, without me having to type any code...
so it is improving.
 
Especially since, ive re-installed windows 7, and even that wont find me a working driver for wifi, even if i download it from the hp website.... insanity.
 
I may tinker around with linux mint somemore within windows xp for a while, see how it goes.
 
But to be honest, my main concerns are:
1. I DO NOT want to have to type that stuff to perfrom tasks, it just totally confuses me, and i dont want to have to lern a new language, i just want an intuitive OS.
 
2. A severe lack of software support / games that i like.
 
other than that, its looking good.
linux was always smooth and stable..thats whats good about it to me.

---

### Post by Viman on 2012-01-31
> **theHands said:**
> my main concerns are:
1. I DO NOT want to have to type that stuff to perfrom tasks, it just totally confuses me, and i dont want to have to lern a new language, i just want an intuitive OS.
 
2. A severe lack of software support / games that i like.
 
other than that, its looking good.
linux was always smooth and stable..thats whats good about it to me.

Have you noticed that Linux is free? Well, one relevant thing about that is that you don't get the coddling for free.

I never discriminate Linux users from others, but sometimes I feel it's necessary to have a slight "knack" for tinkering with the system in order to be able to use a Linux distribution. Now, it's true that some distros require more tinkering and others less, but you still will have to do it at some point (no exceptions).

If you're not willing to do ANY kind of work to get something up and running (I'm sure it's not a lot to begin with) then I'm sorry but the best way for you is to get that Original OS and configurations that came when you purchased it (I'm sure it all worked out of the box, right?). 

No, really, do it. 1000% less headache for you.

But wait, did you really expect successful gaming in Linux? Haven't you heard about it? Gaming in Linux is an oxymoron!

---

### Post by theHands on 2012-02-29
> **Viman said:**
> Have you noticed that Linux is free? Well, one relevant thing about that is that you don't get the coddling for free.

I never discriminate Linux users from others, but sometimes I feel it's necessary to have a slight "knack" for tinkering with the system in order to be able to use a Linux distribution. Now, it's true that some distros require more tinkering and others less, but you still will have to do it at some point (no exceptions).

If you're not willing to do ANY kind of work to get something up and running (I'm sure it's not a lot to begin with) then I'm sorry but the best way for you is to get that Original OS and configurations that came when you purchased it (I'm sure it all worked out of the box, right?). 

No, really, do it. 1000% less headache for you.

But wait, did you really expect successful gaming in Linux? Haven't you heard about it? Gaming in Linux is an oxymoron!

I dont expect much from ubuntu.
Just as well....

---

### Post by Bucky Ball on 2012-02-29
Back to the original problem ... I still don't see the result of this:

```
sudo lspci
```

When you say you installed inside Windows, do you mean as a virtual machine or a Wubi install???

Try a full install to a partition (not using Wubi) if it was a Wubi install. Then again, it's been awhile so you probably tossed in the towel by now ...

---

### Post by theHands on 2012-03-07
Hi
I'm running  windows 7, xp, and linux mint 11 on my netbok.

I installed windows xp first, then 7, then mint.

i made two partition with xp, then added windows 7.
then when i added mint, i had to take some of windows 7 partition, plus another small partition for 'swap' files.

its all installed ok.

but mint is giving me a few issues also..
software, flash players etc..
linux is worth having.. just
but boy, does it have some gaping flaws.

---

### Post by Bucky Ball on 2012-03-07
> **theHands said:**
> Hi
I'm running  windows 7, xp, and linux mint 11 on my netbok.

I installed windows xp first, then 7, then mint.

i made two partition with xp, then added windows 7.
then when i added mint, i had to take some of windows 7 partition, plus another small partition for 'swap' files.

its all installed ok.

but mint is giving me a few issues also..
software, flash players etc..
linux is worth having.. just
but boy, does it have some gaping flaws.

Please start a new thread with a descriptive title and as much info as you can muster. You will get more specific help. Jumping on this thread (hijacking) just makes it confusing for everyone; attempting to solve two problems from two different OPs on the same thread makes it difficult as your issues don't have anything to do with the original OP's. Thanks. ;)

---

### Post by theHands on 2012-03-08
> **Bucky Ball said:**
> Please start a new thread with a descriptive title and as much info as you can muster. You will get more specific help. Jumping on this thread (hijacking) just makes it confusing for everyone; attempting to solve two problems from two different OPs on the same thread makes it difficult as your issues don't have anything to do with the original OP's. Thanks. ;)

ok Bucky Ball, 
will bear that in mind for future
 thanks

---

