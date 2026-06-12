---
title: "Trying to install Bery and I get this"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Darth_Maul on 2007-06-21
~$ sudo apt-get install beryl-manger emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl-manger
-desktop:~$

---

### Post by franck3d on 2007-06-21
you have misspelled manager.
#-o
give it another try!

---

### Post by Darth_Maul on 2007-06-21
now I get this 
~$ sudo apt-get install beryl-manager beryl emerald-manager emerald
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package emerald-manager
-desktop:~$

---

### Post by Znupi on 2007-06-21
Well there is no package emerald-manager. Why should there be one?

---

### Post by EagleRock on 2007-06-21
You're thinking of emerald-themes.  Use that instead of emerald-manager.

---

### Post by corney91 on 2007-06-21
The package is emerald and emerald-themes

---

### Post by franck3d on 2007-06-21
try
sudo apt-get install beryl emerald-themes beryl-manager

this command is from  ubuntuguide.org - a great resource!


-I think what is happening is that you are asking apt to install packages that don't exist in the repository

---

### Post by ryanVickers on 2007-06-21
I just installed it from the Add/Remove thing in Applications!  the last time I used the terminal, it worked fine, but some things didn't work proporly, like there was no tilebar or sides to all the windows!

---

### Post by EagleRock on 2007-06-21
Ryan,

If you're using NVidia drivers, that could be the issue.  if you're getting black screens, that is definitely the issue.  There are plenty of threads about this issue, one of which is here:

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

I recommend right clicking the beryl-manager applet and selecting the following:

Advanced Beryl Settings > Rendering Path> Texture from Pixmap
Advanced Beryl Settings > Rendering Platform > Force AIGLX
Advanced Beryl Settings > Binding > XGL Binding

See if that resolves your issues.  If so, it's due to the NVidia bug.

Here's another thread about this:

[http://ubuntuforums.org/showthread.php?t=423861](http://ubuntuforums.org/showthread.php?t=423861)

---

