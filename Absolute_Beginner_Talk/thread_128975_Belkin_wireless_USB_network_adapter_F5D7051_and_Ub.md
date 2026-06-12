---
title: "Belkin wireless USB network adapter F5D7051 and Ubuntu"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by unidentifiedbones on 2006-02-12
Ok.......first time here, so please forgive me if  I'm repeating a question that has already been answered.
I've tried installing several linux distros on an old K6 powered machine that i have lying around here gathering dust, more to see if I like it or not, really.
After several goes, I've settled on Ubuntu as the one I like.
But......
In common with all the other distros, this just doesn't seem to recognise my usb adapter, so I can't connect to the internet with the damn thing.
I'm very new to this linux malarky, and although I've used various windows incarnations for years, I wouldn't call myself a technically competent computer user.
That being said, the interest is there, so if I can find someone who can offer me one or two pointers as to how to get this up and running, I'll be happy to invest time in learning how this all works.
I've read through a few forums on this subject in the last month or so, and it seems the average newbie is faced with an enormous amount of jargon that renders the whole experience of switching operating systems difficult in the extreme.
Part of the trouble seems to be the huge numbers of variations on the theme of linux......I can see the reason for this, but it makes it a bit baffling, to say the least.
Anyway, if someone can help me out in, plain english with an idiot's guide as to whether I can get this to work, and how to do it, I'd be eternally grateful. 
If not, thanks for reading this anyway

---

### Post by gosh on 2006-02-12
Go to wiki.ubuntu.com and search for wifi and/or for ndiswrapper.

---

### Post by AndyCooll on 2006-02-12
Actually there is a good chance that you won't need ndiswrapper. I have a Belkin USB network adaptor (F5D7050) and that uses Ralink RT2570usb drivers. So, your usb might well be able to use a similar driver.

Here are a couple of threads to set you off in the right direction:
[HOWTO: Ralink RT2570 usb wireless driver]("http://www.ubuntuforums.org/showthread.php?t=106846")
[Rt2x00Wiki]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page")

:cool:

---

### Post by unidentifiedbones on 2006-02-12
Thanks very much, people......a little late here now, but I'll have a go tomorrow.
I really appreciate it.

---

### Post by tattrat on 2006-03-16
[QUOTE=AndyCooll]Actually there is a good chance that you won't need ndiswrapper. I have a Belkin USB network adaptor (F5D7050) and that uses Ralink RT2570usb drivers. So, your usb might well be able to use a similar driver.

[/QUOTE]

HI, I am trying to get the same card going on ubuntu 5.10. However it does not have the same chipset as the f5d7050 - It has a broadcom one : broadcom bcm4320 802.11g usb 2.0 transciever. Web rumour has it that the chipset is the same as the Linksys WUSB54GS v2. The latter is listed as a card which will work with Ndiswrapper but not the former. I am willing to try to get the thing working - but I suspect it may need the latest version of ndiswrapper - and it seems a complex process to upgrade - particularly if you have no connectivity which I don't! 

If anyone is willing to help with the process, I am up for it!

---

### Post by hippy4life on 2007-01-23
Did anyone get any luck with this i have the same card (050d:7051) and would love to get this working.

---

### Post by Bachstelze on 2007-01-23
To know for sure whether your USB wireless adapter is supported, you can see the output of *lsusb*. It should give you a list of all USB devices, each with an identifier of the form [xxxx:xxxx]. The identifier will be the same for each wireless chipset, regardless of the adapter itself. So two different adapters but with the same chipset will give the same id.

Then you can search the id in the [list of devices known to work with ndiswrapper](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) and get the correct driver for it.

---

### Post by hippy4life on 2007-01-23
> **HymnToLife said:**
> To know for sure whether your USB wireless adapter is supported, you can see the output of *lsusb*. It should give you a list of all USB devices, each with an identifier of the form [xxxx:xxxx]. The identifier will be the same for each wireless chipset, regardless of the adapter itself. So two different adapters but with the same chipset will give the same id.

Then you can search the id in the [list of devices known to work with ndiswrapper](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) and get the correct driver for it.


thought i already gave this id?

> **hippy4life said:**
> Did anyone get any luck with this i have the same card (050d:7051) and would love to get this working.

and yes it is listed as supported apparently

---

### Post by Bachstelze on 2007-01-23
You know, you're not the one who started this thred, so replies in it might not be directed at you... Anyway, did you try the driver mentioned on the Wiki page ?

---

### Post by hippy4life on 2007-01-23
the wiki was the first place i started.

The card is installed and Ndiswrapper recognises it but its not being identified by the network manager

so close yet so far

---

### Post by cypher2k on 2007-09-02
This might help you folks :)

[http://ubuntuforums.org/showthread.php?t=540942](http://ubuntuforums.org/showthread.php?t=540942)

---

