---
title: "Which key to select in installer"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by Earthling on 2005-09-27
I am sooo embarassed to be asking this dumb question.
When installing ubuntu I am presented with the opportunity to slect which resolutions to use. Can I find the key to do the selection? Nope!
I scrolled down the list and three resolutions are marked are marked with a * but neither my asterisk key (shift 8) nor the one on the numerical keypad will put an asterisk in the the set of brackets
[*]
I have now reinstalled Ubuntu (breezy) three times as I don't know how to change this without manually editing the configuration file (don't want to do that *choke*)
Can someone help me get a higher res than 1024? without having to reinstall the whole thing.
I don't mind reinstalling if someone will just tell me which key to use to do the select/deselect in the installer....frustraton has a new name...me!
thanks.

---

### Post by Perfect Storm on 2005-09-27
It's the space key :)

There aren't stupid questions, only stupid answers ^^

---

### Post by Earthling on 2005-09-27
Thanks, it worked (of course):D

---

### Post by Perfect Storm on 2005-09-27
My pleasure ^^

---

### Post by Earthling on 2005-09-27
Hmm,
Now I have the problem that the 1600x1200 is too big for the display. I guess I will have to adjust the mode lines (?) Any ideas how to find out how those modelines can e discovered. I basically need everything to shrink down in size. At the moment half the screen is missing and in order to see it I have to move the pointer to the edge of the screen and the whole desktop scolls until the edges come into view
Any help gratefully received.....

---

### Post by Perfect Storm on 2005-09-28
Sysytem ---> Preferences ---> Screen Resolution

If it doesn't help
Do you have your monitor specs? If not Do you know what's the name of your monitor?
Also please post your xorg.conf file.

gedit /etc/X11/xorg.conf

---

