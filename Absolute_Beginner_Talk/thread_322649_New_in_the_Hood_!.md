---
title: "New in the Hood !"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by osazze on 2006-12-20
Hello everyone, I'm osazze.  I've just installed the little "u" on my laptop and I don't know where to go from here.  I know absolutely nothing about Linux but am eager to learn.  I am also eager to retire microsoft.  I have a wireless lan adapter that I would like some assistance in getting setup/configured.  Can someone tell me if it can be used with the"u"?
It is an Air Link 802.11g usb wireless adapter.  I've discovered that there is a forum for wireless but I thought I might as well ask here as well for general suggestions concerning what I should do first about learning this new to me OS.   I look forward to becomning acquainted with many of you in the very near future.

Thanks,
O

---

### Post by dbbolton on 2006-12-20
you can use windows drivers with ndiswrapper

---

### Post by osazze on 2006-12-20
Hey DB!

As I said earlier, I've only just figured out how to get the "u" installed on my machine.  I know nothing about this ndiswrapper ??????  I don't know anything yet .... sorry

---

### Post by Pobega on 2006-12-20
Hello there, I'm new to Ubuntu too :)

A few tips:

A command you may find useful is *aptitude search <name>*, which searches through all of the packages for whatever you put as name. So for example, dbbolton suggested you use ndiswrapper, and I myself had no idea what that is so I plugged it into the terminal.

```
pobega@ackbar:~$ sudo aptitude search ndiswrapper
p   ndiswrapper-common              - Userspace utilities for ndiswrapper       
v   ndiswrapper-modules-1.22        -                                           
p   ndiswrapper-source              - Source for the ndiswrapper linux kernel mo
p   ndiswrapper-utils               - Userspace utilities for ndiswrapper       
p   ndiswrapper-utils-1.1           - Userspace utilities for ndiswrapper       
p   ndiswrapper-utils-1.8           - Userspace utilities for ndiswrapper
```

Although I still don't know what it does, I have a good idea of what it is. And to download it, substitute search for install. Although with this I have no clue which one I should download! Just trying to teach you a thing or two about basic Ubuntu use. Good luck with it, it's a really great operating system.

---

### Post by osazze on 2006-12-20
Thanks Pobe ... 
but all of this still looks like greek to me.  Is this like writing scripts in Unix or something? I've had some exposure to Unix, but that was O so long ago.

---

### Post by d3v1ant_0n3 on 2006-12-20
[ HERE ](http://ubuntuforums.org/showthread.php?t=9454&highlight=how+to+ndiswrapper) is a how to for ndiswrapper - it basically allows you to use Windows drivers for wireless adapters where there isn't a linux driver for that device. Hope that's useful.

You'll find (I know I did) that many of the questions you have about Ubuntu (and Linux in general) have been asked many, many times before- and as such, there is a WONDERFUL search function on these forums- look in the top right corner of the forums and there's a space for text entry and a 'go' button- that's the search feature. 

There's a MASSIVE wealth of knowledge on these forums- it's one of the best community based resources I've seen, so If you want to know something, you'd be suprised how easily you can find information with a quick search.

[ THIS ](http://ubuntuforums.org/showthread.php?t=232059) is probably a good read for newcomers too- contains lots of useful links and information.

And (as is often suggested) have a look at [ THIS](http://psychocats.net/ubuntu/index) link- again, lots of useful information in a very easy to take in, not *too* geeky format.

Now repeat after me.....

LINUX IS NOT WINDOWS
LINUX IS NOT WINDOWS
LINUX IS NOT WINDOWS

And have fun:D

---

### Post by dbbolton on 2006-12-20
just go to the terminal and type "sudo aptitude install ndiswrapper"

you can find drivers here: 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php](http://ndiswrapper.sourceforge.net/mediawiki/index.php)

---

### Post by osazze on 2006-12-20
Thank you so much, this is very encouraging.  It all seems so overwhelming !!! And yes, Linux is not windows and I'm so very pleased the alternative exists

O

---

