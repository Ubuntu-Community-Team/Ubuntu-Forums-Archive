---
title: "Display went black"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by Abu Imak on 2006-03-31
Hi guys, I'm new to linux and Ubuntu and I've run into a snag.

My computer is an old pentium 2 (350mhz) and until yesterday, gnome was working just fine, but yesterday i decided to change the resolution because the text was really small, i used to have a resolution of 800 x 600 on that computer when it used to run windows98 so i decided to allow it to have the same setting on gnome. For some reason, by default, the resolution was 
1600x1200 and so everything looked small. When i changed the resolution to 800x600 everything was larger, however, when i restarted the computer, i would get to the logon screen, i would login, and then it would take me to a black screen, where all i could see is my mouse pointer. i can't right click or left click. I tried failsafe gnome and it had the same effect, the only thing that works is failsafe terminal. Does anyone have any idea how to change my resolution using the terminal? Is my assumption that the resolution is to blame is right? any help would be greatly appreciated.

---

### Post by dermotti on 2006-03-31
**sudo dpkg-reconfigure xserver-xorg ** should work

---

### Post by Abu Imak on 2006-03-31
thanks for the reply, but that didnt work, i like reconfigured the video settings, i tried like simple setups but it doesnt work, i still get the login screen but when i try to use gnome it craps out

---

### Post by dermotti on 2006-03-31
Try creating a new user and logging in as that user. Maybe you screwed something up on the user you usally login as.

---

