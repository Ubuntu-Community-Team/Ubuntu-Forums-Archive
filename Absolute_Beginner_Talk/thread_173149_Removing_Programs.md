---
title: "Removing Programs"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-05-09
If I want to get  all traces of a program, it's directories and subfiles, and all supporting programs/data/files (I mean completely erase everything), what commands would I have to use?

---

### Post by ComplexNumber on 2006-05-09
depends what program. some programs can leave traces in the /var directory and others even after the application is uninstalled. there will usually be some directory thats created in your home directory that keeps the settings for that particular application. i don't know what package manager you're using, but sometimes theres a facility to see exactly what files were installed. you could go onto the command line and enter 'dpkg <whatever option> <application name>'(i'm sorry, but i'm not at all familiar with dpkg or debian systems, so someone else will have to help you here), and that will list all the files that were installed with that application. most of these will be uninstalled, but some may remain for one reason or another (for example, if the application creates an initial empty database  in /var. the database entries will NOT be removed after the application is uninstalled).
thats if you want to be absolutely and totally thorough in the removal of a package. usually, its jsut a case of using whatever packager manager application (eg synaptic, Smart, whatever) you're using to uninstall everything(or almost everything) that was installed with that package.

---

### Post by Guns90 on 2006-05-09
I tried (unsuccessfully) to install wine earlier today. Following the HOWTO Setup Wine steps, everything seemed to work alright after I did the install; however, when I shut the computer down and came back later, I was getting  'fix me....." remaarks in the command line window. I tried to remove everything and start over, but I guess that I'm leaving stuff in because when I get to a place where it says to enter 'cd winetools*' followed by the 'sudo ./install', I get ' You already installed winetools. remove the earlier installation and then come back.' Any suggestions?

I used sudo rm -f wine
           sudo rm -f winetools
           sudo dpkg -r wine
           sudo dpkg -r winetools
           sudo dpkg -P wine
           sudo dpkg -P winetools

---

### Post by ComplexNumber on 2006-05-09
> Any suggestions?
other than the above, no. maybe someone whos had (recent) experience with installing and/or uninstalling wine can help you further. i tried it a few years back....but memories fade....

---

