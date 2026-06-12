---
title: "Going from User to root?"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by georgetoon on 2006-05-03
i did this once before, but forgot how I did it!

I want to edit the etc./fstab file.  I'm in User mode, so the file is locked.  How do I get into root privileges to edit this file?

---

### Post by kart3r on 2006-05-03
try this sudo <command>

---

### Post by ComplexNumber on 2006-05-03
go to the command line and type 'sudo nautilus', then enter your password.

---

### Post by georgetoon on 2006-05-03
[QUOTE=ComplexNumber]go to the command line and type 'sudo nautilus', then enter your password.[/QUOTE]

Thanks, I'll do that when I return home this evening.:)

---

### Post by aysiu on 2006-05-03
While *sudo nautilus* in particular may not harm your permissions, it's generally a good idea to get in the habit of using *gksudo* for graphical Gnome applications, *kdesu* for graphical KDE applications, and *sudo* for terminal commands.

For example: ```
sudo nano /etc/fstab
``` ```
gksudo gedit /etc/fstab
``` ```
kdesu kwrite /etc/fstab
```

---

### Post by georgetoon on 2006-05-03
[QUOTE=aysiu]While *sudo nautilus* in particular may not harm your permissions, it's generally a good idea to get in the habit of using *gksudo* for graphical Gnome applications, *kdesu* for graphical KDE applications, and *sudo* for terminal commands.

For example: ```
sudo nano /etc/fstab
``` ```
gksudo gedit /etc/fstab
``` ```
kdesu kwrite /etc/fstab
```[/QUOTE]

Thank you for this additional info.:) Gonna go with > gksudo gedit /etc/fstab

---

### Post by ComplexNumber on 2006-05-03
**georgetoon**
the reason why i put 'sudo naultilus' is just in case you need to edit more than one file. if you use sudo gedit (or gksudo as aysui more correctly points out), then you have to enter your password again for each file you want to edit. the root user privilages follow down throught down the chain. what i mean is, if you do sudo nautilus, when you then locate the file in question using nautilus and then open it using gedit or any other application, the root user privilages  are passed on to gedit etc. i just think that using gksudo nautilus is the more convenient way of going about things, thats all.

---

### Post by aysiu on 2006-05-03
No, I agree. ```
gksudo nautilus
``` is a handy thing. I was just recommending against ```
sudo nautilus
``` not against using Nautilus in lieu of Gedit.

---

### Post by georgetoon on 2006-05-03
Thanks so much, guys.:) Can hardly wait to get back home and give it a go.:)  Learning lots up here.:)

The two friendliest and helpful forums on the planet, IMHO, are Linspire and Ubuntu.:)

---

### Post by georgetoon on 2006-05-03
Okay, what I did this evening was just launch the terminal and type "sudo nautilus" and that launched my browser and put me in root. I then navigated to my file and was able to edit.:)

Seems easiest for me to understand this way.

---

### Post by aysiu on 2006-05-03
[QUOTE=georgetoon]Okay, what I did this evening was just launch the terminal and type "sudo nautilus" and that launched my browser and put me in root. I then navigated to my file and was able to edit.:)

Seems easiest for me to understand this way.[/QUOTE] Next time you do it, though, please type ```
gksudo nautilus
``` instead of just ```
sudo nautilus
```

---

### Post by georgetoon on 2006-05-04
[QUOTE=aysiu]Next time you do it, though, please type ```
gksudo nautilus
``` instead of just ```
sudo nautilus
```[/QUOTE]

Will do.:) Thank you.:)  

I really am enjoying learning all this despite my being a bit shy the first time around.:)

---

