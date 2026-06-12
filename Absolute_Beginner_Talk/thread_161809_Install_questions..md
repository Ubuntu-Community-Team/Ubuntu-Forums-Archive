---
title: "Install questions."
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by hhandy on 2006-04-17
I'm new to Linux and I'm trying the Ubuntu live cd distro. I want to change the screen resolution from 600X800 to 1024X768 so that the screen will fit my display. I can't change it, I've tried but to no avail.
Also Ubuntu does  not see my HP3745 printer. How do I add it?
Help!!!!
Thanks, hhandy

---

### Post by wolfee on 2006-04-17
I'm using the installed version of Ubuntu so I'm not sure what options the live cd 
gives you but try clicking on 'system' then 'prefrences' then 'screen resolution'
From there you will see a tab called'Resolution' click on the little arrow on the right of it. If it does not give you anymore options higher than 800*600 your video card may not be recognized

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=wolfee]I'm using the installed version of Ubuntu so I'm not sure what options the live cd 
gives you but try clicking on 'system' then 'prefrences' then 'screen resolution'
From there you will see a tab called'Resolution' click on the little arrow on the right of it. If it does not give you anymore options higher than 800*600 your video card may not be recognized[/QUOTE]
Here is how to fix the screen res problem. In terminal type:


> sudo dpkg-reconfigure xserver-xorg

Then procede to answer the questions, it will basically pick the best things. When you get to the part that says "What resolutions would you like X to use ?" Uncheck the 3 at the bottom (using the space bar) and put a * in the box of the resolution that you want to use. Only select the one that you are going to use.

Then restart X when done. CTRL+ALT+X. It should work in the live cd.

---

### Post by hhandy on 2006-04-23
I've tried the suggestions from wolfee and MasterChief but to no avail. When I enter the command "sudo dpkg-reconfigure xserver-org" I don't think it's getting saved and the restart of X doesn't work. I enter CTRL+ALT+X and nothing happens. 
Also I can't print. I have a HP 3745 printer but I can't get the system to see it.
What am I doing wrong?
Thanks, hhandy

---

### Post by xXx 0wn3d xXx on 2006-04-23
[QUOTE=hhandy]I've tried the suggestions from wolfee and MasterChief but to no avail. When I enter the command "sudo dpkg-reconfigure xserver-org" I don't think it's getting saved and the restart of X doesn't work. I enter CTRL+ALT+X and nothing happens. 
Also I can't print. I have a HP 3745 printer but I can't get the system to see it.
What am I doing wrong?
Thanks, hhandy[/QUOTE]
Try using CTRL+ALT+Backspace to restart X.

---

### Post by Nikusan on 2006-04-23
[QUOTE=hhandy]I've tried the suggestions from wolfee and MasterChief but to no avail. When I enter the command "sudo dpkg-reconfigure xserver-org" I don't think it's getting saved and the restart of X doesn't work. I enter CTRL+ALT+X and nothing happens. 
Also I can't print. I have a HP 3745 printer but I can't get the system to see it.
What am I doing wrong?
Thanks, hhandy[/QUOTE]

Try Using the System -> Administration -> Printing menu to add a new printer. Follow the wizard to choose your printer model and it will recommend a driver. After that you should be able to print.

---

### Post by hhandy on 2006-04-28
Well everything is OK now. I switch to a 17 Viewsonic LCD monitor with 1280X1024 resolution and my monitor problems in Ubuntu just went away. I was able to get my printer to print also. Everthing seems to be working fine now.
What information would you recomend to learn UbuntU (KNome) OS?
Thanks, handy.

---

