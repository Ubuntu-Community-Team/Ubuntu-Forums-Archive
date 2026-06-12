---
title: "[SOLVED] why do i have to remove ubuntu desktop"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by brokenhachi on 2008-02-11
as i understand this thread [http://ubuntuforums.org/showthread.php?t=378140&page=2](http://ubuntuforums.org/showthread.php?t=378140&page=2) uninstalling ubuntu-desktop doesnt do anything, but i dont understand why i have to unistall it just to get rid of "kine" and "calculator...


is there any way i can get someone to elaborate on this...?

---

### Post by aeiah on 2008-02-11
ubuntu-desktop is a metapackage. its a list of packages, basically. the list isnt complete if you remove those two packages, so you also remove the list (but not all the packages in the list, obviously, just the two you dont want).

---

### Post by forestpixie on 2008-02-11
you're not actually uninstalling it as I understand it, you just don't have it anymore

ubuntu-desktop is a metapackage which consists of all the packages - when you remove one you no longer have the metapackage - you just have what's left, if you wanted to have ubuntu-desktop again - installing it would only install the bits that are missing

if you had a car and took a seat out you'd still have a car - but a slightly different one - if you put the seat back you have the same car again

---

### Post by Keith Hedger on 2008-02-11
Ubuntu-desktop is a meta package and as such does not contain any files it is used to bring in all the progs etc for a complete desktop via its dependencies , It shouldn't do any harm to remove it (mine has been removed) but make sure you back up all your important files first (just in case!)

---

### Post by brokenhachi on 2008-02-11
ok, the car example worked alot better with me than the beer one.. heh. 

thanks guys.


so im actually not uninstalling anything other than say kine, serpentine, and calculator. its just im letting the update service know that i dont have the full ubuntu-desktop by removing the marker "ubuntu-desktop"


am i right?

---

### Post by tangibleorange on 2008-02-11
That is correct.

---

### Post by brokenhachi on 2008-02-11
werd. thanks home-skillet-s

time to go delete some gomi programs.

---

