---
title: "Problem with update manager"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Kunks on 2008-03-30
After using update manager I got this error message(see attached screen shot)
update manager says my system is up to date but when I click on check it shows that downloads were apparently interrupted & the error box comes up. I don't use the terminal much so I would need step by step instructions as I assume I will need to use the terminal for corrective measures
Toshiba a105 s-1014 laptop
Dual boot xp/ubuntu gutsy 7.10

---

### Post by kellemes on 2008-03-30
Open terminal and start typing..

```
sudo dpkg --configure -a
```

---

### Post by Michael.Godawski on 2008-03-30
open up the terminal
application > accessories > terminal
and run the command

```
sudo dpkg --configure -a
```
hit enter and type in your password
the password won't be displayed just type it in and hit enter

any error messages?

---

### Post by Kunks on 2008-03-30
I think that fixed it no more error message but when I click on check box it shows(see screenshot)  downloading files box but does not ask me to install them- download box closes quickly & it says system up to date..???? it seems the files are downloaded but not installed????

---

### Post by lswest on 2008-03-30
you can force it from the terminal with ```
sudo apt-get update && sudo apt-get upgrade -y
``` otherwise the files were installed when you ran the dpkg command.

the command downloads the list of packages, checks for new versions, then installs all updates while assuming "y" (yes) to all queries

---

### Post by Kunks on 2008-03-30
here is screen shot...sorry

---

### Post by Michael.Godawski on 2008-03-30
if the update manager says the system is up to date then the system should be up to date

---

### Post by Kunks on 2008-03-30
thanks both of you for all your help

---

### Post by lswest on 2008-03-30
yeah, looks to me like the updates were installed at the same time as you ran dpkg --configure -a

---

