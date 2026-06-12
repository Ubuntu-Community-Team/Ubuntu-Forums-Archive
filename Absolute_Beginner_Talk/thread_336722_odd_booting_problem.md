---
title: "odd booting problem"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by ecovillain on 2007-01-12
hello everyone!

i just installed kubuntu 6.10 standard on my dads old sharp UM30 last night, after much trouble. well, most things work okay now, but i do have a strange problem that occurs as the computer boots. 

after turning on the computer, the bios performs its checks and then GRUB loads. kubuntu loads immediately after, but instead of the familiar outpouring of information that i have observed on past computers as they loaded linux, my screen stays blank, with only a rapidly blinking cursor at the top of the screen. after three or so minutes, the kubuntu splash screen appears, i can login, and everything is fine, kde is there, everything works, etc. the same sort of thing happens at shutdown-- i select shutdown from the menu, everything disappears, i ger some random colors on the screen for a few moments, and the there is the same blank screen with flashing cursor for about a minute or so as everything seems to be shutting down, and then the computer turns off. 

any idea whats going on?  thanks

Tosten

---

### Post by sardion on 2007-01-12
Something is wrong with the usplash then... (k)ubuntu displays a nice splash screen instead of a console full of text for bootup.  But in your case, something has gone wrong.  My best guess is that you need to pass a kernel parameter to set the screen up correctly for the console.

Can you post the details about your graphics card and what xorg driver you are using for video?

This is most likely a bug in usplash.

---

### Post by ecovillain on 2007-01-12
my laptop has intel 82830M (i830) integrated onboard graphics. i dont know how to find out about xorg.....where would that information be located?  also driver information...where would i find that?

thanks for your patience....im really new to this linux thing.

---

