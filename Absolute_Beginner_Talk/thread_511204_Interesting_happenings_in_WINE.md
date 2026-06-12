---
title: "Interesting happenings in WINE"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by andyho on 2007-07-27
[COLOR="DarkRed"]There's a program I am using in WINE that I use for my job. In a sense I guess it is almost like an IM client. A customer "calls" me and I accept the session. All is good and the program works until the customer disconnects. Then it's like WINE "dumps" it?!? Is there a way to tell it to stay "connected"? They're actually working on a Linux development of it so hopefully that'll be out soon! The other thing is I removed a program, but it's still showing up in my program list, but if I go into winecfg it's not there? Thanks for any advice!! :) [/COLOR]

---

### Post by Jose Consuervo on 2007-07-27
When you say that the program that you removed stil shows up in your program list, do you mean there is a link for the executable that still exists, or that it is in youre winecfg executable list. And also when you said you removed it, did you use the uninstaller, or did you just delete the files?

---

### Post by andyho on 2007-07-27
It's the link for the executable.. Wine>Programs>program.. I used the uninstaller to get rid of it and it isn't showing in the winecfg list. :confused:

---

### Post by Jose Consuervo on 2007-08-06
Okay, I believe that the location of all of the links on the menu are located at /usr/share/applications/  and there should be the link to the program that you want to be gone. It will be named the same name as the program.

---

