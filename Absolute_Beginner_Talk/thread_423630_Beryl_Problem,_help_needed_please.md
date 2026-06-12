---
title: "Beryl Problem, help needed please"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by MagicBytes on 2007-04-26
Hello reader, I am new to Ubuntu V7.04 and Linux, I managed to install Ubuntu and beryl OK, but after using the 3D desktop feature for 6 hours the 3D desktop decided to stop working and I have no idea why, I tried looking to enable again and could not find, does any one know how I can enable 3D desktop feature so I don't have to reformat and reinstall Ubuntu and beryl all over again please ?

Cheers MagicBytes  :popcorn:

---

### Post by igknighted on 2007-04-26
Please include more information:
1) what hardware are you using?  Video card? Video driver?
2) what version (i386, amd64, etc.)
3) what did you do in the 6 hours it worked, and also did you reboot or anything that was a proximate cause to it's failure?

Not meaning to be snippy, but we need information like this in order to steer you in the proper direction.

---

### Post by MagicBytes on 2007-04-26
Ubuntu V7.04 i386 32 bit

ATI Radeon x1600 graphics adapter 256 Mb video ram

1GB physical memory

AMD Athon 3200+ cpu 939 socket

Gigabyte GA-K8N-SLI mother board

I believe from the instructions that I followed on a web site I found to install Beryl 3D Desktop, I think it installed the drivers for my Video card as the 3D Desktop worked great for 6 hours

In the six hours that I was exploring Ubuntu, I was looking at the Beryl Settings manager, and the Beryl Theme manager, I did try choosing different emerald-themes but nothing seemed to change, plus I selected some features on the left hand column to see what they would do, but don't ask me which ones, as that Beryl Settings Manager is like a rat maze in there, so complicated, I also been trying out lots of other software from the applications menu, I been exploring in all avenues but I cant remember everything I done.

I would like a solution to put the Beryl Settings Manager back to default settings if that is possible as this would fix it like when I finished installing and  setting up because it worked well then.

Hope I supplied you with enough info, if not let me know and I will provide any additional material.

Thank You [-o<  for reading and responding to my posting plus offering to help me, much appreciated

Cheers MagicBytes :-D

---

### Post by Ecthelion on 2007-04-26
What error message do you get when you try to start beryl?

---

### Post by pjrettin on 2007-04-26
Might wanna try left-clicking on the Beryl Manager icon in the system tray and making sure you haven't switched  window managers and that you are still using emerald.

---

### Post by MagicBytes on 2007-04-26
Hello to all who reply to my problem, well I did tried to see if I could recover, I explored all through the Beryl Manager and the Beryl settings manager, but as you know, there are so many features in there that one would need a great understanding of the workings and an awful lot of spare time on there hands to go through all this, but it would be nice if the developers had put a restore default settings button for people like me who try different things and mess things up, so if there is such a  reset default button I would appreciate to know where or how I can accomplish this task, as for any  error messages, I don't get none.

When I tried choosing different emerald themes I DID NOT see any changes.

When I tried choosing different features in the Beryl Settings Manager, I DID NOT see any changes either, all I can tell you is I was exploring all the features that Beryl Theme manager and the Beryl Settings manager has to offer, but DID NOT seem to do anything, maybe I am missing an additional package or something.

The only thing I can tell you is when I first got it all installed and all set up, I had a 3D Desktop and the spinning cube and I was able to change to different sides and I could put different applications on different sides, that part all worked great, I could zoom in an out, but as for choosing different features in the Beryl Settings manager and the Beryl Theme Manager  I DID NOT see any changes.

The mouse and the keyboard short cuts all worked fine when I needed to zoom and spin the 3D desktop.

I have tried many different Linux packages and Ubuntu is by far the best and the easiest installation I have ever uncounted, the Ubuntu Team really did a good job on this distribution, I really enjoyed downloading, checking with MD5 checker and burning the ISO image to cdrom, every thing there went great. I even checked the cdrom during installation at the main menu and my cdrom passed with flying colours, so I believe my disk is good with no errors.

So I don't know what else I can tell you that would help solve this problem.

Thanks again for every ones help and time to reply to my posting, I really appreciate your replies and ideas.

Cheers from MagicBytes  :) 

:popcorn:

---

### Post by Ecthelion on 2007-04-27
Just a trick, try this in commandline:
```
emerald --replace
```

Do this when beryl-manager is running.
Maybe this will still actiavte it.

---

