---
title: "[SOLVED] lan Win'98 to Ubuntu live windows settings?"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Desperate on 2008-01-15
My XP pro crashed and I'm running Ubuntu live there(no hard disk), the data I need I downloaded on an old '98 laptop with only one Ethernet card :) That's where I lost the settings that were working so nice yesterday. But to get that thing on the Internet I needed to change a lot and forgot [ ;( ] to write down the settings. I can install Samba and see Unbutu on the win box but need a password to open it (?)
The other way around would be easier, shared the whole laptop full, deleted all firewalls and anti virus programs on it, but no matter what I do in Win or Ubuntu, Ubuntu will browse for connections [Places--Network] and show windows network which is complete empty :(
If I go to [Places - Connect to server ] I can't open it or get the message, can't show all files which leaves me with nothing too.
I need to get an iso file top the desktop so I can burn the ultimate boot CD and maybe repair my hard disk without loosing data.
Any hints welcome as I'm, after six hours of reboot the winbox, just what the name says ^

Thanks
Richard

---

### Post by twin_57103 on 2008-01-15
Do you have a flash drive big enough for the files (assuming the laptop has USB)?  That might be easier, and should be supported on Ubuntu (if support on the Win 98 machine is a problem, just boot from an Ubuntu disk, then use the flash drive).  Sorry I can't help with the network solution...:(

---

### Post by maybeway36 on 2008-01-15
Try changing the resolve order in /etc/samba/smb.conf to
```
name resolve order = bcast host lmhosts wins
```

---

### Post by Desperate on 2008-01-15
Thanks, but the laptop has no USB :( and will not run Ubuntu, it's a really old thing it barely makes '98 :). The file I have to transport is about 115 Mb so I can burn it to a cd.
The stupid thing is that I had it running without a problem, just plugged it in and was connected, then redid the settings to fit my complicated network to get to the internet and that screwed everything up :(. Tough when you know it's possible, but you can't find out how to fix it. 
@ maybeway36, now you expect that I know anything about Ubuntu :) Learning, but slowly, it's definitely a hands on OS, but also very economic. It runs everything and only uses 20% of the memory available here, I'm amazed.

Thanks for the help, I'm now writing out all the possible combinations for the setup and we'll have a go at it tomorrow again.
"Do you want to reboot" :) I can shoot Billy G on the spot now ::lolflag:

Thanks 
Richard

---

### Post by steevols on 2008-01-15
Wait... are the lost settings on the '98 laptop or the Ubuntu live CD?

---

### Post by Desperate on 2008-01-15
"lost" settings are on the antique laptop :)  But writing that my memory is still above normal made me think I could down load it to this machine in memory and burn from there :) Downloading as I type, I think this one is solved now, if I mark the tread :)

Thanks you all, you give me the urge to go on when I think it's all lost :)

Richard

Edit:

%$@%$@$^# write failure, stupid thing will not boot :(   Don't you love computers :)

C Ya

---

