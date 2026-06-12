---
title: "apt-get doesnt work!"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by ChocoPanda on 2006-02-21
i tried using sudo apt-get install amarok, but it says : 

Reading package lists... Done
Building dependency tree... Done
Package amarok is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package amarok has no installation candidate

and i even tried to sudo apt-get install gstreamer0.8-plugins
but it says the same thing : 

Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate

is there something wrong with my terminal? i tried installing it from the original installation cd that came by mail, but it indicated that afew files were missing, some of them was that plugin... any idea how i can fix that?

please reply~~:confused:

---

### Post by dickohead on 2006-02-21
You need to uncomment the lines in the file: /etc/apt/sources.list, by doing this:
sudo vi /etc/apt/sources.list

then there will be lines that have a # in front of them (not the comments, leave them #'d, but with the repository lines), remove the # by pressing delete.

Then do: 
sudo apt-get update
sudo apt-get install amarok

---

### Post by m.musashi on 2006-02-21
My guess is you don't have the right repositories configured. There are probably ways to do that via the terminal and a file you can edit but I don't know those methods off hand. However, if you go into Synaptic (system-admin-synaptic) there is an option to configure repostitories. I personally just added all I could. That may or may not be good but it will probably get you want you want unless it's in a non-standard repository.

Sorry that's not overly helpful but maybe it will get you started.

Good luck.

---

### Post by Madpilot on 2006-02-21
[http://wiki.ubuntu.com/AddingRepositoriesHowto](http://wiki.ubuntu.com/AddingRepositoriesHowto) will take you through adding the extra repositories via Synaptic.

---

### Post by ChocoPanda on 2006-02-21
ah... re-installing ubuntu 4 times did the trick ;)
and that was befor i found out about the sources list too... it works like a charm now, thanks!

---

### Post by abhaysahai on 2006-02-22
re-install Ubuntu for getting amarok. :confused: 
This really made my day man. I never had so much fun on Ubuntu forums. 
:mrgreen:

---

### Post by ChocoPanda on 2006-02-23
hey, it's my job to make ppl happy :)

---

