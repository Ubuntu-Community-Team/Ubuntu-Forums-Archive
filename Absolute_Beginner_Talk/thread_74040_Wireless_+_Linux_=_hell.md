---
title: "Wireless + Linux = hell"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by CammanB on 2005-10-10
Yes, I know already going into this that Linux and wireless networking cards don't like each other very much, but I would like to try and solve my problem before having to buy another card...

I have a D-Link DWL-G510 Wireless Network Adapter.  The part is not detected in the Ubuntu Network settings and i believe there is no driver installed.  However, when I run lspci, the chip shows up as "Atheros Communications" (if you need the exact line, I can replace the card later and pull it up again).  Hence, Madwifi should detect and work for the card... but it doesn't, to say the least.  I attempted to use ndiswrapper as well, but it said something about a syntax error at 'newline'... not exactly sure what it was but I can update it later... I have a Linux guru friend that is willing to help, but he's in a time crunch right now homework wise and probably will be for a while (I've been trying to get him over here for 3 weeks)  I would like to just find a way to solve this problem myself if at all possible.. is there something obvious I'm overlooking?  I'm more than willing to copy paste, and I am connecting on our family's downstairs computer right now.. I will check back in here as often as possible... any help is greatly appreciated... 

Thanks, 
CB

---

### Post by Zelut on 2005-10-10
Hey I understand how frustrating Linux can be for wireless.  I've now gone thru the motions on 3 computers so trust me I've been there.  The good news is it gets easier with practice :)  The bad news is it still can be a pain in the butt.

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)
That link is a listing of supported/tested wireless cards.  I don't see your exact model but the other similar models seem to work so I doubt we're far off.

[https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper)
this is also instructions on the setup of ndiswrapper.  maybe just double check that you've done all the steps needed... 

Let me know if you've got more questions.

---

### Post by loupy on 2005-10-10
I had the same issue with my D-link DWL-G650 card - I reinstalled the linux restricted module for the kernel and rebooted and it detected my card.  Maybe you can give that a try.

---

### Post by matthew on 2005-10-10
If what the other two posters advised doesn't work, take a look at these links.

[http://www.ubuntuforums.org/showthread.php?t=70672](http://www.ubuntuforums.org/showthread.php?t=70672)
[http://www.ubuntuforums.org/showthread.php?t=73334](http://www.ubuntuforums.org/showthread.php?t=73334)
[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

---

### Post by CammanB on 2005-10-11
Okay... I hope/think I may be near a possible solution.... according to the list of linux-restricted-modules (madwifi) supported/tested cards, on the G520, the Rev.B doesnt work because the madwifi is too old, and it provides a link to a new build of it.  I downloaded the build and burned it to a CD... and sorry, I am new at this... what do I do with the thing... it's a .deb file, and when i double click it it opens the file extractor... I am hoping that if I can figure out how to get this thing installed it will work for my Rev. B version of the card as well since it is based on the same chipset..

---

### Post by Mustard on 2005-10-11
Use the dpkg command.

type this command to find the manual in terminal

```
man dpkg
```

Basically the command will be formatted like this...

```
dpkg -i | --install package_file...
```

For example;
dpkg -i  somewififixingmagic.deb

---

### Post by CammanB on 2005-10-11
alrght... i read through as much as possible... but the error message i get is 

dpkg: --install needs at least one package archive file argument

i thought the --install command unpacked the files and installed them... but am I missing a step?

---

### Post by CammanB on 2005-10-12
nevermind, I got it running with ndiswrapper... :-)

---

