---
title: "Help to getting Wine to work with a program that only works with Windows 2000 or XP"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Bjarkehl on 2007-03-13
I am trying to get a Danish dictionary working (made for Windows 2000 and XP) work in Ubuntu and with Wine. When I am running the setup from my Dictionary-cd, the installation fails and states that it doesn't work with my version of Windows/Wine. Anybody got a clue how to do?

bw

When I try to run the 'dictionary'-exe file, not the setup.exe, it says

Runtime error '339':

Component 'Dguard2.ocx' or one of its dependencies not correctly registered: a file is missing or invalid.

Any ideas?

---

### Post by msaied on 2007-03-13
in th terminal inter:
winecfg

then select the windows version that you want (XP, 2000 etc) then apply and try launching the setup again

---

### Post by Bjarkehl on 2007-03-13
Hi Msaid,

Thanks for your help. I really appreciate it since I have been using hours on this, even though I now can see that it was pretty simple thing to correct...

Thanks, Bjarke

---

