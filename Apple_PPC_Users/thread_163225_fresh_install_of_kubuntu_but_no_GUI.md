---
title: "fresh install of kubuntu but no GUI"
date: 2006-04-20
forum: Apple PPC Users
---

### Post by vincent orange on 2006-04-20
hello everyone,

I'm new to PPC linux so I need some help here. I installed Kubuntu badger onto a G3 500Mhz blueberry iMac (slotloading) with about 700mb ram. Everything was installed fine however, the KDE interface has not come up. Instead I only have command prompt. I tried sudo apt-get kde-desktop and it informs me the latest version is installed. I need to reconfigure the xserver (or PPC equivilent) but I don't know where to start on that and I need some guidence. I can provide you with more details if they are needed.

Thank you in advance,
Vincent

---

### Post by linear on 2006-04-20
You can try **sudo dpkg-reconfigure xserver-xorg**. Or you can try editing xorg.conf manually:

 After booting is complete,
 1. ctrl-option-F1 (should give you a command prompt)
 2. type: sudo nano /etc/X11/xorg.conf (return)
 3. make your edits (see below)
 4. ctrl-O (return) to write edited file
 5. ctrl-X to exit nano back to command line
 6. type: sudo /etc/init.d/kdm restart (return) to restart KDE

For an iMac G3, you'll usually need to modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.

---

### Post by 3rdalbum on 2006-04-21
Do you get a DOS-like dialog box appear, saying that the X server couldn't start?

What happens when you type "startx" at the command prompt?

---

### Post by vincent orange on 2006-04-24
Thanks guys for your help. I managed to get x server working using the step by step help you provided (really did come in handy). But it's working quite slow now, it takes about 15 seconds for the cursor to move across the screen and it's now become unuseable. I'm thinking now I need to use an older kernel perhaps? Would it be safe to use Warty PPC edition on my imac. It'll only be used to surf the internet and check email.

---

### Post by linear on 2006-04-24
In xorg.conf, try disabling dri. Put a hash mark (#) in front of the line that reads "load dri", or just delete the line entirely. Restart KDE and see if that helps any.

---

### Post by vincent orange on 2006-04-26
[QUOTE=linear]In xorg.conf, try disabling dri. Put a hash mark (#) in front of the line that reads "load dri", or just delete the line entirely. Restart KDE and see if that helps any.[/QUOTE]


WOW! I cannot explain why this works but the difference is HUGE, simply HUGE, its just just as fast as my other machines. Everything is working now. Thank you so much.

I think that "Load 'dri" thingy should be duly noted somewhere. Can someone explain why  this made the change?

Thank you all again, I really really did apprecaite the help,
Vincent

---

### Post by Ptero-4 on 2006-04-28
vincent. DRI means direct rendering interface, it's a way for X to render directly into the graphics processor (your videocard's built-in CPU) instead of the computer CPU. DRI works on most machines but in some machines it slows things down because the videocard have an underpowered graphics processor or no graphics processor at all, and the rendering goes into a bottleneck causing performance degradation everywhere.

---

