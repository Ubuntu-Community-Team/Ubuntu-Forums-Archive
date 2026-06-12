---
title: "[SOLVED] only 1 workspace"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by kerrymorgan1 on 2007-08-18
i jut installed my drivers (big dramas) 
and now when i go system>pref>desktop effects and enable cube all the work spaces dissapeer and i have nothing to use the cube on.... i have had it going before but all of a sudden it doesn't go

please help MY SYSTEM IS
500GB SATA HD, AMD64 4000+, 2GB RAM With a Nvidia 8600gt

---

### Post by anothrguitarist on 2007-08-18
Right click the workspace, click preferences, and change the number of workspaces.

Did that work?

---

### Post by Spr0k3t on 2007-08-18
Try this

disable the desktop effects.  Rightclick on the Workspace switcher applet and configure the number of desktops to 1.  Go back and enable the desktop effects... see if that works.

---

### Post by kerrymorgan1 on 2007-08-18
i just tried that ...... i can switch between them but no cube it worked about before i reinstalled ubuntu 7.04

---

### Post by Immolatus on 2007-08-18
maybe try restarting x

ctrl+atl+backspace

---

### Post by kerrymorgan1 on 2007-08-18
when it starts back up there is only 1 work space and if i push alt ctrl right/left the task bar disapeers ..... very strange i thought i was just getting the handel of this

---

### Post by Arthur Archnix on 2007-08-18
In my humble opinion, if you want desktop effects like cube you should probably ignore the "enable desktop effects" option. It's rather limited. If you install compiz-fusion you'll have much more options, and it may work better seeing as how it's the latest version. Go to the forum on desktop effects and read the sticky about it.

---

### Post by kerrymorgan1 on 2007-08-18
thats my goal........ but a huge step i have only installed the drivers and made myself a little pathway there are soo many issues with Compiz i wouldn't be able to handle it just yet
i just wanna make sure that everything i add and install to this PC is 100% installed and flawless
...... if i had a fail proof path-way to follow i would but i know i'll get sick of reinstalling Ubuntu after a while

---

### Post by Arthur Archnix on 2007-08-18
Reinstalling? That's an old windows habit you have there. When thiings go wrong, and you decide to remove them they're gone. To linux its as if they never existed. So you can mess things up, and then remove them and get the right things going and its no different than if you reinstalled and did it right the first time.

---

### Post by kerrymorgan1 on 2007-08-18
[http://ubuntuforums.org/showthread.php?t=359367](http://ubuntuforums.org/showthread.php?t=359367)
thanks for your help guys this one fixed my desk top up completley

now the next stage..... can sombody point me to a good XGL+Compiz thread or sticky?

---

### Post by kerrymorgan1 on 2007-08-18
> **Arthur Archnix said:**
> Reinstalling? That's an old windows habit you have there. When thiings go wrong, and you decide to remove them they're gone. To linux its as if they never existed. So you can mess things up, and then remove them and get the right things going and its no different than if you reinstalled and did it right the first time.

you're the man mate....... thats why i love linux, nothings impossible.... 
i did something last night to my computer and everyone i asked pretty much said i've never heard of that to reinstall would be easier.

---

### Post by Arthur Archnix on 2007-08-18
It's a sticky in the same forum you found your fix. 

Oh and don't forget to mark the thread as solved.

Happy ubuntuing!

---

### Post by Ek0nomik on 2007-08-18
> **kerrymorgan1 said:**
> [http://ubuntuforums.org/showthread.php?t=359367](http://ubuntuforums.org/showthread.php?t=359367)
thanks for your help guys this one fixed my desk top up completley

now the next stage..... can sombody point me to a good XGL+Compiz thread or sticky?

I don't see anything about workspaces in this thread.

---

### Post by Arthur Archnix on 2007-08-18
I presume that he meant this worked:
```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```

It's all about workspaces, but the only way I knew how to do this was through the compiz manager, which is installed with compiz. There doesn't seem to be any need for that now though.

---

### Post by kerrymorgan1 on 2007-08-18
> **Ek0nomik said:**
> I don't see anything about workspaces in this thread.

sorry man it turned into this...... i did something wrong and i only had 1 work space didn't know it was as easy as right click

---

