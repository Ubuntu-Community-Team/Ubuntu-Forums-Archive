---
title: "Help installing, Lockup"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by voiceofxile on 2006-06-05
I'm new to the Linux world, but I am very excited by it. I can't get it to run though. I can get linux installed on it's own partition next to windows, and after I login the graphical based linux begins to load but locks up. I am sure it's a driver issue. I use an ATI All in Wonder x600 series card, with an ASUS SLI mobo, with the AMD FX-57 and a gig of RAM. What should I do?

---

### Post by joshrobinson on 2006-06-05
[QUOTE=voiceofxile]I'm new to the Linux world, but I am very excited by it. I can't get it to run though. I can get linux installed on it's own partition next to windows, and after I login the graphical based linux begins to load but locks up. I am sure it's a driver issue. I use an ATI All in Wonder x600 series card, with an ASUS SLI mobo, with the AMD FX-57 and a gig of RAM. What should I do?[/QUOTE]

you can try booting into recovery mode in the kernel list, and taking a look at your xorg.conf

once everything is up and your at a command prompt type the following

```
sudo nano /etc/X11/xorg.conf
```

look for the part that has your display driver, it will probibly say ati, or radeon
try typing vesa as your driver, save the file with cntrl o hit enter then exit with cntrl x

then at the command prompt type exit or sudo reboot, and see if it lets you into it fine then.. just remeber what driver was in the part you change, so you can go back if vesa doesnt work or the problem is worse

---

### Post by voiceofxile on 2006-06-05
Thank you for your prompt responce to my question. I will do what you said and get back with the details. I have been trying to figure this out for a couple months on my own, but linux is just so different from evil windows. Since I hand built my box, maybe my parts just arent compatable. I'll be back soon.

---

### Post by voiceofxile on 2006-06-05
ok, I tried what you said and that sudo nano /ect/xll/xorg.conf is blank.   When I am at the login screen it freezez up and I have to restart my computer. Can you tell this newbie how to download and install the drivers I need in the text based linux? I really am out of ideas. Thank you for your time.

---

