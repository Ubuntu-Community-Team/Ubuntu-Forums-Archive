---
title: "[SOLVED] Help with Pidgin"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-02-21
I turned on my Pidgin and installed yahoo with it and it worked fine. After I rebooted now when I click on Pidgin it starts the application but never opens??? How can I get it working again???

---

### Post by pedro_orange on 2008-02-21
By 'open', do you mean open your buddy list?

When you start Pidgin, it should run and log you in. Then if you look in the top right corner, you should see an icon like a green circle with a speeh bubble over it? Left click that

---

### Post by N1N31NCHN41L5 on 2008-02-21
When i click on Pidgin it says starting Pidgin Internet Messenger, and runs the circle but then completely disapears and never opens

---

### Post by Sockerdrickan on 2008-02-21
open a terminal and type pidgin and press enter, what does it say?

---

### Post by NightwishFan on 2008-02-21
Run it from the terminal and see if any errors come up.

just type:
> pidgin

---

### Post by pedro_orange on 2008-02-21
I would check if Pidgin is running by using the "ps -C pidgin" terminal command.

If it is, I would kill it. (using "kill -9 pidgin")

And then reinvoke Pidgin from the command line and see if I get any error messages.

Edit: >.< Too slow

---

### Post by N1N31NCHN41L5 on 2008-02-21
I typed pidgin in the terminal and it did nothing

---

### Post by N1N31NCHN41L5 on 2008-02-21
on the ps -C pidgin this is what it said

josh@josh-Entertainment:~$ ps -C pidgin
  PID TTY          TIME CMD
 5826 ?        00:00:00 pidgin
josh@josh-Entertainment:~$

---

### Post by N1N31NCHN41L5 on 2008-02-21
also is it possible to install Ubuntu on a computer with:
Mobile Inte(R) Pentium(R)
III CPU -M 12000MHz
1.2Ghz, 256MB of RAM

---

### Post by NightwishFan on 2008-02-21
That would be more within the realm of Xubuntu.

---

### Post by N1N31NCHN41L5 on 2008-02-21
XUbuntu - what is it and is that what i need for my other computer??? 

and does anyone have any idea why I have NOOOOO Pidgin

---

### Post by NightwishFan on 2008-02-21
I do not have a solution for your problem I am afraid.

Xubuntu is basicly Ubuntu that uses the lighter weight XFCE desktop. I do not recommend using Ubuntu on under 512mb of ram or so, although 384mb should be sufficient. Xubuntu means no compiz effects (without some workarounds) but they would not run well on 256mb ram regardless. I like Xubuntu, the interface is sleek and fast.

---

### Post by N1N31NCHN41L5 on 2008-02-21
i know NOTHING about Linux but have already customized this PC so radically I have fallen in love with Ubuntu and want it on both of my systems. Once all the right things are installed you can basically do anything you can on windows except faster - more secure - and quicker

---

### Post by dasunst3r on 2008-02-21
I have a few possible solutions:
1. Do you have a system notification area added to your panel or whatever?  If not, add one.  I do not know the procedures for doing so for XFCE, however.
2. Preferences for Pidgin may be mucked up.  In that case, open the terminal and issue the command *rm -rf .purple*  This will remove all user preferences for Pidgin and you will have to reconfigure Pidgin to your liking again.

---

### Post by northern lights on 2008-02-21
For the PIII machine I'd check out [Xubuntu]("http://www.xubuntu.org/") or [Fluxbuntu]("http://fluxbuntu.org/js.html").

Both are part of the Ubuntu distribution base. The difference lies foremost in the desktop environment & window management.

Xubuntu uses [Xfce]("http://http://www.xfce.org/") - which is modifiable and **can** be pumped with eye-candy (**not** what you wanna do) also, but ships rather simplistic.

Fluxbuntu is even more geared towards efficiency and comes with specifically lightweight apps. It uses [Fluxbox]("http://fluxbox.sourceforge.net/") as its wm.

OffTopic hint:
You can edit your posts...
...Not only 2, but 3 posts of yours are consecutive - quite unneccessary...

---

### Post by seventhc on 2008-02-21
If you go to *System>Administration>System Monitor* do you see pidgin running in the *processes* tab?
If so, end it and then try to start pidgin again, do it from the terminal and see what, if any errors it gives.
Other than that, you might want to try logging out and then log back in.
Then try starting pidgin again.

---

### Post by N1N31NCHN41L5 on 2008-02-21
Pidgin was sleeping THANK YOU, and am downloading XUbuntu for the Dinosaur computer. It runs Windows XP pretty well, but I want a little more efficiency out of it.

---

### Post by Sceiron on 2008-02-21
> **N1N31NCHN41L5 said:**
>  for the Dinosaur computer.

:lolflag:

---

### Post by seventhc on 2008-02-21
> Pidgin was sleeping THANK YOU,You need to get the *pidgin alarm clock* :tongue:

---

### Post by N1N31NCHN41L5 on 2008-02-21
Thanks to all for the help I now have Pidgin running my yahoo and am downloadin XUbuntu for the PIII, i tried to install 7.10 on it since Ubuntu site says it would be supported but it wasn't able to install. Now I can have Ubuntu on BOTH my computer, VERY HAPPY

---

### Post by northern lights on 2008-02-21
Awesome you're happy and got everything working so far!

Just a tiny clarification: It's a misconception that your Xubuntu will not be 7.10
--> Whether you download the latest Ubuntu, Kubuntu, Xubuntu - they'll all be "Gutsy Gibbon" (7.10). They simply ship with different desktops (Gnome, KDE, Xfce), and a few different packages and apps. On your PIII you thus won't be running an "older version", but simply one that's less hardware demanding.

---

### Post by N1N31NCHN41L5 on 2008-02-21
Yeah I downloaded the Gutsy Gibbon Ubuntu 7.10 for i386, i'll get to install it after i get up in 4 hours. God bless Army PT to wake you up when your tired, lol.

---

