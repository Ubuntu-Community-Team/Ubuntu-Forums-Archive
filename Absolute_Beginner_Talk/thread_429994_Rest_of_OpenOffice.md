---
title: "Rest of OpenOffice"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-05-01
Hi,
Having used it before in Win, I know that OpenOffice.org includes a Math Component (for writing formulas). In 7.04 I have all the others, but cant locate Math. Any help?

---

### Post by starcraft.man on 2007-05-01
Hi, this is simple. Problem is that java isn't installed by default and so you don't get full functionality.

Run this command in terminal:

```
sudo aptitude install sun-java6-jre sun-java6-bin alien
```

You may need to change repositories to get java, I'm not sure. Guide for changing repos [here.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") This is feisty repos btw.

Then follow [this]("http://ubuntuforums.org/showthread.php?t=318865&page=6") guide. Just download 2.2 and substitute that in to any references to 2.1

---

### Post by Sef on 2007-05-01
The easy way for Feisty Fawn users to install java is with Add/Remove (Applications > Add/Remove.)

Add/Remove > All available applications > Search > Sun Java 6 > Click on Sun Java Web Start (The top one) > click apply > click apply again > follow directions to finish.

> You may need to change repositories to get java, I'm not sure. Guide for changing repos here. This is feisty repos btw.


Universe and Multiverse are open by default.

> Run this command in terminal:

Code:

sudo aptitude install sun-java6-jre sun-java6-bin alien



You should run ```
sudo aptitude update
``` first.

---

### Post by teddybairs1 on 2007-05-01
First of all, check to see if it's installed using Synaptic. Open up Synaptic by going to System --> Administration --> Synaptic package manager. enter your password. Search for "openoffice math" It should tell you if the package is in fact installed.

Next, use your file browser and point it to /usr/bin/ This is where all of your executables are located. the Math component for OpenOffice.org is /usr/bin/oomath. In order to launch it open up Terminal (Applications --> Accessories --> Terminal) and type:

sh /usr/bin/oomath

This should launch it.

As to why it's not loaded into the Menu along with the rest of the components I have no idea, but you can add it by opening up the menu editor. Right click on Applications and select edit menus. The rest of it should be self explanatory with a little but of experimentation. In general you would want to create a separate entry under Office. It will ask you for the name of the application and the command to launch it. The command to launch it is the same as what you would put into the Terminal (i.e. what i just gave you above). You can find an icon somewhere in your icons folder under /usr/share/icons or /usr/share/pixmaps.

if it doesn't launch it, let me know.

---

### Post by Nekiruhs on 2007-05-01
Thanks Teddybairs, that did the trick.

---

### Post by teddybairs1 on 2007-05-01
Ya Velcome.:)

---

