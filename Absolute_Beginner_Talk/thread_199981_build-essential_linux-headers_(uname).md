---
title: "build-essential linux-headers (uname) ?????"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by algoart on 2006-06-19
I found a source to help me install my Sagem WIFI USB device:  [http://wiki.ubuntu-fr.org/materiel/wifi/livebox?s=ndiswrapper]("http://wiki.ubuntu-fr.org/materiel/wifi/livebox?s=ndiswrapper")
The instructions require :
*sudo apt-get install build-essential linux-headers$ (uname -r)*
When I enter this command in Terminal, the message "cannot find build" (or similar) is returned.
I have searched the install CD for "build-essential" and "linux-headers" but found nothing installable. I am also confused (a permanent state :D since LinuX) by the expression "uname". Am I getting the syntax right?
As the Wifi adapter (via XP) is my only means of getting on the web, I would love to find the Linux solution.

Thanks in advance to all you helpful people out there.

---

### Post by uzi09 on 2006-06-19
i believe it should be:
```

sudo apt-get install linux-headers-`uname -r` build-essential program_name

```

sub in the program you're trying to install for 'program_name'

---

### Post by BoyOfDestiny on 2006-06-19
[QUOTE=uzi09]i believe it should be:
```

sudo apt-get install linux-headers-`uname -r` build-essential program_name

```

sub in the program you're trying to install for 'program_name'[/QUOTE]

I don't think he needs to anything like program_name. If what he wanted was in the repositories, he could just download it instead of trying to build it from source...

Anyway, good luck, if you are curious, type 
uname -r 
in a terminal

the value it returns is the current kernel version you are running... So basically it's easier than manually putting 2.6.15-25-blah =)

---

### Post by algoart on 2006-06-19
Thanks people, that has brought me one step closer. just need to figure out which headers..... choices, choices :-)

---

### Post by az on 2006-06-19
[QUOTE=algoart]I found a source to help me install my Sagem WIFI USB device:  [http://wiki.ubuntu-fr.org/materiel/wifi/livebox?s=ndiswrapper]("http://wiki.ubuntu-fr.org/materiel/wifi/livebox?s=ndiswrapper")
The instructions require :
*sudo apt-get install build-essential linux-headers$ (uname -r)*
When I enter this command in Terminal, the message "cannot find build" (or similar) is returned.
I have searched the install CD for "build-essential" and "linux-headers" but found nothing installable. I am also confused (a permanent state :D since LinuX) by the expression "uname". Am I getting the syntax right?
As the Wifi adapter (via XP) is my only means of getting on the web, I would love to find the Linux solution.

Thanks in advance to all you helpful people out there.[/QUOTE]
You surely don't have to recompile ndiswrapper.  Just install ndiswrapper-utils.

That guide if for breezy?  Are you using breezy or dapper?

If you installed from the Dapper Desktop cd, you need to boot into ubuntu and then insert the cd again.  You will be prompted to go to the package manager.  That's because there are some extra packages on the cd (that won't show up otherwise).  Once you are at the package manager, search for ndiswrapper-utils and install it.  It will get if from the cd.

---

### Post by algoart on 2006-06-19
Thanks azz,
I'm running dapper, but this is the only lead I've got!
So far I've managed to run the routine for ndiswrapper (your way would have been easier though) and am now trying to install the device drivers. Getting mangled by "permissions".
Linux command line..steep learning curve.

---

