---
title: "Cd not working cant  install ubuntu desktop"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-03-27
hi all

install ubuntu 6.10 on my laptop something went wrong. it didnt install the GUI. i typed :```
sudo aptitude install ubuntu-desktop
```
it asks me to put the cd in the cd drive butt my cd drive is ^$(&*($ so i cant.

Q. How can i do it over the internet.

ta,
nolander

---

### Post by seshomaru samma on 2007-03-27
How come it didnt install the GUI?

anyway , if you want to install without the use of CD
then:
```
sudo gedit /etc/apt/sources.list
```
this will open a file with all the sources apt installs from 
the first one should be your ubuntu cd , cancell it by putting a # at the beggining of the line
save it and then
```
sudo apt-get update
```
then install ubuntu-desktop

---

### Post by Nolander on 2007-03-27
i cant use the gedit command

---

### Post by kittyhawk63 on 2007-03-27
> **Nolander said:**
> i cant use the gedit command
try gksudo gedit ... instead of sudo gedit.

---

### Post by Nolander on 2007-03-27
gksudo command not found

---

### Post by kittyhawk63 on 2007-03-27
> **Nolander said:**
> gksudo command not found

You should be able to type: 

gksudo gedit /etc/apt/sources.list

in _terminal_. I just did it and it works. Terminal is located under Applications->Accessories->Terminal.

You should then get a pop up asking for your password. Enter your password and hit <enter>. A page showing the sources list will soon appear.
kh

---

### Post by Nolander on 2007-03-27
i \m trying to install GUI.
its just text a the moment

---

### Post by kittyhawk63 on 2007-03-27
If you have a scrolling wheel on your mouse, highlight the line and start terminal and press the wheel. It will paste the line for you, Hit enter.

Edit: GUI is over my head. I'm fairly new to Linux. Did you check Google?

---

### Post by kittyhawk63 on 2007-03-27
[quote=Nolander;2359881]hi all

install ubuntu 6.10 on my laptop something went wrong. it didnt install the GUI. i typed :```
sudo aptitude install ubuntu-desktop
```it asks me to put the cd in the cd drive butt my cd drive is ^$(&*($ so i cant.
Q. How can i do it over the internet.

Is this an Ubuntu CD that you made? If it is, how fast did you burn the ISO to CD? If you burned it faster than 4X, you may have problems getting the ISO data properly burned.

---

### Post by seshomaru samma on 2007-03-27
my mistake - gedit is part of the GUI , i think

try nano instead of gedit

---

### Post by Nolander on 2007-03-27
nope,

nano dont work.

thanx for all your help,
nolander

---

### Post by seshomaru samma on 2007-03-27
I think your installation is not complete
I would advice you to install again ,except that if your CD is not working properly it would be difficult.
If you are on a network you can try a network install - I never tried it with Ubuntu but it's possible in Fedora Linux . You can also install from a FAT32 partition (possible with Suse Linux at least)

---

### Post by Nolander on 2007-03-28
all fixed

cd was stuffed

thanx all,
nolander.

---

