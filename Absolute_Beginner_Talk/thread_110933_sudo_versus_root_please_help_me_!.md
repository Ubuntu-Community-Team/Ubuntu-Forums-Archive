---
title: "sudo versus root please help me !"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by sathya on 2006-01-01
whether we should login as sudo or as root in ubuntu ?

when i try root it says bad command.
When i try sudo it shows the syntax but doesn't log  me in.

From the terminal what is the procedure to login as sudo.

the problem is I am able to see the menu.lst file.
But it doesn't allow me to edit it if i login as sathya(user)
(I am unable to boot to XP. It is not listed on menu.lst.)
And it doesnt let me edit.

I have critical data on Xp and need to work. i am really tensed now been trying this stuff from two days. please help me.

---

### Post by kingsidy on 2006-01-01
at terminal, u can type in > sudo su then enter your *password* in order to access super user mode which will allow to edit. 
Or the other option is to type in > sudo gedit /boot/grub/menu.lst if i have the location right the menu.lst should pop up and become editable.

good luck

---

### Post by Madpilot on 2006-01-01
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

You don't log in as sudo, you just append it in front of command lines, basically. Whenever one of Ubuntu's graphical applications asks for your password, it's also using sudo mode.

Note that if you do create a root account and log in as root, some of the graphical utilities won't work - they're set up to use sudo, not root login.

---

### Post by sathya on 2006-01-01
Thanks for the suggestions, I will try that.
While I had these problems and I was trying to solve it I was thinking about migrating to linux thats why i forced myself to install linux on the system, now since Xp is unaccessible, I am trying things on linux and its great !
I long back worked on Unix platform to learn C++.
I had always been a fan of open source code.
I hope I can do everything with linux that I used to do with XP.

But my biggst fear is whether I will be able to comunnicate with my instruments using the ADC card and GPIB cards that I have(Make NI).
Right now I am using Labviewto do that o XP.

with the help of all you guys one day I may be able to do that !

---

