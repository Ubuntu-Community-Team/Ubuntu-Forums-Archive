---
title: "how can i add a menu item for gparted? it's already installed in my gutsy.10 build?"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-11-17
i'm familiar with the menu editor, but i can't seem to put in an item for gparted? the gnome partition manager is already installed as default with my gutsy 7.10 build, but i can't see it listed as an available program for the menu, when i run the command 'parted' or 'gparted' from the alt-f2 start screen i get no results. what the heck?

---

### Post by perfektion on 2007-11-17
<delete post>

---

### Post by perfektion on 2007-11-17
<delete post>

---

### Post by rsambuca on 2007-11-17
It sounds like it isn't installed.  Open a terminal (Applications -> Accessories -> Terminal) and enter```
sudo apt-get install gparted
```

---

### Post by Inxsible on 2007-11-17
After you install it like rsambuca suggests, you will probably find it under System>>Administration>>GParted

---

### Post by abulfares on 2007-11-17
actually, it is under System>Administration>Partition Editor

---

### Post by ijason on 2007-11-17
> jason@jason-laptop:~$ sudo apt-get install gparted
[sudo] password for jason:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gparted has no installation candidate
jason@jason-laptop:~$ 

?? do i need to enable my global respos or something?

---

### Post by Inxsible on 2007-11-17
> **ijason said:**
> ?? do i need to enable my global respos or something?Thats strange. I see it in synaptic. Try to install it thru synaptic. I dont think its in the universe or multiverse. but have those enabled just in case

---

### Post by ijason on 2007-11-17
when i search synaptic for gparted, it shows no results. i just went through and confirmed it's searching all available repos. weird.

it says that i have version 1.7.1-5 of GNUparted already installed, but running 'parted' or 'gparted' from the alt-f2 window does nothing.

---

### Post by rsambuca on 2007-11-17
Post the output of 

cat /etc/apt/sources.list

---

### Post by ijason on 2007-11-17
@ rsam : ah. i see it's #'d out all my deb sources. think that's me problem? :)

---

### Post by ijason on 2007-11-17
@ rsam : is there a way for it to re-learn that list instead of me having to manually edit it?

---

### Post by Inxsible on 2007-11-17
> **ijason said:**
> @ rsam : is there a way for it to re-learn that list instead of me having to manually edit it?
never mind

---

### Post by rsambuca on 2007-11-17
Probably the best way to fix it is to go to "System - Administration - Software Sources".  Click the "Download from:" button and select "Other".  Then press the "Select Best Server" button.  It will test every mirror and pick out the quickest current one.

---

### Post by Inxsible on 2007-11-17
> **ijason said:**
> @ rsam : ah. i see it's #'d out all my deb sources. think that's me problem? :)

/do you mean they are all commented out ?

---

### Post by rsambuca on 2007-11-17
> **Inxsible said:**
> ```
sudo apt-get update && sudo apt-get upgrade
```

???  That won't do it.

---

### Post by rsambuca on 2007-11-17
> **Inxsible said:**
> /do you mean they are all commented out ?

Whoa, Inxsible!  Slow down buddy!!  You're typing your (incorrect) responses too quickly again without reading everything.

---

### Post by ijason on 2007-11-17
@ rsam : ah! great... thank goodness for automation :) yeah, i noticed a weird failure to reach security updates message in the midst of my install. which, is weird, because it hadn't yet given me a chance to enter the pass phrase to connect to the local wifi. i guess it up and decided to just # everything out.

---

### Post by Inxsible on 2007-11-17
> **rsambuca said:**
> Whoa, Inxsible!  Slow down buddy!!  You're typing your (incorrect) responses too quickly again without reading everything.
He mentioned they were #'d out. I am asking him if he means they are commented. 

I don't see anything wrong with trying to clarify something.

---

### Post by ijason on 2007-11-17
it's no problem guys :) yes, they were commented out by the installer. the fix to refresh the update server worked and it just dumped about 85 updates,  and now when i search synaptic for gparted it shows up as available but uninstalled. 

so this should fix everything :)

---

### Post by ijason on 2007-11-17
great! gparted installed and now shows up right where i expected it to. i guess the gnome partition utility (that i couldn't make run) is the one the installer uses to set up the disks?

thanks for the advice! i'm sure those depos being commented out would have bitten me in the butt really soon, anyways.

---

### Post by daimaru on 2007-11-17
deleted cause i did not read post right :)

---

