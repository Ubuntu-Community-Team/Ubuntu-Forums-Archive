---
title: "No 3d acceleration"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Cherry1 on 2007-05-16
I am fairly new to Ubuntu itself, and hav never really used anything other than windows. But, I play World of Warcraft and did have it running fine using wine. I recently installed Beryl and after that i get a "could not start 3d acceleration" error. I updated wine to the latest version and that didnt resolve my issue. Im kinda stuck on what things i should llok for or even where to begin, other than having a current version of wine and the latest drivers for my graphics card. If it helps at all I ma using an Nvidia 6600GT. If anyone can help at all i would very much appreciate it.

---

### Post by blazercist on 2007-05-16
ok the problem is that beryl + 3d apps doesnt really work, you will have to install Xnest, sudo apt-get install Xnest and then use Xnest -display :0 wine wow.exe to run wow.

I'm not 100% sure that thats the correct syntax for Xnest, but its something liek that, theres an entry regarding xnest in the wine user wiki.

Edit:  I just found it for you

>  The application I am trying to run complains that it needs 256 colors but I have millions of colors.
Use Xnest. Once you have installed Xnest, you should be able to 

Xnest -display :1; env DISPLAY=:1 wine name_of_application 

If that doesn't work, try 

Xnest -display :1 -depth 8; env DISPLAY=:1 wine name_of_application 

If you have more than one display, or are using :1 for something already (e.g. vnc or another Xnest session), simply use :n, where n is any unused display number, in place of :1. 



Just use display :0 because i think beryl uses display :1

---

