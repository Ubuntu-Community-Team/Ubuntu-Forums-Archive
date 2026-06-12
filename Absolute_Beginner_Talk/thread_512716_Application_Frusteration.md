---
title: "Application Frusteration"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-07-29
I just installed Wine Doors to install some Windows Applications on my Linux.

I tried to install Paint Shop Pro, but it isn't working.

I also can't uninstall it. What should I do?

Also a in general question.

Where in the system are applications installed?

Also with the ability to run .exe files can't I get viruses now?

---

### Post by sailor2001 on 2007-07-29
your apps are mostly in the usr/bin file...  places/computer/files   there was a tutorial posted in the forums that explains what goes where in the file system.....quite interesting, but lost the url     not to worry about viruses, but if paranoid you can download clamav

---

### Post by Cheese Roller on 2007-07-29
Okay, I give up on Wine.

How do I uninstall it?

Also, when I uninstall it, does that mean that all the Windows programs I have installed right now will go away too?

Some of them are NOT showing on the Uninstall List...

---

### Post by asmoore82 on 2007-07-29
WINE, along with almost 100% of all other Linux Applications, stores its settings for your User
in your home folder in a "hidden" file/directory called a "dot" file (its name begins with '.')

in the case of WINE, the directory is $HOME/.wine and holds a fake C: drive along with the master WINE registry... fooling around with info hidden in here is the real way to make WINE stand up and dance.

To complete your removal of WINE do a Complete Removal of WINE in synaptic AND
delete your .wine folder.

---

### Post by yogo on 2007-07-29
I just got Wine going yesterday, I will keep it, it is good for running many programs, especially small .exe programs.

I just go to program files in Windows and right click the .exe, it gives an option to run with Wine.

I am assuming that you may not have your Windows programs installed but if you do, it works good that way.

---

### Post by Cheese Roller on 2007-07-29
I turned on view hidden files, I did not see any folder like that.

---

### Post by Cheese Roller on 2007-07-29
bump

---

### Post by yogo on 2007-07-29
> **Cheese Roller said:**
> I turned on view hidden files, I did not see any folder like that.

I have the computer icon on my desktop, from there I navigate to where my hard drive is that windows resides in, to program files and to what program I want to use, I right click on the .exe and choose run with Wine.

HTH

---

