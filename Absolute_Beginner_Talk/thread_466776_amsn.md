---
title: "amsn"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by dellboy on 2007-06-07
i have just add amsn to my computer and when i try to login it says this 

is say it need a SSL
and it comes up with a box of what verion of os i am usng so i cclick the 

Liunx-x86  but when i try to install it i get this message 

Erro adiing TL module:: Cant get http//swich.dll.sourcege.net ect ect 


dose any now how i can fix this so i can use amsn 


thank you

---

### Post by Najand on 2007-06-07
How did you try to install amsn?
Try enabling universe repository and try to install it using apt or synaptic.

---

### Post by dellboy on 2007-06-07
i set the permissions then ran the instiller 

was this the right thing to do

---

### Post by seshomaru samma on 2007-06-07
you should be able to install amns by pasting this command at the terminal:
```
sudo aptitude install amsn
```

---

### Post by chunchengch on 2007-06-07
1. Download [ATTACH]34617[/ATTACH] and then open terminal to enter following commands
2. $ [COLOR="Red"]tar xvzf tls-1.5.0-linux-x86.tar.gz[/COLOR]
3. $ [COLOR="Red"]sudo cp -f ~/tls1.50/* /usr/lib/tls1.50/[/COLOR]

start aMSN, it should work! 

If not, open file pkgIndex.tcl with following command

$ [COLOR="Red"]sudo gedit /usr/lib/tls1.50/pkgIndex.tcl[/COLOR]

and then replace text "**package ifneeded tls 1.5**" with "**package ifneeded tls 1.50**" (excluding "), save and exit, start aMSN to check.

---

### Post by dellboy on 2007-06-07
I think amsn instill probaly just when i try to login it ask me to pick a SSL

can any help me i been able to run it before i formate it so that ubuntu is my main os and xp has just a few Gs to run on 

thank you

---

### Post by dellboy on 2007-06-08
dose any one now what i need to do as i cant seem to run as it comes up with SSL 

please help

---

### Post by Xell Strider on 2007-06-13
Thanks Man! that worked fine.

---

