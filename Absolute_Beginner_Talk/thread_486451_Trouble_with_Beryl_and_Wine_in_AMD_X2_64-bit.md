---
title: "Trouble with Beryl and Wine in AMD X2 64-bit"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by vishwas_s on 2007-06-28
I installed the 64-bit Feisty Fawn version about a week ago. Now, the OS is working fine and I have no problems with installing software since I got onto Automatix 2.

But, both Beryl and Wine don't seem to work on the 64-bit version, no matter how much I try.

They installed fine. As for **Beryl, all the effects are on**. I even checked some forumsand added some efeects as recommended.
However, none of the effects seem to work!!!

I have a similar problem with Wine!!!

Urgent Help needed!!!

---

### Post by vishwas_s on 2007-06-28
Help!!! Anyone!!!!

---

### Post by Ayuthia on 2007-06-28
Do you have beryl-manager (you should see a gem on the panel)?  If so, is the desktop manager set to beryl?

---

### Post by vishwas_s on 2007-06-28
Yeah Ayuthia,
Aye Aye to both!!!

All the settings that I have enabled are on Beryl Settings Manager.

I just want to know whether this is some sort of compatibility issue with 64-bit Ubuntu, or is it some mistake on my part?

---

### Post by ruza on 2007-06-28
When you start Beryl what happens? Rihgt click on the red gem on the pannel and check wheather the window manager is set to beryl? Other than that maybe you should chek out [www.beryl-project.com](www.beryl-project.com). FAQ or wiki. . .

---

### Post by Mazza558 on 2007-06-28
Try and open beryl-manager from the terminal and tell us what errors appear.

---

### Post by vishwas_s on 2007-06-28
Hey,

Thanks!!!
Beryl finally worked!!! :D

It happened when I launched Beryl Manager from terminal... for some strange reason, I am not able to do the same on the screen!!!

**But I still have problems with WINE!!!!**


I am not able to run Wine or any Windows applications through Wine, from Terminal as well as the conventional way....

What could be the reason???

---

### Post by amaurynieto on 2007-06-28
Wine is not compatible with 64 bit as far as i know.

A.
Had the same trouble. You´ll notice automatix doesn't show it as an option either to install... that's why.

May I suggest Innotek Virtualbox for your windows needs? seamless compatibility since it's windows itself....

A.

---

### Post by vishwas_s on 2007-06-29
Actually, **I got Wine from Automatix 2**

I already have it installed, but not able to make it work!

As for VirtualBox, can I be assured that it is safe?

One other thing: It's just two days since I got onto the Ubuntu bandwagon and have a little problem
***Does Ubuntu have something similar to Windows Task Manager???***

My computer got hung today when I was on Ubuntu and didn't know what to do... was forced to press the off button on the CPU...

---

### Post by amaurynieto on 2007-07-13
Hi again. While Automatix 2 provides Wine, I believe it's a pain to get it installed. a lot of libraries and a lot of hassle to get it to work. I've personally been using Innotek Virtualbox and it works Absolutely wonderfully. I used Samba to configure a network so I could share files that I use from Windows XP inside Virtualbox to my Ubuntu Box. For example, I use Macromedia Dreamweaver, and I need to export the end product to a Linux based Folder so I can publish it. (I don't HAVE to, but I try to keep XP usage to a minimum). 

Innotek also works with Vista although the user agreement on Vista states you won't install on a VM (god knows why).

As for your question about the Task Manager, yes, if you right click on the top menu and select add application, you'll find one that says something along the lines of "performance indicator" or something like that, I don't remember the accurate phrasing. And when you double click on it, it'll show things like CPU usage, Memory usage, Swap File, Open applications, etcetera.  

- There's another way to get into it, and it's through the system menu, Preferences, I believe, or Administration, ( i'm not on my ubuntu box at the moment ) and you can launch it through there.

Quite useful to terminate unresponsive apps (Force Quit option). Although it happens very seldom.


Cheers and good luck to you. A.

---

