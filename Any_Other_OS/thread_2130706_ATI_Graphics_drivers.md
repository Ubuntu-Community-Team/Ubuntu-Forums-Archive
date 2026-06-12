---
title: "ATI Graphics drivers"
date: 2013-03-30
forum: Any Other OS
---

### Post by zesterer on 2013-03-30
Hi there,

Firstly, two things I want to point out. 1) I am actually using Linux Mint 14, but its is almost identical to Ubuntu deep-down. 2)I am not very good with hardware at all, so please keep things in laymans terms. Thanks :).

Ok, I recently got a new laptop computer (Dell inspiron i5 14R), installed linux mint 14, and it all works fine. However, I am worried because the fan seems to be on constantly even when the CPU is at around 0-4%. This made me think it was the GPU fan, but I'm still not sure. Then I did a bit of research with the help of some people on IRC freenode, and found out something about intel not making linux drivers or something like that. I did a little more digging, and found the bumblebee project, something that you can install to apparently fix the drivers.

Basically: All I want is a solution to the fan issue. Its a fairly fast laptop, and I am confident that it will still be fine if it is a bit slower, so shutting down part of the GPU may be an option, but I would prefer not.

When I do the command "lspci", I get this:
[http://pastebin.com/jdr73ctZ](http://pastebin.com/jdr73ctZ)

How is this helpful, what does it mean, and how can I use this information to fix this fan running so fast? I would prefer not to take risks - I already took a few, managed to kill gdm and the xorg server, as well as disabling Unity and compiz. I only just managed to get it back after 18 hours of research.

Any help would be GREATLY apprectiated!

Thanks,

Barry Smith (Zesterer)

P.S: When installing bumblebee, I got this:
[http://pastebin.com/Cb61G6hG](http://pastebin.com/Cb61G6hG)

---

### Post by zesterer on 2013-03-30
sorry for the bump, I know it probably breaks a few rules, but I REALLY need an answer to this questions fast - I have until tonight to fix the fan for a special event!

Thanks,

Barry Smith

---

### Post by ManamiVixen on 2013-03-30
Bumblebee is for Nvidia, not ATI as listed in your Thread header and ISPC. 
Have you tried installing the ATI driver in the software sources window?

---

### Post by zesterer on 2013-03-30
Thanks for the reply, I'll try that now :)

---

### Post by ManamiVixen on 2013-03-30
You will have to remove bumblebee first. Remove the packages it asked to install before continuing.

---

### Post by zesterer on 2013-03-30
ok thanks :)

---

### Post by zesterer on 2013-03-30
It didn't work :( - It just disabled compiz and/or unity and/or the Xserver. Is there any other solution to the problem? I REALLY need this solved - I just need the fan to turn off more!

Thanks for all your help, especially ManamiVixen :)

Barry Smith

---

### Post by ManamiVixen on 2013-04-01
QII can be of help, He knows a lot about ATI cards, I deal mostly with Nvidia. Give him a message. BTW, he is the guy with the Donkey Avatar. He is also a mod.

---

### Post by deadflowr on 2013-04-01
Install ppa-purge to clear the bumblebee packages.
Run
[CODE ppa-purge --help][/CODE]
To get an understanding of how to use it.

Look over this to see about getting the ati working.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

