---
title: "im a linux newbie... i have a question... thank you ahead of time!"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by Mangledbmx on 2006-05-05
hello all. this is my first official post... woo hoo! anyway down to business

ok first question, how do i log on as root. the reason im asking is cause i want to get into the repositories but i cant seem to find it... i know i have to look in settings but i dont have it as an option... literally.. im using ubuntu 5.10 if that helps

any help would be greatly appreciated... thank you for your time

---

### Post by TheFourElements on 2006-05-05
on the command line type:

sudo su

and then enter you password at the prompt

---

### Post by nanotube on 2006-05-05
you don't need to log in as root to access the repositories. just open synaptic package manager (system>administration>synaptic), when it asks for password, enter your user password.

for more information about the ubuntu security model, check out
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Mangledbmx on 2006-05-05
well im sorry i guess i havent been very  clear.. im attempting to add a program to my computer. when i looked in the add programs section it said i had to add it in the  repositories section... but i cant find settings... or anywhere else that would have it. the only reason i asked about getting into root is cause i thought maybe thats why... im guessing i was wrong

---

### Post by aysiu on 2006-05-05
You don't need to log in as root.
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by nanotube on 2006-05-05
i think if you tell us what program you are trying to install, we can give you some specific instructions on how to do that. so... spill the beans, which program? :)

in general, about installing programs - you will find it helpful to check out the second link in my sig, about installing programs.

---

### Post by danielph on 2006-05-05
[QUOTE=Mangledbmx]i want to get into the repositories but i cant seem to find it[/QUOTE]System, Administrator, Synaptic Package Manager - start the program and type the password for your user account. This will give you root privilages for the program for the session. You will find repositories under Settings.

Or from a terminal (Applications, Accessories, Terminal)
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
sudo gedit /etc/apt/sources.list
```
This will create a backup file /etc/apt/sources.list.old and gedit will open an editor for the repositories list held in sources.list. The password for sudo is your password

Regards

Dan

---

### Post by Rinzwind on 2006-05-05
[QUOTE=danielph]System, Administrator, Synaptic Package Manager - start the program and type the password for your user account. This will give you root privilages for the program for the session. You will find repositories under Settings.

Regards

Dan[/QUOTE]
So true.

1 addition:
After you added new repositories update your package database with the button on the left.

---

### Post by Mangledbmx on 2006-05-05
thank you very much everyone i figured it out. i got power preferences downloaded and now i can tell how much battery is left on my laptop!

---

