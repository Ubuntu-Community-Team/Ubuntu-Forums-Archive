---
title: "Any command to see the computer hardware summarized?"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2007-10-13
Hi!!! I'm looking for a command that when I run it on a ubuntu computer it tells me, for example:

You have a Pentium III
You have 1GB of RAM DDR2
You have 1 hard drive of 80GB
You have the following OS installed:
...


You know the kind of hardware stuff anyone is interested to know when touching for the first time a computer. Very simple stuff.

Of course I guess there's not a simple command, but if you could give me some commands that tell me those things (in a clear way, not 37 lines to tell me "you have a pentium III") I could make a little script for this purpose.


Thank you very much for your help!!!

---

### Post by overdrank on 2007-10-13
> **fredscripts said:**
> Hi!!! I'm looking for a command that when I run it on a ubuntu computer it tells me, for example:

You have a Pentium III
You have 1GB of RAM DDR2
You have 1 hard drive of 80GB
You have the following OS installed:
...


You know the kind of hardware stuff anyone is interested to know when touching for the first time a computer. Very simple stuff.

Of course I guess there's not a simple command, but if you could give me some commands that tell me those things (in a clear way, not 37 lines to tell me "you have a pentium III") I could make a little script for this purpose.


Thank you very much for your help!!!

Hi, well the two I use are 
```
lspci
lshw 
```

---

### Post by ThrobbingBrain66 on 2007-10-13
Are you on a server with no GUI?  Is this why you want it to be a command?

System > Administration > System Monitor > System tab gives all the info you've asked for.

---

### Post by spiderbatdad on 2007-10-13
Of course, System--> Preferences--> Hardware Information  gives you a GUI of your hardware info.

---

### Post by hyper_ch on 2007-10-13
```

sudo apt-get install hwinfo

```
```

cd ~/Desktop
hwinfo > hardware.txt

```

And then you have it in the hardware.txt on your Desktop

---

### Post by fredscripts on 2007-10-13
OK!! Thanks to all, I'm not on a command line server, but on my Kubuntu 7.04 the other day I gone crazy to know how many RAM I had lol (I'm quite newbie, but surfing on KDE I didn't find anything like the question I've done on this post). I'm going to take a look on the replies, many thanks to all!

---

### Post by bodhi.zazen on 2007-10-13
You can see ram/memory use with :

```
free
```

---

### Post by xc3RnbFO8P on 2007-10-13
> **bodhi.zazen said:**
> You can see ram/memory use with :

```
free
```

What is rigth?

---

### Post by Rui Pais on 2007-10-13
an image is better then a thousand words ;)

[ATTACH]46234[/ATTACH]

---

### Post by bodhi.zazen on 2007-10-13
> **Ringi said:**
> What is rigth?

Yes.

Mem = you ram.

You are not using swap ...

The actual free (available)  memory is listed in "+/- buffers/cache" column under "free"

> **Rui Pais said:**
> an image is better then a thousand words ;)

[ATTACH]46234[/ATTACH]

Nice one :twisted:

What Rui Pais "pictured"

---

### Post by xc3RnbFO8P on 2007-10-13
> **Rui Pais said:**
> an image is better then a thousand words ;)

[ATTACH]46234[/ATTACH]

Do I need swap if I have 2 gb ram?

---

### Post by Rui Pais on 2007-10-13
Well is always better, imho... 
Really needed if you want to suspend-to-ram.

---

### Post by bodhi.zazen on 2007-10-13
> **Ringi said:**
> Do I need swap if I have 2 gb ram?

Probably not. The "standard" seems to be swap = ram X2, max 1 Gb

swap is more important on low ram systems.

The only exception I know of is if RAM > 0.5 Gb , swap = ram if you have a laptop and want to use suspend.

Of course if you run a large application and run out of RAM your system will likely crash :)

---

### Post by xc3RnbFO8P on 2007-10-13
> **bodhi.zazen said:**
> Probably not. The "standard" seems to be swap = ram X2, max 1 Gb

swap is more important on low ram systems.

The only exception I know of is if RAM > 0.5 Gb , swap = ram if you have a laptop and want to use suspend.

Of course if you run a large application and run out of RAM your system will likely crash :)

Do swap slow down the computer?

---

### Post by Rui Pais on 2007-10-13
> **bodhi.zazen said:**
> ...

Of course if you run a large application and run out of RAM your system will likely crash :)
yes, it happened to me once, with firefox, tabs are pure memory eaters! I don't realized i had an already opened FF with more then 20 tabs, i opened another FF window and keep reading stuff opening more tabs.
All frozen and i had to go to a console to discover whats wrong a kill the process.
Not a nice experience.


PS: @Ringi
with 2G ram, swap will be hardly touch, so no slows will occur. Think of it as a lifesaver :)

---

### Post by bodhi.zazen on 2007-10-13
> **Ringi said:**
> Do swap slow down the computer?

No. Swap is used only if you run out of ram. If you are using swap, it is slower then ram, so ram is better then swap, but having an un-used swap partition will not slow you down and may protect you in the event you run out of ram, so I do not see a down side.

---

### Post by xc3RnbFO8P on 2007-10-13
> **bodhi.zazen said:**
> No. Swap is used only if you run out of ram. If you are using swap, it is slower then ram, so ram is better then swap, but having an un-used swap partition will not slow you down and may protect you in the event you run out of ram, so I do not see a down side.

I dont know what happend, but I ran in to some problem when  I install Ubuntu after the terrible friday 13. :)

---

