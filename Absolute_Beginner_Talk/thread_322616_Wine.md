---
title: "Wine"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2006-12-20
Hi, 
I've just installd wine, but I am a bit confused, how do I use it? do I need to run it from a terminal? (in this case which is the command, sudo wine?) or what do I need to do?
I am really new in linux so I appreciate any help given by all of you. Thanks

---

### Post by yabbadabbadont on 2006-12-20
Basically, you run your windows program using "wine programname.exe", but only after you have configured wine using the winecfg program.  Here are some wine documentation links that might be helpful:

[http://www.winehq.org/site/docs/wine-faq/index](http://www.winehq.org/site/docs/wine-faq/index)
[http://www.winehq.org/site/documentation](http://www.winehq.org/site/documentation)
[http://www.winehq.org/site/howto](http://www.winehq.org/site/howto)
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Good luck.

---

### Post by bodhi.zazen on 2006-12-20
[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by xabbott on 2006-12-20
> **Jorge32 said:**
> Hi, 
I've just installd wine, but I am a bit confused, how do I use it? do I need to run it from a terminal? (in this case which is the command, sudo wine?) or what do I need to do?
I am really new in linux so I appreciate any help given by all of you. Thanks

btw, i suggest not running wine as root.

---

### Post by Jorge32 on 2006-12-20
I've tried to configure wine but it appears this message:

wine: creating configuration directory  '/home/myuser/.wine'...
libGL warning: 3D driver claims to not support visual 0x4b

and it just stops.
What do I need to do?:confused:

---

### Post by scrooge_74 on 2006-12-20
type winecfg to open the config manager

after then you can install programs from a cd just go into the cd 

wine /cdrom/setup.exe or what ever is the name of the program call so it can be installed to your fake C: drive

---

### Post by Jorge32 on 2006-12-21
> **scrooge_74 said:**
> type winecfg to open the config manager


yes I already typed it, but it appears the message and I can't do anything else

---

### Post by scrooge_74 on 2006-12-21
I don't really know why is not working, try using the repositories in [http://www.winehq.org](http://www.winehq.org)

And go from there maybe that version should work better, they made an update a few days ago

---

### Post by Jorge32 on 2006-12-21
I've already downloaded the last repository version, as the instructions of [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) said. I installed it and when I tried to run the configurator it happens what I already said.

---

### Post by Jorge32 on 2006-12-21
by the way I've just installed the Xubuntu desktop because my computer was very slow, so do it has something to do with the problem?

---

### Post by scrooge_74 on 2006-12-21
You should post your hardware details specially your video driver, I really can't think of any reason why wine is not working for you.

---

### Post by Jorge32 on 2006-12-21
my video card is a Matrox Mga G200 AGP, monitor Samsung SyncMaster 551v, I don't remember the manufacturer of my motherboard, but I have 128 RAM, 8 G hard disk....

---

### Post by Jorge32 on 2006-12-21
hi, I've managed to solve the problem with the message. The fact was that I am using a MAtrox MGA200, and I just needed to update a driver, here is the complete information: [http://ubuntuforums.org/showthread.php?t=234078&page=2](http://ubuntuforums.org/showthread.php?t=234078&page=2), excuse me for all the questions about the topic. By finding this I also solved a problem with screen resolution (now I'm able to get the 1024x768 at 85 Hz!) so this is a very useful information for other people with MGA video cards.
:) 


now the problem is this new one :S 

jorge@ubuntu:~$ wine cfg
wine: could not load L"c://windows//system32//cfg.exe": Module not found

What do I need to do? anyway I'll keep on searching and searching info about it, thanks!

---

### Post by Edho on 2006-12-21
The command is 

winecfg

---

### Post by scrooge_74 on 2006-12-21
by saying wine cfg you told wine to try to launch a program called cfg :D

as Edho said is winecfg

---

