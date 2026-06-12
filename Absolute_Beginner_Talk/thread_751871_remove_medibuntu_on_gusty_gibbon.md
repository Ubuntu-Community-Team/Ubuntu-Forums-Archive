---
title: "remove medibuntu on gusty gibbon"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by davarse on 2008-04-11
hi,,,, is anyone know how to completely remove medibuntu from gusty gibbon???
cheers'

---

### Post by FuturePilot on 2008-04-11
Do you mean the Medibuntu repositories?

---

### Post by davarse on 2008-04-11
yup

---

### Post by kesman on 2008-04-11
System -> administration -> software sources

But why would you want to do this?

---

### Post by Weidbrewer on 2008-04-11
> **kesman said:**
> System -> administration -> software sources

But why would you want to do this?

This question echos in my head as well.

---

### Post by davarse on 2008-04-12
i've got an error messege and i couldn't use the add/remove program, the synaptic packages manager or update manager anymore.... i got the error messege:
 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  
E: _cache->open() failed, please report.

i've tried to remove it before but the error still like that..
what should i do to fix it???
it there any way to reinstall medibuntu???

cheers'

---

### Post by ramjet_1953 on 2008-04-12
OK, the answer isn't removing the medibuntu repository.

Open a terminal and copy and paste this into it:

[COLOR="Red"]sudo dpkg --configure -a[/COLOR]

Now check to see if this has cured the problem.

If not, it's time for 'Plan B'

What is the name of the package that you are trying to install?

Again open a terminal and type this in:[COLOR="Blue"] gksu nautilus[/COLOR]

When nautilus opens in sudo mode navigate to [COLOR="Blue"]/var/lib/dpkg/status[/COLOR]

Right click on this file and open in text editor.

look for the section describing your errant package.

Very carefully delete the lines relating to this package and save the file.

Re-boot and the problem should be gone.

As a backup measure, I would save a copy of your original /var/lib/dpkg/status file before making any changes.

Regards,
Roger :cool:

---

### Post by david_kt on 2008-04-12
> **davarse said:**
> i've got an error messege and i couldn't use the add/remove program, the synaptic packages manager or update manager anymore.... i got the error messege:
 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  
E: _cache->open() failed, please report.

i've tried to remove it before but the error still like that..
what should i do to fix it???
it there any way to reinstall medibuntu???

cheers'

Have you tried to do as suggested? Open terminal, and type below:

```
sudo dpkg --configure -a
```

Type password as requested.

DK

---

### Post by davarse on 2008-04-12
i've tried sudo dpkg --configure -a in terminal, but i got messege:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

from update manager....
i type it in terminal but nothing happened, just like normal, and it doesn't ask for my password as usual...

any idea????

cheers'

---

### Post by davarse on 2008-04-12
i got this messege from ternimal:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

any idea???

---

### Post by david_kt on 2008-04-12
> **davarse said:**
> i got this messege from ternimal:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

any idea???

You should close synaptic before run dpkg or pat-get in terminal. If the problem still persist after you close synaptic, restart your computer and try again (the terminal).

Have you tried:
```
sudo apt-get install -f
```

in terminal?

DK

---

