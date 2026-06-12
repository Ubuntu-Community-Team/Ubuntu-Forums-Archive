---
title: "Arch linux"
date: 2008-05-05
forum: Arch and derivatives
---

### Post by vinceUUUU on 2008-05-05
Hello,

has anybody got Archie linux working?....it is a live distro CD

everytime i try the Archie HDD install script from the desktop....it fails. 

The script gives a gui tool within Archie.  (command line......arch-hdinstall)

The script seams to have a problem with the fact that my drive and partitions are mounted...

The gui HDD install tool asks me to unmount them...but i do not know how to un-mount them because Gparted does not offer the un-mount option...

Archie linux would be great if the HDD installer worked...

thanks

Vince

---

### Post by Trail on 2008-05-05
Are you actually booting the LiveCD or inserting it while running Ubuntu and running the installation script manually?

---

### Post by vinceUUUU on 2008-05-05
Hello

i am booting the live Archie CD...and it is clean hard drive here...nothing else around...

thanks

Vince.

---

### Post by vinceUUUU on 2008-05-05
Hello

can anybody help me to get Arch linux desktop working?

Arch installed correctly.

It runs.....and arrives at a prompt...i log in as root.

I installed the gui desktop called Afterstep..

-----------------------------------------------------------------

now i reboot...and arrive back at the command prompt

what commands will i need to enter to start up the desktop gui (Afterstep)?


xorg 
startx
afterstep

......maybe?

what list of commands will i need to start up my desktop gui?

thanks

Vince.

---

### Post by forumache on 2008-05-05
May I redirect you to Arch Linux forum at [http://bbs.archlinux.org/](http://bbs.archlinux.org/)

Although people familiar with Arch might exist on this forum (I am one of them), you'll have better luck on the Arch dedicated forum.

I posted the same message in the other thread you opened.

Best luck,
Dan.

---

### Post by forumache on 2008-05-05
May I redirect you to Arch Linux forum at [http://bbs.archlinux.org/](http://bbs.archlinux.org/)

Although people familiar with Arch might exist on this forum (I am one of them), you'll have better luck on the Arch dedicated forum.

I posted the same message in the other thread you opened.

Best luck,
Dan.

P.S. Have a look at [http://wiki.archlinux.org/index.php/Beginners_Guide#Part_III:_Installing_and_configuring_a_Desktop_Environment](http://wiki.archlinux.org/index.php/Beginners_Guide#Part_III:_Installing_and_configuring_a_Desktop_Environment)

---

### Post by K.Mandla on 2008-05-05
Moved waaaaay down to the Arch Linux subforum. Welcome to the laboratory, where all the cool stuff happens. 8)

P.S.: Similar threads merged.

---

### Post by finferflu on 2008-05-05
Vince, make sure you follow or give a very close look at the [Beginners Guide](http://wiki.archlinux.org/index.php/Beginners_Guide), that will safely lead you through all the steps you need, and provide you with all the essential information you need to know.

---

### Post by chucky chuckaluck on 2008-05-05
vince, it sounds like you took the path not taken. you can make a .xinitrc file and put *exec afterstep** in it, then *startx* will take you to afterstep.


*i actually don't know what exactly you'd enter for afterstep. usually, *exec whateverthenameofthewmis* will work, but sometimes, it's something like *startkde*, or *xfce4-session*.

---

