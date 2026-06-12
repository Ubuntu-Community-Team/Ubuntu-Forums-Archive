---
title: "Picking up on Dual Boot - Vista, Ubuntu 6.10 :wink:"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by mitch_scaff on 2007-09-09
I took the day off from work, did a bit of research, and over the next hour or so, will be starting again - to try to fix Vista on my laptop now that I've installed Ubuntu (6.10).  

I found some very useful information about how the Microsoft boot process is supposed to work, for pre and post Vista operating systems.  The core of it is at 
      [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Thanks to this and other reading, I now have a plan - as follows:

Goal: A dual boot machine, running Vista normally, and Ubuntu normally.  
Since I already have Ubuntu 6.10 and have it installed, I would prefer to use that for now, and replace it at some later date with 7.04 (fiesty faun).  If 6.10 cannot play nice with Vista I don't object to using fiesty faun sooner, but from what I know at this point, that shouldn't be required. 

There are 5 OS options I'm presented with at bootup presently.  Two claim to be "normal" ubuntu.  One claims to be a recovery mode ubuntu.  Two others are supposedly normal Vista, and no Vista backup or recovery option. 

I would be pleased to have one each Vista and Ubuntu, with maybe one recovery option for each of those. 

To get to "one Vista, one Ubuntu" I imagine there needs to be a set of startup files 
(scripts, programs) that proceed and are linked as follows:

For Ubuntu boot:  

[INDENT]
 BIOS (launches) ==> 
    OSL2000 - 3rd party replacement IPL (initial program loader) 
      [INDENT]this would check some config file to find out what boot menu options 
      to present, then check with the user
      User chooses Ubuntu, and then OSL2000 (launches) ==>[/INDENT]
    Ubuntu startup chain
[/INDENT]    
 
For Vista boot

 [INDENT]   BIOS (launches) ==> 
    OSL2000 - 3rd party replacement IPL (initial program loader) 
      [INDENT]this would check some config file to find out what boot menu options 
      to present, then check with the user
      User chooses Vista, then OSL2000 (launches / calls on) ==> [/INDENT]
    Vista's PBR (launches) ==>
    (windows') bootmgr
      [INDENT]this checks BCD file to learn locationof system32 folder
      then (launches) ==>[/INDENT]
    winload.exe
[/INDENT]
+	+	+	+	+

Unfortunately, what I think I have now is 

[INDENT]BIOS calls ->
IPL (intial program loader) calls ->
GRUB 
  [INDENT]which checks with user and launches Ubuntu fine if that's chosen[/INDENT][/INDENT]

but if the user chooses Vista, Grub fails to call either 

  [INDENT](vista) PBR or
  (vista) bootmgr[/INDENT]

Theoretically, I could get Grub to call vista PBR or vista bootmgr.

I feel vaguely it would be "cleaner", and perhaps easier, to install a 3rd party IPL replacement program like OSL2000, then configure it appropriately (adding the options to boot in recovery mode as I learn how).  

So, to start, I want to find out if what I think is happening is in fact correct.

In particular, I want to see if I can find the files in the Vista startup chain and check to see if they are intact.  

[INDENT]I want to learn about GRUB's startup process/chain.  
I want to see if/how GRUB uses menu.lst.  
I want to see if my entries into menu.lst for Vista point to "the correct" 
 file in the Vista startup chain.
This is another way of saying: 
  [INDENT]I want to find out if the Vista start up chain is broken within the menu.lst file
  (i.e. between GRUB and pre-installed Vista), within the Vista startup chain, 
  or both. [/INDENT]
[/INDENT]

Because Vista will sometimes give me the crawling green worm, I find myself suspecting that there is a failure (perhaps not the only one) within the Vista startup chain. Could it be that reallocating some of the physical disk space and creating a new partition using Ubuntu's tools caused the Vista fault tolerance/ disk signature manager to rearrange (inappropriately) its tables?  That would be typical of Microsoft's dirty tricks.  

I think I can investigate the state of my system to answer these questions with what I already know. 

That would leave me to look on the web for:
 [LIST]
[*]a downloadable and current OSL2000 (or preferred substitute)
[*]  information about the utility/desirability of OSL2000
[*]  an overview of OSL 2000 installation and configuration
[*]  detailled instructions for intalling and configuring OSL2000
[/LIST]

There is a question about what "repairs" to the Vista startup chain are needed.  
I might know more once I have looked the current files over. 

Alternatively, information about how GRUB actually works, and how to use it to 
repair its end of the connection to the Vista chain (and then fix the Vista side of 
the Vista startup chain) would be potentially helpful.

---

### Post by logos34 on 2007-09-10
here are some links that might interest you:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx](http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx)

---

