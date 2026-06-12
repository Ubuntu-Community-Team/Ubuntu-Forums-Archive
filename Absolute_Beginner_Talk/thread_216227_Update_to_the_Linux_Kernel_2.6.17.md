---
title: "Update to the Linux Kernel 2.6.17?"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by sebz2005 on 2006-07-15
I know I have asked many people and posted this in a few threads, but I really need the answer quickly.

Is there a apt-get command that can get and install the latest linux kernel?

---

### Post by SkyNet2029 on 2006-07-15
afaik , 
```
$sudo apt-get dist-upgrade
```
will pull up the latest linux-kernel for you.

---

### Post by Perfect Storm on 2006-07-15
> **sebz2005 said:**
> I know I have asked many people and posted this in a few threads, but I really need the answer quickly.

Is there a apt-get command that can get and install the latest linux kernel?

Well, you could compile your own, other than that you have to wait for the next release of Ubuntu.

---

### Post by sebz2005 on 2006-07-15
> **SkyNet2029 said:**
> ```
$sudo apt-get dist-upgrade
```
I did that, but it said that it had all the updates.
I'm downloading the core now.
What do I type in the terminal to see what version the kernel is?

---

### Post by lordharsha on 2006-07-15
uname -a

---

### Post by sebz2005 on 2006-07-15
Don't know what happened there, but I still have 2.6.15 even though it said that there were no new packages.
Huh.
Thanks anyway.

---

### Post by adam.tropics on 2006-07-15
2.6.15-26 is the latest Dapper kernel. Above that you will have to follow a guide to compile your own, or, and I don't reccomend this yet, move to Edgy testing.

---

### Post by someusernoob on 2006-07-15
The latest Dapper kernel is good.

Other then when you have problems with this kernel, or want something that isnt supported in this one, but is in the latest, i do not recommend to compile the latest Linux kernel. 

I compiled the latest one once to see how it worked and such, didnt need extra features or something. It worked fine, some little problems with the boot progress image/text, it didnt show up, but once loaded it ran fine. Not faster or more stable (that wasnt possible, the Dapper one is rock stable by default), so didnt notice any difference.

I'd say, stick to the default one (it gets updated every time (every few weeks) automaticly). Unless you got lots and lots of spare time, and dont have anything else usefull to do with it :)

---

### Post by sebz2005 on 2006-07-15
Yeah, I want something more stable than testers.
I compiled and installed it and it said to add the Kernel switch in menu.lst (I think)
Tryed that and it came up with an error. Can you recomend a HOW-TO to try it?
I'm only using an old 10Gb Hdd to test it on.
Or should I move to the Edgy testing? How stable is it?

Edit:
The reason I want to update is because Linus has added support for my DVB-T card. And I need it soon.

---

### Post by adam.tropics on 2006-07-15
not at all stable yet..like i said, not really reccomended unless you have alot of time, are comfortable with terminal, and have a spare computer!

---

### Post by sebz2005 on 2006-07-15
Ah.
Is there anyway to pull out the driver for my DVB-T card and put it into my current kernel?

It's a Tevion DVB-T 220RF

---

### Post by linuxnewbie946 on 2006-07-17
There is a guide at [http://www.ubuntuforums.org/showthread.php?t=217657](http://www.ubuntuforums.org/showthread.php?t=217657) on how to compile 2.6.17

---

### Post by dicecca112 on 2006-07-17
> **someusernoob said:**
> The latest Dapper kernel is good.



the latest kernel is not good and has turned away a lot of Ubuntu users, myself included, because the 686 kernel does not work right on Intel Processers.  it kills mouses and keyboards.

---

