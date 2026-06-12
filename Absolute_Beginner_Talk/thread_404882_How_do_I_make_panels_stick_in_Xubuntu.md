---
title: "How do I make panels stick in Xubuntu?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2007-04-09
the default xfce4-panel doesnt stick when I restart my computer, so I downloaded the gnome-panels, I like them alot better, but they also dont appear when I reboot. Anyone have any advice on how to keep them up always? Starting to get a bit tedious to open up a term and 'gnome panel' then hope I dont forget to accidentally close the active term and close out my panels :P

---

### Post by darkrose on 2007-04-09
Just putting the command for your panels in /home/yourname/.xinitrc should do the trick. If the file doesn't exist then make a text file with the command in it, and save as /home/yourname/.xinitrc

When X starts it will check this file to see if there are any commands to run when bringing up the gui. So reboot and you should have your panels.

---

