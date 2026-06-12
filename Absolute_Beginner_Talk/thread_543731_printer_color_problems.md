---
title: "printer color problems"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by lah127 on 2007-09-05
I can't seem to get my printer to just print in black. I have a new black ink cartridge, installed it, and the printer test page from the printer does fine. Ubuntu's printer test page keeps going red. Why?!  What do other colors have to do with printing plain black? How can I fix this? Thanks.

---

### Post by linuxwizard on 2007-09-05
Need more info. What make, model, of printer ? How do you have it connected and are you using recommended driver for it ?

---

### Post by lah127 on 2007-09-05
Sorry, it is a HP PSC 1315v. I should already have the driver installed.

---

### Post by lah127 on 2007-09-05
One more thing, connected by USB cable to the back of my HP Pavilion desktop. The driver is indeed installed.

---

### Post by linuxwizard on 2007-09-05
in terminal 

dpkg -l hplip

post results

---

### Post by lah127 on 2007-09-05
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hplip          1.7.3-0ubuntu1 HP Linux Printing and Imaging System (HPLIP)

Walk with me, what did I do wrong or need to do?

---

### Post by linuxwizard on 2007-09-05
I just wanted to check what versinon HPLIP you were using that printer requires Min. 0.9.5. version HPLIP. Go into your printers settings and look for gray scaling could be under preferences choose that and try to print. I think i missed read your first post on what you want. You want to print black/white no color.

---

### Post by lah127 on 2007-09-05
Right, I've tried that and nothing has changed. Printer test page is fine, ubuntu test page has a LOT of red. I will try a new color cartridge and see what happens. I'd rather have my words in blue or green than red. I really do appreciate this.

---

### Post by Sef on 2007-09-05
How did you install the driver?

---

### Post by rajan on 2007-09-05
i have the same printer, but i think an older model. i never had to install any drivers, CUPS apparently had it covered. 

i had a problem a while ago. the printer would print in either B/W or color. i found out that i could change the settings by going to system (upper toolbar) --> administration --> printers. 

right click on whichever printer you're looking to change to B/W, then go to properties, then to the advanced tab. this should give you an option to change to B/W only. 

just fyi:

```


rajan@paravati:~$ dpkg -l hplip
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hplip          0.9.7-4ubuntu1 HP Linux Printing and Imaging System (HPLIP)
rajan@paravati:~$


```

---

### Post by lah127 on 2007-09-05
I honestly don't remember how I installed the driver. 
And the B/W option and even getting it selected to grayscale isn't helping. It is a new cartridge and I've run through the HP options. It always is fine by itself but never through this system.

---

### Post by rajan on 2007-09-06
you didn't install a driver. HP printers are very good in their support for linux's integrated driver system (Common Unix Printer System -- CUPS). Their drivers are already there (i think mine were there in their entirety) from when you installed ubuntu. 

that being said, trying to mess with the CUPS is probably one of the more difficult things that you can do. i've found this to be true because there's so much literature about CUPS that I could never find the solution to my problem; it's the needle in the CUPS haystack. 

so maybe you should make sure you've tried all the obvious things. I know that after replacing my ink cartridges i needed to reboot and restart the printer/CUPS. there's some info about this in a previous thread of mine:

[http://ubuntuforums.org/showthread.php?t=339621](http://ubuntuforums.org/showthread.php?t=339621)

what happens when you take out one or both of the ink cartridges, or you switch the positions of them? i'm not sure if anything bad could happen by doing this, but if you're feeling risky, i would give it a shot. 

finally, there is the possibility that you can print with a command-line command. 

```

lpr

```

is one command that you could try to google some information about. i think the basic syntax is something like 

```

lpr -options filename

```

but this page will definitely be more descriptive:

[http://www.ss64.com/bash/lpr.html](http://www.ss64.com/bash/lpr.html)

good luck.

---

### Post by lah127 on 2007-09-06
The problem is resolved but I am still so confused. I just installed the *color* ink cartridge for my printer, so now the printer is printing in black. Anyway, Thanks guys! =)

---

