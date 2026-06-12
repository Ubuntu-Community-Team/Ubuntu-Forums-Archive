---
title: "network-manager icon disappeared"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by scotty2hotty on 2006-10-11
Hello to all, I just started using Ubuntu a few weeks ago, and I have managed to some how delete or hide my network-manager icon.  I have read other posts, but none have worked for my problem, ive tried going to the terminal and typing nm-applet and sudo nm-applet to no avail, also i have made sure there is a notification area, and i have made sure it is in the start up menu.  ive also tried installing and uninstalling network-manager many times, any help would be great! also, i can get on the internet, but i just like to see the pretty icon, and know EXACTLY when my internet gets connected. THANKS!

---

### Post by ASUmusicMAN on 2006-10-11
When you added the notification area did you try dragging around the divider it creates to make extra space?  Sometimes thats where my nm-applet goes whenever I mess around with the panels.

---

### Post by scotty2hotty on 2006-10-11
yes, i have tried moving the Notification Area divider around to, and still no icon. :(

---

### Post by PriceChild on 2006-10-11
Could you run
```
nm-applet
```in a terminal and paste any output it gives.

There could be important errors displayed which would be extremely useful :)

---

### Post by scotty2hotty on 2006-10-11
thanks for all the replies, and just to answer you before i give my solution, when i ran "nm-applet" or "sudo nm-applet" all it did was go down to the next line and keep blinking.

my solution: just by fooling around i managed to realize, when i was adding the notification area before, nothing was showing up, that was because for some reason, nm-applet was not started.  so i started nm-applet, and sure enough, the icon was back up. so the suggestions from other posts in the forum worked, i just didnt know there was a specific order in which you had to do them. thanks guys! very big help!

---

### Post by Fitzcarraldo on 2006-10-17
The Network Manager icon disappeared from my Panel too - I somehow managed to delete it when trying to move things around on the Panel.

In my case I just needed to right-click on the Panel, select 'Add to Panel', and then select 'Notification Area' (it's in the Utilities section in the 'Add to Panel' window). Voilà!

---

