---
title: "screen resolution , and msn"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by ceezax on 2007-03-16
hi there 

i just want to edit my screen resolution but when i open it's tab i just find the 800*600

where i want to convert it to 1024*760 which wasn't listed in that tab 

so how can i accomplish that ???


secondly , i want to install msn messenger and yahoo messenger here , so how can i do

that ? and where i can find this dist??

3rd, i want to change the color of the terminal , i don't like that white one , so how can i edit it ??

---

### Post by Zzl1xndd on 2007-03-16
As for MSN i would say just using gaim is your best bet as it supports MSN, Yahoo, AIm and some others and it should be pre-installed

---

### Post by eljalill on 2007-03-16
You can change your screen resolution either in editing your xorg.conf (in /etc/X11/ ) or in doing this in a dialogue which will appear, when you type
sudo dpkg-reconfigure xserver-xorg .

The dialogue is rather legnthy, but doing the editing manually is not necessarily easier. You might chose to keep a backup of the xorg.conf in any case.

And gaim is what I would use, too.

---

### Post by ceezax on 2007-03-16
i still need to know how to change the resolution of my screen ???

---

### Post by Zzl1xndd on 2007-03-16
sudo dpkg-reconfigure xserver-xorg if you use this command in the terminal it will walk you threw setting up your video options and one section is what resolution are selectable. if you dont know the answer to some of the questions it asks just use the default but this will allow you to change the res.

---

### Post by ceezax on 2007-03-16
which command is used to edit ?? please explain in details , i am still junior

---

### Post by Zzl1xndd on 2007-03-16
sorry go to applications > Accessories > open the terminal then type it in. sometimes I forget when I was new.

---

### Post by ceezax on 2007-03-16
for now after i changed resolution through the dpkg-reconfigure command , i restarted the pc 

but for now it can't log into windows and prompt me for the command line and telling me that my vga driver can't stand 24 depth color , 

but what ever i used the dpkg-reconfigure again to change the depth , then i have tried all the options listed in the depth tab from 8 to 32 but none of them makes my windows startup ??????????

so what shall i do nooooooooooowww ??

---

