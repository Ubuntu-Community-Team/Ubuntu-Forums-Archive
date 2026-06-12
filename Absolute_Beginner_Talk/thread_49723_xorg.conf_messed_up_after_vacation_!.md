---
title: "xorg.conf messed up after vacation ?!"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by Swoop on 2005-07-17
Well i have a wierd problem.
When i left for my vacation everything on my laptop running ubuntu linux (fully updated ect) was working great.
I was lucky enough to make a backup stored on my other computer in worst case scenario but what really boggles me is the following. When i left everything worked, and i had no problems. Used the computer for 2 days before departure just for usage, and nothing got installed or anything.
Then when i return and boot up the laptop i get this blue terminal screen saying that it cannot start the x server, and its likely that it is not setup correctly. would i like to view the server output to diagnose the problem.
Now my keyboard doesnt really respont to normal keystrokes here, like enter does nothing, backspace apparently respongs a bit like enter + key right, so im really at a loss on what to do.
This already happenede twice were i just resorted to restoring a backup thinking i actually did something wrong. But now im really confused as to why my xorg.conf suddenly would be broken ... is there any way to have ubuntu restore the defaults automatically or something... i have a backup .tgz but how do i extract only the xorg.conf file from it ?

Anyways hope somebody can help a poor newbie understand why this is happening. I will gladly give any logs ect if you would tell me how to get a hold of them... thanks :D

---

### Post by tonysathre on 2005-08-10
[QUOTE=Swoop]Well i have a wierd problem.
When i left for my vacation everything on my laptop running ubuntu linux (fully updated ect) was working great.
I was lucky enough to make a backup stored on my other computer in worst case scenario but what really boggles me is the following. When i left everything worked, and i had no problems. Used the computer for 2 days before departure just for usage, and nothing got installed or anything.
Then when i return and boot up the laptop i get this blue terminal screen saying that it cannot start the x server, and its likely that it is not setup correctly. would i like to view the server output to diagnose the problem.
Now my keyboard doesnt really respont to normal keystrokes here, like enter does nothing, backspace apparently respongs a bit like enter + key right, so im really at a loss on what to do.
This already happenede twice were i just resorted to restoring a backup thinking i actually did something wrong. But now im really confused as to why my xorg.conf suddenly would be broken ... is there any way to have ubuntu restore the defaults automatically or something... i have a backup .tgz but how do i extract only the xorg.conf file from it ?

Anyways hope somebody can help a poor newbie understand why this is happening. I will gladly give any logs ect if you would tell me how to get a hold of them... thanks :D[/QUOTE]
 just put in the specific name into the command like this
tar zxvf tarball.tgz file1.txt

---

### Post by poofyhairguy on 2005-08-10
[QUOTE=Swoop]Well i have a wierd problem.
When i left for my vacation everything on my laptop running ubuntu linux (fully updated ect) was working great.
I was lucky enough to make a backup stored on my other computer in worst case scenario but what really boggles me is the following. When i left everything worked, and i had no problems. Used the computer for 2 days before departure just for usage, and nothing got installed or anything.
Then when i return and boot up the laptop i get this blue terminal screen saying that it cannot start the x server, and its likely that it is not setup correctly. would i like to view the server output to diagnose the problem.
Now my keyboard doesnt really respont to normal keystrokes here, like enter does nothing, backspace apparently respongs a bit like enter + key right, so im really at a loss on what to do.
This already happenede twice were i just resorted to restoring a backup thinking i actually did something wrong. But now im really confused as to why my xorg.conf suddenly would be broken ... is there any way to have ubuntu restore the defaults automatically or something... i have a backup .tgz but how do i extract only the xorg.conf file from it ?

Anyways hope somebody can help a poor newbie understand why this is happening. I will gladly give any logs ect if you would tell me how to get a hold of them... thanks :D[/QUOTE]

I had that happen. It was a hardware failure. My power supply was going out. 

Software can't change itself, but hardware can decay without your help. It might be a hardware problem.

---

